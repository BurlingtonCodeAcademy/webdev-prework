# Targeting Elements With Pseudo-classes
![a photo lens and a blue background](https://res.cloudinary.com/btvca/image/upload/v1604590551/lens-1209823_1280_hmux2g.jpg)

As you have most likely gathered by this point, CSS selectors are integral in targeting a particular element or elements. This, combined with *combinators*, allow for your stylesheets to be concise and efficient. Styling elements relative to their `id`, `class`, or element name and then using that selection to style the elements surrounding them is a fundamental skill in writing CSS. 

Along with selectors and combinators, there is another aspect to creating attractive and responsive pages. Briefly mentioned in our previous lesson on CSS selectors, *pseudo-classes* are yet another piece to the CSS puzzle. They allow you to target not only the element or elements you desire, but the particular *state* of these elements as well. 

What do we mean by *state*? Read on to find out.

## What are pseudo-classes

CSS pseudo-classes are a series of reserved keywords that can be appended to a specific CSS selector in order to better specify the "state" of the selected elements. *State* can mean many things, depending on the situation. Whenever you click on, hover over, highlight, or de-select an element on your page, you are altering the *state* of that element. In typical CSS fashion, you can alter the style of the element based on these keywords. 

Pseduo-classes are denoted by a colon (`:`) immediately following the selector, or selector/combinator.

The syntax for targeting a pseudo-class is as follows:

```css
selector:pseudo-class{
    /* css styling */
}
```
While that definition is quite dry, rest assured it will make more sense when put in action.

For example, the `:hover` pseudo-class will alter the style of the conjoined selector whenever that targeted element is hovered over by the mouse.

Let's take this HTML and CSS:

```html
<h1>Put your mouse over me!</h1>
```
```css
h1{
    color:red;
}
h1:hover{
    color:blue;
}
```
It renders like so. The default color of the `<h1>` element is `red`, but when that same element (or any other `<h1>` element that you might want to add later) is hovered over with your mouse, the color shifts to `blue`. 

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/pseudo-class-hover-example-bca?path=style.css&previewSize=100&attributionHidden=true"
    title="pseudo-class-hover-example-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

This works with so much more than just the element's `color`, of course. Pseudo-classes can be used to add a level of interactivity to your page that would otherwise require a large amount of tinkering to accomplish. These aspects instead come bundled directly with CSS and modern browsers, so the guesswork is all but forgotten! 


## Common pseudo-classes
Here we will cover a handful of the most common pseudo-classes, as well as typical use cases associated with them. Keep in mind that, like many topics covered to date, there are far more available than will be covered. 

> For a complete list of pseudo-classes, visit the [MDN pseudo-class index](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes#Index)

### `:hover`
As the previous example demonstrates, the `:hover` CSS pseudo-class is applied whenever a mouse or other pointing device directly interacts with the targeted element. This is most typically a result of the user's cursor hovering over the element. 

It is, unsurprisingly, a bit troublesome on touchscreens. Depending on the browser, the elements targeted may apply the styles preemptively, not at all, or regardless of interactions with the web page. As a web developer you be mindful of the user's environment and intended use-cases for whatever you might be designing.

Refer to the previous example for a demo of its application.

### `:active`

The `:active` CSS pseudo-class is used to target an element that is being currently "activated" by a user. "Activated" is a term used to describe anything that the user typically clicks on. If the user is using a multi-button mouse or trackball, this only refers to whatever has been specified as the primary button.  

The `:active` pseudo-class is most-commonly used on `<a>` and `<button>` elements, as their default behavior involves being activated. 

Here is an example of a styled `<button>` element that takes on additional properties when the `:active` pseudo-class is applied.

```html
<button>Click me</button>
```
```css
button{
  font-size:26px;
  padding:10px;
  border-radius:5%;
}
button:active{
  color:white;
  background-color:firebrick;
}
```

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/pseudo-class-active-example-bca?path=style.css&previewSize=100&attributionHidden=true"
    title="pseudo-class-active-example-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

### `:link` and `:visited`

The `:link` and `:visited` pseudo-classes are used to style any element that has an `href` attribute, including both `<link>` elements and `<a>` elements. 

If you've ever clicked on a `blue` link and, upon revisiting the page, discovered that link was `purple`, you have encountered the default styling for these aforementioned pseduo-classes.

`:link` is a pseudo-class that represents an element yet-to-be visited. The styles defined by the `:link` pseudo-class will then be replaced with the default styling, or whatever is denoted in the `:visited` CSS.  Let's take a look at these in action.

```html
<a href="#">Link to something cool</a>
```
```css
a:link {
  color: red;
}
a:visited {
  color: grey;
}
```
The link, when clicked, 

> ADD NOTE ABOUT PROPER ORDER OF OPERATIONS





- highlight a few 
    - :hover
    - :active
    - :link/:visited
    -   See note.

    - :first-child/:nth-child
    - :focus
- mdn list with more
- exercises