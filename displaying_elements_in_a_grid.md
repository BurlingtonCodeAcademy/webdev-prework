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

### `grid-template-area`

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
As long as the provided values are separated by a white space, the provided values dictate the width of each individual container.  The whitespace following each column, then, is the difference between the `width` of your items and the width of the container as a whole.


> This lesson will introduce the `fr` unit, which changes its value relative to the container it resides in. More in a bit!

> **NOTE:** We have intentionally omitted covering most dynamic units to date, as they are often a source of additional confusion. **This is not meant to dissuade you from their use**, as they are a primary means of creating elements that scale as your page changes sizes. Using units that do not change, like `px`, is simply a more direct way of discussing core concepts. 

- Intro
    - why use grid
    - highlight limitations of flexbox
- `grid-template`  columns and rows
- Automatically dynamic
    - `minmax`
- Auto rows
-  `gap`
- Flexbox and Grid together
- Exercises