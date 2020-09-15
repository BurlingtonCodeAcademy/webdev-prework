# Intro
This lesson is intended for those with a basic understanding of JavaScript classes, insomuch that the general syntax is not one of complete mystery to you, the reader. This is instead intended for those who, like most starting developers, need a deeper dive into the curious world of `this`. So, buckle up! We're diving right in!
# This
 ![This](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1600174955/zachary-keimig-VW2UGDpbN94-unsplash_imru8o.jpg)

`this` is a keyword whose value and nature changes based on the environment it finds itself in.

Most of the time, the definition of `this` is dependent on how a function is called. In other words, it isn't something that is assigned or declared, but rather innately holds a value based on the context surrounding it when the script is run. 

This example is pulled directly from the [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this):

```javascript
const test= {
    prop: 42,
    func: function(){
        return this.prop
    }
}

console.log(test.func())
// expected output: 42
```

Here, we have an object named `test` that has been given a property `prop` with a value of `42`. There is a second property on `test` that is the method `func`. `func` is referred to as a method because it is a function as a property on the object `test`. That method returns `this.prop`. So, when called: `test.func()` will return `42`.

In this case, `this.prop` is 42. That is because `this` points towards the context in which it is called. That context is `test`. `this` IS `test`! But that's only once case of what it could be. Let's take a deeper look at the different contexts in which `this` can be used.

The value of `this` is dependent on its *execusion context*. 

## Global Context

![Earth at Sunrise](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1600112565/sunrise-1756274_1920_mdhvke.jpg)
When working outside of any functions or objects or classes, `this` refers to what is known as the global object. The global object is always defined, and much like `this` itself, is dependent on the context in which it is called. That can be (understandably) a bit much to wrap your head around, so let's use an example. 

When running JavaScript in the Browser, `this` in the global scope refers to the `Window` itself. One can just as easily refer to the `Window` object by name and accessing browser-specific [properties](https://developer.mozilla.org/en-US/docs/Web/API/Window#Properties) such as position on a page, address, width of the browser window and many, many more. 

In a Node environment, however, `this` is usually local to that module. Without going too in-depth, that means that when you `require` a module in your script, that module is incorprated through a function that gives `this` its value.

The top-level `this` is then referred to as `globalThis`, which is always defined and contains the core-functionality like `console` and `require` of node, much like `Window` does in the browser. In these 2 contexts `this` is again different. Let me show you! 

The first example is what is known as `globalThis`, or `this` when running node on the CLI. With no file (module) to run, `this` is executed at a top-level and thus returns `globalThis`, or `global` (same thing, different identifiers)
```
λ node                         
Welcome to Node.js v13.8.0.     
Type ".help" for more information.                               
> console.log(this) 

//expected output:      
<ref *1> Object [global] {                                       
  global: [Circular *1],                                         
  clearInterval: [Function: clearInterval],                      
  clearTimeout: [Function: clearTimeout],                        
  setInterval: [Function: setInterval],                          
  setTimeout: [Function: setTimeout] {                           
    [Symbol(util.promisify.custom)]: [Function (anonymous)]      
  },                                 
  queueMicrotask: [Function: queueMicrotask],                    
  clearImmediate: [Function: clearImmediate],                    
  setImmediate: [Function: setImmediate] {                       
    [Symbol(util.promisify.custom)]: [Function (anonymous)]      
  }                                                              
}                            
```
It's fine if this looks like gibberish to you for the moment. Just know that, when outside of a script, `this` and `globalThis` are one in the same, and contain most of your highest level functionality are are available in all modules. 



## Function Context

![functions](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599680156/functions_title_card_ftkut4.jpg)

When you're in a JavaScript file, the *execution context* changes once again!

Say we have a file:

```javascript
//thisTest.js
console.log(this)
```
And we run it:

```
node thisTest.js
// expected output: {}
```

We see that it returns an empty object, and not the `global` object we saw before. This is the other node case mentioned. Because `this` is now in a script (`thisTest.js`). This is also known as *function context*

Here we make a function with 2 parameters, `firstName` and `lastName`, and assign them to `this` as properties. We also include a method `greet` which prints a string when called. In this context, *this is an empty object* but like any other object, can be manipulated and added to in order add functionality and store values. The difference is that the context points to the function itself. 

Then, we will ready this function for export as a *module*

```javascript
//exportModule.js
module.exports = function (firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.greet = function(){
        console.log(`Hello, my name is ${this.firstName} ${this.lastName}`)
    }
}
```
In a separate file, we'll run this code:

```javascript
// importModule.js
let person = require('./exportModule.js')
let joey = new person('Joey','Baggadonuts')
joey.greet()
//expected output: Hello, my name is Joey Baggadonuts
```
We see here that, when imported as a module, the instance created from it with the `new` operator maintains the `this` instilled within the function's definition, as `this` is local to a module.


In simple words, the value of `this` comes from when it's called. And, when its called globally, it looks to that global context. If you're in the browser, it finds the `Window`. If you're on the CLI, it's `globalThis`. If you're in Node JS script, it's local to the module.

But mose of these are atypical use cases for `this`, although its helpful in understanding how `this` operates. Let's take a look at the most applicable use case:

## Class Context

Mostly, you'll encounter `this` in a `Class` context. When writing code inside of a `Class` body (everything inside the `{ }`,) `this` will be a regular object, much like when we were defining the function before in `exportModule.js`. When defining methods on a `Class`, then, those methods will be available to the class within its definition.

Let's take a look at a basic example

```javascript
class Example {
    constructor() {
    }
    method1() {
        console.log("I am the first method")
    }
    method2() {
        this.method1()
    }
}

let test = new Example()
test.method2()
// expected output: "I am the first method"
```

As the example shows, `this` is defined with the context of itself in mind. `method2` is using `this` to access `method1`, even though they are both methods defined in the `Example` class.  

That same level of reflexive behavior can be used to assign properties in the `constructor` method, which is an intrinsic part of what makes a class behave as it does. 

> Aside: The `constructor` method is a special and *reserved* word in JavaScript that allows for the initializing of an object when created with a `class`. They're unique, and much like the highlander, their can be only one (per `class`)

```javascript
class Person {
    constructor(name, age, address) {
        this.name = name
        this.age = age
        this.address = address
    }
    greet() {
        console.log(`Hello, my name is ${this.name}`)
    }
}
let paul = new Person('Paul',29,'123 Main St.')
paul.greet()
//expected output: Hello, my name is Paul
```
Whenever a `class` is *instantiated* with the `new` operator, an empty object is *bound* to it that contains the properties and methods you set up as part of its definition.

In this example, `paul` has 3 properties: name, age, and address.

They can be referred to in the definition of the class as `this.<property-name>`, and outside as the class instance's property name, like `paul.<property-name>`. `this` acts as a self-referencing placeholder term that is replaced by whatever the instance is called. This makes it ideal for classes, as the definition can act as a sort of template for which to define the properties and methods of `this`.

Using `this` when defining a `class` is extremely useful when creating multiple objects that have the same or very similar properties. This makes your code more readable, and much shorter.

Which do you see saving more time and code?

a)
```javascript
let stacy ={
    name:'Stacy',
    age:18,
    address: '456 South St.',
    greet: function(){
        console.log(`Hello, my name is Stacy`)
    }
}
let paul ={
    name:'Paul',
    age:29,
    address: '123 Main St.',
    greet: function(){
        console.log(`Hello, my name is Paul`)
    }
}
let emma ={
    name:'Emma',
    age:36,
    address: '898 Pine St.',
    greet: function(){
        console.log(`Hello, my name is Emma`)
    }
}
```

