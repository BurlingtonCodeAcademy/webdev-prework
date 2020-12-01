# Making Decisions with Conditionals
>Focus is a matter of deciding what things you're not going to do.

-- John Carmack, Co-founder, id Software

![sign](https://res.cloudinary.com/btvca/image/upload/v1599838751/sign_aan0k2.jpg)

Deciding what to do next is a part of our lives every day. As humans it's hard to investigate our process of decision making. When we wake up in the morning and feel hungry, our minds make a decision about what to eat. Later when we get dressed for the day, we decide what clothes to combine into our outfit. Some of these decisions are conscious, while others are made without thinking. Within a computer program, we as the programmer must determine how to make each choice, and the instructions about how to do so must be clear.

Making a decision requires several things, without which it would be impossible to decide. You must have some things to compare against each other, you must have some means to compare them, and you must have some actions to choose from based on the outcome of the comparison.

The requirements of a decision

**1)** Have something to compare against.

**2)** Have a means of comparison.

**3)** Have an action to take based on the comparison.

In the following lesson, we will learn how JavaScript can fulfill the requirements above, what tools it provides to express decisions from simple to complex.

## Making Comparisons

When you compare anything to something else you need a way to determine what attribute of each is different, and in what way it is different. For example, imagine you want to make breakfast, you have two eggs laid in front of you, and want to know which egg is larger than the other so that you can choose the largest one.

