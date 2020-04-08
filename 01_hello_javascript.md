# Hello JavaScript!

![placeholder](https://via.placeholder.com/350x200)
<caption><em>Image of a Robot waving hello</em></caption>

Welcome to the first lesson of our course pre-work! You are about to begin a journey of learning about programming that will change the way that you think about problems, solving problems, and the world around you.

In this first lesson we will keep the concepts fairly high level and cover what programming is all about, why JavaScript is important in the modern technology landscape, and how to write your first lines of code.

## Overview

- What is Programming?
  - What do we mean when we say 'Programming'?
  - What are 'programming languages'?
  - How are programming languages different then spoken languages?
- Why JavaScript?
  - why are you learning JavaScript instead of Python, Ruby, C++, etc
  - How the demand in JavaScript jobs is accelerating
  - How a Browser is becoming a universal deployment target
- Opening the Web Browser Developer Tools
  - Opening the Browser Inspector using the menu bars
  - Opening the Browser Inspector using the keyboard shortcuts
  - Opening the Browser Inspector using the mouse right click
- How to Run JavaScript
  - Navigating to the JavaScript console
  - Running some simple math
- The Syntax of Hello World
  - Words, period, parenthesis, quotes, and semicolon

## What is Programming?

### What do we mean when we say Programming?

Long ago, people used to program computers by connecting wires from one physical circuit to another, which allowed electricity to flow through parts of the computer, energizing clusters of wires that saved their charge as data. This was the very beginning of the computer era, and many techniques and tools had yet to be invented.

Years later people built special tools that punched holes into stacks of cards, which were read by other special devices and the process of connecting the circuits was automated away from the hands of programmers. This allowed for faster reading of the instructions, without the delay of moving connections manually.

More years passed and then instead of punching holes into cards and having a computer read those cards the process was performed on special keyboards which were connected directly to the computer, this allowed the programmer to type keys and see their output immediately on a screen. After the program was written it could be translated into machine instructions that would operate the computer's central processing unit(CPU) and display the output on a screen.

Today we can write programs the same way those programmers did decades ago, by writing our instructions down in a file and running that file, and we can also write and run a program directly within our web browser. We can use our program to change a web page, receive inputs from a user, and make decisions based on those inputs.

This act of encoding human though into instructions that a computer can understand is known as programming, and it is powerful ability that will change the way you think about solving problems.

### What are Programming Languages?

Just like in human spoken or written languages where there are many ways to describe the same thoughts, there are many "programming languages" that can represent the same instructions, but in different ways.

A computer is not like a thinking person who can "interpret" the meaning of a message even if it's vague, or has multiple meanings. A computer is not able to determine what to do if there is any wiggle room in your instructions, it only does what it is told. For this reason human languages are ill fitted for providing computers instructions to carry out. Even the most specific forms of human language like the law, medical, scientific, or mathematical descriptions fall short of the specificity needed. This is why decades ago a group of people came together and determined how to create the first "languages" that computers could understand.

There have been thousands of distinct programming languages created since their first introduction over fifty years ago. Of those thousands there are about about one hundred which are still in common use today, and of those there are about a dozen languages that you might have heard of. See if you recognize some of these language names:

- JavaScript
- C
- C++
- Python
- SQL
- Java
- C#
- Visual Basic .NET
- PHP
- Go

Do any of those languages ring a bell? Each of those languages are used in hundreds of thousands of applications. In fact your computer is using some of those languages at this very moment while you are reading this lesson.

The reason that there are so many languages is that each one has been designed to do something better than or different than all the other languages that existed at the time. It's a bit like thinking about why there are so many different insects, or birds, or fish. Each kind of thing specializes in something different, and that makes it the right tool for a certain job.

### How are Programming Languages Different Than Spoken Languages?

Let's think about how to answer a simple question. How would you describe the process of printing a list of prime numbers, less than one ten?

Below is the [Wikipedia definition of a Prime Number](https://en.wikipedia.org/wiki/Prime_number):

> A Prime Number is a natural number greater than 1 that cannot be formed by multiplying two smaller natural numbers

Here is another description of a prime number:

> A prime number is a whole number, greater than one which is only evenly divisible by itself and one.

And here is one way to describe the process of printing a list of prime numbers.

```
Starting at the lowest prime number, 2
Check if the given number is a prime number
  By dividing the number by those lower than it, starting at 2
    And checking if there is a remainder when the number is divided by the possible divisor
      When the remainder is zero, the number is NOT prime
      When the remainder is not zero, the number MAY be prime
    If after dividing by all numbers lower then the number, there is a remainder for each
      Then the number is prime
If the number is prime
  Print out the number
  And increment the given number by one
If the number is not prime
  Increment the given number by one
Stop when the given number exceeds the maximum number
```

As humans we can read the description above and think about how this could be performed on a sheet of paper. Unfortunately a computer is not able to translate the text written above into basic operations that run on a CPU and use data from computer memory. Computers need more explicit instructions to follow, and those instructions have to adhere to the rules of a given programming language. Have a look at the JavaScript code below, which follows the steps written above.

```js
let max = 10;
let currentNumber = 2;

while(currentNumber < max) {
  let divisor = 2;
  let isPrime = true;

  while (divisor < currentNumber) {
    let remainder = currentNumber % divisor;
    if (remainder === 0) {
      isPrime = false;
      break;
    }
    divisor = divisor + 1;
  }

  if (isPrime === true) {
    console.log(currentNumber);
  }

  currentNumber = currentNumber + 1;
}
```

The JavaScript code that you see above is a precise set of instructions which tells the computer what to do in order to print out all the primes from two up to ten. When the computer reads those instructions there is zero ambiguity for the steps it must follow. As a human however you may have a difficult time reading and understanding the code above. During the next several lessons you will see and understand what each part of that program does, such that you could write your own version which results in the same output.

## Why JavaScript?

### Why are you learning JavaScript instead of Pythin, C/C++, Ruby, etc.

The JavaScript language is the language of the web. It has a special place in the internet world as the language that is able to run **natively** on all web browsers. As a result of this, nearly every webpage you use has some form of JavaScript running on it. While there are many programming languages, some of which we listed above, we chose JavaScript for the following reasons.

1. JavaScript is ubiquitous, running on billions of devices and hundreds of billions of web pages.
1. JavaScript is portable between every modern computer, meaning the same code can run on many different devices.
1. JavaScript is expressive, meaning we are able to express our thoughts and intents within the language to a large degree.
1. JavaScript can run in the browser as well as on web-servers and databases. This allows us to use one language in multiple places, amplifying our reach as programmers.
1. JavaScript is evolving and improving rapidly. Meaning that new features are being added to the language constantly.


