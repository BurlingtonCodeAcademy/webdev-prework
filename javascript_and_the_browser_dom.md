# JavaScript and The Browser DOM

<a style={{color:"blue"}} href="https://forum.burlingtoncodeacademy.com/t/week-4-javascript-and-the-browser-dom/292">Discuss in Forum</a>

![technical blueprints](https://res.cloudinary.com/btvca/image/upload/v1605811042/blueprint-4056027_1280_ztranq.jpg)

Think back to our lesson, **A Deep(er) Dive into HTML**. In it, we discuss the fundamentals of HTML and moreso, the DOM. As discussed, the DOM, or *document object model*, is the browser's interpretation of your HTML, CSS, JavaScript, and other assorted media. It takes these various resources and compiles them into a visual representation of those resources so you can see, interact, and manipulate it. 

In this lesson, we will be exploring the basics of DOM manipulation through JavaScript. With the use of JavaScript, we will be able to alter the DOM, which then alters the page as any user may see it in the browser. 

## DOM Manipulation 101

As with CSS, JavaScript is used to alter the appearance and behavior of the DOM. Remember that the DOM is not the HTML, but rather the compiled version of *all sources and assets* the browser interprets. Thus, by including JavaScript in that process, we can create a "livelier" web page. Instead of having to include additional HTML every time we want to add an element, we can simply write a script that allows for such things to happen, through JavaScript instead.

This added functionality allows our page (DOM) to change without making additional edits to the source code! What's that look like? Let's take a look at 2 examples, one of which is our standard way of creating HTML elements: in HTML! The other accomplishes the same thing, but through JavaScript alone.

```css
.green-text{
    padding: 10px;
    border: 1px solid cornflowerblue;
    color: #5ba358;
    background-color: #c4edc2;
}
```
```html
<div class="green-text"> Here is a div with some text </div>
```
That CSS and HTML will render like so:

<div style={{padding:"10px", border: "1px solid cornflowerblue", color:"#5ba358", backgroundColor:"#c4edc2"}}>Here is a div with some text</div>

<br/>
This is nothing new. We have some CSS that defines a class with `padding` and `color`. In our HTML, we create a div, give it some text content, a class that points towards the styling, and send it on its merry way. 

There is another option, however, that allows for additional possibilities. And, as mentioned, it can be done with JavaScript!

Instead of jumping right into our HTML, we can *manipulate* the DOM with the `document` object, as long as we have included our JavaScript within our HTML via the `<script>` element. It works just like your `<link>` element you use to link a CSS stylesheet, except in should be included at the BOTTOM of your HTML. 

> `<script>` tags link to your JavaScript. They are typically located at the bottom of your HTML because HTML is read top-to-bottom and the JavaScript often manipulates the HTML already rendered. By including it at the bottom of your document, the rest of said document is made available to it.

We can add elements via JavaScript by the following steps:

1. Create the element in JavaScript with `document.createElement()`
2. Customize the element.
    - add classes
    - add text content or inner HTML
3. Append the created element to your document.

Let's go step by step.

### Create the element in JavaScript

`document.createElement()` is a *method* available to all JavaScript that has been included in the browser. It takes a string as an argument that represents the type of element you intend on creating. For example, we can create a generic div element like so:

```js
let div = document.createElement('div')
```
It is important that we store the created element in a variable so we can refer back to it for the next steps. 

>Note that the `<>` are not included when creating the element in JavaScript.  That is an HTML syntax not required here.

### Customize the element

Now that we have a free-floating element defined in our JavaScript, it is time to give it some personality.  Assuming that the previous `.green-text` class is still included in our document's stylesheet, we can include it via the `className` property on the created element. You can access the property like so:

```js
let div = document.createElement('div')
div.className = "green-text";
```
> Note that the value provided to `className` needs to be a string.

We have provided the class to our div, but there's no *content* still. We can add content in one of two ways: `textContent`, or `innerHTML`.

`textContent` is a means of interpreting the provided string *literally* as whatever has been provided.

`innerHTML` will render the string provided as HTML instead of literal text, meaning that you can provide additional HTML inside of that attribute. This is helpful if you'd like to add some inline elements to italicize some text, for example. Let's see the two options here:

```js
let div = document.createElement('div')
div.className = "green-text";

// textContent
div.textContent = "Here is some <em>text</em> inside the div"

// innerHTML
div.innerHTML = "here is some <em>text</em> inside the div"
```

These will render very similarly to one another, the primary difference being that the `innerHTML` will honor the provided `em` elements, whereas the `textContent` will not. See here: 

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/textcontent-vs-innerhtml-example?path=style.css&previewSize=100&attributionHidden=true"
    title="textcontent-vs-innerhtml-example on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

### Append the created element to your document

To actually add the element to your document, we need to insert it directly with JavaScript. We can do so with the `.append()` method, which takes the created element as an argument.

Just like the `document` object has the `.createElement()` method available to it, it also has the `body` element, which as we know, is the element that contains all other visible elements in our HTML! 

We can append an element to the document's body like so!

```js
// create the element
let div = document.createElement('div')
// add class name
div.className = "green-text";
// add text content (or innerhtml)
div.innerHTML = "Here is some <em>text</em> inside the div"

// appends it as last element to the document's body
document.body.append(div)
```
Will look like:

<div style={{padding:"10px", border: "1px solid cornflowerblue", color:"#5ba358", backgroundColor:"#c4edc2"}}>Here is some <em>text</em> inside the div</div>

## Adding elements where you want them

`append` is just one of the methods that determine where the element is placed. It will add the element at the bottom of your document. If there are other elements already included in your HTML, any elements appended will display underneath them in the document flow.

You may also `prepend` the element(s) to the beginning of the document's body.

```js
// create the element
let div = document.createElement('div')
// add class name
div.className = "green-text";
// add text content (or innerhtml)
div.innerHTML = "Here is some <em>text</em> inside the div"

// appends it as first element to the document's body 
document.body.prepend(div)
```

You do not need to append directly to the document's body, however. You can also append to any element within the document. For example, we can append an element to any element already in the DOM. 

If appending to an element other than the body, there are additional methods that allow you to add these elements (nodes) before or after that particular node.

Here, we create a div and two paragraph elements. By appending the div to the document's body, we can then use it as a touchstone for your additional elements to be placed relative to it:

```js
// creates elements
let div = document.createElement('div')
let beforePar = document.createElement('p')
let afterPar = document.createElement('p')

// adds text to elements
div.textContent= "here is my div's text"
beforePar.textContent = "paragraph before div"
afterPar.textContent = "paragraph after div"

// adds div to body
document.body.append(div)

//  adds paragraph before div
div.before(beforePar)
//  adds paragraph after div
div.after(afterPar)
```

The result will be like so:

<p> paragraph before div </p>
<div>here is my div's text</div>
<p> paragraph after div </p>

<br/>

 You may also replace them with `replaceWith`. As the name implies, the element it is called on is replaced with whatever string or element you provide as an argument.

```js
// creates elements
let div = document.createElement('div')
let replacer = document.createElement('p')

// adds div to body
document.body.append(div)

// replaces div with paragraph
div.replaceWith(replacer)
```


To remove an element from the document, simply call `remove` on it:

```js
// create the element
let div = document.createElement('div')
// add class name
div.className = "green-text";
// add text content (or innerhtml)
div.innerHTML = "Here is some <em>text</em> inside the div"

// appends it to the document's body
document.body.append(div)
//  remove the targeted element
div.remove()
```

This will not render anything, as the element is removed immediately after it is appended. This is much more useful when dealing with *events*, like clicking on a delete button, which we will cover in an upcoming lesson. 

Let's review what we have so far.

## Final Musings
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

Thus concludes our first steps into using JavaScript to manipulate the DOM! With it, our tool belts expand even further; no longer is there one way to add elements to your web page. Now there's two! Review below, then move onto the exercises.

- JavaScript is included in your HTML document via `<script>` elements.
- `script` elements are usually found as the last element in the document's body, so they can actively manipulte the elements that have already been rendered.
- JavaScript can create elements with `document.createElement()`
- They can be inserted into the document based on the `body`, or other elements.
    - `append`
    - `prepend`
    - `before`
    - `after`
    - `replacewith`

## Exercises

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/javascript-and-the-browser-dom-exercises?path=script.js&previewSize=100&attributionHidden=true"
    title="javascript-and-the-browser-dom-exercises on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>


In the coding environment above, complete the following:

### 1
create an `h1` element `mainHeader`
- Give it the `textContent` "Header"
- append it to the document's body

### 2
create an `ol` element `list`
- create and `append` 3 `li` elements to `list`
- give `list` the `className` of `list-class`
- `li` elements should have text content "one","two", and "three" respectively.
- append `list` just after `mainHeader`

### 3 
create a `div` element called `div`
- give it inner HTML of `"<em>div text</em>"`
- prepend it before `list`

<details>
<summary>Answer</summary>

```js
//  question 1

let mainHeader = document.createElement("h1");

mainHeader.textContent = "Header";
document.body.append(mainHeader);

// question 2
let list = document.createElement("ol");

list.className = "list-class";

let itemOne = document.createElement("li");
itemOne.textContent = "one";
list.append(itemOne);
let itemTwo = document.createElement("li");
itemTwo.textContent = "two";
list.append(itemTwo);
let itemThree = document.createElement("li");
itemThree.textContent = "three";
list.append(itemThree);

document.body.append(list);

// question 3
let div = document.createElement("div");
div.className = "div-class";
div.innerHTML = "<em>div text</em>";
list.prepend(div);

```
</details>