![eggs](https://res.cloudinary.com/btvca/image/upload/v1599838936/eggs_gxcxbn.jpg)

How do you tell which is larger? Do you measure the egg width, height, weight, surface area? Usually humans don't think this hard about the eggs they are about to eat, but a computer program would need to know the process to make that decision. If we decided that the most important attribute to compare against was the weight of the eggs, then we could compare them like so.

```javascript
let brownEgg = 0.95;
let greenEgg = 0.75;

console.log('Brown egg is heavier ' + brownEgg > greenEgg);
```

This is the first time that you've seen what is known in JavaScript as a Comparison Operator. This operator is a special character within the JavaScript language that allows for two values to be compared against one another. In the example above the values that are being compared are the weights of the eggs,`0.75` and `0.95`. Those values are evaluated from the variables `brownEgg` and `greenEgg`.

The operator that was used above is known as the Greater Than Operator, it appears as an angle bracket facing left, like so: `2 > 1`. This operator only does one thing, which is to look to its left and its right, and then return either `true` or `false` based on whether the value on the left is larger than the one on the right. The comparison of values always looks left first and compares that value to the other value on the right-hand side.

You could write the expression `brownEgg > greenEgg` in english as the following:

```
Q: Is the value of the brownEgg larger than the value of the greenEgg?
A: Yes
```

Instead of getting back a string of text containing the characters "Yes" JavaScript returns the value `true` back to you. This is for a number of reasons, but one of them is because it's easier to use the values of `true` or `false` to choose which action to take after the comparison is made.

## Comparison Operators

There are a number of operators that perform comparisons in JavaScript. Below you will see a table outlining the most commonly used among them along with their descriptions. For a full list of comparison operators, make sure to use the [Mozilla Developer Network reference page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators).

### Equality
```javascript
42 == 42  // true
2.71828 == 3.14159 // false
"alan turing" == "alonzo church" // false
1123581321 == "1123581321" // true
```

The equality operator determines if the value to the left can be considered the same as the value on the right. It's possible to compare two values of the same type, or different types, such as strings and numbers. This quality of equating two values of different types can cause confusion or even bugs if used too casually.

### Inequality
```javascript
42 != 42  // false
2.71828 != 3.14159 // true
"alan turing" != "alonzo church" // true
1123581321 != "1123581321" // false
```
The inequality operator determines if the value to the left can be considered different from the value on the right. It's also possible to compare two values of the same, or different types, in the same way as the equality operator. You can think of this operator as returning the opposite of whatever equality would result in.

### Identity
```javascript
42 === 42  // true
2.71828 === 3.14159 // false
"alan turing" === "alonzo church" // false
1123581321 === "1123581321" // false
```
The identity operator compares whether two things are exactly the same value. This means that comparing two values of different types will always result in false. It also means that the comparison is simpler, and will yield consistent results. In general, it is recommended to use the identity operator over using the equality operator, unless you have a good reason not to.

### Relational
```javascript
42 > 42  // false
2.71828 < 3.14159 // true
"alan turing" >= "alonzo church" // true
1123581321 <= "1123581321" // true
```

- (>) Greater Than
- (>=) Greater Than or Equal
- (<) Less Than
- (<=) Less Than or Equal

Each of the relational operators compares the two values and determines if the value on the left side has the relationship of the operator's meaning. These relationships can be confusing at times such as when you are comparing two numbers of the same value with a greater-than or a less-than operator, which would result in false, since neither number is greater or less than the other since they are equal.


### Summary
With the operators described thus far, you will be able to make many comparisons and determine what actions to take as a result. The hardest part of making a decision is determining what qualities of the conditions you need to compare, and then deciding what course of action to take as a result of the comparison. The next section will cover how to take one action if the comparison's results are true and another if it is false.

## Conditionals
Earlier we mentioned that to decide on something you need to be able to make a comparison and then choose a course of action based on the result of that comparison. Conditional statements and expressions are the tools you will use within JavaScript to make those choices.

The simplest kind of conditional to use is known as an If-Statement and they look like the following.
```javascript
// the someValueMaybeTrue stands in for any value or comparison

if (someValueMaybeTrue) {
  // run the code below if someValueMaybeTrue is True, otherwise skip it
  console.log("Congratulations it is true!");
}
```
Within the parentheses following the if ( ... ) you can place any valid JavaScript expression, which just means a piece of code that returns a value. For example, any comparison between the two values will always return either true or false. This makes comparisons like greater-than, less-than, equality, or identity ideal for use with an IF statement like the one above. Let's see another simple example.

```javascript
let firstNumber = 42;
let secondNumber = 97;

if (firstNumber < secondNumber) {
  console.log("Congratulations, firstNumber is smaller!");
```

Let's go back to the egg comparison for a moment and see what it would look like to use a conditional statement to decide which egg to use.
```javascript
let brownEgg = 0.95;
let greenEgg = 0.75;

if (brownEgg > greenEgg) {
  console.log("The brownEgg is heavier!");
}
```

You can also create conditions that evaluate multiple cases at once with the `||` (or) and `&&` (and) operators. 

```js
if (someValue && someOtherValue){
    // run the code below if someValue and someOtherValue are both true 
  console.log("Congratulations they're both true!");
}

if (someValue || someOtherValue){
    // run the code below if either someValue or someOtherValue are true 
  console.log("At least one of these is true!");
}

```


## Branching Based on Conditions
Now that you understand how to use a comparison, and make a decision based on that comparison, it's time to see how you can choose one of several branches of actions to take.

Remember that a simple conditional if-statement looks like the following:
```javascript
if (/* some condition or comparison */) {
  /* some code to run when the condition is true */
}
```
This if-statement allows for some code to be run conditionally, meaning that it depends on if another value or expression is true. If, however, the value or condition is false, and we want to take some action as a result of that falseness, then we need to extend the if-statement to have code to run.

What you need is a way to tell JavaScript:
```
Run this chunk of code if this condition is true, otherwise run this other chunk of code.
```
There is a convenient way to do that, which is known as an else-clause. The easiest way to understand this sort of construct is to see one in action, so let's take a look at the code below.

```javascript
let firstNumber = 42;
let secondNumber = 97;

if (firstNumber > secondNumber) {
  console.log('First number is larger');
} else {
  console.log('Second number is larger');
}
```
This code acts like a fork in the road in a sense.

- When the condition (firstNumber > secondNumber) results in true,
    - Then the line of code console.log('First number is larger') is run
    - Otherwise the code console.log('Second number is larger') is run.

## Final Musings

- Conditions are statements that equate to a boolean, `true` or `false`.
- Conditions must have something to compare against
- Conditions provide a course of action to take `if` the provided statement is true.
- Conditions may also provide "contingencies" in the case that the previous condition is not `true`. These are *else-clauses*.

## Exercises

Will anything print to the console with the following?

```js
if("will it print?"){
    console.log("Printing!")
}
```
<details>
<summary>Hint</summary>

Think about what primitive data types (or values) in JavaScript equate to `true`. Are strings among them? 
</details>

<details>
<summary>Answer</summary>

It will print. Strings equate to `true`, or are *truthy*.
</details>

<br/>

The following code returns a random number between 1 and 10 and stores it in `randomNum`

```js
let randomNum = Math.round(Math.random()*10)
```

write the conditions for the following logic:

1) if `randomNum` is even, print `"even"` to the console
2) if `randomNum` is odd, print `"odd"` to the console
3) if `randomNum` is even and over 6, print `"big even"` to the console
4) can you make these all apply to the same logic chain?

<details>
<summary>Hint</summary>

The `%` (modulo) operator returns the remainder of a division. A remainder of `0` means that a number (dividend) is divisible by the provided divisor.
</details>

<details>

<summary>Solution 1</summary>

```js
 if(randomNum % 2 ===0){
    console.log("even")
}

```
</details>

<details>

<summary>Solution 2</summary>

```js
 if(randomNum % 2 !==0){
    console.log("odd")
}
```
</details>
<details>
<summary>Solution 3</summary>

```js
if((randomNum % 2 ===0 ) && (randomNum >6)){
    console.log("big even")
```
</details>


<details>

<summary>Solution 4</summary>

```js
if((randomNum % 2 ===0 ) && (randomNum >6)){
    console.log("big even")
} else if(randomNum % 2 ===0){
    console.log("even")
} else {
    console.log("odd")
}
```
</details>

