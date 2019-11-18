## HTML5 Tags

A collection of current HTML5 tags, obsolete or removed tags are not encluded.

Information are from [here](https://developer.mozilla.org/en-US/docs/Web/HTML).

**`<a>` - Anchor Element**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a)

> A hyperlink to web pages, files, email addresses, locations in the same page, or anything a URL can address.
> 
> **Attributes**
> 
> - `download`
>   
>   Prompts user to save linked URL instead of navigating to it.
>   
>   Filename will be value passed.
>   
>   If no value is passed browser will suggest a filename/extension.
> 
> - `href`
>   
>   URL pointing to, not necessarily HTTP-based.
> 
> - `hreflang`
>   
>   Hints at the human language of linked URL.
>   
>   Allowed values are same as [the global `lang` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/lang)
> 
> - `ping`
>   
>   List of URLs separated by space, brower will send `POST` request with body `PING` to each URL.
>   
>   Typically for tracking.
> 
> - `referrerpolicy`
>   
>   How much of the referrer to send when following the link.
>   
>   See [`Referrer-Policy`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referrer-Policy) for possible values and their effects.
> 
> - `rel`
>   
>   The relationship between current document and linked URL as space-separated [link types](https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types).
>   
>   Note: search engine may use this attribute to get more information about this link.
> 
> - `target`
>   
>   Where to display the linked URL, as the name for a browsing context (a tab, window, or `<iframe>`)
>   
>   The following keywords have special meanings for where to load the URL:
>   
>   - `_self`: the current browsing context. **(Default)**
>   
>   - `_blank`: usually a new tab, but users can configure browser to open a new window instead.
>   
>   - `_parent`: the parent browsing context of the current one. If no parent, behaves as `_self`.
>   
>   - `_top`: the topmost browsing context (the "highest" context that's an ancestor of the current one). If not acestors, behaves as `_self`.
>   
>   Note: it might not be very obvious what `_parent` and `_top` does, they are usually used with nested `iframe`. If you're not passing in a keyword (ie. target="test"), URL will be displayed in `<iframe name="test"></iframe>`.
> 
> - `type`
>   
>   Hints at the linked URL's format with a [MIME type](https://developer.mozilla.org/en-US/docs/Glossary/MIME_type). No built-in functionality.

**`<abbr>` - Abbreviation**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/abbr)

> Represents an abbreviation or acronym.
> 
> **Attributes**
> 
> - `title`
>   
>   Must contain a full human-readable description of expansion of the abbreviation.

**`<address>` - Address**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/address)

> Indicates the enclosed HTML provides contact information for a person/people/organization.
> 
> **Attributes**
> 
> Global attributes only.

**`<area>` - Area**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/area)

> Defines a hot-spot region on an image.
> 
> Must be used within a **`<map>`** element.
> 
> **Attributes**
> 
> - `alt`
>   
>   Text to display when image is unavailable.
> 
> - `coords`
>   
>   Coordinates of the hot-spot region to display.
>   
>   Number and meaning of values depend on the value of **shape** attribute
>   
>   - `rect` or rectangle: the value is `left,top,right,bottom`, 
>   
>   - `circle`: the value is `x,y,r` where `x,y` is a pair specifying the center of the circle and `r` is the value of the radius.
>   
>   - `poly` or polygon: the value is a set of `x,y` pairs for each point in the polygon: `x1, y1,x2,y2,x3,y3,...`
>   
>   In HTML4 values are numbers of pixels or percentages (if % is appended).
>   
>   In HTML5 the values are values of CSS pixels.
> 
> - `download`
>   
>   Prompts user to save linked URL instead of navigating to it.
>   
>   Filename will be value passed.
>   
>   If no value is passed browser will suggest a filename/extension.
> 
> - `href`
>   
>   URL pointing to, not necessarily HTTP-based.
> 
> - `hreflang`
>   
>   Hints at the human language of linked URL.
>   
>   Allowed values are same as [the global `lang` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/lang)
> 
> - `ping`
>   
>   List of URLs separated by space, brower will send `POST` request with body `PING` to each URL.
>   
>   Typically for tracking.
> 
> - `referrerpolicy`
>   
>   How much of the referrer to send when following the link.
>   
>   See [`Referrer-Policy`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referrer-Policy) for possible values and their effects.
> 
> - `rel`
>   
>   The relationship between current document and linked URL as space-separated [link types](https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types).
>   
>   Note: search engine may use this attribute to get more information about this link.
> 
> - `target`
>   
>   Where to display the linked URL, as the name for a browsing context (a tab, window, or `<iframe>`)
>   
>   The following keywords have special meanings for where to load the URL:
>   
>   - `_self`: the current browsing context. **(Default)**
>   
>   - `_blank`: usually a new tab, but users can configure browser to open a new window instead.
>   
>   - `_parent`: the parent browsing context of the current one. If no parent, behaves as `_self`.
>   
>   - `_top`: the topmost browsing context (the "highest" context that's an ancestor of the current one). If not acestors, behaves as `_self`.
>   
>   Note: it might not be very obvious what `_parent` and `_top` does, they are usually used with nested `iframe`. If you're not passing in a keyword (ie. target="test"), URL will be displayed in `<iframe name="test"></iframe>`.
> 
> - `shape`
>   
>   Shape of hot spot.
>   
>   - `rect`: a rectangular region.
>   
>   - `circle`: a circular region.
>   
>   - `poly`: a polygon.

**`<article>` - Article**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/article)

