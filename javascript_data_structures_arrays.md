# JavaScript Data Structures: Arrays

<a style={{color:"blue"}} href="https://forum.burlingtoncodeacademy.com/t/week-4-javascript-data-structures-arrays/291">Discuss in Forum</a>


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

The methods used to operate on a *stack* are `.pop()` and `.push()`. We've already covered `.push()`, which only leaves `.pop()`. 

### `.pop()`

`.pop()` is like shift, but for the end of the array. It extracts the last element in an array and returns it for your use.

```js
let colors = ["red", "yellow", "green"]

let popped = colors.pop();

popped // "green"
colors // ["red", "yellow"]
```

There is one additional method that doesn't necessarily fit with the *queue* and *stack* methodologies, but is useful nonetheless, and that is `.unshift()`. 

### `.unshift()`

`.unshift()` simply adds an element to the beginning of the array, much like `.push()` does to the end of an array.

```js
let arr = [1, 2, 3]
```

> Array methods have a variety of uses, but there are some things worth noting in terms of speed and efficiency. If at all possible, when designing your applications, use `push/pop` before reaching for `shift/unshift`. This is because the former do not have to re-orient the indexes of subsequent elements. `push/pop` only deal with the last element in an array, and as a result are much more efficient. 

## Looping over arrays

Now that we've covered some basic examples of array declaration and syntax, let's take a look at ways to manipulate the data as a whole, ie. looping. 

Remember `for` loops? We declare a variable that can increase or decrease every iteration, like so:

```js
for (let i = 0; condition; i++){
    // your code here
}
```
But what about the condition?  How might we want to loop over every element in the array? Well, if an element in the array is accessed by its index, and arrays are indexed starting at 0, we could effectively iterate (cycle through) an array by using the `length` property to determine the end index, while the starting index is 0!

Let's take our *first* example array again:

```js
// starts at index 0 and ends at index 8
let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]

// arr.length is 9
```

To effectively iterate over an array with a `for` loop, then, we would need to incorporate every index between 0 and 8 inclusive, like so:

```js
for (let i = 0; i < arr.length; i++){
    // your code here
}
```

Since `arr.length` is 9, in this case, we do not want `i` to ever equal that. Thus the choice is `<`, instead of `<=`. 

Now, we can cycle through the array by tying these 2 concepts together and performing certain actions on each element. Let's take every element in the array and *double it*.

```js
let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]

for (let i = 0; i< arr.length; i++){
    arr[i] = arr[i] *2
}
// arr will now be [2, 4, 6, 8, 10, 12, 14, 16, 18]
```

This will use the incrementer variable `i` as the index, starting at 0 and running through all elements. Then, for each element, that position in the index is set to double its own value. Effective!

> Note that the `length` property will update whenever the array is modified. 

> When comparing arrays should not be compared to one another using `==`. This is because they, while possibly containing the same values, are technically different objects. 

## Final Musings 
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

And there you have it! An introductory glance at JavaScript arrays. This barely scratches the surface, but nonetheless provides an introductory concept of arrays and their general behavior. Review, then move onto the exercises below.

- Arrays are ordered sets of data
- They can be declared like any other variable, and are bookended by square brackets (`[]`)
```js
let exampleArray = [2, 4, 6]
```
- Arrays have a `length` property that determines the number of indexes within it.
- `pop()` removes and returns the last element
- `push()` adds an element to the end 
- `shift()` removes and returns the first element  
- `unshift()` adds elements to the beginning

- You can loop over an array by using a `for` loop based upon the array's length.

```js
let loopedArray = [1, 5, 10, 20, 100]
for (let i = 0; i < loopedArray.length; i++){
    console.log(loopedArray[i]) // prints each value to the terminal
}
```

## Exercises


<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/array-exercises-bca?path=script.js&previewSize=0&attributionHidden=true"
    title="array-exercises-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

### 1

1. Create an array `colors` with "blue" and "green" in that order.
2. Add "red" to the end of it
3. Change the middle value ("green") to "yellow"
    - Try to make it work based on `length`, instead of a fixed index.
4. Remove the first value ("blue").
5. Add "purple" to the beginning of the array.


<details> 
<summary>Answer</summary>

```js
let colors = ["blue", "green"]
colors.push("red")
colors[Math.floor((colors.length-1)/2)]= "yellow"
colors.shift()
colors.unshift("purple")
questionOne.textContent = colors;
```

</details>

### 2
1. create an array `numbers` with the values 2,4,6,8, and 10 (in that order).
2. loop over the array and change each element to be half of its original value.
3. remove the first number and place it at the end of the array `numbers`.
4. create a separate array `newNumbers` that only contains the even numbers of the new array.


<details> 
<summary>Answer</summary>

```js
let numbers = [2, 4, 6, 8, 10];

for (let i=0; i< numbers.length; i++){
  numbers[i] = numbers[i]/2;
}

let shifted = numbers.shift()
numbers.push(shifted)

let newNumbers=[]

for (let i=0; i< numbers.length; i++){
  if (numbers[i] %2===0){
    newNumbers.push(numbers[i])
  }
}
```

</details>