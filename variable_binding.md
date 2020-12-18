# Binding Variables

<a style={{color:"blue"}} href="https://forum.burlingtoncodeacademy.com/t/discussion-variable-binding/266">Discuss in Forum</a>

![twine wrapping around a pair of scissors](https://res.cloudinary.com/btvca/image/upload/v1605452229/cord-4088055_1280_y7szwr.jpg)

> Many years later, as he faced the firing squad, Colonel Aureliano Buendía was to remember that distant afternoon when his father took him to discover ice. At that time Macondo was a village of twenty adobe houses, built on the bank of a river of clear water that ran along a bed of polished stones, which were white and enormous, like prehistoric eggs. **The world was so recent that many things lacked names, and in order to indicate them it was necessary to point.**

*Excerpt from One Hundred Years of Solitude, by Gabriel García Márquez.*

So far in your programming you have used two kinds of values; Strings and Numbers. You have also used a function like `console.log('some message to log');`. Values are an important part of programming in that they serve as the data that the computer uses to perform its work. The problem with values is that they can be hard for a human to remember, they lack the meaning that we are used to in our spoken languages.

As humans we naturally want names for things. Names give us a means to communicate fluently. Names provide a common meaning.

This lesson introduces what may be the most important tool we have as programmers, the ability to apply a name to a value. It seems like a simple thing, a name, but choose good names and your program will be understandable, choose misleading or cryptic names, and your program will be frustrating and confusing.

## Names for Values

Let's imagine we need to make some calculations on circles. A length around a circles edge is known as its circumference, and mathematics tells us there is a relationship between the circumference length and the width of the circle, also called the diameter.

```
circumference is equal to the diameter multiplied by "some value"
```

Written as an equation the statement looks like this:

**C = x * d**

This "some value" is a special number in math and we are going to calculate using words and then using a programming expression.

Let's rearrange the statement above to solve for "some value".

```
"some value" is equal to the circumference divided by the diameter
```

Again written as an equation the new rearranged statement looks like this:

**x = C / d**

Given we have a circle with a diameter of 2 and a circumference of about 6.28, let's find  out what "some value" equals approximately.

**x = 6.28 / 2**

**x = 3.141592**

Wonderful, we now have a value of approximately 3.14, and if we give a name to it, we can use it within the statements above. The mathematical name for this value is **Pi**, so we should use the same name.

```
circumference is equal to the diameter multiplied by Pi
```

```
Pi is equal to the circumference divided by the diameter
```

We have just given the name **Pi** to the value which is the relationship between two other names with values. In JavaScript we could express the same things as we did using English language like so.

```js
let circumference = 6.283185;
let diameter = 2;
let pi = circumference / diameter;
console.log('Pi is approximately: ', pi);
```

The code above does several things but for now let's focus on just a couple of them.

```js
let circumference = 6.283185;
```

What you see above is called a variable binding. This creates a name `circumference` and then binds that name to the value `6.283185`. Any time that you use the name `circumference` you can then think of it as the value `6.283185`.

## Evaluating Variables

Variables are names which point at a value, in the case of the variable `circumference` it points to the value `6.283185`. You can use that variable anywhere in your program, and when the program reaches that variable it will do what is known as **evaluate** the variable. This means that the JavaScript program will look up what the value is at that point in the program.

To explain why that's important, you need to know that a variable can point to another value at different points in your program. Let's see what that looks like with an example.

```js
let circumference = 6.283185;
console.log('The circumference starts as ' + circumference);

circumference = 3.141592;
console.log('The circumference is now ' + circumference);
```

What the code snippet above is showing is that the `cicrumference` variable can change throughout your code. That is a very useful quality in a variable, because it allows for you to use a variable to do more things than simply act as a name for a value. When a variable can be updated, instead of serving as a simple label attached to a value, it serves as a labeled box where a value can reside.

Another thing you may have noticed about the code snippet is that the first time we created the variable we did it like this `let circumference = 6.283185` and the second time we created the variable we did it like this `circumference = 3.141592`.

```js
let circumference = 6.283185; // Notice the keyword let
circumference = 3.141592;     // let is not needed this time
```

*Why is `let` not needed on the second line?*

The reason for `let` being present on the first line, but not the second is subtle. The keyword `let` is used to create a variable for the first time. It has a special effect that allows for only one variable to be created with the same name in the same place. This means that the second line doesn't **create** a new variable, but instead **reuses** the existing `circumference` variable and changes the value it points to.

## Let vs. Const vs. Var

There are several ways to create variables in JavaScript, and it's confusing to know which one is correct to use. In addition to the `let` keyword that creates variables, JavaScript also has two other keywords, `const` and `var` that can perform similar functions. Why then should you use `let`?

The `const` keyword creates variables whose value, which they point to, cannot be changed. It stands for the action **create a constant**. You might be asking why creating a variable whose value cannot be changed would be useful, and the answer is that sometimes you want to **know** that a variable will not change, but still have a name for it, so that the value is easier to remember.

The `var` keyword also creates a variable, and like `let` it will allow you to change the value that the variable points to. So why do both `let` and `var` exist? The answer is that `var` is an older, and less safe version of `let`. What we mean when we say **less safe** is that `var` allows you to change the value of the variable in **more** places, it's more liberal in the access it provides to the rest of your program. That sounds like a good thing, but usually it's not. Part of your job as a programmer is to control access to data within your program, to ensure that other parts don't mistakenly change it. When you use `let` instead of `var` it's easier to ensure that the variable is safe from being tampered with.

## Valid Names

You have a lot of creativity when it comes to variable names, but your choices are not unlimited. There are rules that govern what constitutes a valid name, meaning which combination of characters will be allowed and which will not. Below we describe those rules and provide a few recommendations.

### Available Characters

When naming a variable you can choose any letters or numbers to use in the name, and you can also use the special characters `$` and `_` , but you cannot begin the name with a number. So for example if you wanted to name your variable something like `circle_1` , then that would be okay, but conversely `1_circle` would not be allowed.

```js
let circle_1 = 6.283185;
```

Keep in mind that the only special characters allowed anywhere within a variable name are `$` and `_`.  For example if you wanted to name a variable something like `circle$` that would be allowed. You can create a variable that begins with a `$`  or `_`  like `_circle$$$`, or `$$$_circle`. It's debatable whether these are **good** names for variables, but they are allowed by the rules of the language.

If you attempt to name your variable something like `first&last` which includes an illegal character within the variable `&` then you will see the following error in your browser console.

```
Uncaught SyntaxError: Unexpected token '&'
```

What this error is trying to communicate is that the character `&` is not allowed in the creation of variable names of any kind. If you use any characters other than `$` or `_` within a variable name, you will see the same error.

### camelCasingNames

Most variable names are formatted in a particular way, known as **camelCase**. This formatting is a convention, meaning that while it's not enforced by the JavaScript language, it is a common expectation by the JavaScript community.

To **camelCase** a variable, all you have to do is apply the following rules.

1. If the variable description is a single word, like `name` then just lowercase the word.

2. If the variable is described in two words like `first name` or `last name` then lowercase the first word, and uppercase the first character of the second word, then combine the two words.

3. If the variable is described in more than two words like `full given name` then perform the same operations to each word, as described in step two above.

Here are some example variable descriptions, and the **camelCased**  variable created for each description.

| Original        | Description                | camelCased      |
| --------------- | -------------------------- | --------------- |
| `name`          | A person's name            | `name`          |
| `firstname`     | The first name of a person | `firstName`     |
| `fullgivenname` | The person's full name     | `fullGivenName` |

### Reserved Words

In addition to the limitations around variable names containing special characters, there are some **words** that are not allowed for variables. These **words** are special sequences of characters that are built into the JavaScript language, and so cannot then also be used for variables.

An example of a word that would not be allowed for a variable is the word `let` this word has been reserved for the use of creating new variables, and so cannot also be used as a variable itself. Other examples include the words `const` and `var`. So for example the following would not be allowed.

```js
let var = 'my special variable';
```

If you attempt to run the code above you will receive a syntax error like the following.

```
Uncaught SyntaxError: Unexpected token 'var'
```

This error is trying to communicate that the keyword `var` cannot be used as a variable name. The error is just not very expressive, and makes that intent difficult to understand.

## Choosing Good Names
When writing code, chances are you won't be the only one to read it. Aside from leaving comments and organizing things clearly, choosing names that are reflective of what that variable holds for a value is paramount to a legible program.

> Aside from examples of basic arithmetic and a few rare edge cases, **avoid single-character variables**

let's say you're writing a program that stores a `boolean` in a variable, `true` if the number is even, `false` if its odd. 

`isEven` would be a much better choice for a variable name than say, `z`.


## Global Variables
When a variable is bound to a value on the top-level of the program (outside of functions, objects, etc,) it is called a *global* variable and is thus accessible anywhere within the program. 

If you declare a variable right at the top, line 1, first thing right out of the gate:
```javascript
let globalVar = 'I am a global variable'
```
*Anywhere* below that will be able to refer to the `globalVar`. Useful in some cases, but be mindful as well! If that variable is available everywhere (and declared with `let`,) its value is subject to change at any point!

## Exercises
Create a variable with `let` that has the value of your middle name.
    - What is a proper naming convention to do so? 
    - What are the benefits of a name like this?

Open your browser's console, and do the following:
 - "Declare 2 variables, `name` and `userName`
 - Assign value "Doug" to `name`
 - assign `name` as a value to `userName`
 - show the value of `userName` with `console.log`

<details>
<summary>Solution</summary>

```js
let name, userName
name = "Doug"
userName= name
console.log(userName)
```
</details>

Open your browser's console and do the following:
   - Declare 3 variables, `firstName`, `lastName` and `age`
   - Assign values to all 3 of these variables
      - `firstName` and `lastName` should have a string value
      - `age` should have a number value
   - Using these variables, display a string that displays their first and last name as well as their age.

<details>
<summary>Solution</summary>

```js

let firstName, lastName, age
firstName = "Bill"
lastName = "Hader"
age= 42
console.log(`My name is ${firstName} ${lastName} and I am ${age}!`)
```

</details> 