> Represents a self-contained composition in a document, page, application, or site, which is intended to be idependently distributable or reusable.
> 
> Example: a forum post, a magazine or newspapaer article, or a blog entry.
> 
> A document may have multiple articles, for example, on a blog that shows the text of each article one afer another as the reader scrolls, each post would be contained in an `<article>` element, possibly one or more `<sections>` within.
> 
> **Attributes**
> 
> Global attributes only.
> 
> **Usage**
> 
> - Each `<article>` should be identified, typically by including a heading `<h1>`-`<h6>` element as a child of the `<article>` element.
> 
> - When `<article>` elements are nested, the inner element represents an article related to the outer element. For example, the comments of a post can be `<article>` elements nested in the `<article>` representing the post.
> 
> - Auther information of an `<article>` element can be provided through the `<address>` element.
> 
> - The publication date and time of an `<article>` element can be described using the `datetime` attribute of a `<time>` element.

**`<aside>` - Aside**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/aside)

> Represents a portion of a document whose content is only indirectly related to the document's main content.
> 
> **Attributes**
> 
> Global attributes only.
> 
> **Usage**
> 
> - Do not use the `<aside>` element to tag parenthesized text, this kind of text is considered part of the main flow.

**`<audio>` - Audio**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio)

> Used to embed sound content in documents. May contain one or more audio sources, represented using the `src` attribute or `<source>` element, the browser will choose the most suitable one. It can also be the destination for streamed media using a `MediaStream`.
> 
> **Attributes**
> 
> - `autoplay`
>   
>   A Boolean attribute, if true audio will play  automatically as soon as it can do so, without waiting for the netire audio file to finish downloading.
> 
> - `controls`
>   
>   Allows user to control audio playback if present, including volume, seeking, pause/resume playback.
> 
> - `crossorigin`
>   
>   Indicates whether to use CORS to fetch the related audio file. CORS-enabled resources can be reused in the `<canvas>` element without being tainted.
>   
>   - `anonymous`
>     
>     Sends a cross-origin request without a credential. Sends the `Origin:` HTTP header without a cookie, X.509 certificate, or performing HTTP Basic authentication.
>   
>   - `use-credentials`
>     
>     Sends a cross-origin request with a credential. Sends the `Origin:` HTTP header with a cookie, a certificate, or performing HTTP Basic authentication.
>   
>   If the server does not give credentials to the origin site (by note setting the `Access-Control-Allow-Origin:` HTTP header), the image will be tainted, and its usage restricted.
> 
> - `currentTime`
>   
>   A double-precision floating-point value indicating the current playback position, in seconds, of the audio.
>   
>   If audio is streamed and setting `currentTime` to a data already expired from the media buffer will cause fail.
> 
> - `duration`(Read only)
>   
>   A double-precision floating-point value which indicates the duration (total lenth) of the audio in seconds. If no media is present on the element, or the media is not valid, the returned value is `NaN`.
> 
> - `loop`
>   
>   A Boolean attribute, if specified the audio player will automatically seek back to the start upon reaching the end of the audio.
> 
> - `muted`
>   
>   A Boolean attribute, if specified the audio will be initially silenced.
> 
> - `preload`
>   
>   - `none`: Audio should not be preloaded.
>   
>   - `metadata`: Only audio metadata (e.g. length) is preloaded.
>   
>   - `auto`: Whole audio file is preloaded, even if the user is not expected to use it.
> 
> - `src`
>   
>   URL of the audio embed, may instead use `<source>` element.

**`<b>` - Bring Attention To**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/b)

> Used to draw the reader's attention to the element's content.
> 
> **Attributes**
> 
> Global attributes only.
> 
> **Usage**
> 
> - Used to indicate keywords in a summary, product names in a review, or other spans of text whose typical presentation would be boldfaced (but not including any special importance).
> 
> - Do not confuse `<b>` with `<strong>`, `<em>`, or `<mark>` elements. `<strong>` element represents text of certain importance, `<em>` puts some emphasis on the text and the `<mark>` element represents text of certain relevance. `<b>` element doesn't convey such special semantic information, use it only when no others fit.
> 
> - Do not mark titles and headings using the `<b>` elements. Use `<h1>`-`<h6>` tags.
> 
> - It's a good practice to add `class` attribute to `<b>` element in order to convey additional semantic information as needed. This makes it easier to manage multiple use cases of `<b>` if your stylistic needs change.

