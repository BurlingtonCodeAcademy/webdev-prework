# Targeting the DOM with JavaScript

<a style={{color:"blue"}} href="https://forum.burlingtoncodeacademy.com/t/week-4-targeting-the-dom-with-javascript/293">Discuss in Forum</a>

![blue squares with a hand pointing at one of them](https://res.cloudinary.com/btvca/image/upload/v1606138080/selection-68953_1280_zmalry.jpg)

When using JavaScript in the browser, it is paramount to success that you understand how to manipulate specific elements by *targeting* them. This can be achieved in a similar way to our CSS selectors in that the practice for both is often based on `class`, `id`, or element type. By specifying exactly what element(s) we are looking for, we can inevitably work towards injecting JavaScript into our web pages to do a whole lot more than we've seen so far. But what do they look like?

Much like `document.createElement()` is available to us when using JavaScript in the browser to create and `append` elements to our DOM, there are methods that allow us to target elements that already exist in the DOM. These methods are available in the same way that the `createElement()` method is; on the `document` object. 

> Remember, the DOM is the interpretation of our HTML that can be actively manipulated with CSS and JavaScript! When discussing the DOM, it is important to remember that we're not changing the source code, just the way the page looks and acts!

## `getElementById()`

The Document method `getElementById()` will return a single element whose `id` matches the string passed to it as an argument. This is an effective (and straightforward) means of quickly selecting a single element. IDs in your HTML should be unique, so the fact that it only returns a single element is a bit redundant.

Let's take the following HTML and CSS:

```html
<body>
    <div id="unique">target this div</div>
    <div>Not this one</div>
    <div>Or this one</div>
</body>
```
```css
#unique{
    color: cornflowerblue;
}
.big-text{
    font-size: 26px;
}
```

To target only the one div, we can use `getElementById()` and provide the necessary string.

```js
let selectedDiv = document.getElementById("unique") // targets the proper div
selectedDiv.className = "big-text" // adds class to the targeted div
```

This will effectively result in the targeted div increasing in font-size, as defined by the class `big-text`, and will look like so:
<br/>

<div style={{color:"cornflowerblue", fontSize: "26px"}} id="unique">target this div</div>
<div>Not this one</div>
<div>Or this one</div>


### Notes

Again, `document.getElementById()` is useful when targeting a single element; if no element matches the specified ID, it will return `null`. 

The camel-casing of the `getElementById()` function is strictly enforced, meaning that if you do not properly capitalize the necessary inner characters, your code will not work.  

The `id` parameter is also case-sensitive. The strings passed to it as an argument must match exactly. 

## `getElementsByClassName()`

The Document method `getElementsByClassName()` will return multiple elements that all match the given class name(s). When called, it searches the entire document (DOM) and returns an *array-like object* of all elements within it that match the class. 

What's an array like object? Well, it's like an array, but doesn't behave exactly like an array. Perhaps it's easiest to see an example:

Given the HTML and CSS:

```html
<body>
    <div class="my-class">text in a div</div>
    <div class="my-class">text in a div</div>
    <p class="my-class">text in a paragraph</p>
    <div class="my-class">text in a div</div>
</body>
```

```css
.my-class{
    color:cornflowerblue;
}
.big-text{
    font-size:26px;
}
```
We can select the elements with the proper class name. Note that, when logging the value to the terminal, you will see that the result is referred to as an HTML Collection. This is the *array-like object* we referred to before.

```js
let elements = document.getElementsByClassName("my-class")
console.log(elements)
// HTMLCollection(4) [div.my-class, div.my-class, div.my-class, div.my-class]
```

> An *array-like object* behaves much like an array, with some key differences. In this case, the "array" that contains the sought elements is a live HTML Collection, meaning that it will only ever contain the elements that *currently* match the class provided. If you remove the matched class from any of the elements, they will no longer remain in the the array-like object.

Now that we have the `elements` variable holding all of our elements, let's add the `big-text` class to each of them. We can achieve this like we achieve anything with arrays; by looping!

Here, we add more to our JavaScript. To add more than one class to an element with JavaScript, we can access the `classList` property on each element. The `add` method allows us to add additional class names. Afterall, elements can have any number of classes available to them. 

```js
let elements = document.getElementsByClassName("my-class")

// loop over the array-like object
for (let i=0;i<elements.length;i++){
  elements[i].classList.add("big-text")
}
```
The result:
<br/>

<div style={{color:"cornflowerblue", fontSize: "26px"}} id="unique">text in a div</div>
<div style={{color:"cornflowerblue", fontSize: "26px"}} id="unique">text in a div</div>
<div style={{color:"cornflowerblue", fontSize: "26px"}} id="unique">text in a paragraph</div>
<div style={{color:"cornflowerblue", fontSize: "26px"}} id="unique">text in a div</div>

<br/>

### Notes

HTML Collections are live, meaning they are ever-changing. If an element's class used to group it and others in a collection is removed, the element will be removed from the collection as well.

You can match through multiple classes at a time, so long as each class name is separated by a white space. To target elements after the JavaScript above has been run, you could use this:

```js
// searches for multiple class names
document.getElementsByClassName("my-class big-text")
```

If you target another element, you can call `getElementsByClassName()` *on* that targeted element. This will limit the results to child elements of the targeted element.


## `querySelectorAll`

`querySelectorAll` is probably the most versatile selector method. It, like the `getElementBy*` methods listed above, takes a string that refers to the CSS in the DOM, but does so in a much broader context.

When given a CSS selector as an argument, `querySelectorAll` will return all matched cases in the document. Now, all of the same power provided by CSS selectors in the styling phase can be used here as well. Unlike the `getElementsByClassName()` method, `querySelectorAll()` returns a *static* NodeList that represents the matched elements.

> When in doubt, use `querySelectorAll()` over `getElementsByClassName`, solely for the fact that the returned value is static. This means that, should you store its value in a variable, that value will never change without your direct manipulation. The reference to that element will not disappear simply because a class has been removed. 

Perhaps it's easiest to see in action. 

Given the HTML CSS:

```html
<ul>
  <li>These</li>
  <li>Are</li>
</ul>
<ul>
  <li>Unordered</li>
  <li>Lists</li>
</ul>
```

```css
.applied-class{
    color: cornflowerblue;
}
```

Let's say we only want to target the *second* `<li>` element in each ordered list (those that contain the words "Are" and "Lists"). Then, we will give them a the `applied-class` class name. We can do so through the power of selectors AND pseudo-classes! Remember, any CSS selector is valid.

```js
// targets second children of ul elements
let listItems= document.querySelectorAll("ul > li:nth-child(2)")

// loops over result and adds classes
for (let i=0; i < listItems.length; i++){
      listItems[i].className = "applied-class"
}
```

The result is like so:

<ul>
  <li>These</li>
  <li style={{color:"cornflowerblue"}}>Are</li>
</ul>
<ul>
  <li>Unordered</li>
  <li style={{color:"cornflowerblue"}}>Lists</li>
</ul>

### Notes 

`querySelectorAll` honor *any* CSS selector syntax that is compatible with your current browser. This makes it highly customizable.

## `querySelector`

`querySelector` is a truncated version of `querySelectorAll` in that it only returns the *first* element found, as opposed to all elements that match. This is helpful for use cases where the first-encountered instance of an element is the only one of any importance. As such the returned value is a single element (like `getElementById()`) and not an array-like object/collection.

## Return Values
As you may have gathered, there are a number of formats that your DOM queries (targeting elements with JavaScript) can come in. Before closing out, let's address these a bit more.

### Single Element
Queries (searches) that look for a single element will implicitly return a single element. This means that no additional formatting is needed to use/manipulate it however you see fit. `className` can be directly accessed on the element, for example. This also means that, unless it is removed from the document altogether, that returned value will *always* point to the element in question, regardless of what changes have been made to it.


### Static Lists (AKA Node lists)
Node lists are the *static* version of HTML Collections. They are array-like objects as well, and can be looped over with `for` loops and accessed through their index.  The difference between them is that static lists are exactly that; static. In this case, "static" simply means that the information will not be changed unless you explicitly do so. If any elements are changed outside of the static list, the static list will not be updated to reflect those changes.

### HTML Collection
HTML Collections are array-like objects that contain a number of elements. The main trouble with this is the fact that it is a live record of the elements returned. If you say "find all elements with the class name `my-class`," for example, removing `my-class` from any of those elements after the fact will also remove it from your HTML Collection. 

Aside from that, they can be actively manipulated like any array, by way of `for` loops and indexes. Should you, for whatever reason, use `document.getElementsByClassName()` to return an HTML Collection, but want it to behave like a static list, you can do so by passing it into the `Array.from()` method.

```js
let collection = document.getElementsByClassName("my-class")
// convert collection into static array
collection = Array.from(collection)
```

`collection` will no longer be a live version of the elements queried.

## Final Musings 
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

Much of what has been covered in this lesson should seem *familiar* despite being so new. We have discussed additional functionality of JavaScript in the browser, but all (so far) has been based off of the power of the `document` object. Like in the previous lesson where we created elements via `document.createElement()` and appended them to our pages, so too have we utilized `document` to target elements that have already *been* created. It is our gateway to using JavaScript in the browser! Use it well, and use it often!

Review below, then complete the exercises.

- `querySelectorAll` returns a array-like object that contains all elements that match the given CSS selector.
    - All CSS selectors are valid, but must be in string format.
    - Returns a static list.
- `querySelector` returns the first encountered instance of the matched CSS selector. Returns a single element.
- `getElementById` returns the element that matches the given ID. Should be unique.
- `getElementsByClassName` returns a live HTML Collection of all elements that match the given class name. 
    - Will update when classes are added/removed.
    - Not static.

## Exercises
Access the coding environment below, and answer the following questions.

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/targeting-the-dom-js-bca?path=style.css&previewSize=100&attributionHidden=true"
    title="targeting-the-dom-js-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

Using JavaScript:

- Target the element with `id` of `section-one`
    - use two different methods

<details> 
<summary>Answer</summary>

```js
document.getElementById("section-one")
document.querySelector("#section-one")
```

</details>

- Create an array-like object `arrayLike` of all `div` elements that are children of elements with the class `flex-row`

<details> 
<summary>Answer</summary>

```js
let arrayLike = document.querySelectorAll(".flex-row > div")
```

</details>

- Create an HTML Collection `collection` of all elements with the class name `flex-item`

<details> 
<summary>Answer</summary>

```js
let collection = document.getElementsByClassName("flex-item")
```

</details>

- Create an array-like object `firstChildren` of the first children of any div with the class of `flex-row`.

<details> 
<summary>Answer</summary>

```js
let firstChildren = document.querySelectorAll(".flex-row > *:nth-child(1)")
```

</details>