b)
```javascript
class Person {
    constructor(name, age, address) {
        this.name = name
        this.age = age
        this.address = address
    }
    greet() {
        console.log(`Hello, my name is ${this.name}`)
    }
}
let stacy = new Person('Stacy',18,'456 Sout St.')
let paul = new Person('Paul',36,'123 Main St.')
let emma =new Person('Emma', 36,'898 Pine St.)
```

The answer, of course, is **b.** 

The `class` uses the awesome power of `this` to reflexively bind values to each individual *instance* of the `Person` class. Yes, this makes your code a bit more abstract, but at the cost of infinite possibility!

# Other `this` behavior

## Binding `this`
Sometimes, when the *execution context* of a method is secondhand, `this` will not point to the original context, but rather the new context it is found in.

Let's take our original example:

```javascript
const test= {
    prop: 42,
    func: function(){
        return this.prop
    }
}

console.log(test.func())
// expected output: 42
```

If we were to assign the method `func` to a new variable, like so:

```javascript
let unboundFunc= test.func
console.log(unboundFunc())
// expected output: undefined
```
The output will not be `42`, as the context in which it is called is now outside of `test` and at the global scope. To remedy this, we use the keyword `bind` to maintain the original context.

```javascript
let boundFunc = test.func.bind(test)
console.log(boundFunc())
// expected output: 42
```

These cases are on the rarer side, as you can simply access methods through the original object, but it does drive home the point that the *execusion context* is the most important aspect of defining and using `this`. 


## Arrow Functions
In arrow functions, `this` points toward the enclosing level of *execution context*, so it will always point *lexically* up a level, no matter where it is called. Arrow functions maintain that context regardless of the place they're called. 

As such, they should not be used as methods, but make a fine use case *inside* of methods, as they bind to the same place.

example:

```javascript
function Person() {
    this.age = 42,
        this.greet = function () {
            let arrowFunc = () => console.log(`Hi, I'm ${this.age}`)
            arrowFunc()
        }
}
let personAge = new Person()
personAge.greet()
//expected output: Hi, I'm 42
```

If `arrowFunc` was defined as a `function` declaration, the `this` keyword in its definition would not point to its enclosing scope where `age` was defined:

```javascript
function Person() {
    this.age = 42,
        this.greet = function () {
            let arrowFunc = function(){
                console.log(`Hi I'm ${this.age}`)
            }
            arrowFunc()
        }
}
let personAge = new Person()
personAge.greet()
//expected output: undefined
```

Arrow functions contextualize `this` lexically, in that they refer to their enclosing scope to justify its value. Useful, especially in higher level concepts!

# Final Musings


![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

`this` is a lot, and that's that! Highly adaptable and elusive in its concept, `this` has grown alongside JavaScript's many iterations to the point where it comes in many forms based on its evnironment. 

But don't be wary of `this`! Using it in the proper context, we can:

- define a `class` in ways that make your code highly scalable.
- access the browser's `Window` given the proper context
- Create highly modular subsets of code that you can then `require` in your main file
- create dynamic methods based on the properties given to a function or class. 

For further reading, I (as always,) suggest familiarizing yourself with [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this) and the way they approach topics. Although dry at times, the material there will never steer you wrong. 

Happy Coding :)

-Paul