# JavaScript Data Structures: Arrays

![athletic track starting line with numbers](https://res.cloudinary.com/btvca/image/upload/v1605535961/athletic-field-1867053_1280_tga7m9.jpg)


Now that we have a nice review under our belts, let's move on. In this lesson, we will be using the concepts covered to explore an important aspect of programming with JavaScript: data structures. Particularly, arrays! When we're done here, you'll understand how to bunch information together in a nice, orderly fashion so you can return to it for later use. This allows us as programmers to keep things "clean", as well as efficient. By clustering information together into an array, we can perform operations en masse, or refer to information based on its position within the array. So, without further ado, let's get into it!

## What is an Array?

Arrays are ordered sets of data that, when created, are given certain tools that allow you to manipulate them quickly and efficiently. More specifically, arrays are *list-like objects* that have a number of functions attached to them that you may call in order to alter.

Arrays are denoted by comma-separated values, encased in square brackets (`[]`). An array that contains the numbers 1 through 9 would like like this:

```js
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

These numbers are *indexed* inside of the array and can be referenced directly by referencing their *index*. To reference the number 4 in this array, we would do so by accessing index 3 like this:

```js
[1, 2, 3, 4, 5, 6, 7, 8, 9][3] // 4
```

The second set of square brackets containing a single integer is the index of the array preceding it. Like strings, arrays are *zero-indexed*, meaning that the first value in an array is accessed at index 0. 

You can declare an array as a variable like you would any other value. To assign the previous array to a variable, use `let` or `const`. Accessing the index is the same as before. 

```js
let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]

arr[3] // 4
```

When assigned to a variable, we can also replace elements by redefining them like you would any other variable. Let's replace the number 4 with the string "four" instead.

```js
let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]

arr[3] = "four" // [1, 2, 3, "four", 5, 6, 7, 8, 9]
```

You may also add elements in this way. Note that the index is very important! It determines where in the array that element will be added. If the index already exists, like above, the element will be replaced.

To add an element to the end, we need to target the proper index. Because the array starts at 0, index 9 is the first open index. 

```js
let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]

arr[9] = "ten"; // [1, 2, 3, 4, 5, 6, 7, 8, 9, "ten"]
```

You don't have to worry about determining the `length` of the array every time you want to add an element to the end. Instead, you can use the `length` property to determine that index. For example, the following array has 4 elements. Note that all primitive data types are valid (boolean, number, string, even functions!)

```js
let arr = ["one", true, 3, "four"];

arr.length === 4 // true
```

Arrays can also be manipulated with a variety of *methods*.

### Quick aside (something familiar)
Remember working with strings? When given a string, we were able to manipulate them with all sorts of methods, like `.toUpperCase()`, and `.replace()`, like so:

```js
"car".toUpperCase() // "CAR"
```

These are known as *string methods*; simply by virtue of being strings, we are able to invoke those special methods and return a desired result. Similarly, arrays contain their own native methods that allow for similar results that are array-specific.

## Array Methods
![line of wooden ducks](https://res.cloudinary.com/btvca/image/upload/v1605737181/duck-3217049_1280_ttqf9m.jpg)

Arrays are often used to *queue* up elements within them, allowing order to be maintained. This is helpful when you need to display things in sequential order. There are 2 methods used to access those elements.

### `.push()`

To add an element to the end of an array regardless of its length and index, reach for the `.push()` method. This will take whatever value has been given to it and append it to the end of the array.

```js
let groceries = ["bread", "milk", "ice cream"]

groceries.push("coffee") // ["bread", "milk", "ice cream", "coffee"]
```

This lets you keep things in a nice and orderly manner. As you add elements to your array with `.push()`, they will add themselves to the end of the array.

### `.shift()`

To access the first element of the array, use `.shift()`. Whereas `.push()` will add an element to the end of the array, `.shift()` will get the first element from the array, `return` it for use, and then "advance" the array so that what was the second element is now first in line.

```js
let arr = [1, 2, 3, 4]

let shifted= arr.shift()

shifted // 1
arr // [2, 3, 4]
```

> These are used frequently when trying to run through an array in order. For example, if you have a number of messages that you would like to display on screen in a particular order, it would make sense to `shift` through them one at a time in order to lay them out in proper order.

![stack of pancakes](https://res.cloudinary.com/btvca/image/upload/v1605735799/pancake-3099315_1280_xyr1kf.jpg)

Arrays are also used to facilitate what is referred to as a *stack*. Stacks are a way of structuring your data in an array so that elements are added as normal to the end of the element, but they can only be removed in reverse-order.  Think of a stack of pancakes, or a deck or cards. An item placed in the pile must be removed before accessing the next in the list.

The methods used to operate on a *stack* are `.pop()` and `.push()`. We've already covered, `.push()`, 