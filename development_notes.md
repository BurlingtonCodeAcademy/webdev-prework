# Questions v. Exercises

## Issue:

Depending on the scope of the lesson, it may or may not be condusive to exercises for the student. 

Some lend themselves to discussions more than application, like "Why is JavaScript important?" and "Where does it run?" (hello javascript)

Other topics like *strings* and *functions* are also more concept-based in their current form, but could be retrofitted to work towards exercises. 

How do you make an exercise around some of these?

## Solutions:

- Case-by-case basis (Questions *or* exercises)

- Smaller, secondary lessons that introduce workable material.
    - for example, after the arithmetic lesson, provide a brief writeup and a few exercises to go along with it. 
        - Will arithemtic lessons be too easy?

## Proposal:
Combination of the 2

For earlier topics, like arithmetic, provide questions to reflect upon;
    - "What is the order of operations?"
    - "What are some issues with large numbers in JavaScript?" and "How are they handled?"

For other topics, like *strings* and *functions*, introduce a small secondary exercise-based lesson;

- Now that you know what strings are, let's see what you can do with them! (some basic methods)
-

**hello javascript**
- Questions
- Already in place

**Arithmetic**
- Questions
- Maybe fill in the blanks? 9_9 = 81 ?
    - Too simple?
- If 

**Strings**
- Second, smaller lesson to demonstrate method and their simple application
- 4 or 5 exercises after covering a handful of common methods.

**variable binding**
- Exercises: Make the following statements `true`
```javascript
let x = // your code here
x/30 = 6
```

**conditions**
- Questions
- What will the following conditional logic equate to??

```javascript
let x = 10
let y = 2
let z = 20
x < y // false
x + y < z //true
```

**loops**
- Exercises:
- write a `while` loop that...
- write a `for` loop that...

**functions**
- Exercises:
- Write a function that:
    - Takes a string and turns it entirely uppercase
    - Takes a number and prints "odd" or "even"
    - etc. 

**I/O**
- Questions?

- Write a command line application using `process.stdin` that returns your input in lowercase.
- Bonus: make the output return in lower case with a space " " between every character. 


# Progress

Action Items:

- Track progress with github issues and PRs
- Track inspiration/resources with google sheet (test run)
- Track Scope of lessons in a google doc
- Prework and Bootcamp tracked in separate google doc

## Notes: 

Flow of lessons may be off

If we are trying to give practical exercises along with the lessons, leaving variable declaration to the 4th lesson is a detriment. Without covering variables, examples and exercises are difficult to demonstrate in a larger context.

Basic JavaScript syntax 1st!

Proposed order

[x] means proposed exercises

- 01 hello_javascript 
- 02 Variables
- 03 arithmetic [x]
- 04 strings 
- 05 conditionals
- 06 loops
- 07 functions
- 08 I/O
- Project


- Node or no? 
    - If not, a few of my plans need to change. 


### Changes to Strings Lesson:

Add content on manipulating strings!

Cover:
- String behavior (like indexing and coercion)
- Manipulating strings
    - Method examples
    - How to chain them

Exercises

- Capitalize a word 
- No functions!
- See if a word is present in a long string
- Format a string `01Calvin_&_Hobbes` (slice and replace)


### Variable Binding:

Exercises
- Step by step, with words
    - "Declare 2 variables, `name` and `userName`
    - Assign value "Doug" to `name`
    - assign `name` as a value to `userName`
    - show the value of `userName` with `console.log()` or `alert` if in browser

- Create a variable with `let` that has the value of your middle name.
    - What is a proper naming convention to do so? (ie. `myMiddleName`)

### Conditions

Exercises
The following code returns a random number between 1 and 10 and stores it in `randomNum`

- Will anything print to the console with the following?

```js
if("will it print?"){
    console.log("Printing!")
}
//yes
```
<br>

```js
let randomNum = Math.round(Math.random()*10)
```

write the conditions for the following logic:

- if `randomNum` is even, print `"even"` to the console
- if `randomNum` is odd, print `"odd"` to the console
- if `randomNum` is even and over 6, print `"big even"` to the console

### 