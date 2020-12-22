# Targeting Elements With Pseudo-classes

<a style={{color:"blue"}} href="https://forum.burlingtoncodeacademy.com/t/week-3-targeting-elements-with-pseudo-classes/287">Discuss in Forum</a>

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
The link, before being visited, is colored `red`. Upon clicking it, the color of the link turns to `grey`. This can be helpful for a number of reasons. Providing additional behavior that indicates whether a link has been visited or not will serve to further your site's design.

> Note that `:link`, `:visited`, `:hover`, and `:active` are order-dependent in your CSS. Since CSS is read top-to-bottom, adding certain stylings before others will override whatever has previously been applied. Elements with `href` attributes have more states than the average element, so this order is important. Follow the LVHA rule: `:link`, `:visited`, `:hover`, `:active`.

A prime example of the proper flow is so:

```html
<a href="https://www.google.com">A link styled with pseudo-classes</a>
```
```css
a:link{
  color:red;
}
a:visited:{
  color:green;
}
a:hover{
  color:orange;
}
a:active{
  color:yellow;
}
```

See it in action:

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/pseduo-classes-links-bca?path=style.css&previewSize=100&attributionHidden=true"
    title="pseduo-classes-links-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>  

Note the different colors indicated the different states of the anchor tag.

> Styles defined by the :link pseudo-class will be overridden by any subsequent link-related pseudo-class (:active, :hover, or :visited) that has at least equal specificity. To style links appropriately, put the :link rule before all other link-related rules, as defined by the LVHA-order: :link — :visited — :hover — :active.



### `:nth-child()`
The `:nth-child()` pseudo-class is a powerful one that, unlike the others covered so far, is used more as an addition to CSS selectors, instead of as a means to customize the element's state itself. 

With `:nth-child()`, you can match a single element out of a group of siblings. What's that mean? It means that given HTML like so:

```html
<ul>
  <li>1</li>
  <li>2</li>
  <li>3</li>
  <li>4</li>
</ul>
```

We can select any elements based on their relationship to one-another. In this case, we can select the *second* `<li>` element with the following:

```css
/* selects any <li> element that is the second child of an element*/
li:nth-child(2){
  color:firebrick;
}
```
This will render like so:

<ul>
  <li>1</li>
  <li style={{color:"firebrick"}}>2</li>
  <li>3</li>
  <li>4</li>
</ul>


As you can see, `:nth-child()` takes an argument that determines what the selected elements will be. A number, starting with `1`, will determine what element is selected based on its index. The targeted element must match the selector *and* the position given to the `:nth-child()` pseudo-class. It will not select an element that is for example, the *3rd* child, even if it is only the second element matching the selector.

There are a number of keywords that allow this pseudo-class to handle more than a single element. `nth-child(even)` and `nth-child(odd)` will select every other sibling, starting at 2 or 1, respectively. 

Looking at our previous example:

```html
<ul>
  <li>1</li>
  <li>2</li>
  <li>3</li>
  <li>4</li>
</ul>
```

This:

```css
li:nth-child(even){
  color:blue;
}
li:nth-child(odd){
  color:red;
}
```
Will look like this:


<ul>
  <li style={{color:"red"}}>1</li>
  <li style={{color:"blue"}}>2</li>
  <li style={{color:"red"}}>3</li>
  <li style={{color:"blue"}}>4</li>
</ul>

We can also utilize what is referred to as *functional notation*, where `:nth-child()` accepts a pattern that allows for more customizability.

It takes the form of `nth-child(An+B)`. This may look confusing, but rest assured it is actually quite straightforward.

`B` represents the starting index, and `A` represents the interval that elements will be selected by. For example, `nth-child(3n+5)` will start with the 5th element, if any match, and then select the 8th, 11th, 14th, and so on. This is a powerful tool and can really help you to quickly style your elements while adhering to more complex patterns. 

For a full list of `nth-child()` examples, visit [MDN's list of nth-child() examples](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-child#Examples)

### `:focus`
We will close out this lesson on pseudo-classes with `:focus`, another that focuses on particular state of an element. When an element is *focused*, that means that it (typically) clicked on, tapped, or selected with the <kbd>tab</kbd> key. A prime example is a text box, or `<input>` element.

Giving the elements a `:focus` pseudo-class allows you to harness the otherwise default appearance of such elements.

Let's take a look at a few examples:

```html
<input value="This is the default">
<br/>
<input class="grey-background" value="This will have a grey background when focused">
<br/>
<input class="yellow-background" value="This will have a yellow-background when focused">
```
```css
.grey-background{
  background-color: grey;
}
.yellow-background{
  background-color:yellow;
}

```

Try selecting each of these `<input>` elements below to see the result. 

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/pseudo-classes-focus-bca?path=style.css&previewSize=100&attributionHidden=true"
    title="pseudo-classes-focus-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

## Final Musings 
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

Well, there you have it! Some of the most common pseudo-classes and their behavior in a nutshell. Along with CSS selectors and combinators, pseduo-classes add even more customizability to your style choices, without having to bloat your HTML with too many `id` and `class` attributes to target them. Helpful and specific in their use cases, pseudo-classes are another tool to reach for when you want to customize the user's interaction with certain elements, on top of how the element might appear upon first load of the page.  

There are many, many more pseudo-classes than what has been covered here. For a complete list, visit [MDN's list of pseduo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes#Index)

Now, review the points below, and then move on to the exercises.

- Pseudo-classes are used to target a particular state of a given element.
- An element's state is frequently determined by the user's interaction with said element.
- Some elements, like those with `href` attributes, have many different states.
  - Due to CSS's top-down application of styles, order of declarations may matter.
  - Follow the order of `:link`, `:visited:`, `:hover`, `:active`
- Some pseudo-classes, like `:nth-child()`, are more of a means to select patterns of elements that are siblings to one-another. 
- Pseudo-classes are used in tandem with selectors and combinators, like so:
  - `div > p:nth-child(odd)`
  - Only selects odd children of `<p>` elements that are direct children of `<div>` elements.


Happy Coding :)

-Paul

# Exercises
<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/pseudo-class-exercises-bca?path=index.html&previewSize=0&attributionHidden=true"
    title="pseudo-class-exercises-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>


In the environment provided, complete the following tasks listed below. Feel free to add classes and other identifiers as you see fit, so long as pseudo-classes are involved in the end result.

- Make the `<input>` element's background color `lightgrey` when focused, with a padding of `10px` on all sides.
- Select every 3rd list item that is a child of the `<ul>`element and make their text color `cornflowerblue`
- make the button that reads "Change" have a background color of `firebrick`
- make the `<img>` element `scale(1.1)` slightly larger when hovered over.
  - use the `transform` property on the image and give it the value of `scale(1.1)`

<details>
<summary>Example stylesheet</summary>

```css
input:focus{
  background-color:lightgrey;
  padding:10px;
}
ul > li:nth-child(3n+3){
  color:cornflowerblue;
}
div button:active{
  background-color:firebrick;
}
img:hover{
  transform:scale(1.1);
  border: 5px solid black;
}
```
 </details>