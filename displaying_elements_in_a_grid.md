# Displaying Elements in a Grid

![grid of multicolored squares](https://res.cloudinary.com/btvca/image/upload/v1604083040/square-2724387_1280_mqncbb.jpg)


As you may have gathered at this point, there is no single way to design your web pages. The `display` property allows you do orient your elements in a variety of ways. So far, we have covered 2 of them. One, the **static way**, with `block`, `inline`, and `inline-block` properties that orient themselves relative to default page flow, or top-to-bottom. The other is the **Flexbox way**, a one-way ticket to creating container elements that allow you to orient its contents left-to-right, or top-to-bottom based on the `flex-direction` you provide.

Flexbox in particular is a fantastic tool, that allows for a quick, scalable, hands-off approach to web design. Need a few items spaced evenly left-to-right? flexbox is your guy. Need a column? Same. But what happens if you need orient your elements relative to both the horizontal and vertical axes?

That is where `grid` comes in! With it, you can take the *items* within your *container* and place them relative to more than just the single dimension of a flex row or a flex column! 

## Creating a Grid

`grid` is a two-dimensional layout system in CSS, and can be used to lay out larger sections of a page or smaller, complicated elements. Like in mathematics, a grid is a series of horizontal and vertical lines that make up *tracks*, or the columns and rows that are created by those lines intersecting, like graph paper:

![graph paper](https://res.cloudinary.com/btvca/image/upload/v1604349757/notepad-593363_1280_rdui6b.jpg)

`display:grid`

By setting a parent container to `display:grid`, we can state how many columns we would like in a given area, as well as how many *rows* we would like that container to consist of. Those columns and rows can be assigned *fixed* or *flexible* sizes that determine their dimensions. 

Just like with Flexbox, Grid can be assigned to an element like so:

```html
<div id="grid-container">
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
</div>
```
```css
#grid-container{
    display: grid;
}
.grid-item{
    /* To make the empty divs visible */
    width: 50px;
    height: 50px;
    background-color: cornflowerblue;
    border: 1px solid black;
}
```

This will render like so:

<div style={{display:"grid"}}>
    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>
        <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>
   
</div>

Um... this is a column, right? Yes! That is because our *grid container* doesn't have any additional columns defined. What you see above is as intended: a grid container with six grid items inside of it. The only thing is, all of the `.grid-item` elements reside within a single column. Our grid isn't very 2-dimensional yet. 

### `grid-template-columns`

If we add a `grid-template-columns` property, we can make these grid items orient themselves automatically across a few columns. Let's do so now:

```html
<div id="grid-container">
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
</div>
```
```css
#grid-container{
    display: grid;
    grid-template-columns: repeat(3, 100px)
}
.grid-item{
    /* To make the empty divs visible */
    width: 50px;
    height: 50px;
    background-color: cornflowerblue;
    border: 1px solid black;
}
```
Will render as:

<div style={{display:"grid", gridTemplateColumns:"repeat(3, 100px"}}>
    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>
        <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>
   
</div>

The `grid-template-columns` property defines the number of columns, and the `repeat()` CSS function does so with a little bit of style. `repeat(3, 100px)` is shorthand for "make three columns that are `100px` wide each". The same can be said like so:

```css
#grid-container{
    display: grid;
    grid-template-columns: 100px 100px 100px;
}
```
As long as the provided values are separated by a white space, they dictate the width of each individual container.  The whitespace following each column, then, is the difference between the `width` of your items and the width of the column as a whole.

### `grid-template-rows`
`grid-template-rows` is similar to `grid-template-columns`, except that the values given will determine the *height* of the rows in a grid. They can be assigned in the same way that the `grid-template-columns` is, by using the `repeat()` CSS function, or values separated by a whitespace. 

Let's add some rows to our current grid, like so:

```html
<div id="grid-container">
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <!-- Added more divs -->
</div>
```
```css
#grid-container{
    display: grid;
    grid-template-columns: repeat(3, 100px);
    /* Add rows that are 150px tall */
    grid-template-rows: repeat(3,150px);
}
.grid-item{
    /* To make the empty divs visible */
    width: 50px;
    height: 50px;
    background-color: cornflowerblue;
    border: 1px solid black;
}
```

<div style={{display:"grid", gridTemplateRows:"repeat(3, 150px", gridTemplateColumns:"repeat(3,100px)"}}>
    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>
        <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>
         <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>  <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>  <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div> 
   
</div>

More grid items have been added to show that these elements will be placed inside of the grid in the order they appear in your html. You can define your grid with `grid-template-columns` and `grid-template-rows`! Easy! 

But what happens when you add more items to your grid than there are spots (cells) for them to live in? There is some unique behavior 

## Additional Behavior
By default, when a grid is created, you will need to determine the number of columns. As we saw before, not doing so results in a single-column grid, and that's probably not what we want. Not much of a grid at that point!

The `grid-template-rows` property is not as necessary, as the default behavior is to automatically adjust the height of a row to fit the largest content of that row. When all rows have been filled but there are more items to place in the grid, a new *implicit row* will be created automatically, that will also (by default) fit the content provided. 

### `grid-auto-rows`
You can set automatic row creation with the `grid-auto-rows` property. The value you assign to it will dictate the height of additional rows outside of those that have already been defined.

> If no rows have been explicitly defined, but a `grid-auto-rows` value has been given, all rows will default to that given value.

Let's see it in action:

``` html
<div id="grid-container">
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <div class="grid-item"></div>
    <!-- Added more divs -->
</div>
```

```css
#grid-container{
    display: grid;
    grid-template-columns: repeat(2, 100px);
    /* Add rows that are 150px tall */
    grid-auto-rows: 100px;
}
.grid-item{
    /* To make the empty divs visible */
    width: 50px;
    height: 50px;
    background-color: cornflowerblue;
    border: 1px solid black;
}
```

Will render like so:

<div style={{display:"grid", 
gridAutoRows:"100px",gridTemplateColumns:"repeat(2,100px)"}}>
    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>
        <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}></div>
        </div>

Note that, to demonstrate the functionality, we reduced the number of columns to 2. Each `row` is then automatically (or *implicitly*) created, has a height of `100px`.  If you are creating a grid but don't know exactly how many items will inhabit it, this is a good property to have in your back pocket. 

### `grid-column` and `grid-row`
So, we've outlined our grid with the proper number of columns and rows. The grid items are placed automatically in the grid, and we go about our merry way. But what happens when you want to change the order of the items in your grid? We can do so by adding properties to the item itself. These properties are `grid-column` and `grid-row`.

Here, we have a 3x2 grid, where the divs from before have been numbered to indicate order:

```html
<div id="grid-container">
    <div class="grid-item">1</div>
    <div class="grid-item">2</div>
    <div class="grid-item">3</div>
    <div class="grid-item">4</div>
    <div class="grid-item">5</div>
    <div class="grid-item">6</div>
</div>
```
```css
#grid-container{
    display: grid;
    grid-template-columns: repeat(3, 50px)
}
.grid-item{
    /* To make the empty divs visible */
    width: 50px;
    height: 50px;
    background-color: cornflowerblue;
    border: 1px solid black;
}
```
Will render as:

<div style={{display:"grid", gridTemplateColumns:"repeat(3, 50px"}}>
    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>1</div>
        <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>2</div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>3</div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>4</div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>5</div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>6</div>
</div>

Now, let's say we want to move box 3 to where box 1 is. We can do so by indicating the start and stop position of the rows and columns to determine exactly how much space we want any individual item to take up.

The syntax for this is as follows:

```css
#grid-item{
    grid-column: start / stop;
    grid-row: start / stop;
}
```

`start` and `stop` are placeholder values that will be replaced by the row and column lines you would like your item to span. These are numbers, and determined like so:

![grid row and column](https://res.cloudinary.com/btvca/image/upload/v1601046389/grid_lines_yus78s.png).

So, if we want to place item 3 in the position of item 1, we would assign it the values:

```css
#grid-item{
    grid-column: 1 / 2;
    grid-row: 1 /2;
}
```

Let's see it in action:


```html
<div id="grid-container">
    <div class="grid-item">1</div>
    <div class="grid-item">2</div>
    <div id="item-three" class="grid-item">3</div>
    <div class="grid-item">4</div>
    <div class="grid-item">5</div>
    <div class="grid-item">6</div>
</div>
```
```css
#grid-container{
    display: grid;
    grid-template-columns: repeat(3, 50px)
}
.grid-item{
    width: 50px;
    height: 50px;
    background-color: cornflowerblue;
    border: 1px solid black;
}
/* placing the div based on its column and row */
#item-three{
    grid-column: 1 / 2;
    grid-row: 1 / 2;
}
```
Will render as:

<div style={{display:"grid", gridTemplateColumns:"repeat(3, 50px"}}>
    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>1</div>
        <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>2</div>    
        <div style={{ gridColumn:"1/2",gridRow:"1/2",width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>3</div>  
          <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>4</div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>5</div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>6</div>
</div>

If you have something that needs to be oriented differently relative to the default flow of a grid, reach for these! **But that's only the beginning!** You can also make items take up more than one cell (grid square)!  Simply change the rows and columns to take up more than one!



```html
<div id="grid-container">
    <div class="grid-item">1</div>
    <div class="grid-item">2</div>
    <div id="item-three" class="grid-item">3</div>
    <div class="grid-item">4</div>
    <div class="grid-item">5</div>
    <div class="grid-item">6</div>
</div>
```
```css
#grid-container{
    display: grid;
    grid-template-columns: repeat(3, 50px)
}
.grid-item{
    width: 50px;
    height: 50px;
    background-color: cornflowerblue;
    border: 1px solid black;
}
/* placing the div based on its column and row */
#item-three{
    grid-column: 1 / 3;
    grid-row: 1 / 3;
}
```
Will render as:

<div style={{display:"grid", gridTemplateColumns:"repeat(3, 50px"}}>
    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>1</div>
        <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>2</div>    
        <div style={{ gridColumn:"1/3",gridRow:"1/3",width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>3</div>  
          <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>4</div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>5</div>    <div style={{width:"50px",height:"50px",backgroundColor:"cornflowerblue", border:"1px solid black"}}>6</div>
</div>

## Quick dynamic layouts with `minmax`

One of the most useful aspects of creating grids is the ability to have them quickly scale to different screen sizes, so your page looks good regardless of its dimensions. Maybe you'll have 4 columns when your browser is full-screen, but on a phone you'll only want one.

You can do so quickly and efficiently with the `minmax()` CSS function, which allows for default behavior based on the current size of the container.

```css
#grid-container{
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr))
}
```

The CSS above is using a few things we have yet to cover:

- `auto-fill` is a value that can be passed to `repeat()` that says, fill the container with as many columns as possible.
- `minmax(100px, 1fr)` determines the width of the individual column: `100px` denotes the *smallest* width of the column possible.
- `fr` is a grid-specific unit of measure that divides the container's width into proportionate widths relative to the number of units.
    - For example, a column with a `width` of `2fr` will be twice as wide as one with a `width` of `1fr`

> **NOTE:** We have intentionally omitted covering most dynamic units to date, as they are often a source of additional confusion. **This is not meant to dissuade you from their use**, as they are a primary means of creating elements that scale as your page changes sizes. Using units that do not change, like `px`, is simply a more direct way of discussing core concepts. Familiarize yourself with `fr`, as it is wildly helpful in creating dynamic grids!

## Final Musings
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

It is worth mentioning that, like Flexbox, the scope of this lesson is very limited! But, some of the most important fundamentals have been touched upon. Review, and then complete the exercises.

- A grid is created with `display: grid`
- That container is given a number of `column`s and `row`s with `grid-template-columns` and `grid-template-rows` respectively.
- Like flexbox, the immediate children are turned into grid items and places within the outlined grid.
- "overflow" grid items are placed sized to the content by default, but can be defined further using `grid-auto-rows`.
- Grid items can also be moved around the grid by defining their `grid-column` and `grid-row`.
- `minmax()` is a CSS function that allows you to create highly dynamic grids, with column and row numbers determined by the current width of the container itself.

## Exercises

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/fork-heliotrope-radar?path=style.css&previewSize=0&attributionHidden=true"
    title="fork-heliotrope-radar on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

1) Turn `#grid-one` into a grid with 3 columns that has columns `50px` wide.


<details>
<summary>Answer</summary>

```css
#grid-one {
    display: grid;
    grid-template-columns: 50px 50px 50px
    /* or:
    grid-template-columns: repeat(3,50px)
     */
}
```
</details>


2) Turn `#grid-two` into a grid with 2 `50px` columns that has default behavior set for every *implicit row*. Make each new row `150px`.

<details>
<summary>Answer</summary>

```css
#grid-two {
    display: grid;
    grid-template-columns: 50px 50px;
    grid-auto-rows: 150px;
}
```
</details>

3) Turn `#grid-three` into a grid with 2 columns where the SECOND column is `100px` and the first is `50px`. Make 3 rows where the first and third are `50px` and the second is `150px`.

<details>
<summary>Answer</summary>

```css
#grid-three {
    display: grid;
    grid-template-columns: 50px 100px;
    grid-template-rows: 50px 150px 50px;
}
```
</details>


4) Turn `#grid-four` into a grid with 2 columns whose widths are `50px`. Make 3 rows that are `150px` high. Add the appropriate `id`that allows you to move `div` number 5 so that it replaces `div` number 2. Then do that. 

<details>
<summary>Answer</summary>

```css
#grid-four {
    display: grid;
    grid-template-columns: 50px 50px;
    grid-template-rows:150px 150px 150px;
}
#grid-item-five{
  grid-column: 2/3;
  grid-row:1/2;
}
```
</details>