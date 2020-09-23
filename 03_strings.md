# Strings in JavaScript

![focus dictionary index page](https://images.unsplash.com/photo-1451226428352-cf66bf8a0317?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=1080&fit=max&ixid=eyJhcHBfaWQiOjkwODQwfQ "Romain Vignes")

## Overview

When building programs, it's common to work with text, either single characters, or extensive collections of characters. You are reading some character collections right now! There is a specific name for these groups of characters in JavaScript and programming in general, and they are called **Strings**. This type of data is used most often for processing input from a human being and responding using messages during or after a program runs. You will also find Strings interspersed throughout your code, because you may need to make decisions based on what a user types, selects, or chooses while your program is running. This lesson will serve to familiarize you with what Strings are and how to use them.

- Strings by Themselves
  
   - Single vs Double Quotes
  
   - Combining Strings
  
   - Escaping Special Characters

- Strings and Numbers

- Template Strings

- Long Strings

## Strings by Themselves

In JavaScript, it's easy to create a String of text. All you need is a pair of quotation marks and some characters. How does a string look? Check out the example below!

```js
'Hello, JavaScript!'
```

What you've just read may look familiar. We used a String of text just like it when we completed the Hello JavaScript lesson. There are three parts to this String, and I'll break them down below.

1. The first quotation mark, `'`, or `"`, which starts the **String**.

2. The list of characters that make up the **String** text, `Hello, JavaScript!`, you can use any characters in the [Unicode](https://en.wikipedia.org/wiki/List_of_Unicode_characters) character set, which includes characters for many languages, including English.

3. The closing quotation mark,  `'`, or `"`, which ends the **String**.

### Single vs. Double Quotes

It's possible to create a String with either single quotes, or double quotes at the beginning and end. There is a recommendation to use single quotes that much of the JavaScript community follows for consistency, but it is not a requirement. The rule you'll need to remember to follow is this; If you start a **String** with single-quotes, you **must** end it with single-quotes, and if you start it with double-quotes, then you must finish it with double-quotes. 

You might be asking yourself, "What if I need to use quotes within my String?". To answer that question, read on to the next section.

#### Using quotes within a String

How can you use quotes within a string like the following? `The author said, "This may be my finest work!".`The answer is easier than it may first appear. When you need to use quotes within a **String**, simply use whichever quote style, single or double, you did **NOT** use to start the **String**. Let's explain with an example; check out two of them below.

##### Single Quote Example

Example of using double-quotes within a single-quote **String**.

```js
'Sometimes I ask myself "How did I get here?!".'
```

##### Double Quote Example

Example of using single-quotes within a double-quote **String**.

```js
"Then the officer asked, 'Have you seen this person before?'."
```

##### Using Quotes within Strings Conclusion

Using the technique above, you should be able to see that whenever you want to use a quotation character within a **String**, you'll simply need to switch to the opposite style of the quote than you used to create the **String**.

### Combining Strings

What if you have two **Strings** and want to combine them into a single output string? That's possible using a technique known as **Concatenation**, and it's easy to do.

Say you have a **String** that is composed of multiple parts, and you want to print them as one string to the browser JavaScript console.

The first part of the string is:

```js
'All the world is a stage,'
```

And the second part of the string is:

```js
'And all the men and women merely players;'
```

To combine the two strings, you simply place a plus symbol `+` between them, outside the string quotes. See below for an example.

```js
'All the world is a stage,' + 'And all the men and women merely players;'
```

Now to output that String, open the JavaScript console in your browser and run the following code.

```js
console.log('All the world is a stage,' + 'And all the men and women merely players;');
```

> 'All the world is a stage, And all the men and women merely players;

*Quote by William Shakespeare, from As You Like It*

![man taking photo](https://images.unsplash.com/photo-1562342101-ec26556bb233?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=1080&fit=max&ixid=eyJhcHBfaWQiOjkwODQwfQ "David Anderson")

You may wonder if one type of quoted **String** (single), can be combined with another kind (double), and the answer is yes, this is no problem at all. 

```js
console.log("Be yourself; " + 'everyone else is already taken.');
```

> "Be yourself, everyone else is already taken."

*Quote by Oscar Wilde*

You can even combine two **Strings** that have quotes within them, no matter the quote style. For example, see the example below.

```js
'The joke goes "Time flies like an arrow,"' + " 'fruit flies like a banana.'"
```

If you wanted to output this **String** to the console, you could run the following code.

```js
console.log('The joke goes "Time flies like an arrow,"' + " 'fruit flies like a banana.'");
```

> "Time flies like an arrow,  fruit flies like a banana."

*Quote by Groucho Marx.*

### Escaping Special Characters

Did you run the following as **String** in the browser console above? If not, try to do so now. Try to notice something strange about the result.

```js
'The joke goes "Time flies like an arrow,"' + " 'fruit flies like a banana.'"
```

.

.

[suspenseful music playing]

.

.

Did you get a result that looks like this?

```js
"The joke goes \"Time flies like an arrow,\" 'fruit flies like a banana.'"
```

![](https://cdn.pixabay.com/photo/2014/07/25/23/05/groucho-marx-401923_960_720.jpg)

What are the backslash characters (`\`) doing there? The reason why they exist is that while JavaScript can handle a string containing both kinds of quotes, single and double, it needs to mark those that otherwise end the string as being **part of** the **String**. This process of marking what are usually considered **special characters** is known as **escaping**, and it's quite common within Strings.

You witnessed one example in the quote from Groucho Marx, but what about the earlier quote from William Shakespeare? The quote `"All the world is a stage, And all the men and women merely players;"` typically displays with a break between the parts, so that it would look like the quote below.

```js
"All the world is a stage,
And all the men and women merely players;"
```

Try and run that code in your browser console, and you'll likely see an error that reads something like:

```
SyntaxError: "" string literal contains an unescaped line break
```

So then how can you create a string that spans more than one line? The answer is to use what is known as a **new-line character** to indicate that you want the current line to end, and the rest of the **String** to begin on the next line. Let's see an example below.

```js
"All the world is a stage,\n" + "And all the men and women merely players;"
```

Notice that after the **String** `All the world is a stage,` there is a `\n`. That character is saying to JavaScript, "Hey, I want you to place a line-break  here, and then add whatever comes next to the line below the current one.". We have to use the  backslash`\` character here to let JavaScript know the next character is special, and in this case, it's the new-line character.

#### Escaping Quote Characters

Quotation characters are considered to be **special** in JavaScript because they signify the start or end of a **String**; This means that you can escape them too! 

Below you will see a string that has a quote within it, and then the same quote which uses matching quotation marks within itself, without ending the **String** by using **escape** characters.

```js
"Outside of a dog, a book is a man's best friend." +
"Inside of a dog, it's too dark to read."
```

*Using single quotes within double-quotes.*

```js
'Outside of a dog, a book is a man\'s best friend.' +
'Inside of a dog, it\'s too dark to read.'
```

*Using single quotes by escaping inner quotation characters.*

![black and white dog with disguise eyeglasses](https://images.unsplash.com/photo-1466921583968-f07aa80c526e?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=1080&fit=max&ixid=eyJhcHBfaWQiOjkwODQwfQ "Braydon Anderson")

## Strings and Numbers

If you find yourself needing to use numbers that JavaScript calculates within a String, there are several ways to do so. The first way would be to concatenate the number with the **String** using the plus symbol operator `+` like you see below.

```js
"The answer to life, the universe, and everything is ... " + 42
```

If you need to calculate the number before **concatenating** it with the string, you can do so by simply having a mathematical expression appear before, after, or within the string like the following. Notice that the parentheses wrap the expression.

```js
"The answer to life, the universe, and everything is ... " + (100 - 58)
```

Parenthesis are used here is to prevent `100` from being concatenated with the **String**, and then for JavaScript to try and subtract `58` from that **String**. Remember from the lesson on [Arithmetic](./arithmetic) that if you attempt to subtract a **String** and a **Number**, that the result will be the value `NaN`, which is different than what you want.

It's possible to add the number anywhere within the **String** by placing breaks within the **String** where you want the number to be. See the example below.

```js
"The sum of " + 90 + " and " + 137 + " equals " + (90 + 137) + "."
```

By breaking our string into pieces and then reassembling those pieces in a way that fits our needs, we can construct any message we want to convey using **Strings** and **Numbers**.

![](https://images.unsplash.com/photo-1574507664658-4114817f5956?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=1080&fit=max&ixid=eyJhcHBfaWQiOjkwODQwfQ "Le Toan")

## Template Strings

If we are working with a particularly complicated **String** and want to use numbers or any other form of JavaScript **expression** within the final output, you can also reach for another tool known as a **Template String**. This kind of **String** uses a different quote to start and end them and allow for marking parts of the **String** as an **expression** that will be **evaluated** to a **value** and then inserted into the **String**. Let's see some examples so you can see what we mean.

```js
`Hello, I am a template. 1 + 1 = ${1 + 1}`
```

We are going to break down the String above into its parts below.

1. The opening back-tick quote mark, <code>`</code>, which starts the **Template String**.

2. The list of characters that make up the **String** text, `Hello, I am a template...`

3. The template evaluation region `${1 + 1}` which will return a value and inject it.

4. The closing back-tick quote mark, <code>`</code> which ends the **String**.

A **Template String** is a powerful tool in the sense that it allows you to use any JavaScript code you want to return values into the **String** text. They are also convenient in that since they do not use single-quotes or double-quotes as their starting and ending **delimiters**; you can use either freely within the **String** text without the need to **escape** them to avoid closing the **String**.

## Long Strings

Sometimes you may find your self needing to write out a long string of text that could wrap beyond one line, and onto another. In this situation, you might feel like your only solution is to break the long string up into many smaller strings and then concatenate those Strings together. Fear not, as there is another way to solve this problem.

When a string is long, and wrapping from one lone to another, you can use the special character backslash `\` combined with a line-break to instruct JavaScript that you have more String to add and not to end the String. 

Let's see an example to illuminate this point.

```js
'Once upon a midnight dreary, while I pondered, weak and weary, \
Over many a quaint and curious volume of forgotten lore— \
    While I nodded, nearly napping, suddenly there came a tapping, \
As of some one gently rapping, rapping at my chamber door. \
"Tis some visitor," I muttered, "tapping at my chamber door— \
            Only this and nothing more."'
```

*The opening stanza of the poem "The Raven" by Edgar Allen Poe.*

The poem above is multiple lines, but it is only a single String, the `\` characters following each line are saying to JavaScript, "Hey, I know that a line-break is coming up, but please do not end the String because there is more to come, okay?". Using these backslashes, we can use a **String** that spans multiple lines without needing to combine multiple shorter **Strings**.

This same solution can be used for **Template Strings** without any changes other than the starting and ending quotes being back-tick <code>(`)</code> characters.

## Indexing
As discussed, strings are a series of characters. Each *character* in that string exists at a location relative to itself, called an *index*. 

**An *index* is a number that identifies the location of a character in a string. The index comes at the end of that string, inside of square brackets (`[ ]`)**

Try this in your browser console:

```js
'here-is-a-string'[1]
// will return 'e'
```
Wait, why am I getting '`e`'? isn't the first letter '`h`'? 

Why yes! Yes it is. But it is at `index 0`. 

In programming, most things are **zero-indexed**,
meaning that when accessing a character within a string or any other data-type, you do so starting at `0`. Be mindful of the implications this holds; if your string's first character starts at `0` instead of `1`, then the *last* character will not be the length of the string, but rather `1` less than the length.

Example:
```js
'this-string'
// has 11 characters

'this-string'[11]
// should return undefined

'this-string'[10]
// should return 'g'
```
Do I have to *know* the length of a string? Nope! It can be found by adding `.length` to the end of *any* string. The result will be the number of characters that string is comprised of. 

```js
`this-string`.length
// should return 11
```

## String Methods
So, we've covered the basics of what strings *are*, but how do we use them in programming? While a pre-determined string can be the preferred output in a number of use cases (like a "log in successful" message,) they are much more dynamic than that.

JavaScript has a TON of *methods* that are natively available to use on *any* string. 

What are methods? 

More on that when we discuss functions. For now, all you need to know is that they are tools for manipulating strings in a variety of ways. 

For example, the method `.toUpperCase()` will take a string and return an uppercase variation of it. Methods need to be *called* with open and closed parentheses, '`()`', and accessed with a period '`.`'

**Try this in your browser console:**

```js
`capitalized`.toUpperCase()
// should return 'CAPITALIZED'
```
There are many methods, each with unique and sometimes confusing behaviors. Some take values inside the parentheses that determine how that method will behave. 

For example, the `.replace()` method replaces a part of a string. This method accepts 2 values inside of its parentheses: the first is the *substring* (or part of the string) that you will replace, and the second is what you'd like to replace it with.

**Try this in your browser console:**

```js
`Yes-No?`.replace('-',' or ')
//should return 'Yes or No?'
```
This takes the string `Yes-No?` and replaces the `-` with `' or '` (note the whitespaces).

Here are a few more examples: 

### `.repeat()`

The `.repeat()` method returns a string repeated the given number of times. 

```js
`haha`.repeat(3)
// should return 'hahahahahaha'
```

### `.indexOf()`
The `.indexOf()` method returns the starting *index* of the string being searched for within the string the method is called on.

```js
'looking for something?'.indexOf('for')
//should return 8
```
If no substring is present, it will return `-1`


### `.slice()` 
The `.slice()` method extracts a section of the string the method is being called on. It expects 1 or 2 numbers inside the parentheses:

- The first number is the index at which to start the slice.
- The second number is optional, and denotes the END of the slice. If omitted, it takes the rest of the string with it. The character at this index is not included in the returned string.

```js
"let's slice this string".slice(6)
// should return "slice this string"

"let's slice this string".slice(6,11)
// should return "slice"
```
For a complete list, check out [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#Instance_methods)

## Exercises

What is the term for combining two separate strings together?

<details>
<summary>Answer</summary>
Concatenation
</details>
<br/>


Find the index of the  substring `hello` if its present in the following string!

`hereisara41n2do#%!mstringofhello(teststring8323`

<details>
<summary>Hint</summary>

`.indexOf()` will return the index of a given substring, or `-1` if the substring does not exist.
</details>

</details>

<details>
<summary>Solution</summary>

```js
`hereisara41n2do#%!mstringofhello(teststring8323`.indexOf('hello')
// 27
```
</details>
<br/>

Format the string `01Calvin & Hobbes97` by removing the number at the beginning and end.

<details>
<summary>Hint</summary>

`.slice()` can take 2 numbers to indicate starting and ending indexes of the substring you'd like to extract.
</details>


<details>
<summary>Solution</summary>

```js
`01Calvin_&Hobbes`.slice(2,17)
```
</details>
<br/>

**Capitalize a word** 

Write a statement that takes the string '`apple`', capitalizes the first letter,and *concatenates* it to the remaining string.

<details>
<summary>Hint</summary>

The first character of a string is at index 0.
</details>
<details>
<summary>Hint</summary>

use `.slice()` to remove the first letter of string.
</details>

</details>
<details>
<summary>Solution</summary>

```js
`apple`[0].toUpperCase() + `apple`.slice(1)
```
</details>
<br/>