**`<base>` - Document Base URL**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/base)

> Specifies the base URL to use for all relative URLs in the document.
> 
> There can be only one `<base>` element in a document.
> 
> The used base URL of a document can be accessed from scripts with `document.baseURI`. If no `<base>` element then it defauts to `document.location.href`.
> 
> **Attributes**
> 
> - `href`
>   
>   The base URL to be used throughout the document for relative URLs. Absolute and relative URLs allowed.
> 
> - `target`
>   
>   A keyword or auther-defined name of the default browsing context to display the result when links or forms cause navigation.
>   
>   The following keywords have special meanings for where to load the URL:
>   
>   - `_self`: the current browsing context. **(Default)**
>   
>   - `_blank`: usually a new tab, but users can configure browser to open a new window instead.
>   
>   - `_parent`: the parent browsing context of the current one. If no parent, behaves as `_self`.
>   
>   - `_top`: the topmost browsing context (the "highest" context that's an ancestor of the current one). If not acestors, behaves as `_self`.
> 
> **Usage**
> 
> - Should be used before other elements with attributes whose values are URLs, such as `<link>`'s `href` atribute.
> 
> - If multiple `<base>` elements are used, only the first `href` and first `target` are obeyed, all others are ignored.

**`<bdi>` - Bidirectional Isolate**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/bdi)

> Tells the browser's bidirectional algorithm to treat the text it conatins in isolation from its surrounding text. It's particularly useful when a website dynamically inserts some text and doesn't know the directionality.
> 
> **Attributes**
> 
> Global attributes only.

**`<bdo>` - Bidirectional Text Override**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/bdo)

> Overrides the current directionality of text, so that the text within is rendered in a different direction.
> 
> **Attributes**
> 
> - `dir`
>   
>   The direction in which text should be rendered in this element's contents. Possible values are:
>   
>   - `ltr`: left-to-right direction.
>   
>   - `rtl`: right-to-left direction.

**`<blockquote>` - Block Quotation**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote)

> Indicates the enclosed text is an extended quotation. Usually this is rendered visually by indentation. An URL for the source of the quotation may be given using the `cite` attribute, while a text representation of the source can be given using the `<cite>` element.
> 
> **Attributes**
> 
> - `cite`
>   
>   A URL that designates a source document or message for the information quoted. This attribute is intended to point to information explaining the context or the reference for the quote.
> 
> **Usage**
> 
> To change the indentation applied to the quoted text, use the CSS `margin-left` and/or `margin-right` properties, or the `margin` shorthand property.
> 
> To include short quotes inline rather than in a separate block, use the `<q>` element.

**`<body>` - Document Body**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/body)

> Content of an HTML document. There can be only one `<body>` element in a document.
> 
> **Attributes**
> 
> - `onafterprint`
>   
>   Function to call after the user has printed the document
> 
> - `onbeforeprint`
>   
>   Function to call when the user requests printing of the document
> 
> - `onbeforeunload`
>   
>   Function to call when the document is about to unloaded
> 
> - `onblur`
>   
>   Function to call when the document loses focus
> 
> - `onerror`
>   
>   Function to call when the document fails to load properly
> 
> - `onfocus`
>   
>   Function to call when the document receives focus
> 
> - `onhashchange`
>   
>   Function to call when fragment identifier part (starting with the has `#` character) of the document's current address has changed
> 
> - `onload`
>   
>   Function to call when the document has finished loading
> 
> - `onmessage`
>   
>   Function to call when the document has received a message
> 
> - `onoffline`
>   
>   Function to call when network communication has failed
> 
> - `ononline`
>   
>   Function to call when network communication has been restored
> 
> - `onpopstate`
>   
>   Function to call when the user has navigated session history
> 
> - `onredo`
>   
>   Function to call when the user has moved forward in undo transaction history
> 
> - `onresize`
>   
>   Function to call when the document has been resized
> 
> - `onstorage`
>   
>   Function to call when the storage area has chagned
> 
> - `onundo`
>   
>   Function to call when the user has moved backward in undo transaction history
> 
> - `onunload`
>   
>   Function to call when the document is going away

**`<br>` - Line Break**, [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/br)

> Produces a line break in text (carriage-return). Useful for writing a poem or address, where the division of lines is significant.
> 
> **Attributes**
> 
> Global attributes only.
