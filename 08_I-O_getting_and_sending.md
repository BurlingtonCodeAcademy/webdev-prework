# Input and Output

Telephones. Coffee grinders. Engines. People.

Things that take a thing and use it to do a thing, or give back a different thing. What, that's not helpful? 

As redundant as that statement may be, it demonstrates the fundamental idea of **Input/Output**, often referred to by its shorthand, **I/O**. It's probably not surprising to hear, but necessary to discuss, especially in the context of computer programming. 

So let's leave the coffee grinders and telephones by the way side and discuss the properties of Input/Output (I/O) in a context useful to us programmers: the command line.

But first, what is I/O in computing?

![keyboard](https://res.cloudinary.com/btvca/image/upload/v1599749989/keyboard-70506_1920_u4tbm6.jpg)

When dealing with computers, I/O is the process in which an entity receives some information, interprets that information, and does something based on that interpretation.

In other words, the *input* is the signal, and the *output* is the response to the signal. Let's look at some common examples.

Some devices, like keyboards and mouses (mice?), are what is known as **input-only**. They are the starting point for a user-fueled signal, be it a click, a keystroke, or a scroll. 

Others, like speakers and printers, are **output-only**. These are an end-point to a chain of events. You click "print" (the input), and the printer prints (the output). Pretty straightforward stuff so far, right? 

The combination of these two types of devices creates an I/O relationship, or an *interface*. Thus, a thing (printer) takes a thing (mouse click) and does a thing (prints a document).

Cool. Pretty straightforward. Now:

**It starts to get fun when you, the programmer, start working on customizing that I/O to do what YOU want it to do.** 

For the following lesson, we're going to be creating an I/O workflow from the CLI (command line interface).


# Getting User Input
![command line](https://res.cloudinary.com/btvca/image/upload/v1599750226/command-line-pt-2-8-1243728_cmpytn.jpg
)
The CLI is a default standard interface for programming due to its ease of use and ability to integrate into different operating systems through what's known as a *shell*.

It's also a compound *input* and *output* device. Think about it! 
- You enter a command
- You receive information back

Input AND output!

**So what's that look like in a JavaScript context?**

JavaScript was a browser-only language that, thanks to **Node.js**, has the capacity to run in its own environment locally on your computer. It comes bundled with a ton of useful stuff for controlling the execution of your program. The first thing we'll look at is the `process` object.

`process` is available in a node environment right out of the gate, and comes with a ton of info and tools to control your current, well, process!  

It has a property called `process.stdin` that is directly tied to the command line's input. That input comes in the form of a *readable stream*. Don't worry too much about that for now, just know that these are used to handle *dataflow*. In this case, that dataflow is the input provided by you, the user. 

So what's that look like? At its most basic level, this:

```javascript
process.stdin.on('data',(function(chunk){
    console.log(chunk)
})
) //will print: <Buffer 50 61 75 6c 0d 0a>
```
Wait hold up, what's this **Buffer** nonesense?

It's all part of the readable stream! Again, don't worry too much about it for now. Essentially, it's the form that the input takes when text is entered to the command line. It's made visible on a `data` event, which is triggered when the input is entered and the function that uses `console.log` is called.

Buffers are objects that represent data that has a fixed length. When that data is supposed to wind up as a *string*, you can make it visible (AKA "decode it") by calling a *method* on it. 

What's that look like?

It looks like this!

```javascript
// input.js
process.stdin.on('data',(function(chunk){
    console.log(chunk.toString())
})
)
```
The big takeaway is that, to see your input, you need to *stringify that buffer* 

And if we try this, we'll see something like the following:

![hanging curosr](https://res.cloudinary.com/btvca/image/upload/v1599765909/hanging_cursor_whz5rj.png)

And when you enter some text...

![input](https://res.cloudinary.com/btvca/image/upload/v1599766075/Input_r2vjgq.png)

It logs back what you enter! success!

In our previous code, the user's input is available for all sorts of shenanigans now in the form of the `chunk` parameter. Of course, all we're doing is turning it into a string and printing it to the command line as the *output*.

Here, let's do something else with it to drive the point home:

```javascript
process.stdin.on('data', (function (chunk) {
    let input = chunk.toString()
    console.log(`You entered the following text: ${input}`)
})) 
```
![better example](https://res.cloudinary.com/btvca/image/upload/v1599832051/i-o_example_j8aw2c.png)

This isn't much different than the previous example, right? It only really serving to emphasize the fact that `chunk` is your information, and by appending `.toString()` to it, it converts that *buffer* into something readable.

# Sending Output

![skateboard phone](https://res.cloudinary.com/btvca/image/upload/v1599832410/sport-3365503_1920_rrhf4m.jpg)

As you may have guessed, the *output* aspect of I/O is handled by the `console.log` in the previous example. While `console` is meant for debugging purposes, its printing capabilities make it an excellent choice for any sort of default command line *output*. 

Under the hood, it accesses `process.stdout`, just like the *input* was accessed by `process.stdin`, and prints to the CLI with a new line character appended to the end.  

Thus `process.stdin`/`process.stdout` is our I/O relationship.

**Now, let's say you want to prompt the user to enter some information. It asks a question, and the user answers. Good news: Node has you covered.**



## readline
![Books](https://res.cloudinary.com/btvca/image/upload/v1599835857/books-1245690_1920_nmgj68.jpg)

Node has a massive list of *modules*, which you can think of as additional features that come bundled with an initial node installation. All you have to do is give your file the go-ahead to be used in your specific program. 

To create an *interface* that uses the command line we'll need to include the core-node module `readline`. 

From the [Node](https://nodejs.org/api/readline.html#readline_readline) documentation:

>The `readline` module provides an interface for reading data from a *readable stream* (such as `process.stdin`) one line at a time. It can be accessed using:

```javascript
const readline = require('readline')
```
Some of that should sound familiar:

- Readable stream
- `process.stdin`
- interface

Didn't we just do that? Yes we did! But now we can do it with the help of the `readline` module. In doing so, we create a more versatile application in which we can utilize the tools it comes with. What tools? I'll show you!

Readline has a *method* called `createInterface` that can be used to configure its I/O, among other things (like how many spaces in a tab, what the default prompt character is, things like that.) For now, let's focus on setting that up. 

```javascript
const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});
```
> Note: `const` is another keyword used for variable declaration. Unlike `let`, `const` is used for things that are not meant to change. Once declared, they will not take kindly to being changed. Short for *constant*.

See the `process.stdin` and `process.stdout`? They're both included in the `createInterface` instance `rl`. Now that we've defined what our interface is, we can use it to design our program! `rl` now has access to all sorts of fun stuff, like `.question()`!

Remember our example? Say we want the command line to display a question and wait for a response. `readline` makes that easy to do. 

```javascript
const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

rl.question("Do you like to code?\n", function(answer){
    rl.write(`You answered: ` + answer)
    rl.close()
} )
```
Running this code produces a result like so:

![readline example](https://res.cloudinary.com/btvca/image/upload/v1599836880/readline_example_dcgzvd.png)

There are a few things going on here, so let's break it down:

- `question()` has 2 parameters
    - The prompt (text) that is printed to the configured output (`process.stdout`)
    - The `function` that does something with the `answer` variable (could be named anything). The user's input is given to this function as that variable name.

`rl` also has access to `write()` and `close()`
- `write()` takes a string and *writes* it to the defined output
- `close()` ends the exchange and allows the program to continue

In this case, because our interface's *output* has been configured to `process.stdout`, you could also use `console.log`. As mentioned in our previous example, `console.log` is printing to `process.stdout` under the hood, so they both would achieve the same result. 

There's more than one way to do most things in programming, so don't be afraid to ask questions and try something new! And with that being said, that ends this intro to I/O.

# Final Musings

The CLI is an *interface* that is accessed in a node environment through `stdin` and `stdout` on the `process` object like so:

- `process.stdin`
- `process.stdout`

Node comes bundled with many helpful modules to handle some of the more prevalent tasks, like user input on the CLI.

the `readline` module helps take the guesswork out of handling readable streams and buffers from `stdin`, as well as provides functionality for programs to handle user input in a manageable and *modular* way. 

For more on this topic and topics like it, I suggest going right to the source. Although it might be confusing at first, try to familiarize yourself with the format of frequented-traveled technologies. It will help you immensely down the road.

https://nodejs.org/api/readline.html#readline_readline

Happy coding :)

-Paul