# Hello JavaScript!

#### [View in Forum](https://forum.burlingtoncodeacademy.com/t/discussion-hello-javascript/264)

![white robot near brown wall](https://images.unsplash.com/photo-1485827404703-89b55fcc595e?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=1080&fit=max&ixid=eyJhcHBfaWQiOjkwODQwfQ "Alex Knight")

<caption><em>Image of a Robot saying hello!</em></caption>

Welcome to the first lesson of our course pre-work! You are about to begin a journey of learning about programming that will change the way that you think about problems, solving problems, and the world around you.

In this first lesson we will keep the concepts fairly high level and cover what programming is all about, why JavaScript is important in the modern technology landscape, and how to write your first lines of code.


### What do we mean when we say Programming?

Long ago, people used to program computers by connecting wires from one physical circuit to another, which allowed electricity to flow through parts of the computer, energizing clusters of wires that saved their charge as data. This was the very beginning of the computer era, and many techniques and tools had yet to be invented.

Years later people built special tools that punched holes into stacks of cards, which were read by other special devices and the process of connecting the circuits was automated away from the hands of programmers. This allowed for faster reading of the instructions, without the delay of moving connections manually.

![white microwave oven](https://images.unsplash.com/photo-1574027542338-98e75acfd385?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=1080&fit=max&ixid=eyJhcHBfaWQiOjkwODQwfQ "Alex Motoc")

More years passed and then instead of punching holes into cards and having a computer read those cards the process was performed on special keyboards which were connected directly to the computer, this allowed the programmer to type keys and see their output immediately on a screen. After the program was written it could be translated into machine instructions that would operate the computer's central processing unit (CPU) and display the output on a screen.

Today we can write programs the same way those programmers did decades ago, by writing our instructions down in a file and running that file, and we can also write and run a program directly within our web browser. We can use our program to change a web page, receive inputs from a user, and make decisions based on those inputs.

This act of encoding human thought into instructions that a computer can understand is known as programming, and it is a powerful ability that will change the way you think about solving problems.

### What are Programming Languages?

Just like in spoken or written languages where there are many ways to describe the same thoughts, there are many "programming languages" that can represent the same instructions, but in different ways.

A computer is not like a thinking person who can "interpret" the meaning of a message even if it's vague, or has multiple meanings. A computer is not able to determine what to do if there is any wiggle room in your instructions, it only does what it is told. For this reason, human languages are ill-fitted for providing a computer instructions to carry out. Even the most specific forms of human language like the law, medical, scientific, or mathematical descriptions fall short of the specificity needed. This is why decades ago a group of people came together and determined how to create the first "languages" that computers could understand.

![MacBook Pro on brown wooden surface](https://images.unsplash.com/photo-1544980919-e17526d4ed0a?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=1080&fit=max&ixid=eyJhcHBfaWQiOjkwODQwfQ "Joshua Aragon")

There have been thousands of distinct programming languages created since their first introduction over fifty years ago. Of those thousands there are about one hundred which are still in common use today, and of those there are about a dozen languages that you might have heard of. See if you recognize some of these language names:

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

Do any of those languages ring a bell? Each of those languages are used in hundreds of thousands of applications. In fact, your computer is using some of those languages at this very moment while you are reading this lesson.

The reason that there are so many languages is that each one has been designed to do something better than, or different than all the other languages that existed at the time. It's a bit like thinking about why there are so many different insects, or birds, or fish. Each kind of thing specializes in something different, and that makes it the right tool for a certain job.

### How are Programming Languages Different Than Spoken Languages?

Let's think about how to answer a simple question. How would you describe the process of printing a list of prime numbers, less than ten?

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

As humans we can read the description above and think about how this could be performed on a sheet of paper. Unfortunately a computer is not able to translate the text written above into basic operations that run on a CPU and use data from computer memory. Computers need more explicit instructions to follow, and those instructions have to adhere to the rules of a given programming language known as **syntax**.

Have a look at the JavaScript code below, which follows the steps written above.

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

The JavaScript code that you see above is a precise set of instructions that tells the computer what to do in order to print out all prime numbers from two up to ten. When the computer reads those instructions there is zero ambiguity for the steps it must follow. As a human however you may have a difficult time reading and understanding the code above. During the next several lessons you will see and understand what each part of that program does, such that you could write your own version which results in the same output.

## Why JavaScript?

### Why learn JavaScript instead of Python, C/C++, Ruby, etc.

The JavaScript language is the language of the web. It has a special place in the internet world as the only language that is able to run **natively** on all web browsers. As a result of this, nearly every webpage you use has some form of JavaScript running on it.

There is a quote by Netscape co-founder Marc Andreessen that states:

> *More and more major businesses and industries are being run on software and delivered as online services - from movies to agriculture to national defense.
> ...
> Six decades into the computer revolution, four decades since the invention of the microprocessor, and two decades into the rise of the modern Internet, all of the technology required to transform industries through software finally works and can be widely delivered at global scale.*

From: [Why Software Is Eating the World - Andreessen Horowitz](https://a16z.com/2011/08/20/why-software-is-eating-the-world/)

As software continues to "eat the world", JavaScript is the knife in its hand.

![selective focus photography of cutlery on bucket](https://images.unsplash.com/photo-1523674714772-4ea01e5ce882?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=1080&fit=max&ixid=eyJhcHBfaWQiOjkwODQwfQ "chuttersnap")

While there are many programming languages, some of which we listed above, we chose JavaScript for the following reasons.

1. JavaScript is ubiquitous, running on billions of devices and hundreds of billions of web pages.
2. JavaScript is portable between every modern computer, meaning the same code can run on many different devices.
3. JavaScript is expressive, meaning we are able to communicate our thoughts and intents within the language in precise and creative ways.
4. JavaScript can run in the browser as well as on web-servers and databases. This allows us to use one language in multiple places, amplifying our reach as programmers.
5. JavaScript is evolving and improving rapidly. Meaning that new features are being added to the language constantly.

![](https://miro.medium.com/max/1358/0*RAW-_uc7AcSli4aL)

###### Image from NPM Inc. This year in JavaScript 2018

Link: <https://medium.com/npm-inc/this-year-in-javascript-2018-in-review-and-npms-predictions-for-2019-3a3d7e5298ef>

### Accelerating JavaScript Jobs

The number of jobs available that require JavaScript experience has been increasing for years, and will continue to increase for the foreseeable future. JavaScript's position within technology has been growing at an astounding rate, largely due to the importance of the web browser as a target for applications, and the standardization of web browser APIs over the past decade.

In addition to there being more jobs in need of JavaScript skills, the overall satisfaction with the language has been increasing for several years. This can be seen in the recent StackOverflow developer survey, which listed JavaScript as the most popular language in 2019.

> For the sixth year in a row, [JavaScript](https://stackoverflow.com/jobs?sort=i&q=javascript) is the most commonly used programming language. Python has risen in the ranks, surpassing C# this year, much like it surpassed PHP last year. Python has a solid claim to being the [fastest-growing major programming language](https://stackoverflow.blog/2017/09/06/incredible-growth-python/).

Beyond the world of JavaScript, the role of "Software Developer" has become the #1 job in the United States according to U.S. News & World Report.

- https://money.usnews.com/careers/best-jobs/software-developer

### JavaScript Skills in Demand

Take a look at the following study [2018 Student Developer Report by HackerRank](https://research.hackerrank.com/student-developer/2018#skills) and notice that the demand for JavaScript skills is greater than those available by potential employees. A recent report by [Devskiller](https://devskiller.com/technical-hiring-skills-report-2019/#Two) in 2019 also outlines that based on over 100,000  skills tests that 70% of companies are looking to hire for developers who understand JavaScript. All of this demand equates to higher average developer salaries as evidenced by the [PayScale JavaScript salary calculator](https://www.payscale.com/research/US/Skill=JavaScript/Salary).

![](https://www.hiringlab.org/wp-content/uploads/2020/01/top_skills_full_stack_developer.png)

### JavaScript Frameworks are Growing

Along with the number of jobs available to developers growing year-after-year, the tools available have also continued to keep pace with the breadth of uses for JavaScript. Among the most popular frameworks available today, [Node.js, Angular, and React sit in the top three places among all languages](https://insights.stackoverflow.com/survey/2018/#technology) according to the Stack Overflow developer survey. In 2019 the State of JS survey found that in 2019 there were six widely used frameworks for just front-end JavaScript and that React, the framework taught in our boot camp, 71% of respondents have used React and would use it again.

![](https://miro.medium.com/max/1400/0*7jbtUx39ehZHpiG4)

###### React framework popularity growth, from NPM Inc. This year in JavaScript 2018

Link: <https://medium.com/npm-inc/this-year-in-javascript-2018-in-review-and-npms-predictions-for-2019-3a3d7e5298ef>

## How to Run JavaScript

### Navigating to the JavaScript Console

Open a new tab in your web browser by clicking **File** then **New Tab** in the **Menu Bar** and then within the new tab opening the browser's JavaScript Console by following the command below based on your web browser type.

#### Open the Browser Console

The browser developer tools are an important tool while programming client side JavaScript. They are included in all modern browsers and can be accessed via several methods.

---

#### Google Chrome

##### Official Documentation

Take a look at the documentation from Google if any of the instructions below are confusing.

[Open Chrome DevTools - Google](https://developers.google.com/web/tools/chrome-devtools/open "Open Chrom DevTools - Google")

##### Open the JavaScript console using the Menu Bar

Near the top right of the Chrome window find a button with **three vertical dots**, then click, "**More Tools**", then  "**Developer Tools**", and then click the "**Console**" tab in the window that opens.

#### Open the JavaScript console using right-click

Anywhere on the currently loaded page, use the right-click mouse button and select **Inspect**, you should then see a developer tools window appear at the bottom, or the right-hand side of your browser. Within the developer tools window, select the tab with the name **Console**.

#### Open the Browser Inspector with a Keyboard Shortcut

`Command + Option + J (Mac)` or `Command + Option + I`

`Control + Shift + J (Windows, Linux, Chrome OS)` or `Control + Shift + I`

---

#### Mozilla Firefox

##### Official Documentation

Take a look at the documentation from Mozilla if any of the instructions below are confusing.

[Open Firefox Developer Tools - Mozilla](https://developer.mozilla.org/en-US/docs/Tools "Open Firefox Developer Tools - Mozilla")

##### Open the JavaScript console using the Menu Bar

At the top of the Firefox window find the **Tools** menu, then click **Web Developer**, and then click **Web Console**.

#### Open the JavaScript console using right-click

Any where on the currently loaded page, use the right-click mouse button and select **Inspect Element**, you should then see a developer tools window appear at the bottom, or the right-hand side of your browser. Within the developer tools window, select the tab with the name **Console**.

#### Open the Browser Inspector with a Keyboard Shortcut

`Command + Option + K (Mac)`

`Control + Shift + K (Windows, Linux, Chrome OS)`

---

#### Apple Safari

##### Official Documentation

Take a look at the documentation from Apple if any of the instructions below are confusing.

[Open Safari Developer Tools - Apple](https://support.apple.com/guide/safari/use-the-developer-tools-in-the-develop-menu-sfri20948/mac "Open Safari Developer Tools - Apple")

##### Open the JavaScript console using the Menu Ba

At the top of the Safari window find the **Developer** menu, then click **Show JavaScript Console**

#### Open the JavaScript console using right-click

Any where on the currently loaded page, use the right-click mouse button and select **Inspect Element**, you should then see a developer tools window appear at the bottom or on the right-hand side of your browser. Within the developer tools window, select the tab with the name **Console**.

#### Open the Browser Inspector with a Keyboard Shortcut

`Command + Option + C`

---

#### Microsoft Edge

#### Official Documentation

Take a look at the documentation from Microsoft if any of the instructions below are confusing.

[Open Edge Developer Tools - Microsoft](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide-chromium "Microsoft Edge Developer Tools - Microsoft")

#### Open the JavaScript console using right-click

Any where on the currently loaded page, use the right-click mouse button and select **Inspect Element**, you should then see a developer tools window appear at the bottom or on the right-hand side of your browser. Within the developer tools window, select the tab with the name **Console**.

#### Open the Browser Inspector with a Keyboard Shortcut

- Windows - `Control + Shift + C` OR `F12`
- macOS - `Command + Option + C`

---

### Running a Simple Program

Within your JavaScript console, type the following code and then press `ENTER`.

```js
console.log("Hello JavaScript!");
```

![MacBook Pro on brown wooden surface](https://res.cloudinary.com/btvca/image/upload/v1586818922/curriculum/hello-javascript-console-example_okzsl8.png "Joshua Aragon")

Do you see the text `Hello JavaScript!` print below the code you wrote?

#### Congratulations!

You just wrote your first line of code in JavaScript.  Over the next several weeks we will expand on what you know, and you will be able to make your programs do many more things. For now though, sit back and enjoy this moment as a first simple program.

## The Syntax of Hello JavaScript

Now let's take a look at the JavaScript program that you just wrote.

Below you will see a diagram of the simple program that outputs the string:

```js
Hello JavaScript!
```

![anatomy of a console.log](https://res.cloudinary.com/btvca/image/upload/v1586817842/curriculum/hello-javascript-statement-anatomy_egkvoj.png)

There are lots of pieces to this program that you may see, or you may not yet. Let's list the parts so that you can start to see them more easily.

#### Input to the Console

```js
console.log('Hello JavaScript!');
```

#### Expected output from the Console

```
Hello JavaScript!
```

The program starts with the word **console** which is what's called an **Object** in JavaScript. This object is a bit like a model of the browser developer console that you opened before, it allows for you to send messages to the browser console and see those messages appear. We send one such message to the console called **log**, this message also needs some text to display, which we provide in the **String** containing the characters `'Hello JavaScript!'`.

When the browser receives the message `console.log('Hello JavaScript')`, it prints those characters to the screen. Notice that there are **parentheses** surrounding the **String** on the left and right sides, the first is an **opening** **parenthesis**, meaning that it faces like a spoon to the right, and the second **parenthesis** comes after the **String** and faces to the left, that one is called a **closing parenthesis**. Together these **parenthesis** are called a **pair** and they **enclose** the **String**.

Finally take a look at the end of the line of code and see that there is a **semicolon** as the last character. This **semicolon** tells the JavaScript program that your line of code is finished. It serves a lot like a period in English text, in that it is explicitly saying "this line is complete".


# Exercises

## Print Your Name

Now that you know how to output the string `Hello JavaScript!` how would you change that program to output your name?

```js
// What should go inside the code below to print your name?
console.log();
```

<details>
<summary>Answer</summary>

```javascript
console.log("Your Name Here")
```
</details>


# Questions

1. **How does a programming language differ from a spoken language?**


2. **What is JavaScript primarily used for?**

<details>
<summary>Answer</summary>

Browser automation, and creating highly functional web pages.
</details>

3. **Where is JavaScript run?**

<details>
<summary>Answer</summary>

The browser, and in runtime environments like `Node.js`
</details>

