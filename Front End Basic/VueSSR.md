## Vue Server Side Render

#### Requirements

`vue`,`vue-server-render`, `express`(not required but used in this example)

`vue` and `vue-server-render` must have matching versions.

#### Rendering A Vue Instance

###### Step 1 - Create A vue Instance

```js
const Vue = require('vue')
const app = new Vue({
    template: `<div>Hello World</div>`
})
```

###### Step 2 - Create A Renderer

```js
const renderer = require('vue-server-renderer').createRenderer()
```

###### Step 3 - Render The Vue Instance To HTML

```js
renderer.renderToString(app, (err, html) => {
    if (err) throw err
    console.log(html)
    // html => <div data-server-rendered="true">Hello World</div>
})
```

In 2.5.0+, returns a Promise if no callback is passed

```js
renderer.renderToString(app)
    .then(html => {
        console.log(html)
    })
    .catch(err => {
        console.log(err)
    })
```

#### Integrating With A Server

server.js

```js
const Vue = require('vue')
const server = require('express')()
// step 2
const renderer = require('vue-server-renderer').createRenderer()

server.get('*', (req, res) => {
    // step 1
    const app = new Vue({
        data: {
            url: req.url
        },
        template: `<div>The visited URL is: {{ url }}</div>`
    })
    
    // step 3
    renderer.renderToString(app)
        .then(html => {
            res.end(`
                <!DOCTYPE html>
                <html lang="en">
                    <head><title>Hello</title></head>
                    <body>${html}</body>
                </html>
            `)
        })
        .then(err => {
            res.status(500).end('Internal Server Error')
        })
})
```

You can now start server with `node server.js`

#### Using A Page Template

Create new file `index.template.html`

```html
<!DOCTYPE html>
<html lang="en">
    <head><title>Hello</title></head>
    <body>
        <!--vue-ssr-outlet--> // where app's markup will be injected
    </body>
</html>
```

Edit `server.js`

```js
const renderer = createRenderer({
    template: require('fs').readFileSync('./index.template.html', 'utf-8')
})

renderer.renderToString(app)
    .then(html => {
        res.end(html)
    })
```

###### Template Interpolation

Edit `index.template.html`

```html
<html>
    <head>
        <!-- use double mustache for HTML-escaped interpolation -->
        <title>{{ title }}</title>
        
        <!-- use triple mustache for non-HTML-escaped interpolation -->
        {{{ meta }}}
    </head>
    <body>
        <!--vue-ssr-outlet-->
    </body>
</html>
```

Edit `server.js`, add context to renderer

```js
const context = {
    title: 'Hello',
    meta: `
        <meta ...>
        <meta ...>
    `
}

renderer.renderToString(app, context)
    .then(html => {
        res.end(html) // title will be 
    })
```

#### Universal Code

Universal code referres to code that runs on both the server and the client.

###### Data Reactivity On The Server

In a client-only app, every user will be using a fresh instance of the app in their browser. For server-side rendering we want the same behaviour, each request should have a fresh, isolated app instance so that there is no cross-reques state pollution.

Because the actual rendering process needs to be deterministic, we will also be "pre-fetching" data on the server - this means our application state will be already resolved when we start rendering. This means data data reactivity is unnecessary on the server, so it is disabled by default. Disabling data reactivity also avoids the performance cost of converting data into reactivity objects.

##### Component Lifecycle Hooks

Since there are no dynamic updates, only `beforeCreate` and `created` will be called during SSR. Other lifecycle hooks such as `beforeMount` or `mounted` will only be executed on the client.

Another thing to note is that you should avoid code that produces global side effects in `beforeCreate` and `created`, for example setting up timers with `setInterval`. In client-side only we may clear interval in `beforeDestroy` or `destroyed`, however these codes are not called during SSR and stay around forever. To avoid this, move side-effect code into `beforeMount` or `mounted`.

###### Access To Platform-Specific APIs

Universal code cannot assume access to platform-specific APIs such as `window` or `document`, executing in Node.js will throw errors.

For tasks shared between server and client but use different platform APIs, it's recommended to wrap the platform-specific implementations inside a univeral API, or use libraries that do this for you. For example `axios` is an HTTP client that exposes the same API for both server and client.

For browser-only APIs, the common approach is to lazily access them inside client-only lifecycle hooks.

Note if a 3rd party library is not written with univeral usage in mind, it could be tricky to integrate it into an server-rendered app. You _might_ be able to get it working by mocking some of the globals, but it would be hacky and may interfere with the environment deetction code of other libraries.

###### Custom Directives

Most custom directives directly manipulate the DOM, and therefore will cause error during SSR. There are two ways to work around this:

1. Prefer using components as abstraction mechanism and work at the Virtual-DOM level (e.g. using render functions) instead.

