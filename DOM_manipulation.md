# DOM Manipulation
![Marionette](https://res.cloudinary.com/btvca/image/upload/v1601662492/wooden-mannequin-791720_1280_afuriq.jpg)


As you begin building dynamic web pages and apps, you might find the need to change the document structure and add additional functionality to make them look and behave like you'd like them to. This is typically done through *manipulating* the DOM, a browser interface that allows you to program changes to your page or app. These extensively use the `document` object, which allows you to target a specific element or elements (see DOM Queries) and perform changes on said element(s).

In this lesson, we will cover some of the basic use cases when targeting an element or node on a given page. With the help of JavaScript, you'll be able to change your web page, adding all sorts of delightful features!

Let's start with the basics.

## DOM manipulation 101
Let's say we have a link on our page that brings us to BCA's home page:

```html
<a id="example-link" href="https://burlingtoncodeacademy.com">Burlington Code Academy</a>
```
It looks like this: <a id="example-link" href="https://burlingtoncodeacademy.com">Burlington Code Academy</a>

In our JavaScript, we  can *select* it with a DOM query, like so:

```js
let link = document.querySelector('#example-link')
```

Now, we can manipulate the `link` variable we have used to define the selected anchor element. This `link` variable has a number of properties that are open for change now that you have selected it and stored it in a variable. Let's start by changing the `href` of our *selected element*:

```html
<a id="example-link" href="https://burlingtoncodeacademy.com">Burlington Code Academy</a>
```

```js
let link = document.querySelector('#example-link')
link.href="https://www.google.com"
```
Voila! Thanks to the DOM, we are able to treat any *selected element(s)* as objects to be manipulated directly with our JavaScript. Now, that same link, when clicked, will redirect you to Google instead. But, the text that comprises of the link itself has not changed yet.So, we effectively have this:

```html
<a id="example-link" href="https://www.google.com">Burlington Code Academy</a>
```
The site redirect has been changed, but now the link is misleading! So we'll need to change another aspect of this anchor element: `textContent`. You can do so in the same way as `href`. Because the variable selected is an *anchor* tag, some of those properties that can be altered are the same as the *attributes* on the element itself (like `href`), and others are more general, being things you will find shared among many elements when working with DOM scripting. 

```js
let link = document.querySelector('#example-link')
link.href="https://www.google.com"
link.textContent="Google"
```
And now, what is still a link to the BCA website in the HTML, is now a link to Google in our DOM. The DOM has been *manipulated* to alter the appearance and functionality of our page! 

## Making new elements

Sometimes, you will need to programatically create elements and add them to your page through some code. You can do so with a similar practice to DOM queries, by using methods exposed to your program through the `document` object.

Let's look at the previous example of the BCA anchor tag we've been using. Immediately after it, as a sibling element, we want to add a `<p>` (paragraph) with a brief description of the site.

We want the end result to be something like this (in HTML):

```html
<a id="example-link" href="https://burlingtoncodeacademy.com">Burlington Code Academy</a>
<p>Learn the skills to change your career.</p>
```

To do so with solely JavaScript, we must take the proper steps. 

- create a container the element will reside in (if one does not exist)
- create the element you'd like to add
- add that element to the container

let's go step by step.

### create a container

For simplicity's sake, we'll add a container to the starting HTML. You can do so with JavaScript, but we get into a chicken-or-the-egg scenario where we create the container which needs a container which needs a container, etc...

So, our starting HTML will look like this:

```html
<section id="container">
    <a id="example-link" href="https://burlingtoncodeacademy.com">Burlington Code Academy</a>
</section>
```
Now, the goal is to add a paragraph inside of `#container`

### create the element you'd like to add

In our JavaScript, we create a paragraph element with the `document.createElement()` method. This method takes a string that represents the tag name in question, but does NOT take the `<>` that typically denote the start and end to an HTML tag. 

Let's make the paragraph and give it some text here, like so:

```js
// 
let description= document.createElement('p')
description.textContent= "Learn the skills to change your career."
```

This code creates a `<p>` and gives it the text content it needs. Now we have the element created in our JavaScript, but it hasn't been *placed* anywhere yet.

### add the element to the container

The final step to adding an element to the DOM is with another method on the `document` object, `appendChild()`. We can do so by targeting the *parent node*, or in this case the `#container` element. We can do so like this:


```html
<section id="container">
    <a id="example-link" href="https://burlingtoncodeacademy.com">Burlington Code Academy</a>
</section>
```
```js
// creates paragraph element
let description= document.createElement('p')
// customizes paragraph element
description.textContent= "Learn the skills to change your career."
//targets parent
let container = document.querySelector('#container')
// adds paragraph to parent node
container.appendChild(description)
```
This is the general flow you'll need for adding nodes/elements to the DOM. You'll use these methods frequently, so get used to them!

## Moving (and removing) elements
You can also move and remove nodes from the DOM. Moving elements is relatively straighforward, given you have a reference variable for the element you'd like to move, and one for what you'd like to move it next to. 

If you have a section with multiple elements, like so:

```html
    <section id="container">
        <div id="one">item1</div>
        <div id="two">item2</div>
        <div id="three">item3</div>
    </section>
```
You can use selectors to target the elements you'd like to move around, like so:

```js
let container = document.querySelector('#container')
let itemOne = document.querySelector('#one')
let itemThree = document.querySelector('#three')
```
Then, you can use `insertBefore()` and `insertAfter()` to adjust the order of these elements like so:

```js
container.insertBefore(itemOne, itemThree)
```

The first argument is the node/element you'd like to insert, and the second is the node you'll be referencing to insert before or after. 

using `appendChild()` will, by default, add the given node as the last child in the parent node/container. If the node given as an argument already exists in the container, it will simply be moved to the end. Easy!

## Changing styles 1

You can, like any other attribute in an element, actively change their CSS styles with JavaScript. You can access the `style` property on any element, and then any CSS property within that `style` property. 

Let's take an ordinary paragraph:

```html
<p id="example-paragraph">This is a paragraph, it exists solely to be styled.</p>
```
We can target it with a DOM query in our JavaScript like so:

```js
let paragraph= document.querySelector('#example-paragraph')
```

Now, `paragraph`, like all DOM objects, has a `style` property on it which allows for direct manipluation of any CSS properties!

```js
paragraph.style.color= "red"
paragraph.fontSize= "25px"
```

**Note that `font-size` in CSS is now camel-case `fontSize` when manipulated directly with JavaScript. This is an idiosyncrasy you simply must remember.**

## Changing styles 2

You can also use the `setAttribute()` method to directly add and remove classes on your elements. Doing so prevents the use need to mix JavaScript in a single file, and allows you to add classes, IDs, or whatever attributes you might need a little more programatically.

Assuming we have this in our css:

```css
.big-paragraph {
    color: red;
    font-size: 25px;
}
```

We can simply add the class to our `paragraph` variable we defined previously:

```js
let paragraph= document.querySelector('#example-paragraph')
paragraph.setAttribute('class', 'big-paragraph')
```

The first argument for `setAttribute` is the attribute name, and the second is its value. That effectively sets the class of the paragraph to `big-paragraph`, which has been defined in our CSS.

## Event handlers
These DOM manipulations are used to alter the document in some way shape or form. As is often the case, these changes can be "triggered" by certain *events* that happen on the page (think clicking, scrolling, entering information, etc.) 

>Event handling a very large topic that deserves its own lesson entirely, but below is a quick example of how DOM manipulation is utilized through these events. If you have no experience with event handlers yet, do not worry. This is simply meant to stretch your brain a bit :)

Here, we make a `div` with the `id` of `click-div`. The goal is that, when clicked, the text will increase in size to `25px` and turn `red`. 

```html
<div id="click-div">placeholder text</div>
```

So, in our JavaScript, we create what is known as an *event listener*:

```js
let clickableDiv = document.querySelector('#click-div')
clickableDiv.addEventListener('click', () => {
    clickableDiv.style.fontSize = '25px'
    clickableDiv.style.color = 'red'
})
```
What this effectively says, is that when *clicked*, the `fontSize` and `color` of `clickableDiv` will be changed. Again, don't dwell on it too much right now, just know that *events* are a common way to trigger the DOM manipulation we've covered in this lesson. Think of this as a context in which you will be practicing DOM manipulation!

## Final Musings
![sunset](https://res.cloudinary.com/btvca/image/upload/v1599682636/sunset-1211475_1280_xtjrjn.png)

You can use JavaScript to make changes to your initial HTML through the DOM. With it:
- You can alter current DOM nodes by targeting them with DOM queries
- You can create and add elements to the DOM
- You can remove and rearrange elements in the DOM
- You can add styling to the selected element(s)
- You can use *events* to make changes to the DOM based on behavior on the page.


Happy Coding :)

-Paul