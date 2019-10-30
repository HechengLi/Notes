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