2. If you have a custom directive that cannot be easily replaced by components, you can provide a "server-side version" of it using the `directives` option when creating the server render.

#### Source Code Structure

###### Avoid Stateful Singletons

Unlike client-only code, Node.js server is a long-running process, when code is required into the process, it will be evaluated once and stays in memory, this means singleton object is shared between every incoming request.

So instead of directly creating an app instance, we should expose a factory function that can be repeatedly executed to create fresh app instances for each request

Create new file `app.js`

```js
const Vue = require('vue')

module.exports = function createApp(context) {
    return new Vue({
        data: {
            url: context.url
        },
        template: `<div>The visited URL is {{ url }}</div>`
    })
}
```

Edit `server.js`

```js
const createApp = require('./app')

server.get('*', (req, res) => {
    const context = { url: req.url }
    const app = createApp(context)
    
    renderer.renderToString(app)
        .then(html => {
            res.end(html)
        })
})
```

The same rule applies to router, store and event bus instances as well. Instead of exporting it directly from a module and importing it across your app, you need to create a fresh instance in `createApp` and inject it from the root Vue instance.

Note this constraint can be eliminated when using the bundle renderer with `{ runInNewContext: true }`, however it comes with some significant performance cost because a new vm context needs to be created for each request.

###### Code Structure With Webpack

Assume we are using webpack to process the app for both server and client already, the majority of our source code can be written in a universal fashion, with access to all the webpack-powered features. At the same time, there are a number of things you should keep in mind when writing universal code.

```
src
├── components
│   ├── Foo.vue
│   ├── Bar.vue
│   └── Baz.vue
├── App.vue
├── app.js # universal entry
├── entry-client.js # runs in browser only
└── entry-server.js # runs on server only
```

`app.js`

Note the responsibility for mounting directly to DOM is moved to client-only entry file for SSR.

```js
import Vue for 'vue'
import App from './App.vue'

// export a factory function for creating fresh app, router and store instances
export function createApp() {
    const app = new Vue({
        // the root instance simply renders the App component
        render: h => h(App)
    })
    return { app }
}
```

`entry-client.js`

The client entry simply creates the app and mounts it to the DOM

```js
import { createApp } from './app'
// client-specific bootstrapping logic...
const { app } = createdApp()

// this assumes App.vue template root element has `id="app"`
app.$mount('#app')
```

`entry-server.js`

The server entry uses a default export which is a function that can be called repeatedly for each render.

At this moment, it doesn't do much other than creating and returning the app instance - but later we will perform server-side route matching and data pre-fetching logic here.

```js
import { createApp } from './app'

export default context => {
    const { app } = createApp()
    return app
}
```

###### Routing with `vue-router`

Currently our server code uses a `*` handler which accepts arbitrary URLs. This allows us to pass the visited URL into our Vue app, and reuse the same routing config for both client and server.

It is recommended to use the official `vue-router` for this purpose. 

Create a file where we create the router, similar to `createApp`, we also need a fresh router instance for each request.

router.js

```js
import Vue from 'vue'
import Router from 'vue-router'

Vue.use(Router)

export function createRouter() {
    return new Router({
        mode: 'history',
        routes: [
            // ...routes
        ]
    })
}
```

Edit app.js

```js
import Vue from 'vue'
import App from './App.vue'
import { createRouter } from './router'

export function createApp() {
    // create router instance
    const router = createRouter()
    
    const app = new Vue({
        // inject under into root Vue instance
        router,
        render: h => h(App)
    })
    
    // return both the app and the router
    return { app, router }
}
```

Edit entry-server.js with routing logic

```js
import { createApp } from './app'

export default context = {
    // since there could potentially be asynchronous route hooks or components, we will be returning a Promise so that the server can wait until everything is ready before rendering
    return new Promise((resolve, reject) => {
        const { app, router } = createApp()
        
        // set server-side router's location
        router.push(context.url)
        
        // wait until router has resolved possible async components and hooks
        router.onReady(() => {
            const matchedComponents = router.getMatchedComponents()
            // no matched routes, reject with 404
            if (!matchedComponents.length) {
                return reject({ code: 404 })
            }
            
            // the Promise should resolve to the app instance so it can be rendered
            resolve(app)
        }, reject)
    })
}
```

server.js

Assuming the server bundle is already built (ignoring build setup for now), the server usage would look like this

```js
const createApp = require('/path/to/built-server-bundle.js')

server.get('*', (req, res) => {
    const context = { url: req.url }
    
    createApp(context)
        .then(app => {
            renderer.renderToString(app)
                .then(html => {
                    res.end(html)
                })
                .catch(err => {
                    if (err.code === 404) {
                        res.status(404).end('Page not found')
                    } else {
                        res.status(500).end('Internal Server Error')
                    }
                })
        })
})
```


