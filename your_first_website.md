# Your First Website
![website](https://res.cloudinary.com/btvca/image/upload/v1601489831/webdesign-3411373_1280_hiakqt.jpg)

## Overview
Having answered the question, "what is HTML?" as well as having discussed the general anatomy of what an HTML element *looks* like, it's time to address these things in a more specific context! HTML is a crucial building block when designing websites, so that is the scope in which we will be discussing HTML for this lesson. 

When getting your first site up and running, there are a few higher-structure elements and concepts you need to know that, one way or another, have to be included in order to make a site work as intended. They provide the browser with information unique to the page, like:

- What character set is being used to encode the HTML - What text you'd like to have display on the tab in your browser
- What stylesheet(s) you'd like to use to style your page 
- What scripts(s) you'd like to run on your page
- What content you'd like to appear on the page

This lesson covers:


## Basic HTML document layout

Let's start as we normally do, with a simple example: 

![website_example](https://res.cloudinary.com/btvca/image/upload/v1601560981/website_example_nn3frg.png)

This HTML will render in the browser like so:

![website_rendered](https://res.cloudinary.com/btvca/image/upload/v1601560981/website_rendered_golyfn.png)

> Not the fanciest, of course, because it has not been styled yet. And it won't be for now, as this lesson doesn't cover styling with CSS! Just keep in mind that HTML is only 1 piece of the puzzle responsible for dynamic and engaging websites (the other pieces being CSS and JavaScript.)

Now, let's break this HTML down into its smaller points. We'll cover everything you see above, top to bottom.

## `<!DOCTYPE html>`
This is legacy code from a bygone era known only as *the 1990s*. Essentially DOCTYPE, short for *document type*, was used to link a ruleset for the document to be viewed through, like a critical lens of sorts. Now, it is included as `<!DOCTYPE html>` to bypass that old system. All that's needed to know about it is that **it is required** for your document to be considered valid HTML. Put it before everything else. 

## `<html></html>`
The `<html>` element is the highest-level element that all other contents of the document are *nested* within. Sometimes referred to as the *root element*, it is the element that the browser looks inside of to render a page. Put this immediately after `<DOCTYPE html>`.

## `<head></head>`
The `<head>` element is where all of the site's information that does NOT show up on the page lives. This content will NOT show up on the page, but rather provides crucial information for how the page will work overall. This information is called **metadata**.  The head element expects many different elements to be nested within it. 

In the above example, there are three elements nested within the `<head>` element: `<title></title> ` and *two* `<meta></meta>` elements. 

### `<title></title>`

The `<title>` element assigns the name of the website for SEO and readability. it is also determines what text will display on that page's tab in our browser. In our example, the text "Document" will display on a tab. 

### `<meta></meta>`
The `<meta></meta>` element is redundantly named. It is another element that exists as a child to the `<head></head>` element that contains *additional* metadata. There is a lot that can go into these, but currently, the only information being provided is what character set the document will be read with (`charset`), and the `viewport` in which it will be viewed in. `viewport` is a valid value for the `name` attribute, just as the value proived to `content` is. 


The `<head></head>` element can include many other elements as children (nested elements), such as `<link>` and `<script>`.

### `<link></link>`
This will be covered more in depth next week when we discuss styling your site (adding color, orienting your elements, adding animations, etc.) but for now, the most important thing to know is that it exists, and takes 2 attributes: `href` and `rel`. 

`href` is the path (think url or filepath) of the file to be used as a styling guide. 

`rel` is an attribute that defines type of file being linked to. In many cases, the value will be "stylesheet".  [Full list](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/rel)


It looks something like this:
```
<link rel="stylesheet" href="style.css">
```

### `<script></script>`
This will be covered more in depth in your final week of prework, but it is effectively the JavaScript alternative to the `<link>` element. It is used to either point towards a script to execute, or include the code itself within the tags that will be run when the page loads. Again, more on that later.


For a full list of elements and attributes, pay a quick visit to the [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/head#See_also ).

## `<body></body>`

This is where the rubber meets the road! And where the elements we've already touched upon live. All of the content that you want the user to see will live inside of this element. Headers, footers, lists, images, videos, music, paragraphs, you name it. It all lives here. 

**There can be only one `<body></body>` element in any given HTML document.**

In the body of our example, we see a number of elements, some old and some new. Let's review/introduce them!

###  `h1`-`h6` 
These elements are used to denote section headings. `h1`, as seen, is the largest of the options. `h2`,`h3`, `h4`, `h5` and `h6` get incrementally smaller.  

They have no unique attributes.

In this case, the `h1` is immediately followed with an `h4`, a smaller version. Both are *block level* elements.

### `<img>
The `<img>` element is used to embed an image into the HTML document. It requires a `src` attribute, which needs the path to the image you want to include. 

It is also HIGHLY encouraged to provide an `alt` attribute, which is a *text description* of the image. This is important for accessibility, particularly the visually impaired. Those using screen readers will benefit highly from a proper description of the image.

`height` and `width` may also be directly scaled here, like so:

```
height="100px" width="100px"
```
Play around with it below!

<p class="codepen" data-height="320" data-theme-id="dark" data-default-tab="result" data-user="burlingtoncodeacademy" data-slug-hash="WNwqEbZ" data-editable="true" style="height: 320px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="&amp;lt;img&amp;gt; exercise">
  <span>See the Pen <a href="https://codepen.io/burlingtoncodeacademy/pen/WNwqEbZ">
  &lt;img&gt; exercise</a> by Burlington Code Academy (<a href="https://codepen.io/burlingtoncodeacademy">@burlingtoncodeacademy</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

> **Note** The `<img>` element is SELF-CLOSING, meaning there is no `</img>` closing tag to denote the end of the element. All defining characteristics of this element are provided as attributes and as such there is no *content* to exist within the opening and closing tags. 


### `p` - paragraph 
The `<p>` element represents a paragraph. It is block-level, and has no unique attributes.

### `a` - anchor 
We touched briefly upon *anchor tags* last lesson, and they have the potential for complexity, so we'll keep this one brief.

Anchor tags have an `href` attribute which, like `<link>` elements, take a URL that the hyperlink points to. The link itself is the *content* inside of the opening and closing tags. 

### <blockquote>
`<blockquote>` elements are meant to emphasize certain text the particular way shown. They come with default indentation.

### `<button>`
Like anchor tags, `<button>` elements style the content in a certain, interactive way. Buttons, however, need more customization in order to actually **do** anything noteworthy. This is accomplished through running additional code snippets. We will discuss these more when learning how JavaScript is used in the browser.


And that's it! There's your first website! Let's recap:

- `<!DOCTYPE html>` is required (legacy) element
- `<html></html>` is where ALL of the code lives within. 
- `<head></head>` is where the *metadata* lives, which is all information that the site might need that will not be visibile to the user. This includes titles, and links to stylesheets and scripts (code that will be executed)
- `<body></body>` is where visible content lives.



Make a "website" in the code sandbox below that has the following: 

- An `h1` element with an `h4` directly underneath it.
- A `<p>` element with a few words about why you're interested in HTML!
- An `<img>` element with a picture of your choosing!


Note there is no `<head>`, as that metadata has been taken care of by codepen. Treat the "HTML" area as the `<body></body>` element! 

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="html,result" data-user="burlingtoncodeacademy" data-slug-hash="bGpPYop" data-editable="true" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Your first website">
  <span>See the Pen <a href="https://codepen.io/burlingtoncodeacademy/pen/bGpPYop">
  Your first website</a> by Burlington Code Academy (<a href="https://codepen.io/burlingtoncodeacademy">@burlingtoncodeacademy</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>