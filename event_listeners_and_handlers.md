![silhouetted crowd at sunset](https://res.cloudinary.com/btvca/image/upload/v1606159383/celebration-3443779_1280_vtgiix.jpg)

So, up until this point, we have been addressing fundamental aspects of JavaScript in the browser. By including a `<script>` with relevant code inside or linked to it, we can both `create/append` elements to our document as well as target those and other elements for further manipulation. The latter, targeting and manipulating, has been effectively glorified JavaScript. We load our HTML, CSS, and JavaScript relatively instantaneously. The effects of CSS and JavaScript have been relatively interchangeable because of this; add a class here or there, and change the `color` or `font-size`.

The true strength of JavaScript in the DOM is its ability to change things on your page after certain triggers. What if you want to make a button that, when clicked, removes an item from the page? What if you want to trigger an alert window when scrolling down the page? What if we want to change the color of an element based on the keys pressed? All this and much, much more is capable through the use of browser events.

In this lesson we will discuss browser events, listeners, and handlers, as well as some common use cases. 

## Introduction to Browser Events: Events as Attributes

Events in the DOM are an implicit part of making responsive and functional web pages. They are supported occurrences that your browser can notify your code of. Any time you interact with your browser by clicking, scrolling, typing, highlighting, focusing, opening, closing, and so on, the browser is emitting an **event**. 


These events can then be customized by you via the JavaScript you provide to your page. To say there are a few events would be a massive understatement; for practically everything a browser is capable of, there is an event that you can "latch onto" in order to have the desired effect. 

To get a taste of just how many events there are, check out  <a style={{color:"blue"}} href="https://developer.mozilla.org/en-US/docs/Web/Events">MDN's Event Reference List</a>

So what's it look like in action?

Let's start with a simple example, and go on from there. Take this HTML:

```html
<button onclick="alert('Button Clicked')">Click Me</button>
```

That will render like so. Click to see it in action:

<button onClick={()=> alert('Button Clicked')}>Click Me</button>

This is one of the many ways to include a *click event handler* to our web pages. Here, the JavaScript is included directly in our HTML through the `onclick` attribute. That JavaScript (effectively the `alert` function,) is what is known as the *event handler*, or what is actually triggered during the event. 

That is simply one way to handle a click event. On top of that, it's not exactly a convenient way to do so. Like so many things in web development, it is made easier with a separate JavaScript `script` to handle the details and keep everything else more manageable. 

We can separate the two, like so. Assume that the JavaScript is linked properly to our HTML.


```js
function countdown() {
  alert("T minus:");
  for (let i = 3; i > 0; i--) {
    alert(i);
  }
  alert("Blastoff!");
}
```

```html
<body>
    <button onclick="countdown()">Click Me</button>
</body>
```

See it here:
<br/>

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/countdown-example-event?path=script.js&previewSize=100&attributionHidden=true"
    title="countdown-example-event on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

<br/>

Now we're getting somewhere! Our `function` (AKA handler, or the code we run when the event is triggered), is moved into our JavaScript file, allowing us to make a more complicated function without making our HTML entirely illegible. This also gets the job done, but it is far from the only (or best) option available to you. 

Let's discuss the other options: events/handlers as element properties, and events/handlers in pure JavaScript.

## Event Handlers as DOM Properties

We've seen that with browser events, we can directly add an attribute to our HTML with the `onclick` (among many) event handler. Then, we can either define the function's behavior as the value to the `onclick` attribute, or point it to the `function` defined elsewhere in our JavaScript. 

The next possibility is to directly assign the handler using a DOM property. We can do so by adding the `onclick` attribute that is normally found in the HTML directly to the JavaScript! This will employ our JavaScript selectors we learned in the previous lesson (like `querySelector`).

Below, we can see that in action. Given a `button` element with a unique `id`, we can easily target and assign the `onclick` attribute that has been previously assigned directly the HTML:


```html
<button id="my-button">Click Me!</button>
```

```js
// target the button in the HTML
let button = document.querySelector("#my-button")
// define the function to call when clicked
function buttonClick(){
  alert("Button Clicked!")
}
// provide the function definition to the button
button.onclick = buttonClick
```

This will render like so:

<br/>
<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/onclick-example-javascript-bca?path=style.css&previewSize=100&attributionHidden=true"
    title="onclick-example-javascript-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

### Notes

>When assigning the *event handler* to your elements, you always want to pass your `function` definition and not function call. In simple terms, this means you should provide something like this:

<h3 style={{color:"#4BB543"}}>Correct Way:</h3>

```js
button.onclick= buttonClick
```

<h3 style={{color:"#FC100D"}}>Incorrect Way:</h3>

```js
button.onclick= buttonClick()
```
<br/>

When you add the `()` parentheses to the end of a function, you are *calling* the function immediately when it encountered. Instead, we want to provide the `function`'s definition so that it will be *called* when the event happens. In this case, it's when the button is clicked. Otherwise, the function will be immediately called when the page loads, effectively defeating the purpose of the event handler!

## `addEventListener`

Ok. Now that we've covered the relationship between HTML and JavaScript vis a vis event handlers, we can focus on a more thorough way of going about it. All of the examples above have one thing in common: `onclick`. That attribute (and any other that refers to other event handlers) has one glaring flaw, and that is that there can only be a single handler for that event. 


If we take our previous example and assign more than one `onclick` property, the second will overwrite the first!

```js
// adds buttonClick function to click event
button.onclick = buttonClick 

// overwrites the previous handler
button.onclick = differentClick
```

This is fine for simple examples and a means to familiarize yourself with the process, but the **standard** way of adding event listeners and handlers is with the `addEventListener` method. 

Effectively, the `addEventListener` method needs 2 arguments that determine the `event` and the `handler` for that event. It is called on the element that you would like to add the event listener to.

This looks like so:

```js
targetElement.addEventListener(eventType, eventHandler)
```

Let's refactor the previous example one more time, utilizing `addEventListener`. Given the same HTML:

```html
<button id="my-button">Click Me!</button>
```

We can target the button in the same way as before, with `querySelector`.

```js
let button = document.querySelector("#my-button")
```
 the next step is to define the function that we will be using as an event handler. Let's use the same `buttonClick` function as before:

 ```js
let button = document.querySelector("#my-button")

function buttonClick(){
  alert("Button Clicked!")
}
 ```
 
Lastly, we must take that target element and call `addEventListener` on it. Then, we pass a *string* that represents the desired event as the first argument, and the handler function as the second:

```js
let button = document.querySelector("#my-button")

function buttonClick(){
  alert("Button Clicked!")
}

button.addEventListener("click", buttonClick)
```

This will be the same result as before, with the `function` definition (no parentheses) passed as the second argument. Again, the big benefit here is that we can add more than one event listener to the targeted element. Why limit yourself?

We can add as many event listeners as we want this way. Let's define a second function, `secondClick` and add an event listener so that it triggers after the first:

```js
let button = document.querySelector("#my-button")

function buttonClick(){
  alert("Button Clicked!")
}

function secondClick(){
  alert("Button Clicked Again!")
}

button.addEventListener("click", buttonClick)
button.addEventListener("click", secondClick)
```

Now, when clicked, 2 handlers will be called, one after the other. Give it a shot below:

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/addeventlistener-example-bca?path=script.js&previewSize=100&attributionHidden=true"
    title="addeventlistener-example-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>


> Again, this lesson uses `click` events predominately for examples. For a full list of events, visit <a style={{color:"blue"}} href="https://developer.mozilla.org/en-US/docs/Web/Events">MDN's Event Reference List</a>


## removeEventListener
A second (and important) aspect of `addEventListener` is `removeEventListener`. As the name implies, this allows us to remove the event listener from a particular element so that we can effectively deactivate it. It takes the same form as its counterpart, `addEventListener`:

```js
targetElement.removeEventListener(eventType, eventHandler)
```

The important aspect of this is that the `removeEventListener` must take the SAME EXACT function as the one that was passed to it. In other words, you must define the `function` (handler) elsewhere as a standalone variable and pass it to both `addEventListener` and `removeEventListener` under the same variable name.

```js
function handlerFunction(){
  alert("handler")
}

targetElement.addEventListener("click", handlerFunction)
targetElement.removeEventListener("click", handlerFunction)
```

> If the same variable, `handlerFunction` in the above case, is not directly provided to both methods, the `removeEventListener` will not receive a proper "pointer" to the handler function, and thus will not know what exactly to remove. Being clear and explicit with our `function` definition before passing it off to the event listener methods is your best bet.

## Final Musings

![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

There you have it! Your first step towards making your page that much more functional with JavaScript. Let's review what we've covered in this so far, then move onto the exercises.

- `onclick` (and other `on*` attributes) can be assigned to your elements in HTML as the attribute `onclick="someFunction()"`
  - limit one per element
  - not the standard
- `on*` can be added in your JavaScript as a *property*
  - `targetElement.onclick=someFunction()`
- `addEventListener` is the web development standard for adding event listeners and handlers to your HTML elements.
  - passed `function` definition, NOT `function` call()
- `removeEventListener` must receive the same `function` name in order to properly remove the event listener on the targeted element.


## Exercises

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/event-listener-exercises-bca?path=script.js&previewSize=0&attributionHidden=true"
    title="event-listener-exercises-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

### 1 Adding classes on click

Add JavaScript so that the `button` element with the `id` of `question-one` will gain the class `hidden` when clicked. This should hide the button when clicked.

<details>
<summary>Answer</summary>

```js
let button = document.getElementById("question-one")

function addClass(){
  button.classList.add("hidden")
}

button.addEventListener("click", addClass )
```
</details>

### 2 CSS transitions on click

Add a click event to the `div` element with the `class` of `question-two` so that it will add a class `bigger` to your `div`. If the class `bigger` is already *on* the `div`, remove it.

**Bonus points for utilizing a CSS transition!**


<details>
<summary>Answer</summary>

```js
let div = document.querySelector(".question-two");

function toggleSize() {
  if (div.classList.contains("bigger")) {
    div.classList.remove("bigger");
  } else {
    div.classList.add("bigger");
  }
}

div.addEventListener("click", toggleSize);
```
</details>

### 3 Count by double clicking

Using <a style={{color:"blue"}} href="https://developer.mozilla.org/en-US/docs/Web/Events">MDN's Event Reference List</a>, add JavaScript to the `input` element with the `id` of `question-three` so that, when double clicked, the `div` with the `id` `counter` increases by 1 every time. 

> Be mindful of data types! `textContent` is evaluated as a string, and we're dealing in numbers here. Be sure to convert the current `textContent` to a number before incrementer. Otherwise, you may be concatenating! 

<details>
<summary>Answer</summary>

```js

let incrementer = document.querySelector("#question-three");
let counter = document.querySelector("#counter");

console.log(incrementer)
console.log(counter)

function increment() {
  console.log("clicked")
  counter.textContent = +counter.textContent + 1;
}

incrementer.addEventListener("dblclick", increment)
```
</details>