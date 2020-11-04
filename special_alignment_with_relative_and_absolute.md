# Special Alignment With Relative and Absolute Positioning 
![Pencils](https://res.cloudinary.com/btvca/image/upload/v1604432022/pencils-806604_1280_nkrrhc.jpg)

In the current world of web development, Flexbox and Grid reign supreme. They are powerful and concise, allowing for quick, clean, and predictable layouts, yielding often-sought-after results. 

But there a number of instances where you will need to reach for other CSS properties to achieve the intended layout. Adding additional functionality like drop-down menus, or creating nav bars that remain on your screen no matter where you navigate to, or styling an element to be slightly "askew' from where it would normally are just a few examples of a powerful tool: positioning.

## `position`
The `position` property in CSS allows you to determine exactly where an element is positioned within the document as a whole. `position` is accompanied by `top`, `right`, `bottom`, and `left` properties that, when given values, will change the orientation of the element by that given value. 

`position` can take a number of values that inform exactly how that element will position itself: `static`, `relative`, `absolute`, `fixed`, and `sticky`. 

Let's run through these to show you exactly what they do.

### `static`
An element with `position:static` has no additional behavior or change to orientation, as it is the default position of any given element. The position of the element is determined by the normal flow of the document. Use this to overwrite any subsequent `position` values that you might encounter should you need to.


### `relative`
`position:relative`, like `position:static`, leaves the element "where it found it" in relation to the normal document flow. The difference is that elements that have the `position:relative` property can be moved up, down, left, and right by a given value by providing the additional properties `top`, `right`, `bottom`, and `left`.  

For example, let's say we have a flex-row of empty `<div>` elements, with space between them, set to `50px` by `50px` and a `background-color` of `cornflowerblue`, like so:

```html
<div id="flex-container">
      <div class="flex-item"></div>
      <div class="flex-item"></div>
      <div class="flex-item"></div>
      <div class="flex-item"></div>
</div>
```
```css
#flex-container{
  display: flex;
  justify-content: space-between;
}
.flex-item{
  width:50px;
  height: 50px;
  background-color:cornflowerblue;
  border: 1px solid black;
}
```
<div id="flex-container" style={{display:"flex", justifyContent:"space-between", border:"2px dotted lightgrey"}}>
      <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div>
       <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div> <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div> <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div>
</div>

But, now let's say we don't want to align any of those elements to the top or bottom of the container, which we could do with flexbox, but rather we want to orient the elements just a *little* off from where they currently reside. 

Let's create a class called `moved-down`, and apply it to 2 of the flex items, like so:


```html
<div id="flex-container">
      <div class="flex-item move-down"></div>
      <div class="flex-item"></div>
      <div class="flex-item move-down"></div>
      <div class="flex-item"></div>
</div>
```

In that `.move-down` class, we will use apply `position: relative`, and a `top` value of `20px`.

```css
.move-down{
    position:relative;
    top: 20px;
}
```

The result will be so:

<div id="flex-container" style={{display:"flex", justifyContent:"space-between", border:"2px dotted lightgrey"}}>
      <div style={{position:"relative", top:"20px",width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div>
       <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div>     <div style={{position:"relative", top:"20px",width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div> <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div>
</div>

Those elements with the `.move-down` class are not removed from their normal position in the document, but they appear `20px` lower than they would otherwise. **The `top` property determines how far from the default top of the element it should currently be oriented**. The same goes for `right`, `bottom` and `left`; the value given is how far the element is moved in the opposite direction.

### `absolute`
When applied to an element, `position:absolute` removes the element from the document flow as a whole. Additionally, the space that the element would otherwise inhabit is no longer on the page either. **While `position:relative` allows for moving elements around based on the normal flow of your page, `position:absolute` removes it completely, and places it as the first element in its container. `top`, `bottom`, `left` and `right` are still available to it.

> Note: When applying `position:absolute` to an element, that element be placed as relative to the closest positioned container, i.e. an element that has a `position` property. Should one not be provided, it will default to the initial document flow, which is effectively the top corner of the page. 

Let's take a look at our previous example:

<div id="flex-container" style={{display:"flex", justifyContent:"space-between", border:"2px dotted lightgrey"}}>
      <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div>
       <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div> <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div> <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div>
</div>

Now, let's apply the `.move-down` class to only one element this time, and set the `position` property to `absolute` instead, to demonstrate it's behavior.

```html
<div id="flex-container">
      <div class="flex-item"></div>
      <div class="flex-item"></div>
      <div class="flex-item move-down"></div>
      <div class="flex-item"></div>
</div>
```
```css
#flex-container{
  position:relative;
  display: flex;
  justify-content: space-between;
}
.flex-item{
  width:50px;
  height: 50px;
  background-color:cornflowerblue;
  border: 1px solid black;
}
.move-down{
    position:absolute;
    top:20px;
}
```
The result is this:

<div id="flex-container" style={{position:"relative",display:"flex", justifyContent:"space-between", border:"2px dotted lightgrey"}}>
      <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div>
       <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div> <div style={{position:"absolute", top:"20px",width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div> <div style={{width:"50px",height:"50px", backgroundColor:"cornflowerblue",border:"1px solid black"}} ></div>
</div>

The element with the `position:absolute` property has been effectively removed from the document's flow. This means that the container readjusts the remaining three `<div>` elements as the only elements in the `#flex-container`. The "missing" element then, is positioned on top of the first element of the container, as that same `#flex-container` has been given the `position:relative` property. By moving the element down `20px`, we see that they are effectively taking up the same space in the container.

### `fixed`
`position:fixed` is similar to `position:absolute` in that an element is removed from the normal flow of the document. The primary difference is in that, unlike `position:absolute`, `position:fixed` will ALWAYS orient itself relative to the document as a whole. This makes it perfect for nav bars, or anything else that, regardless of how the rest of the page is oriented, that particular element will *always* appear wherever it is given. This is difficult to demonstrate within the flow of the lesson, so please take a look at the sandbox below to see it in action.

```html
    <h1>
      Header
    </h1>
    <p>
      "Sed ut perspiciatis unde omnis iste natus error sit voluptatem
      accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab
      illo inventore veritatis et quasi architecto beatae vitae dicta sunt
      explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut
      odit aut fugit, sed quia consequuntur magni dolores eos qui ratione
      voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum
      quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam
      eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat
      voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam
      corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur?
      Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam
      nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas
      nulla pariatur?"
    </p>
    <br />
    <p>
      "Sed ut perspiciatis unde omnis iste natus error sit voluptatem
      accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab
      illo inventore veritatis et quasi architecto beatae vitae dicta sunt
      explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut
      odit aut fugit, sed quia consequuntur magni dolores eos qui ratione
      voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum
      quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam
      eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat
      voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam
      corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur?
      Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam
      nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas
      nulla pariatur?"
    </p>
    <br />
    <p>
      "Sed ut perspiciatis unde omnis iste natus error sit voluptatem
      accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab
      illo inventore veritatis et quasi architecto beatae vitae dicta sunt
      explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut
      odit aut fugit, sed quia consequuntur magni dolores eos qui ratione
      voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum
      quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam
      eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat
      voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam
      corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur?
      Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam
      nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas
      nulla pariatur?"
    </p>
    <nav>
      <ul>
        <li>link</li>
        <li>link</li>
        <li>link</li>
      </ul>
    </nav>
```
```css
nav{
  position:fixed;
  top:0px;
  left:0px;
  background-color:#aaa;
  width:100%
}
ul{
  display:flex;
}
li{
  list-style-type:none;
  padding-right:15px;
}

h1{
  margin-top:50px;
}
```

Will render like so. Try scrolling.

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/position-fixed-bca?path=style.css&previewSize=100&attributionHidden=true"
    title="position-fixed-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

Note that, despite the `<nav>` element being placed at the bottom of the HTML, the `position:fixed` CSS property removes the element from the natural flow of the document and, in conjunction with the `top` and `left` properties, serves to make it remain at the top of your page regardless of other behavior.

### `sticky`
An element with `position:sticky` is similar to `position:relative`, except that it works within any element that has what is referred to as a "scrolling mechanism".  This means when an element, whether embedded or otherwise, has a scrollbar, the contained element that has the property of `position:sticky` will remain at the provided `top`/`bottom`/`left`/`right` values regardless of its position within the scrolling element. 

It can be thought of as a combination of both `relative` and `fixed` positioning. An element with `position:fixed` will remain `relative` until it crosses the point determined by the one of the positioning values, like `top`. Then, after crossing that threshold, the element will be `fixed` to that position. Great when you want something to start following you as you scroll, without initially behaving as fixed on the page.

In this example, we have a series of `<h2>` elements that have been given the following CSS:

```css
h2{
  position:sticky;
  top:0px;
  background-color:#fff;
}
```
Now, when any `<h2>` element crosses that threshold of `top: 0px`, it will remain there until the action is reversed. Note that these elements stack atop one another as you scroll.

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/position-sticky-bca?path=style.css&previewSize=100&attributionHidden=true"
    title="position-sticky-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

## Final Musings
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

The `position` property in CSS is made available from the get-go, and can be used to achieve all of those strange edge-cases that would otherwise be a difficult process. Used along `display` properties like `flex` and `grid`, we can create highly dynamic pages that are ready for any style or functionality you might want. Review here, then continue onto the exercises.

- The `position` property is used to alter an element's placement within the HTML document.
- The `position` property is used in conjunction with `top`, `bottom`, `left` and `right` properties.
- There are 5 values for the`position` property: `static`, `relative`, `absolute`, `fixed` and `sticky`.
- `static` is the default flow of an element in the document.
- `relative` allows for the positioning properties (`top/bottom/left/right`) to shift the element.
- `absolute` removes the element from the flow and orients itself in relation to the closest element with a `position:relative` property.
- `fixed` is like `absolute` but always lifts to the entire document.
- `sticky` is like `relative` until it is scrolled to the provided `top/bottom/left/right` value, at which point it becomes `fixed` and stays on that position on the page.

Happy Coding :)

-Paul

## Exercises

1) Position the `<h1>` element so that it will always be `50px` from the top, and `100px` from the left, *in relation to the document as a whole*.

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/position-exercise-one-bc?path=style.css&previewSize=0&attributionHidden=true"
    title="position-exercise-one-bc on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

<details> 
<summary>Answer</summary>

```css
#question-one{
  color: red;
  position:fixed;
  top:50px;
  left:100px;
}
```
</details>

2) Position the `<h1>` element `150px` left and `40px` down relative to where it normally is without disrupting the natural flow of the document.

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
   src="https://glitch.com/embed/#!/embed/position-exercise-two-bca?path=style.css&previewSize=0&attributionHidden=true"
    title="position-exercise-two-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>


<details> 
<summary>Answer</summary>

```css
#question-two{
  color:red;
  position:relative;
  top:40px;
  left: 150px;
}
```
</details>

3) Position the element with the `bottom-left` class relative to container element. Have it be `50px` from the bottom and `50px` from the left. Throw some background-color in there too for fun.


<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
  src="https://glitch.com/embed/#!/embed/position-exercise-three-bca?path=style.css&previewSize=0&attributionHidden=true"
    title="position-exercise-three-bca on Glitch" allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>


<details> 
<summary>Answer</summary>

```css
.bottom-left{
  color:red;
  position:relative;
  top:40px;
  left: 150px;
}
```
</details>
