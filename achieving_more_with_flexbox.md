# Achieving More With Flexbox
![various tools on a table](https://res.cloudinary.com/btvca/image/upload/v1603985723/tool-2820946_1280_ytxwyg.jpg)

So, we've seen what basic `display` properties like `inline`, `block`, and `inline-block` are capable of. Admittedly, you can achieve a lot with them, but you will often find yourself limited. What about orienting things relative to a parent container? Or ensuring that elements have equal spacing, without having to count every pixel? 

Flexbox is a hands-off layout approach that allows you to quickly create responsive elements within a container that are automatically arranged and adjusted based upon the parent container, and by proxy, the screen size. With it, you can answer questions like:

**How do I place 2 elements on opposite ends of a container?** 

or

**How can I make the elements inside a parent container run exclusively from top-to-bottom?**


## Creating a Flexbox
`flex` is a two-dimensional `display` property that turns the element(s) it is applied to into what are referred to as a *flex container*. The *immediate* children of the flex container are called flex items, and can be oriented relative to the container's vertical (`column`) *or* horizontal (`row`) orientation.

Perhaps it's best to start with an example. Let's take a generic `<div>`, as it has no additional default styling. We want to fill it with 3 equally sized child elements, that will also be `<div>` elements. Let's do that now:

```html
<div id="flex-container">
    <div class="flex-item">item 1</div>
    <div class="flex-item">item 2</div>
    <div class="flex-item">item 3</div>
</div>
```
Let's size and color the container and items for visibility:

```css
#flex-container{
    background-color:lightgrey;
}
.flex-item {
    border: 1px solid black;
    background-color: cornflowerblue;
}
```
We start with something like this:

<div style={{backgroundColor:"lightgray"}} id="flex-container">
    <div style={{border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 1</div>
    <div style={{border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 2</div>
    <div style={{border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 3</div>
</div>

As expected, the nested `div` elements take up the full width of their container because they are `block` level elements. The `lightgray` background color of the parent element is entirely covered by the elements themselves.

But, by turning the *parent* element into a *flex container*, we can manipulate the orientation of it's children (those elements with `class="flex-item"`) with various properties and values that dictate how those elements will appear in the container. Let's add `display:flex` to the parent `div`:

```css
#flex-container{
    background-color:lightgrey;
    display:flex;
}
.flex-item {
    border: 1px solid black;
    background-color: cornflowerblue;
}
```
The new orientation of the elements is like so:

<div style={{display: "flex",backgroundColor:"lightgray"}} id="flex-container">
    <div style={{border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 1</div>
    <div style={{border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 2</div>
    <div style={{border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 3</div>
</div>

Simply by adding that `display:flex` property, the immediate children (flex items) are turned into `inline` elements and await further orientation. The parent `div` is still block level, as the `display:flex` property allows you to orient its flex-items, not the element itself. 

> The idea of a **main axis** in Flexbox is very important. Most properties allow you to move flex items around, providing space above, below, and between them. This is also done based relative to the main axis. Read on for more :)

## Main Axis:  `flex-direction`
By default, when a flex container is created by giving it the `display:flex` property, the flex items inside of it are oriented left to right as a `row`. This property can be actively manipulated through the `flex-direction` property. 

Let's take our previous example, and spin it a little bit.  By adding a `flex-direction:column` property to it, the container re-orients itself to the previous top-down approach, now they are defined as flex items and able to be oriented based on the container.


<div style={{display: "flex", flexDirection: "column",backgroundColor:"lightgray"}} id="flex-container">
    <div style={{width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 1</div>
    <div style={{width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 2</div>
    <div style={{width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 3</div>
</div>

Now, if we give the container a height larger than the default, say `200px`, these elements will now have room to *orient* based upon the new main axis, which is vertically.

```html
<div id="flex-container">
    <div class="flex-item">item 1</div>
    <div class="flex-item">item 2</div>
    <div class="flex-item">item 3</div>
</div>
```

```css
#flex-container {
  height: 200px;
  background-color: lightgray;
  display: flex;
  flex-direction: column;
}
.flex-item {
  width: 50px;
  border: 1px solid black;
  background-color: cornflowerblue;
}
```
<div style={{display: "flex", height:"200px", flexDirection: "column",backgroundColor:"lightgray"}} id="flex-container">
    <div style={{width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 1</div>
    <div style={{width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 2</div>
    <div style={{width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 3</div>
</div>


## `justify-content` and `align-items`
So we've talked a lot about orienting flex items within its parent container, but we haven't actually *done* it yet. Enter `justify-content` and `align-items`. These are two of the most frequently used Flexbox properties which serve to do this ever-elusive "orientation" being discussed. 

Take the previous example:

<div style={{display: "flex", height:"200px", flexDirection: "column",backgroundColor:"lightgray"}} id="flex-container">
    <div style={{width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 1</div>
    <div style={{width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 2</div>
    <div style={{width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 3</div>
</div>

Here, we have space to orient the items at our discretion. Let's say we want them spaced evenly, from our **main axis**, which is the vertical axis thanks to the `flex-direction:column` property given to the `#flex-container`.  To do so, we can use the `justify-content` property, and give it the value of `space-evenly`, like so:

```css
#flex-container {
  height: 200px;
  background-color: lightgray;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}
.flex-item {
  width: 50px;
  border: 1px solid black;
  background-color: cornflowerblue;
}
```

<div style={{display: "flex", height:"200px", flexDirection: "column", justifyContent: "space-evenly",backgroundColor:"lightgray"}} id="flex-container">
    <div style={{width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 1</div>
    <div style={{width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 2</div>
    <div style={{width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 3</div>
</div>

There are a number of valid options for the `justify-content` property that allow you to orient your flex items in a few different ways.  They include `space-between`, `space-around`, `center`, `flex-start`, and `flex-end`.  More on these during the actual program! For now, know there are many values available to you. And remember:

> `justify-content` only works on the **flex container**, not the individual flex items and orients along the main axis. If your container has a `flex-direction:column` property, the main axis is the vertical (y) axis. If you have no `flex-direction` property, it defaults to `row`, the horizontal (x) axis.

Here's an example of the same thing, except oriented along the *horizontal axis`


```html
<div id="flex-container">
    <div class="flex-item">item 1</div>
    <div class="flex-item">item 2</div>
    <div class="flex-item">item 3</div>
</div>
```

```css
#flex-container {
  height: 200px;
  background-color: lightgray;
  display: flex;
  /* justify content along x axis */
  justify-content: space-between;
}
.flex-item {
  width: 50px;
  height:50px;
  border: 1px solid black;
  background-color: cornflowerblue;
}
```
<div style={{display: "flex", height:"200px", justifyContent: "space-between",backgroundColor:"lightgray"}} id="flex-container">
    <div style={{height: "50px",width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 1</div>
    <div style={{height: "50px",width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 2</div>
    <div style={{height: "50px",width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 3</div>
</div>

The other common property to orient your elements based on the container is `align-items`.  Where `justify-content` aligns items along the *main* axis, `align-items` is a property that orients your items along the perpendicular axis. For example, if have a flex container that is a column (vertical), `align-items` will slide the contents of that container left or right, depending on the value given. 

```html
<div id="flex-container">
    <div class="flex-item">item 1</div>
    <div class="flex-item">item 2</div>
    <div class="flex-item">item 3</div>
</div>
```

```css
#flex-container {
  height: 200px;
  background-color: lightgray;
  display: flex;
  /* justify content along y axis */
 flex-direction: column;
 align-items: center;
}
.flex-item {
  width: 50px;
  height:50px;
  border: 1px solid black;
  background-color: cornflowerblue;
}
```
<div style={{display: "flex", height:"200px", flexDirection:"column", alignItems: "center",backgroundColor:"lightgray"}} id="flex-container">
    <div style={{height: "50px",width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 1</div>
    <div style={{height: "50px",width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 2</div>
    <div style={{height: "50px",width:"50px",border: "1px solid black", backgroundColor: "cornflowerblue"}}class="flex-item">item 3</div>
</div>

Despite the container (area with gray background) being a `column`, the elements inside (flex items) have been oriented left-to-right by way of `align-items`.  Used in conjunction with `justify-content`, you can orient the contents of a container. There are more options for the main axis (`justify-content`), as it informs the primary behavior of the container.


- Intro
- Creating a Flexbox
    - `display:flex`
- Main Axis vs. Off axis
    - Justify vs Align
    - Container vs. Item