![desk with pen and paper](https://res.cloudinary.com/btvca/image/upload/v1605036728/still-life-851328_1280_e5clui.jpg)


Hello, and welcome to week 4 of the BCA prework! In this final chapter, we will be incorporating everything we have learned so far: JavaScript, HTML, and CSS (together at last!). We will learn how to apply JavaScript logic (remember conditionals?) and operators to add functionality to our pages. With JavaScript in the browser, it is possible to create dynamic web pages that do more than we have previously seen. 

Using JavaScript in your web pages lets you harness its powers in a website's context: you can make certain things happen `if` other conditions are true, or `while` something exists! We'll see how to accomplish just this in the coming lessons, but for now, let's take a nice review before continuing. 

>If you need a deeper review than what has been provided here, it is highly encouraged to go back and revisit week 1! 

## Arithmetic
JavaScript has a lot of useful features that allow you to create mathematical expressions. These operators essentially include everything that you might find on your typical calculator, plus a few that are unique to programming. 

The basic operators:

- addition (`+`)
- subtraction (`-`)
- multiplication (`*`)
- division (`/`)
- exponentiation (`**`)
- remainder AKA modulus (`%`)

These follow the typical [PEMDAS](https://socratic.org/questions/what-does-pemdas-mean) order of operations, where certain sub-expressions will be calculated before others. 

Example:

```js
3 + 5 * 3 
// equals 18
(3 + 5) *3 
// equals 24
```

Numbers in JavaScript (and most programming languages) are limited in their scope and cannot exceed certain values. This means that for **really large** numbers it is possible that the number will be an estimation of the value as opposed to a precise representation. Anything beyond the number represented by `Number.MAX_SAFE_INTEGER` will be an approximation. 

> If you plan on doing large, data-intensive calculations, JavaScript may not be the most effective choice. 

JavaScript has the `Math` object that contains many properties and methods that provide additional features. Just like the `π` button on a calculator, `Math.PI` returns the ratio of a circle's circumference to its diameter, or better known as pi!

`Math.floor()` rounds the number in the parentheses *down*, whereas `Math.ceil()` rounds the number up. `Math.round()` rounds up or down to the nearest integer. 

`Math.random()` returns a random number between 0 and 1. 


## Strings

Strings are groups of characters that represent text in a programming context. They are most often used to process input from a user, but can (and will) be used to refer to aspects of CSS as well, like class names, IDs and properties. 

In JavaScript:
```js
let newString= "this is a string"
```

In HTML:
```html
<div style="color:red" class="container">This is a red element</div>
```

Strings are bookended by single quotes (`''`), double quotes (`""`), or backticks (``). Anything inside of them are considered to be nothing more than their literal value, with the exception being with backticks.

Backticks allow for *template literal*, where a computable value can be included within the string as a whole. This opens the door for more dynamic values for your strings. The value that you would like in your string (but to be calculated first) is placed with a `${}`, like so:

```js
// Math.random() returns a different number every time it is run
let randomNum = Math.random()
console.log(`The random number is: ${randomNum}`)
```

## Variables

Variables are the means in which value is stored for later use. That data can be in a variety of forms, be it strings, numbers, booleans (true or false), or more. It can also be defined in a number of ways that allow the value to be accessed based on the context in which it was defined. 

Variables can be defined with one of three keywords: `let`, `const`, and `var`. 

`const` is the strictest of the 3. When defined, you can no longer change the value bound to it. This is useful in programs where a **constant value** is needed. If that variable is going to be used in multiple places and it *needs* to be the same across all use-cases, reach for `const`.

`let` allows you to change the value that the variable points to, as does `var`. The latter, however, is an older, less safe version of the former. `var` allows you to change the value of your variable in more places than `let`, and because of the additional access allowed to it, there is an increased risk that the value changes without you necessarily intending for that to be the case.

`const` variables cannot be changed
```js
const constant = "constant"
constant = "changed"
// Uncaught TypeError: Assignment to constant variable.
```

```js
let variable = "value"
variable = "different value"
// will reassign the value of variable
```

It is deemed best practice to capitalize variable that consist of of more than one word. Here is a table for examples:

| Original        | Description                | camelCased      |
| --------------- | -------------------------- | --------------- |
| `name`          | A person's name            | `name`          |
| `firstname`     | The first name of a person | `firstName`     |
| `fullgivenname` | The person's full name     | `fullGivenName` |

## Conditionals

Conditionals are the the means in which a computer evaluates given expressions to eventually deem the statement `true` or `false`.  That decision is made when two things are compared against one another by some means, which then allows some action to be taken based on that decision. There are a number of operators used for comparisons in JavaScript.  They are as follows:

Equality (`==` or `===`) is used to determine whether two values are equal to one another. If so, the statement is true. The two equals signs allows for *type coercion*, which automatically changes datatypes and broadens the realm of valid comparisons. Three equals signs is much stricter.

```js
3 == "3" //true
3 === "3" //false
```

Inequality operators evaluate as `true` if the statement is otherwise NOT true. it effectively flips the result, and is denoted by a `!` before the operator.

```js
3 == "3" //true
3 !== "3" //false
```

The remaining operators are the *relational* operators, or those that compare the two values to one another based on their relationship to one another. This allows for a broader range of conditions to be `true` or `false` depending on the given operator. The relational operators are:


- (>) Greater Than
- (>=) Greater Than or Equal
- (<) Less Than
- (<=) Less Than or Equal

Conditionals are used with the `if` and `else` key words that incorporate these operators. The operators are used to determine when a condition is `true`, and if so, is then executed in the `if` block. Otherwise, an `else` statement can be provided to determine the code to be run should the inital `if` block not be triggered.

```js
if (condition){
// run this code if condition is true
} else {
//  run this code if condition is false
}
```
You may provide more than one operators within the `if` condition by using `&&` and `||`. 

`&&` will equate to `true` only when both conditions are true:

```js
if(conditionOne && conditionTwo){
    //  run this code if both conditions are true
}
```

`||` will equate to `true` if either conditions are true:

```js
if (conditionOne || conditionTwo){
    // run this code if either condition is true
}
```

## loops

Loops are the means in which code is executed multiple times, until a condition is met. In order to ensure that the given loop does not run forever, the loop itself must incorporate some logic that allows for the condition to evenutally be `false`.  

While there are many ways of achieving this, the two primary types covered thus far have been `while` and `for` loops.

A while loop executes its statements (another word for the code contained within the loop) as long as a specified condition evaluates to true. The condition check happens before the loop is executed, meaning there is the chance that this loop will never run. 

```js
let condition = false;
while (condition){
    // this code will never run
}
```

If you need your code to run at least once, append a `do` statement before the `while` condition. The code within the `do` block will run once before the condition is evaluated.

```js
let condition = false;
do {
    console.log(condition)
}
while(condition === true)
// will only run once
```

`while` loops need some code that, when run enough times, will eventually cause the condition to be false. This is known as an *iterator*, and prevents the never-ending loop that programmers fear.

```js
let count = 1;
while(count <= 10){
    console.log(count)
    count++;
    // The incrementer means that count will eventually be greater than 10, causing the loop to stop running.
}
```

`for` loops are highly customizable loops where your starting values and conditions are defined in one nice and neat space. They take 3 semicolon separated expressions in order to work properly:

- initial expression
- condition expression
- increment expression

This looks like so:

```js
for (let i=0; i<10; i++){
    // This code will run while i is less than 10. 
    // i increases by 1 each time this code is run.
}
```
> `i++` is shorthand for `i=i+1`

## functions

Functions are the primary means of creating code that can be reused in many different contexts. This allows us to keep our programs small, concise, and dare I say, elegant.

Functions can be declared with the `function` keyword, which effectively makes the function available anywhere in your program.

When defining a function, it is given a name that can be invoked elsewhere. Any additional *parameters* are defined here as well. The definition of the function has no innate value, but defines the relationship between the parameters (if any) and the code that will be run with that provided values later.

When the function is then given actual values, those values are referred to as *arguments*. 

```js
function timesTen(parmeter){
    console.log(parameter * 10)
}
let argument = 100
timesTen(argument)
// will print 1000 to console
```

Functions must either manipulate values outside of the function to have any effect, or explicitly define a `return` value so that it may be stored as a variable for later use.

```js
function timesTen(parameter){
    return (parameter * 10)
}
let result = timesTen(100)
// result = 1000
```

Functions deal in *scope*, which is the principle that dictates whether or not a variable is available outside of a specific function. As a general rule, whenever a variable is defined *inside of* a function with `let` or `const` (the two variable declaration keywords you SHOULD be using), it is only available to within that function, or *other* functions that are called and/or defined within it. 

Try to avoid going too deep in function declarations. This will help you to maintain your code and worry less about reference errors where your program can't "find" the variable in question. 

## Exercises

The following exercises are a cumulative review of the first 3 weeks of prework. 

<a class="jsbin-embed" href="https://jsbin.com/embed?live">Editor</a><script src="https://static.jsbin.com/js/embed.js"></script>