# Loops

![Loops Title Card](https://res.cloudinary.com/btvca/image/upload/v1599680156/loops_title_card_bi2qmp.png)

Ahh, loops. A fundamental part of what makes programming such a tour de force. Knowing what they are and how they behave is paramount to being a programmer of any skill level. Whether just starting out or a lifelong coder, you won't build anything of use until you harness them properly. Probably.


## What are loops
Loops are, in a nutshell, blocks of code that will run over and over and over and over and over and over until they meet a certain criteria in which they stop. If they never meet said criteria, then they will never stop. Plain and simple.

Consider the following:

![Imageofallworknoplay](https://res.cloudinary.com/btvca/image/upload/v1599680156/allwork_cli_qmjjax.png)

Besides being a play on the beloved 1980s classic *The Shining*, this screenshot of the terminal on my computer was not the product of my descent into madness, but rather a simple and effective `while` loop. Harnessing the awesome power of a loop, I was able to to repeat a block of code over and over and over! In this case, that code simply printed a line of text to the terminal. 

## A ridiculous example
Try it for yourself! While in a *Node environment*, run: 


```javascript
while (1 < 10){
    console.log("All work and no play makes Jack a dull boy")
}
```
When you get the point, press `ctrl +c` twice to exit the program.

<br>
So, what happened? Well, as you might have guessed, this block of code: 

```javascript
console.log("All work and no play makes Jack a dull boy")
```

was executed over and over and over and over. Because this *condition*:

```javascript
1 < 10
```
will *never* not be true. 1 is *always* less than 10. 

> A loop will run *until* the condition equates to `false`. Thus, this loop will always run, or at least until some outside force terminates it. 

Well, this isn't exactly helpful. Who wants a program that runs forever with no way of stopping? 


## A reasonable example
To fix this, we need to alter the condition:

```javascript
1 < 10
```

so that at some point, the loop will end. This means that something in the loop will have to change after each go around. 

To do so, let's store the value in a *variable* so we can change its value over time, like so:

```javascript
let i = 1
while (i < 10) {
    console.log("All work and no play makes Jack a dull boy")
    i = i + 1 
}
```
Now, run this in your terminal. It should look much more manageable. 

![While loop example](https://res.cloudinary.com/btvca/image/upload/v1599680156/loop_terminated_ti1bbp.png)


Sucess! The loop stopped without breaking our computers. Note that the text was only printed 9 times.

Let's see what's happening in more depth.

We store an initial value in `i`. That value is 1, and 1 is a number. 

```javascript
let i = 1
```
Then, we enter the loop! Only this time, something is different with the condition. `i` is being compared against 10. Before, 1 was being compared to 10. 

The first run through, when `i` has a value of 1:

```javascript
i < 10 //  1 < 10 is true
```
the condition still equates to `true`.
 1 is still less than 10.
 
Then, the text prints to the command-line:

```javascript
console.log("All work and no play makes Jack a dull boy")
```
 
 But something different happens this time around.
 
 Included in the loop is a second part that wasn't there before: 

```javascript
i = i + 1 // i now equals 2
```
Now, this says `i` is no longer 1, but `i` is `i + 1`.

`i` now has a value of 2. So we check the condition against the new value:

```javascript
i < 10 // 2 < 10 is true
```
And the loop runs again.

The text prints to the command line, and `i` is again redefined as `i + 1`
Now, `i` has a value of 3.

```javascript
i < 10 // 3 < 10 is true 
```
And the loop runs again.

The text prints, and the value of `i` increased by 1.

Pretty straightforward so far. Now, let's skip ahead to when `i` has a value of 9.

The code within the loop will still run because 9 is less than 10, but then `i` is redefined to `i + 1` as it has been so many times before.  `i` now has a value of 10. 

```javascript
i < 10 // 10 < 10 is false
```

Hold the phone! Now give the phone to me. 10 is not less than 10. The text will not be printed to the command line. The loop is done. 

By manipulating the value of `i` in each iteration of the loop, we have created a condition that WILL eventually equate to `false`, thus ending the loop.

**** This why the loop only ran 9 times. The 10th iteration (when `i` is 10) does not run the loop because the *condition* isn't true. Changing the condition to `i <= 10` (less than or equal to) would allow for that one final print to the command line!

```javascript
i <= 10 // 10 <= 10 is true!
```

This is, in its simplest form, how a loop behaves.

 Now, let's take a look at the different types of loops that exist in programming; JavaScript in particular.

# Loops in JavaScript

## While loops

Let's start with a summary of what a `while` loop does before continuing.

A `while` loop executes its *statements (another word for the code contained within the loop)* as long as a specified condition evaluates to `true`.

The *condition* check hapens before the loop is executed, meaning there is the chance that this loop will never run. This will be discussed more in a moment.

The following example will count to 5:

```javascript
let i = 0
while(i <= 5){
    console.log(i)
    i++
}
```

## Do...While loops
`while` loops have another form that is slightly different : the `do...while` loop.

As mentioned, `while` loops, on their own, simply run until a condition is no longer true. This means that there is a chance it will never run. For example:

```javascript
let i = 100
while (i > 500){
   // do some loop stuff
}
```
will never run, simply because that *condition* will never be true.

Enter `do...while`

In this loop, the code will always be executed at least once, thanks to the trusty `do`. 

let's refactor the previous example to print the value of `i` at least once, regardless of its value. That would look something like this:

```javascript
// This will only print once, as 100 is NOT greater than 500. But it's still run once. 
let i = 100
do {
    console.log(i)
}
while(i > 500) 
```
The power of a `do...while` comes from the order in which things are evaluated. If you wind up having code you would like to see executed *at least* once no matter what, this might be your best bet!

## For loops

`for` loops are a more verbose way of defining the *condition* and behaviors the loop will be executed under. This makes them **a powerful tool that you should strive to master as early as possible in your career**. 


The following is ripped directly from [MDN](https://developer.mozilla.org/en-US/)

A [for](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/statements/for) loop repeats until a specified condition evaluates to `false`. This should sound very familiar. If not, reread the previous section. 

The formal definition of a `for` loop is:

```javascript
for ([initialExpression]; [conditionExpression]; [incrementExpression])
  statement
```
What?

Don't worry, it's really just a more explicit version of our previous `while` example.

In fact, let's compare the previous example to this shiny new `for` loop syntax!

Here's the `while` loop from before:

```javascript
let i = 1
while (i < 10) {
    console.log("All work and no play makes Jack a dull boy")
    i = i + 1 
}
```

And here's the same thing with a `for` loop:

```javascript
for (let i = 1; i < 10; i++){
    console.log("All work and no play makes Jack a dull boy")
}
```

Tada! 

You may see the parallels already, but let's explain them further. 

The `for` keyword precedes the parameters the loop expects, `initailExpression`, `conditionExpression`, `incrementExpression`. 

`initialExpression`: any 'setup' required to make the block of code run.  In this case, it's declaring `i` and assigning it a value. Just like we did outside of the `while` loop.

`conditionExpression`: the condition that, when `true`, will cause the statement to run again. `statement` is another word for the code that will be run inside the loop.

`incrementExpression`: What to do after each time through the loop. 

> `i++` is shorthand for `i = i + 1`.


Now let's take a look at it again:

```javascript
for (let i = 1; i < 10; i++)
```
This says the following:

- `i` starts at 1

- as long as `i` is less than 10, run this loop

- after each *iteration*, increase `i` by 1

- check the condition and run again if still `true`

**Note! This is one of the FEW times that a semicolon inbetween each expression is absolutely necessary.  DO NOT FORGET THEM!**


# Final Musings

`for`, `while`, and `do...while` loops are all variations of a simple concept; do something until a condition is no longer `true`.

There are more mechanisms native to javascript that allow for quick and easy ways to do something repeatedly, but these are far beyond the scope of an introductory article to demonstrate the basics. *That being said,* those more advanced concepts will come easier to you if you sit down and truly internalize the uses of what has been covered here.

Drill them. Learn them. Embrace them! Do not fear them! They'll make you a better programmer, I promise.

<br>
-Paul