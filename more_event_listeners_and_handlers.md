# More Event Listeners and Handlers
![silhouetted crowd at sunset](https://res.cloudinary.com/btvca/image/upload/v1606159383/celebration-3443779_1280_vtgiix.jpg)


When creating event listeners and their handlers in your web pages, there are a number of other things you can do beyond direct and immediate assignment of handlers to specific elements. By defining your handler functions in "looser" terms, you make room for reusability. A change in specificity can help your code be readable, concise, and quite powerful!

In this lesson, we will be discussing the various ways in which we can create event handlers in more general terms so that we can use them on more than a very specific instance. 

## The problem

The main issue with our previous examples, as mentioned, is reusability. Let's use an example to demonstrate the tediousness of explicitly defining every handler.  Say we have 3 identical divs, and we would like to add an event handler to each that makes them stretch out when they are hovered over. 

> You might be thinking, why not use the `:hover` pseudo-class in our CSS? The answer is that we do not want the element to return to its previous dimensions when the mouse leaves its space.

So this:

```css
div{
    width: 50px;
    height:50px;
    background-color: cornflowerblue;
    border: 1px solid black;
    margin-top: 10px;
}

div:hover{
    width: 100px;
}
```

```html
<div></div>
<div></div>
<div></div>
```

Will not work, as the `:hover` class is dependent on the state of the element. We can't achieve what we want through CSS alone. In the below example, the new `width` does not remain:

<br/>

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/prework-4-7-1?path=style.css&previewSize=100&attributionHidden=true"
    title="prework-4-7-1 on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

That leaves us with designing some event handlers to make this work. So, in order to do so, we would need to isolate/target each individual `div` and assign an event listener to it that manipulates that particular element when the event happens.

So, let's throw some JavaScript into the mix to make this work! We'll change the `:hover` pseudo-class into a regular class that we can add and remove from the class list for each element.

HTML
```html
<div id="one"></div>
<div id="two"></div>
<div id="three"></div>
```
CSS
```css
div{
    width: 50px;
    height:50px;
    background-color: cornflowerblue;
    border: 1px solid black;
}
.wider{
    width: 100px;
}
```
JS
```js
// targeting divs
let divOne = document.querySelector("#one")
let divTwo = document.querySelector("#two")
let divThree = document.querySelector("#three")

// div one handler and listener
function expandDivOne(){
    divOne.classList.add("wider")
}
divOne.addEventListener("mouseenter", expandDivOne)

// div two handler and listener
function expandDivTwo(){
  divTwo.classList.add("wider")
}
divTwo.addEventListener("mouseenter", expandDivTwo)

// div three handler and listener
function expandDivThree(){
  divThree.classList.add("wider")
}
divTwo.addEventListener("mouseenter", expandDivThree)
```
> `mouseenter` is one of the many events that are standardized across browsers. As always, refer to the full list here at <a href="https://developer.mozilla.org/en-US/docs/Web/Events" style={{color:"blue"}}>MDN's Event Reference</a>

As you can see, this does what we intend:

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/prework-4-7-2?path=script.js&previewSize=100&attributionHidden=true"
    title="thoracic-gem-stetson on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

But it's redundant! We have to create what is essentially the same exact function multiple times, just so the elements can each be given the `wider` class. Fortunately, there are other, more effective ways of reusing elements based on a few things. 

## `this` element
`this` is a key word in JavaScript that will inevitably provide a great deal of confusion. In a nutshell, the value of `this` is dependent upon the context in which it is read. Without going too in depth, `this` in the context of an event handler points towards the element itself. 

In other words, when an event listener is added to an element, and `this` is used in the handler `function` definition, `this` will refer to the element the event was triggered on.

So, in the context of our long-winded example above, the three `expandDiv*` functions can all be effectively written like so:

```js
let divOne = document.querySelector("#one")
let divTwo = document.querySelector("#two")
let divThree = document.querySelector("#three")

// One function with multiple uses
function expandDiv(){
  this.classList.add("wider")
}

divOne.addEventListener("mouseenter",expandDiv)
divTwo.addEventListener("mouseenter", expandDiv)
divThree.addEventListener("mouseenter", expandDiv)
```
<br/>
<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/prework-4-7-2?path=script.js&previewSize=100&attributionHidden=true"
    title="prework-4-7-2 on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

Now, *any* element triggered by that event can be altered in the context of the triggering event! No longer do you need to explicitly state which elements will be manipulated. The `function` handles it, thanks to `this`.

But, we still have a good bit of repeated code. We call `addEventListener` on *each* of these elements. What if there are 300 of these `div`s? You wouldn't want to manually assign the event listener to each and every one; doing so is error-prone and time consuming. Fortunately (again,) there is a better way. We can target multiple elements with our `querySelectorAll` and/or `getElementsByClassName` methods!

## Assigning Event Listeners to Multiple Elements

Oftentimes, when setting up the basic behavior of your page, you will want to set up certain handlers for whenever you trigger an event on all elements of a certain type. While pseudo-classes can handle a lot of the default styling behaviors, changing thing CSS has no jurisdiction over, `textContent` and `innerHTML`, you will find again that you need to reach for event listeners. 

In order to do so efficiently *and* effectively, you may have to assign an event handler to numerous elements in your page.

Let's say we have 5 divs, much like the ones before:

```html
<div>text</div>
<div>text</div>
<div>text</div>
<div>text</div>
<div>text</div>
```
```css
div{
    width:50px;
    height:50px;
    background-color: cornflowerblue;
    border: 1px solid black;
    /* orients text */
    color: whitesmoke;
    display:flex;
    justify-content: center;
    align-items: center;
}
```

Rendered: 

<div style={{color:"whitesmoke", display:"flex", justifyContent:"center", alignItems:"center", width:"50px", height:"50px", backgroundColor:"cornflowerblue", border: "1px solid black"}}>text</div><div style={{color:"whitesmoke", display:"flex", justifyContent:"center", alignItems:"center", width:"50px", height:"50px", backgroundColor:"cornflowerblue", border: "1px solid black"}}>text</div><div style={{color:"whitesmoke", display:"flex", justifyContent:"center", alignItems:"center", width:"50px", height:"50px", backgroundColor:"cornflowerblue", border: "1px solid black"}}>text</div><div style={{color:"whitesmoke", display:"flex", justifyContent:"center", alignItems:"center", width:"50px", height:"50px", backgroundColor:"cornflowerblue", border: "1px solid black"}}>text</div><div style={{color:"whitesmoke", display:"flex", justifyContent:"center", alignItems:"center", width:"50px", height:"50px", backgroundColor:"cornflowerblue", border: "1px solid black"}}>text</div>

Now let's say we want to change the `textContent` of the element when a `mouseenter` event occurs. When we move our mouse over it, we want the text to change to `"Ahh!"`. So, we start with the function to do so. Using `this`, we can make a handler for all instances:

```js
// changes text of an element
function changeText(){
    this.textContent = "Ahh!"
}
```
Now, instead of going into our HTML and adding `class` or `id` attributes to all of our `div`s, let's instead select all `div`s in our HTML:

```js
// changes text of an element
function changeText(){
    this.textContent = "Ahh!"
}
// targets all divs
let divCollection = document.querySelectorAll("div")
```

Now we have an *array-like object* that contains all of our `div`s we would like to assign the `changeText` function to run on when a `mouseenter` event happens. 

This can be accomplished with a `for` loop, where each element within the array-like object will have an event listener added to it:

```js
// changes text of an element
function changeText(){
    this.textContent = "Ahh!"
}
// targets all divs
let divCollection = document.querySelectorAll("div")

for (let i=0; i< divCollection.length;i++){
    divCollection[i].addEventListener("mouseenter", changeText)
}
```

The result:

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/prework-4-7-3?path=&previewSize=100&attributionHidden=true"
    title="prework-4-7-3 on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

And just like that, we have taken a problem that could have been a massive amount of code, and truncated it to the point that it can be applied to all instances with very little code. Not only that, we can now add as many `div` elements as we would like and they will *all* have the event listeners applied to them. This code is what is considered *scalable*.

> scalable code is a term used to describe code that is structured in such a way that it is not dependent on any constants that may change. The code in the example above will run properly, regardless of how many `<div>` elements are included in your HTML.

## The `event` object
Sometimes, an event itself is not enough to design the behavior you desire. Take the `keydown` event, for example. It will trigger whenever you press a key on your keyboard, but does nothing to answer additional details. What key was pressed? You need more information. Another example is the `scroll` event, that triggers whenever you scroll on a web page. The event is triggered, sure, but there is no additional information provided. Which direction? When did it happen?

This additional information lives in an *event object* that is **automatically** sent to your event handler as an argument. 

Let's take a `click` event, and affix it to a `div` that is 100px by 100px. The goal will be to use the `alert()` function to display the `x/y` coordinates of the click relative to the browser window.

We can do so like we would any other `click` event, except we will need to provide a variable that represents the event object that is automatically passed to the browser.

Let's start with the basics:

```html
<div>Click Me</div>
```
```css
div{
    width:100px;
    height:100px;
    background-color: cornflowerblue;
    border: 1px solid black;
    /* orients text */
    color: whitesmoke;
    display:flex;
    justify-content: center;
    align-items: center;
}
```
```js
// target the div
let div = document.querySelector("div")
```

The `div` renders like so:


<div style={{color:"whitesmoke", display:"flex", justifyContent:"center", alignItems:"center", width:"100px", height:"100px", backgroundColor:"cornflowerblue", border: "1px solid black"}}>Click Me</div>

Now, in our JavaScript, we need to create the `event` handler that will trigger on a click event. We'll call it `alertCoordinates`. **When we define this handler `function`, we will include a parameter that represents the event object**. This event object has the information we're looking for, in this case the `x/y` coordinates of the `click` event itself.

```js
// target the div
let div = document.querySelector("div")

// automatically takes an event argument
function alertCoordinates(event){
    alert(`X: ${event.clientX}, Y: ${event.clientY}`)
}
div.addEventListener("click", alertCoordinates)
```

Let's see it in action:

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/prework-4-7-4?path=index.html&previewSize=100&attributionHidden=true"
    title="prework-4-7-4 on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

> `clientX` and `clientY` are default properties on the event object, and can be accessed through it. Like events themselves, the properties provided to them are dependent on the type of event themselves. See the full list here: <a href="https://developer.mozilla.org/en-US/docs/Web/API/Event#Introduction">Interfaces based on Event</a>. This example is part of the "MouseEvent" section.


As you might have guessed, the information provided in the event object is dictated almost entirely by the `event` itself. Coordinates, while useful in `click` events, serve no purpose in a keyboard event, like pressing the space bar. The opposite is true as well, where there will be no indicator of what key has been pressed, as that property is irrelevant for a `click` event.

## Final Musings

![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

Thus concludes another installment of BCA's prework. As you round the final corner to completion, let's review what has been covered in this lesson before moving on to the exercises.

- To prevent redundency in your JavaScript, handler functions can be made scalable.
- `this` is a keyword that, when used in a handler function's definition, refers to the element it has been assigned to.
- When selecting multiple elements with a DOM query (`querySelectorAll` or `getElementsByClassName`), you may iterate over the result with a `for` loop.
- Event handlers that are assigned by `addEventListener` are automatically passed an event object that contains event-specific information that can be used to better inform your handler `function`.


## Exercises

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/good-kaput-physician?path=index.html&previewSize=0&attributionHidden=true"
    title="good-kaput-physician on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

Write JavaScript to accomplish the following:

### 1
Whenever a `div` with the class of `close-button` is clicked, remove the `section` element it resides in. This will effectively delete the comment as a whole.

> Note that there is no one way to accomplish this; the tools provided to you thus allow you to do so, but alternative options are welcome as well.

<details>
<summary>Hint</summary>

Add the event listener in context to the parent container. `parentNode` is a property that refer to an element's parent.
</details>


<details>
<summary>Answer</summary>

```js
let closeButtons = document.querySelectorAll(".close-button")

function removeComment(event){
  this.parentNode.remove()
}

for (let i=0; i < closeButtons.length; i++){
  closeButtons[i].addEventListener("click", removeComment)
}
```
</details>

### 2 
When clicking on the "add comment" button, create and append another comment to the bottom of the `section` with `id` `comment-section`.

<details>
<summary>Hint</summary>

`innerHTML` allows you to determine the residing HTML of an element. Create an element, define its `innerHTML`, and append it to your `#comment-section`. The `innerHTML` has been provided (to alleviate stress!)

</details>

<details>
<summary>Hint</summary>

Remember `innerHTML` is a string representation of the HTML provided; it can directly mirror an already-existing series of nested elements.
</details>


<details>
<summary>Answer</summary>

```js
let addButton = document.querySelector("#add-button")
let commentSection = document.querySelector("#comment-section")

let innerHTMLString= '<div class="close-button">[ X ]</div><heading>Title</heading><p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed doeiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim adminim veniam, quis nostrud exercitation ullamco laboris nisi utaliquip ex ea commodo consequat.</p>'

function addComment(){
  let comment = document.createElement("section")
  comment.classList.add("comment")
  comment.innerHTML = innerHTMLString
  
  commentSection.append(comment)
  
}
addButton.addEventListener("click", addComment)
```
</details>

### 3 
When the user presses the "enter" key, turn the font color of all headings to `cornflowerblue` by adding the class `title-color` to them.

<details>
<summary>Hint</summary>

The event for keyboard presses is `keydown`. The event object contains a `key` property that is a string representing the key pressed. The value for the enter key is `"Enter"` and is case sensitive.
</details>

<details>
<summary>Hint</summary>

Some event handlers, like those for keyboard events, can be assigned to the `document` object directly!
</details>

<details>
<summary>Answer</summary>

```js
let titles= document.querySelectorAll('heading')

function changeColor(event){
  if(event.key==="Enter"){
    for(let i=0; i < titles.length;i++){
      titles[i].classList.add("title-color")
    }
  }
}
document.addEventListener("keydown", changeColor)
```
</details>