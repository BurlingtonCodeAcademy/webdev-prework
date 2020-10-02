# DOM Queries
![Highlighted Door](https://res.cloudinary.com/btvca/image/upload/v1601645585/doors-1690423_1280_vc45lf.jpg)

There is a lot that goes into designing a website. It needs structure, style, and functionality, which are effectively handled by HTML, CSS, and JavaScript respectively (although it really isn't as black as that sounds). When a site is built, the interplay between these languages is as important as what those languages are saying in the first place.

Consider how CSS and HTML "talk" to one another. HTML elements are given IDs, Classes, tag names, etc... that are later referenced by the CSS in order to manipulate and style those elements. With this relationship in mind, The DOM does its magic, and renders the page in the browser as a tree of objects that our third language, JavaScript, can now play with. 

In other words, when the *static* assets on the site are loaded (HTML and CSS,) the DOM is created, which allows any scripts (i.e. JavaScript) to run on that page, manipulating not the HTML and CSS, but the browser's interpretation of that information (the DOM). This is what you *actually* see in the browser, and it is primed for JavaScript to manipulate it in all sorts of ways. 

But how do I actually *use* JavaScript to make things happen on my page? How do I select a button that, when clicked, changes the color of the box next to it? How do I increase the font when I click on the little "+" button next to a paragraph? How do I anything? The answer lies in what is known as **DOM Queries**


## What are DOM Queries
DOM Queries are the *methods* that are called on the DOM to select and return one or more of the elements represented in the DOM. The returned element(s) from the DOM query is then free to be used by a programming language to do all manner of things. If you can dream it, you can do it!

Let's take a look at a really basic example, then we will discuss the many approaches to making DOM Queries.

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="js,result" data-user="burlingtoncodeacademy" data-slug-hash="mdPZZba" data-editable="true" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="DOM Query Example 1.0">
  <span>See the Pen <a href="https://codepen.io/burlingtoncodeacademy/pen/mdPZZba">
  DOM Query Example 1.0</a> by Burlington Code Academy (<a href="https://codepen.io/burlingtoncodeacademy">@burlingtoncodeacademy</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

In the above example, we are given 3 `<p>` elements, with filler text:

```html
 <p>lorem</p>
 <p id="example">ipsum</p>
 <p>dolor</p>
```
One has been given an `id`. 

That `id` is used in the CSS to make that specific `<p>` element red:

```css
#example {
    color: red
}
```

Then, in JavaScript, we see our DOM Query:

```js
let selected = document.getElementById("example");
console.log(selected);
```

Viewing the console, we see the `console.log` in action:

```
"<p id='example'>ipsum</p>"
```

Wait wait wait, what's `document.getElementById`?


Now, that same element has been isolated and exposed in both the CSS and JavaScript. And, now that it's available in JavaScript, we can apply all the logic and functionality that JavaScript has to offer!

That's the DOM Query! When the DOM has been created in the browser, the `document` object is exposed to your JavaScript. It contains a LOT of [information](https://developer.mozilla.org/en-US/docs/Web/API/Document), and is the entry point to actively manipulating the DOM. The *method* currently being used is `getElementById()`, which as the name implies, selects the element in the DOM with an `ID` matching the string passed in as an argument. 

> This lesson will not cover what do when the elements have been selected, but rather HOW to select them! For actively changing their place and behavior in the DOM, see lessons on DOM Manipulation.

That's the basic idea: the DOM is made available to your JavaScript through the `document` object, and has a number of query *methods* that allow for highly customizable selector options. 

Now, let's take a look at some of those methods:

## DOM Query Methods

### `document.getElementById()`
This method returns an *element object* that represents the element whose `id` matches the string passed in as an argument. Seeing as IDs are unique (or at least should be!), theis method will return *at most* one element. If none are found, it will return `null`. **Note the camel-case nature of this method.** 

```html
<h1 id="unique-value">Here is my header</h1>
```
```js
document.getElementById("unique-value")
```

### `document.getElementsByClassName()`
This method returns an HTML Collection (more on this in a moment) of all elements which match all of the given class name(s). 

```html
    <div class="sharedClass">item 1</div>
    <div class="sharedClass">item 2</div>
    <div class="sharedClass">item 3</div>
    <div class="sharedClass">item 4</div>
    <div class="sharedClass">item 5</div>
```
```js
document.getElementsByClassName('sharedClass')
// will return all
```
___
```html
    <div class="sharedClass">item 1</div>
    <div class="sharedClass">item 2</div>
    <div class="sharedClass unique">item 3</div>
    <div class="sharedClass">item 4</div>
    <div class="sharedClass">item 5</div>
```
```js
document.getElementsByClassName('sharedClass unique')

// will return <div class="sharedClass unique">item 3</div>
```

Unlike `document.getElementById()`, this method can be called on elements WITHIN the DOM tree. So, if you have a section of a document that you would like to select that has the same class name(s) as another section, you can also do something like this:

```html
<section id="desired-section">
    <div class="sharedClass">item 1</div>
    <div class="sharedClass">item 2</div>
    <div class="sharedClass">item 3</div>
</section>
<section id="undesired-section">
    <div class="sharedClass">item 4</div>
    <div class="sharedClass">item 5</div>
</section>
```
```js
let section= document.getElementById('desired-section')
section.getElementsByClassName('sharedClass')

// will select the top 3 (item 1, item 2, item 3)
```

### `document.querySelector()`
This method returns the first element within the document that matches the selector passed in as an argument. It returns, at most, a single element. 

**Any valid CSS selector string will work!** This makes it a powerful ally, and one you should thoroughly familiarize yourself with. Even [combinators](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors#Combinators) work! This lets you thoroughly customize your queries, so you can be sure you are only selecting the elements that you really want to. 

```html
<section id="desired-section">
    <div class="sharedClass">item 1</div>
    <div class="sharedClass">item 2</div>
    <div class="sharedClass">item 3</div>
</section>
<section id="undesired-section">
    <div class="sharedClass">item 4</div>
    <div class="sharedClass">item 5</div>
</section>
```
```js
let selected = document.querySelector('.sharedClass')
console.log(selected)
// <div class="sharedClass">item 1</div>
```
Refresh yourself with CSS selectors [here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors).


### `document.querySelectorAll()`
This method returns a **Node List** (more on that in a moment) that represents the list of the document's elements that match the given selector(s). Like `document.querySelector()`, it expects one or more CSS selectors to compare against.

```html
<section id="desired-section">
    <div class="sharedClass">item 1</div>
    <div class="sharedClass">item 2</div>
    <div class="sharedClass">item 3</div>
</section>
<section id="undesired-section">
    <div class="sharedClass">item 4</div>
    <div class="sharedClass">item 5</div>
</section>
```
```js
let selected = document.querySelectorAll('.sharedClass')
console.log(selected)
// NodeList(5) all 5 divs
```

## Array-like objects
Array-like objects are objects that have properties like an array; they have a length property, and they are indexed to denote the position within the object itself. 

These are difficult to manipulate and iterate over. The best practice is to convert them into an array so they have access to the highly-valuable *array methods*, like `.map()`, `.reduce()`, `.forEach()`, `.push()`, etc. This can be achieved with `Array.from()` where the argument is the array-like object in question.

```html
    <div class="sharedClass">item 1</div>
    <div class="sharedClass">item 2</div>
    <div class="sharedClass">item 3</div>
    <div class="sharedClass">item 4</div>
    <div class="sharedClass">item 5</div>
```
```js
let selected= document.getElementsByClassName('sharedClass')

let selectedArray = Array.from(selected)
// selectedArray can now be used as an array 

```
###  Nodelists 
**`document.querySelectorAll()` returns a *Nodelist*.** A Nodelist is a *static* array-like object that is immutable. It consists of a list of *nodes* that match the DOM query. That list can be used to target and change information in the DOM itself, and those changes will be shown in the browser. 

They will not, however, affect the original nodelist that has been returned from the query. If you are trying to gather a list of elements in your JavaScript that you will be referring to multiple times **regardless** of the changes made to the browser's representation of them, then nodelist is a fine choice!

### HTML Collections
An *HTML Collection* is a live version of the elements returned by `document.getElementsByClassName()`. By live, we mean that they are actively manipulatable. Should you change anything directly on a collection, it will remain like that, directly changing the elements contained within it as well. 

### Importance
Knowing how to query multiple elements is important when dealing with sweeping changes to the DOM. Whenever you want to manipulate more than a single element at a time, you will encounter these *array-like objects*, so you will need to know how to act accordingly. 

## Final Musings
![sunset](https://res.cloudinary.com/btvca/image/upload/v1599682636/sunset-1211475_1280_xtjrjn.png)

- The DOM is the tree-like object representation of our site.
- The DOM allows programming languages to access the document (site) directly.
- This access gives JavaScript the ability to *query* the DOM directly.
- Based on the query, a single element or *array-like object* of multiple elements may be returned.
- These returned values can be used to make changes to the DOM, and effectively the browser itself. 

### Practice

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="html,result" data-user="burlingtoncodeacademy" data-slug-hash="vYGoYgb" data-editable="true" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="DOM Query Quiz">
  <span>See the Pen <a href="https://codepen.io/burlingtoncodeacademy/pen/vYGoYgb">
  DOM Query Quiz</a> by Burlington Code Academy (<a href="https://codepen.io/burlingtoncodeacademy">@burlingtoncodeacademy</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

<details>
<summary>1</summary>

```js
document.getElementsByClassName('section-one-class")
```
</details>

<details>
<summary>2</summary>

```js
document.querySelectorAll('#section-one>.newClass')
//or
document.getElementById('section-one').querySelectorAll('.newClass')
```
</details>


<details>
<summary>3</summary>

```js
document.querySelector('.newClass.unique')
```
</details>

<details>
<summary>4</summary>

```js
document.querySelectorAll('#section-one :nth-child(4)')
```
</details>