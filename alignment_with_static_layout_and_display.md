# Alignment With Static Layout and Display

<a style={{color:"blue"}} href="https://forum.burlingtoncodeacademy.com/t/week-3-alignment-with-static-layout-and-display/283">Discuss in Forum</a>

![blueprint with pencil and ruler](https://res.cloudinary.com/btvca/image/upload/v1603458455/blueprint-964629_1280_bsinth.jpg)
You might remember from our lessons on HTML that elements typically orient themselves on the page in one of 2 ways, being either `inline` level or `block-level`. This is the default way of the web; HTML elements come bundled with their own style and behavior that causes them to act in the way they do with no additional CSS. It's what makes a header (`<h1>`) so big, or the list-items (`<li>`) in an `<ol>` indented with bullets. 

Nowadays, there are a number of tools that allow us to overwrite such behaviors in order to orient our elements on the page how we would like. You can place two `<h1>` elements side by side! Or place a `<div>` inside of a `<p>` element without interrupting the flow of the text! **In this lesson, we will be readdressing the default behavior of certain elements, while also discussing ways to alter the flow and layout of your page.** 

## The `display` property
Before moving on, let's take a quick look at what makes this all possible: the `display` property. The `display` property specifies how (and sometimes if) an element is displayed on a page. The default properties are `block` and `inline` for most elements. You will see more in the coming lessons, but know that you can reach for the display property whenever you want an element to change its layout behavior. 
 
## Typical Element Behavior
By default, elements are laid out on a page by placing the content within it, followed by the addition of any default `margin`, `border`, and `padding` properties that might be a part of it.

Remember this?
![chrome box model](https://res.cloudinary.com/btvca/image/upload/v1603143645/altered_box_model_kklv0l.png)

That's a visual representation of a given element. Should that element be, say, an `<h1>`- `<h6>` element, the `margin` will be calculated and applied after the content (in this case text) has been placed. This means that the `width` of the element as a whole will be width of the page, or have the `display: block` property. 

### block level elements
```css
div {
    display: block;
}
```

By default, block level takes up the entire width of its parent element, which in many of our examples has been the `<body>`. It also has no implicit `height` value, meaning that *block-level* elements will adjust their height according to the content of the block-level element. 

Let's see this in action by applying a border to a header element (`<h3>`)

```html
<h3>I am a block level element</h3>
```
```css
h3{
    border: 1px solid red;
}
```
<h3 style={{border: "1px solid red"}}>I am a block level element</h3>

See the additional whitespace to the right of the text, but not above or below? That is the additional space (`margin`) added solely because it is a block-level element. That extra space will not exist (by default on) inline elements.

### Inline level elements
```css
em {
    display: inline;
}
```
Inline elements, unlike block-level elements, will not only adjust their height to their content, but *also* their width. Note that you can't set the `height` and `width` properties of an inline element, as they are meant to, as the name implies, sit in line with the contents of other block level elements. A good example of this is the `<em>` tag, which is meant to exist within another element as a means of additional styling:

```html
<h5>I am a block level element and <em>this is an inline element</em></h5>
```
```css
h5{
    border: 1px solid red;
}
em{
    border: 3px solid black;
}
```
<h3 style={{border:" 1px solid red"}}>I am a block level element and <em style={{border: "3px solid black"}}>this is an inline element</em> </h3>

Note that the inline elements take up as much space as their content and no more, in contrast with the block level element it resides in, which still takes up the full width of the container (parent element). If you want to control the `width` and `height` of the element, you'll have to use the third property, `inline-block`

### Inline-block elements
```css
span {
    display: inline-block;
}
```
Elements do not come by default with the property of `inline-block`, but it can be easily assigned, as shown above. `inline-block` elements adopt behavior from both `block` and `inline` elements, in that they accept `height` and `width` properties, and can be given `margin` and `padding` values as well. They also sit like `inline` elements would, so they don't take up the entire width of the container, like `block` elements.

> If you have an `inline` element that needs additional adjustments, reach for `inline-block`. 
This is helpful when elements need to be oriented horizontally, but with some distance between the elements.

Unlike the `<em>` element we saw before, `inline-block` elements can be given additional `padding` or `margin` values to "space them out". Let's see this in action:

Here, we have our previous example, but the `<em>` element has been turned into an `inline-block` element instead. Now, it accepts additional properties like `height`, `width`, `padding`, etc...

```html
<h5>I am a block level element and <em>this is an inline element</em></h5>
```
```css
h5 {
    border: 1px solid red;
}
em {
    display: inline-block;
    border: 3px solid black;
    padding-left:15px;
}
```

<h5 style={{border: "1px solid red"}}>I am a block level element and <em style={{display:"inline-block", border: "3px solid black",paddingLeft:"15px"}}>this is an inline element</em></h5>

This can be extremely useful for a number of cases! For example, you might want to use this to make your nav bars look a little more like nav bars.


For example, this:
```html
<nav>
    <ul>
        <li><a href="#top">Top</a></li>
        <li><a href="http://example.com">example.com</a></li>
        <li><a href="/about.html">About</a></li>
    </ul>
</nav>
```
```css
nav {
    display: inline-block;
    background-color: yellow;
}
ul {
    list-style-type: none; /*to remove bullets*/
}
li{
    display: inline-block;
    padding-right: 15px;
}
```
will render like this:

<nav style={{backgroundColor:"yellow"}}>
    <ul style={{listStyleType:"none"}}>
        <li style={{display:"inline-block", paddingRight:"15px"}}><a href="#top">Top</a></li>
        <li style={{display:"inline-block", paddingRight:"15px"}}><a href="http://example.com">example.com</a></li>
        <li style={{display:"inline-block", paddingRight:"15px"}}><a href="/about.html">About</a></li>
    </ul>
</nav>

Note that the `<nav>` element has *also* been given the `display: inline-block` so the nav bar will not take up the width of the parent element either! 

## Vertical orientation and `display`
![brick wall](https://res.cloudinary.com/btvca/image/upload/v1603469006/backdrop-21534_1280_vwbkhe.jpg)
As shown by our nav bar example, utilizing different `display` properties allows us to orient our elements horizontally within block-level elements. You can say things like, "make this element as wide as the page (block-level), and then space the elements inside of it by adding `padding` or `margin` to them. The inverse is also true, in that you can turn `inline` elements *into* `block` elements, all to serve this left-to-right (or right-to-left, depending on your language!) layout attempt. The last thing to note when discussing these uses is the line break (`<br>`) element, that you might remember from our initial HTML lessons.

The `<br>` element "clears" the current line,  treating the remainder after the `inline` or `inline-block` elements as `block` as `margin`. 

Take the following:

```html
<div>This div is inline-block <em>for you</em>!</div>
<div>inline div next to another div</div>
```
```css
div{
  display:inline-block;
  background-color:yellow;
  border: 1px solid black;
}
```

Because the `<div>` elements are `display: inline-block`, they saddle right up to one another, like so:

<div style={{display:"inline-block", backgroundColor:"yellow", border: "1px solid black"}}>This div is inline-block <em>for you</em>!</div>
<div style={{display:"inline-block", backgroundColor:"yellow", border: "1px solid black"}}>inline div next to another div</div>

They are adjacent to one another, but we want two things:

1) The `background-color` to fit the divs snugly, and not span the entire width of the container. 
    - This means `block` level elements are out!
2) The `<div>` elements to exist on separate lines.

So, we use a line break (`<br>`) to achieve this:


```html
<div>This div is inline-block <em>for you</em>!</div>
<br/>
<div>inline div next to another div</div>
```
```css
div{
  display:inline-block;
  background-color:yellow;
  border: 1px solid black;
}
```

This will render like so:

<div style={{display:"inline-block", backgroundColor:"yellow", border: "1px solid black"}}>This div is inline-block <em>for you</em>!</div>
<br/>
<div style={{display:"inline-block", backgroundColor:"yellow", border: "1px solid black"}}>inline div next to another div</div>

Note that `<br/>` elements are self-closing. Adding a second will provide additional vertical-spacing between the elements whose height is based on default font height.

<div style={{display:"inline-block", backgroundColor:"yellow", border: "1px solid black"}}>This div is inline-block <em>for you</em>!</div>
<br/>
<br/>
<div style={{display:"inline-block", backgroundColor:"yellow", border: "1px solid black"}}>inline div next to another div</div>

We can also do something similar with CSS, `margin` and `padding`! In the example below, a line break is still utilized to "clear" the rest of the line. The vertical orientation, however is taken care of entirely by CSS.

```html
<div>This div is inline-block <em>for you</em>!</div>
<br/>
<div>inline div next to another div</div>
```
```css
div{
  display:inline-block;
  background-color:yellow;
  border: 1px solid black;
  margin-bottom:10px;
}
```

## Final Musings 
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

As mentioned before, this is the tip of the iceberg in terms of what the `display` property has to offer (you may have come to the conclusion yourself!). You are limited to left-to-right, top-to-bottom! Any spacing you are afforded has to be done manually, and we haven't even *started* to mention responsive design! But, be that as it may, this is a fundamental aspect of web-design and can accomplish much of what you might need, particularly `inline-block` and its multiple use cases.

Review here, then move on to the exercises.

- Block level elements take up the entire width of its container. 
    - No `height` and `width` properties.
- Inline level elements take up the same space as its contents.
    - No `height` and `width` properties.
- Inline-block elements take up the same space as its contents.
    - `height`, `width`, `margin` and `padding` available to it!
- Line breaks, `margin`  and `padding` can be used to align contents vertically.

## Exercises

Given the `<div>` and `<p>` elements below, make them appear as one paragraph. Color the `div` text `red` and the `p` text `blue`.

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/static-layout-exercise-?path=style.css&previewSize=0&attributionHidden=true"
    title="static-layout-exercise- on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

<details>
<summary>Answer</summary>

```css
div{
  color:red;
  display:inline;
}
p{
  display:inline;
  color:blue;
}
```
 </details>
<br/>

Given the unordered list (`<ul>`), orient the listen items (`<li>`) inside left-to-right, with each item having a right-hand `margin` of `15px`. Set the `list-style-type` property to `none` to get rid of those pesky bullets.

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/static-ayout-exercise-two?path=style.css&previewSize=0&attributionHidden=true"
    title="static-ayout-exercise-two on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

<details>
<summary> Answer </summary>

```css
li {
  list-style-type:none;
  margin-right:15px;
  display: inline-block;
}
```
 </details>

<br/>

Given the following, orient the `<section>` elements so all three reside side-by-side, left-to-right.

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/static-layout-exercise?path=index.html&previewSize=0&attributionHidden=true"
    title="static-layout-exercise on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>


<details>
<summary> Answer </summary>

```css
section{
  width: 30%;
  display:inline-block;
  padding-right:5px;
}
```
 </details>

