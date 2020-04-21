# Arithmetic

![black and white Texas Instruments calculator](https://images.unsplash.com/photo-1563212034-a3c52118cce2?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=1080&fit=max&ixid=eyJhcHBfaWQiOjkwODQwfQ "Ray Reyes")

Solving mathematical equations has been one of the primary uses of computers since they were first created over fifty years ago. In fact the term "computer" was inherited by the ancestors of our devices from the human beings who computed the answers to long equations, often while working for the military or aerospace organizations. 



> ...Mr. Theo I. King throughout the year, in the grade of computer until April 20, 1897, and subsequently in the grade of assistant astronomer; Computer Frank B. Littell... Computer E. A. Boeger throughout the year; Computer G. K. Lawton ...

Source: [ United States Naval Observatory report 1884]((https://books.google.com/books?id=v8ARAAAAYAAJ&pg=PR4-IA110&dq=computer&hl=en&ei=ygbzTYXpNIOosQO-7YmvCw&sa=X&oi=book_result&ct=result#v=onepage&q=computer&f=false)

Today our "computers" can tally up answers to even the most difficult questions which would have required weeks or months to calculate by hand. In this lesson you will learn how to communicate a mathematical expression in JavaScript such that your computer can provide you with an answer before your finger even leaves the enter key. You will also learn about some of the limitations that are inherent with using digital device to calculate, and how you can work around these limitations.

Read on, and learn one of the most fundamental data types, Numbers, which you will draw upon often in your journey of JavaScript.

## Overview

- Simple math expressions
  
   - Adding two numbers
  
   - Subtracting two numbers
  
   - Multiplication of numbers
  
   - Division of Numbers
  
   - Exponentiation
  
   - Modulus, getting the remainder of a division

- Number types
  
   - Integers
  
   - Floats
  
   - BigInt
  
   - Scientific notation
  
   - Bases other than 10
  
   - Weird types: Nan, Infinity, -Infinity

- Operators and precedence
  
   - Parenthesis
  
   - Exponentiation
  
   - Multiplication / Division
  
   - Addition / Subtraction

- Idiosyncrasies of Floats
  
   - Rounding due to memory space
  
   - Rounding due to base 2

- Maximum Size of Integer
  
   - MAX_SAFE_INTEGER
  
   - Example of 2**53 + 1
  
   - Using BigInt as a workaround

## Simple math expressions

JavaScript can run nearly any mathematical expression you can imagine, and below we will show you how to communicate some of them.

Let's start off with some simple equations just to kick the tires a bit. In the web browser, you are using to read this, open your **JavaScript console** by following the steps in the **hello-javascript** lesson and type the following into the text area.

```js
1 + 1
```

Did you get the number `2` back? If so congratulations, you just evaluated an answer to your first mathematical expression. That seems a little too easy, so let's try something a little meatier.

```js
123 * 45 * 56 * 78 * 90
```

Is your answer the number `2175919200`?  Great work! Your computer works as expected. One of the nice things about writing math expressions in JavaScript is that what you write looks a lot like what  you would punch into a calculator, or even write out by hand on paper ... who does that any more?

Now let's try some other expressions, this time we will use more of the tools that JavaScript gives you to work with when writing math expressions. We have only seen addition and multiplication so far, bu there is a lot more we can do.

Try this on for size.

```js
6789 / 543 - 432 + 98 * 7**2
```

The answer to this expression is `4382.50276243094`

 Whoa! Suddenly you're getting introduced to a whole bunch of new tools. Let's give a quick rundown of what is going on in this example. 

You have certainly already used some mathematical operators before in school or work. Below we list the operators that we used in the code example above

**NOTE:** any of the symbols listed below can be applied to any pair of number which can both be positive, both be negative or be a mix of positive and negative.

![black retractable pen on white printer paper](https://images.unsplash.com/photo-1509228627152-72ae9ae6848d?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=1080&fit=max&ixid=eyJhcHBfaWQiOjkwODQwfQ "Antoine Dautry")

###### Addition

The **addition** symbol `+` when placed between two numbers represents the addition of the number on the left and the number on the right. The most common usage of the `+` symbol is to add two numbers, resulting in the sum of the numbers.

###### Subtraction

The **subtraction** symbol `-` when placed between two numbers represents the subtraction of one number on the left  from the number on the right. The most common usage of the `-` symbol is to subtract two numbers, resulting in the difference between the numbers

###### Multiplication

The **multiplication** symbol `*` when placed between two numbers represents the multiplication of the number on the left by the number on the right. The multiplication of two numbers results in the product of the two numbers.

###### Division

The **division** symbol `\` when placed between two numbers represents the division of the number on the left by the number on the right. The division of two numbers results in the quotient of the two numbers.

###### Remainder

The **remainder** symbol `%`, also known as the **modulus** operator, calculates the amount left over after dividing the number on the left evenly by the number on the right. The application of the **remainder** operator on two numbers will always produce a number of the same sign as the number on the left, which is the amount remaining after evenly dividing the number on the left by the number on the right.

###### Exponentiation

The **exponentiation** symbol `**`, also known as the **power** operator, calculates the value of the number on the left raised to the power of the number on the right. It results in a number equal to the the number on the left multiplied by its own value the number of times to the number on the right.

## Operator Precedence

Based on the operators that have learned above you may be asking "how do I know which of these acts on the numbers first?". The answer is that there are rules that determine which classes of operators which take **precedence** over others. 

The table below has a column **priority** which describes based on ascending numbers in which operators are applied, also called **evaluated**, first. This means that an expression using an operator with a **priority** of 1 is **evaluated** *before* one with an operator of **priority** 2. If there are two operators used in the same expression with the same **priority** then the **associativity** rule determines which one is applied first.

| Priority | Operator       | Associativity |
| -------- | -------------- | ------------- |
| 0        | Grouping       | N/A           |
| 1        | Exponentiation | Right to left |
| 2        | Multiplication | Left to right |
| 2        | Division       | Left to right |
| 2        | Remainder      | Left to right |
| 3        | Addition       | Left to right |
| 3        | Subtraction    | Left to right |

Do you notice something familiar about the rules in the table above? They are the same rules as those used in general mathematics called the **order of operations**. Maybe you remember them as their acronym **PEMDAS** or by their mnemonic:

> Please-Excuse-My-Dear-Aunt-Sally

This mnemonic is used to remember the following order or precedence rules:

- Parenthesis

- Exponentiation

- Multiplication  and Division

- Addition and Subtraction

You might notice that there is anther kind of operator in that list which we haven't covered yet called **grouping**. Can you guess which mathematical operator this represents?

If you guessed **parenthesis** then you are correct! 

The pair of left and right **parenthesis** operators `( )` are used together to represent a **grouping** within a larger expression, and this means that **grouping** will be evaluated before its result is then used in the larger expression.

![](https://upload.wikimedia.org/wikipedia/commons/7/76/AST_binary_tree_arithmetic.svg)

Example of a simple expression tree

Source [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:AST_binary_tree_arithmetic.svg)

## Number types

In most programming languages there are multiple types of numbers, for example there are **Integers** which are whole numbers, or numbers without a fractional component, and there are **Floating-Point Numbers** that are numbers which are represented by some fraction or fractional approximation. Many people think of **Floating-Point Numbers** also called **Floats** as numbers that have some number of digits after the decimal point or `.`, such as `3.14159` or `2.71828`. These are numbers that can be approximated in JavaScript by taking some integer and raising it to some exponential value.

When you express a number in JavaScript that number will by default be a **Floating-Point number**. This is a bit of strange behavior on the part of JavaScript as most languages choose to represent numbers without a decimal point value as **Integers**, but JavaScript has chosen a different route. In order to create a number in JavaScript that **IS** and integer, you can use a fairly modern addition to the language known as **BigInt**. This feature of the language allows for you to represent **Integers** in a similar way to other languages, but with the caveat that **BigInt** numbers can only be used with other **BigInt** numbers. Check out the example below.

**NOTE**: *You will need to be using a relatively recent version of Google Chrome, Mozilla Firefox, or Edge to use this language feature. Internet Explorer and Safari will not work.*

```js
1n + 2n
```

Did you get the answer `3n`? If so congratulations! You just added your first two JavaScript **BigInt** numbers. 

Why do these kinds of numbers exist? Well it's a bit complicated, but is has to do with how much information can be stored in a regular old JavaScript **Number** type. To make a long story short, there is only so much room within the default **Number** type, and so as your number gets **really** large, as in quadrillions, then it's possible that when you combine that number with another using math you *could* get the wrong answer. By using **BigInt** for **Integer** numbers you do not have to worry about those limitations, but you **DO** have to use them together with other **BigInt** numbers, and you **DO** have to be using a modern browser or another JavaScript environment.

## Idiosyncrasies of Floats

JavaScript has a somewhat strange way of representing numbers by default, in that **ALL** numbers are **Floating Point** unless told to be some other kind, this decision carries with it some strange behaviors. One of the side-effects of this decision is that numbers which are integers, without a value after the decimal point, behave as expected when using any of the basic mathematical operators up to very large numbers. However numbers that **DO** have decimal point values can behave in ways not expected in comparison to those that you might enter into a calculator.

This behavior is best communicated using examples, so please take a look at the JavaScript below and test it out by running it in your browser's console, like prior lessons.

##### Normal Integer Subtraction

```js
100 - 58
```

Do you get the number `42` as the result of the subtraction expression above?

Excellent!

This shows that integers can be subtracted from one another and yield the expected result.

##### Floating Point Subtraction

```js
0.3 - 0.2 - 0.1
```

Did you get the exact number `0`?

Huh, I wonder why not?

##### Floating Point Subtraction Answer

The reason you didn't get `0` as an answer above is that JavaScript cannot represent the number `0.1`exactly using the **Floating Point** number representation scheme. Before you start getting angry at JavaScript for its bad decisions, consider that **ALL** programming languages that use **Floating Point** have to make the same trade-offs for representing them. This is due to the way all computers store information, which is represented as a series of `0s` and `1s` known as binary which we will cover later. Some numbers can be represented exactly using binary, while other numbers such as `0.1` or `0.7`cannot. As a result of this, numbers which are the result of certain mathematical operators involving these approximations, are themselves approximations.

![clear glass pitcher](https://images.unsplash.com/photo-1570438395701-aee966d0e8bc?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=1080&fit=max&ixid=eyJhcHBfaWQiOjkwODQwfQ "Zac Harris")

## Maximum Safe Integers

Recall above where we explained how an **Integer** has a limited space in which to be stored by JavaScript. This means that for **really large** numbers it is possible that the number is an estimation of the value, rather than a precise representation. What this means is that there is a number in JavaScript which is the maximum **integer** that you can be sure to be represented exactly. Any **integers above**  this number have the possibility to be in-precise and therefore result in the wrong value when combined with  other numbers.

This maximum safe **integer** number is equal to `9007199254740991`, written another way it is `2` raised to the power of `53` minus `1`

```js
2**53 - 1
```

This number also has a special representation that might be a little easier to remember.

```js
Number.MAX_SAFE_INTEGER
```

Here's an example to illustrate the point, run these  expressions in your browser console and see their results.  Notice anything strange?

```js
Number.MAX_SAFE_INTEGER
Number.MAX_SAFE_INTEGER + 1
Number.MAX_SAFE_INTEGER + 2
```

# Exercises

# Assessments
