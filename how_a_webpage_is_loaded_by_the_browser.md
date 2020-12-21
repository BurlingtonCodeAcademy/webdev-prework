## How a webpage is loaded by a browser

<a style={{color:"blue"}} href="https://forum.burlingtoncodeacademy.com/t/week-2-how-a-webpage-is-loaded-by-a-browser/274">Discuss in Forum</a>

![blueprint](https://res.cloudinary.com/btvca/image/upload/v1601924324/architecture-1857175_1280_qv4kbl.jpg)

Designing a web page is a thorough process. Every `<link>` or `<script>` element, every video or image or piece of audio is loaded into your page based relative to the document's flow. Depending on how you have laid out your HTML, your page may perform differently than you might anticipate. In the following lesson, we will discuss the fundamentals of how a page is loaded and executed. Try not to get too bogged down with the provided information; this is meant as an introduction to some helpful concepts that could assist you in the future.



## From Top to Bottom
HTML is, by default, parsed from top to bottom. When a browser properly requests a webpage, (ie. a user navigates to a valid address), the corresponding HTML document is sent back to the browser and parsed. As things are interpreted by our browser, the page begins to load and render the information it has found. You'll typically see this effects immediately, as the HTML is read, styles are applied to it, and the scripts that give it functionality are run. 

Let's take a look at our site from the previous lesson:

![HTML EXAMPLE WITH LINKS AND SCRIPTS](https://res.cloudinary.com/btvca/image/upload/v1601929002/html_example_with_link_u7h2qv.png)

As we have covered, the *metadata* of a webpage is contained in the `<head>` element. It contains all of the information that the user won't implicity see on the page as content, but instead informs the behavior of the page and resources needed to make it function as intended. So, going from top to bottom, the order of operations is as follows:

1) The language is expected to be english, due to the `lang="en"` attribute on the containing `<html>` element. 

2) The character set is defined as `UTF-8` in a self-closing `<meta>` tag. `UTF-8` is a highly dynamic and backwards compatible character encoding. It is BY FAR the most common encoding.

3) The `name` and `content` values are provided in a second self-closing `<meta>` tag that dictate how the page will be rendered in terms of width, height, and zoom level.

4) the `<title>` element determines what will be displayed in its browser tab or title bar.

5) **This is where things start to get interesting.** a `<link>` tag is provided with a link to a `css` stylesheet. This is not something that your HTML document knows how to immediately parse. Rather, it follows the `href` provided, to retrieve the intended resource from elsewhere.
    - When a `<link>` is provided, a request is made to get that information, but:
    - The browser does not wait for that request to finish.
    - When it is loaded, it is applied. 

6) The `<body>` element is parsed, starting with the `h1` and `h4` tags.

7) When we get to the `<img>` tag, a request for that image is made, much like the one made for the `stylesheet` in step 5. 
    - When it is loaded, it is rendered.

8) The remaining elements in the `<body>` are parsed and loaded, until:

9) **This is where The `<script>` tag is encountered.** A `<script>` is known as a **blocking** resource, which means that any `<script>` tags encountered are, by default immediately requested and executed. 
    - It is good practice to provide any JavaScript you want to use on your page as the *last* thing in your `<body>`.
    - Scripts can be added anywhere, but in doing so, you are pausing the browser process.


## Implications
![person with question mark over their face](https://res.cloudinary.com/btvca/image/upload/v1601995612/question-2736480_1280_ehfg5n.jpg)
As you may have noticed, most of the browser's processes are triggered on a first-come-first-serve basis. This allows, for the most part, things in the browser to become immediately available once the request for additional resources have been processed. Additional assets will be applied as soon as possible, cutting down on the time required for content to appear in the browser.

Most things are loaded and applied in this manner namely for the sake of browser performance. If every aspect of the document has to be completely loaded and applied before the next, performance would drag considerably. These *asynchronous* requests allow for information to trickle in at its own rate, which helps consolidate the codependent nature of resources on the page. Scripts, however, are mostly functional in uses, so the need to "drop everything" to execute the provided script is frequently necessary and expected.

And what if you need a bit of JavaScript to run before the page loads? Say you're using an external JavaScript library, or incorporating some code that is needed *BEFORE* the page is loaded. `<script>` tags are welcome in the `<head>` as well. Given their nature, they will prevent the HTML from being parsed until it the encountered script is loaded and run. In some cases, this is necessary for the page to work as a whole. In others, it can be a hindrance that pauses the flow of information being read.

## `async` and `defer`
If the `<script>` in question is not one that needs to be loaded in a particular order, you can see to it that they are loaded like stylesheets and additional assets are. This can be done through the `async` and `defer` attributes.

### `defer`
The `defer` attribute, when added to a script, looks like this:

```html
<script defer src="./script.js">
```
where `src` is wherever the script in question resides, either internally like shown or externally at a separate url altogether.

`defer` tells the browser to continue processing the HTML and building the webpage regardless of whether or not the encountered script has been loaded yet. **When the page is loaded, the script will run**. This is essentially the same as adding your script to the bottom of the `<body>`. 

The other important aspect of `defer` comes when utilizing it in multiple `<script>` elements. When more than one script has been set to `defer`, **all scripts with `defer` as an attribute will execute consecutively.**

```html
<script defer src="./script1.js">
<script defer src="./script2.js">
<script defer src="./script3.js">
```

When the page has been loaded completely, these scripts will then run in order.

### async 
`async`, short for *asynchronous*, is simliar to `defer` but with a little less predictability. Like `defer`, it is used to make a script non-blocking. But, unlike `defer`, **`async` makes a script load and run independent of all other things happening in the browser.**

Instead, it will begin loading when encountered, and run immediately when loaded, regardless of the state the browser currently finds itself in. If there are multiple `<script>` tags with the `async` attribute, they will all run on a first-loaded basis, regardless of which one began loading first.

```html
<script async src="./longScript.js">
<script async src="./shortScript.js">
```
When the page is loaded, chances are that `shortScript.js` will run before `longScript.js`, simply because it is smaller and will be loaded first, regardless of which began loading first. This is useful when working with scripts that won't affect other things on the page (think adds, or counters).

## Final Takeaways
Hopefully some of the concepts addressed have helped you understand what happens when your browser attempts to load a page. 

- HTML is read top-to-bottom
- All assets like images, videos, and stylesheets, are rendered as soon as they are loaded.
- Scripts, or automated code that runs in the browser, innately blocks this top-to-bottom process and is loaded and ran immediately after being encountered.
- `defer` overrides this blocking, and executes code in the order presented.
- `async` overrides the same blocking, but executes the code on a first-load basis.

## Questions
1) When would using `async` scripts be useful?

2) When would using `async` be harmful?

3) Why are `<script>` tags frequently placed at the end of the `<body>`?