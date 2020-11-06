# Making Things Smooth With CSS Transitions
![assorted color dandelions](https://res.cloudinary.com/btvca/image/upload/v1604691739/dandelion-2817950_1280_rjht7y.jpg)

And so, you've almost made it through another week of our web development pre-work track. Congratulations! As a reward for your hard work, we will be turning our attention from some of the "drier" CSS topics and will instead be having fun with one of the most fun aspects; transitions! 

The topics covered in this lesson will tie together a lot of what you have learned so far, while adding a few of the more exciting aspects as well. Through this combined knowledge from previous lessons we will learn how to define the transition between two different states of an element for a smoother application of styles. So, without further ado, we let's take a look at *CSS transitions*.

## Basic Concepts
CSS transitions allow for an easy, relatively hands-off tool for controlling properties between different states. Think back to our previous lesson. Remember the `:hover` pseudo-class? When implemented, it would change the style of the given element when a cursor moves over it, but would do so instantaneously. Thanks to CSS transitions and their surrounding properties, you can cause those same changes in state to occur, but over a fixed period of time instead of immediately. 

Let's take a look at an example before getting into the the terminology and nuances that accompany them.

Here, we have a `<div>` element that, when hovered over, will increase it's `border-radius` and effectively become a circle:

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/css-transitions-hover-example-bca?path=style.css&previewSize=100&attributionHidden=true"
    title="css-transitions-hover-example-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

The CSS that makes this possible looks like the following:

```css
div {
  width: 50px;
  height: 50px;
  background-color: cornflowerblue;
  border:3px solid black;
  transition: all 1s ease-in;
}

div:hover{
  background-color:firebrick;
  border-radius:50%;
}
```

The browser handles the in-between aspects of the CSS transition, with the end result being whatever has been defined by the pseudo-class. The `transition` property, then, dictates how that browser-handled behavior will act. It is shorthand for 4 crucial aspects to CSS transitions: ` transition-property, transition-duration, transition-timing-function, and transition-delay.`

### `transition-property`
