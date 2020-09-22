# I/O in the Browser
![coffee cup and beans](https://res.cloudinary.com/btvca/image/upload/c_limit,h_540,w_1080/v1600709948/coffee-171653_1280_ntdjqd.jpg)

A barista takes a bag of mouthwatering coffee beans and empties it into the industrial grinder. Out comes fine grounds, coarse grounds, medium-coarse grounds, any grounds of their choosing! These are then put into a state of the art machine that makes the hot brown bean water that keeps the world moving. It's both delicious, and a prime example of what we're here to talk about today: input and output.

**Input** and **Output** describe the ongoing relationship between the information or items being provided (input), and the product of that information or item's consumption (output). 

In the above example, there were 2 instances of the Input/Output (often shortened to "I/O") relationship. The first was when the barista loaded the coffee beans into the grinder and unloaded coffee grounds.

```
coffee beans => grinding => grounds
       input => process  => output
```

The second was the grounds being brewed into coffee

```
grounds & hot water => brewing => coffee
              input => process => output
```

Simply put, something goes in, something comes out. In this case, coffee. In computer programming, however, this relationship is more abstract. It deals with information. Typing, mouse scrolling, e-commerce, navigating the browser, playing games, you name it! 

For the scope of this lesson, we're going to discuss one of the simplest use cases; I/O in the browser. 

# The Browser
![PNG of browser icons](https://res.cloudinary.com/btvca/image/upload/c_limit,h_540,w_1080/v1600709346/browser-773215_1280_au75hj.png)

Google Chrome, Mozilla Firefox, Apple Safari, Microsoft Internet Explorer. I'm sure many of these are familiar to you. Chances are pretty good you're using one to read this right now. I, of course, am speaking of the web browser.

Simply put, a web browser is a software application that assists a user in navigating the World Wide Web. Through its *graphical user interface* (GUI), a user can request pages, provide credentials, view multimedia, follow links... you know, internet stuff. 

It does so by retrieving information from other parts of the web via *Hypertext Transfer Protocol*, or *HTTP*. *HTTP* is fundamental in designing and enforcing how data like images, text, and video, are sent and received between pages. This data is typically received in the form of HTML, which we will cover more in depth in the next module.

For now, just know that the browser is a GUI that lets a user efficiently navigate and *interact* with the network of pages laid out before them. 

**Interact?** 

Yes! Modern web browsers come with not only their own native functionality, but full JavaScript support as well. As a web developer, you will be utilizing this JavaScript compatability constantly. Creating login forms, buttons, animations, transitions, you name it! 

When writing JavaScript that is to be run in the browser, the primary way of invoking this functionality is with the `window` object.

# The `Window` object

`window` is a reserved word in JavaScript that has a *huge* amount of functionality behind it. With it, you can make all sorts of things happen in the browser, from scrolling and selecting, to opening new tabs and resizing! All with JavaScript.


While still on this page, open up your console and enter the following:

```js
window
```
You should see something similar to the following:
![window](https://res.cloudinary.com/btvca/image/upload/v1600790639/window_object_sz8q8u.png)

Click on the arrow to the left to view its contents, and you should see something like so:

![window object](https://res.cloudinary.com/btvca/image/upload/v1600790639/window_object_2_iptesh.png)

This is the window object, in all its glory. There is an amazing amount of information and resources here that you will familiarize yourself with over time. Don't worry about understanding everything; There is a lot of functionality you can harness quickly and easily.


Let's take a look at a basic example. In the same console, underneath the window object, enter the following:

```js
window.open()
```
Boom! You just opened a new tab with JavaScript. Please don't judge the number of tabs I had open.

![new tab](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1600788078/newTab_l7dfkq.png)

Now, in the console on that new, empty tab, enter this:

```js
window.close()
```

Boom! You just closed that same tab. 

Now, there is, as seen, a lot more `window` can do than opening tabs. You can find a full list on [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Window#Methods), but for now let's highlight a few more. 

## `window.print()`

`window.print` opens the print dialog modal on the current page (frequently referred to as a *document*).

```js
window.print()
```
![print modal](https://res.cloudinary.com/btvca/image/upload/c_limit,h_540,w_1080/v1600789259/print_modal_yc0sth.png)

## `window.scrollBy()`

`window.scrollBy()` scrolls the document in the window by a provided amount.  That amount comes in x-y pixel coodrdinates, and is based relative to the current location of the window. The top left of any given window is the coordinate `0,0` and the height and width of said window is dependent on screen and current window size. 

At any time, you can access the current X or Y position of the page with `window.scrollX` and `window.scrollY`, respectively.

Give it a shot! 
```js
window.scrollBy(0,1000)
// will scroll the page down 1000 pixels
window.scrollY
// will return how far down (in pixels) the page you window currently is
```

## `window.prompt()`

`window.prompt()` creates a *prompt* dialog box that halts all current processes on the page until the user inputs a value or cancels. The text displayed in the box is a string-coerced version of whatever is passed to it. That value is then returned, and can be assigned to a variable for further use.

```js
let answer = window.prompt("What is your name?")
console.log(answer)
// should return the value entered in the prompt box
```
![prompt window](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1600795290/prompt_window_qolppv.png)

While there are far more elaborate examples of collecting user input, `window.prompt()` is widely supported across browsers and is an great starting place to understand and begin dealing with user input in a browser context. 

## `window.confirm()`

Like `window.prompt()`, `window.confirm()` displays a dialogue box with the string version (or "stringified version") of whatever has been passed into it. This box still has 2 options, `OK` and `Cancel`, but instead of having a text box to enter information into, it will return `true` if `OK` has been selected, and `false` if `Cancel` has been selected.

This makes it perfect for verifying, or *confirming* information previously entered. And, because it only returns `true` or `false`, we can use it in a condition, too!


```js
if (window.confirm("are you sure?")){
    console.log("you are sure!")
} else {
    console.log("you are NOT sure")
}
```
## `window.alert()`

`window.alert()` is another use that incorporates a dialogue box, although this one simply displays text to the user. It strips functionality down, but still "pauses" everything in the process. Clicking `OK` will cause things to resume.

```js
window.alert('login successful!')
```

## A note on compatability

>Not all browsers are created equally! They are constantly being updated and revised, so some of the more abstract or peripheral aspects of the `window` object may not be supported on certain browsers. The examples covered in this lesson were explicitly chosen for their wide support and simplicity. 

# Final Musings

Remember, this is just the tip of the iceberg. More will be covered in the coming weeks, and all will be made clear. If you have questions, good!! 

Here are some takeaways to hold onto for now:

 - Browsers are used to visually navigate the WorldWide Web
 - All major browsers natively support the use of JavaScript.
 - That usage is made available by the `window` object
 - The `window` object is **full** of information and functionality that pertain to the browser.

 ## Exercises

 Define a function `askName` in the browser's console that, when called, asks you for your name. 
 
 After entering a name, ask the user to confirm if that is in fact their name.

 If the user confirms, displays a custom hello message with their name. 

 Otherwise, display the generic message, "Hello, user!"

 <details>
 <summary>Hint 1</summary>
Start with a function definition so you can later call this code multiple times! AKA:


 ```js
function askName(){
    let name = // your codehere
}
 ```
 </details>

 <details>
 <summary>Hint 2</summary>

You can store the value of a window prompt in a variable for later use:

```js

```
 </details>

 <details>
 <summary>Hint 3</summary>

Use `window.confirm()` to verify whether the entered value is desired.

 </details>

 <details>
 <summary>Solution</summary>

```js
function askName() {
    let name = window.prompt("What is your name?")
    let isTrue = window.confirm(`You entered: ${name}. Are you sure?`)
    if (isTrue) {
        window.alert(`Hello, ${name}!`)
    } else {
        window.alert(`Hello, user!`)
    }
}
```
 </details>
