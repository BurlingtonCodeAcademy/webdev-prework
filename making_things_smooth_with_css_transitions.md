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
The `transition-property` property identifies what property or properties will actually be effected during a transition. The property can be any that has a visual implication and included in the list maintained by MDN.  To see the full list of animatable CSS properties, visit [their site.](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties).

Aside from the custom identifier that explicitly indicates what the property in question should be, you may also give it the value of `none` or `all` to indicate that *no* CSS properties should be animated, or if *all* CSS properties should be animated. 

Separating the values with a comma allows for multiple CSS properties to be selected while not having to select all of them.

```css
/* only animates color */
div{
  transition-property: color
}
/* animates all properties */
div{
  transition-property: all;
}
/* animates no properties */
div{
  transition-property: none;
}
```

But specifically designating what properties will be animated during the change in state is not enough to cause your elements to animate. Is is but one piece of the `transition` puzzle; the next is how long you'd like the animation to take.

### `transition-duration`

Besides `transition-property`, there is only one other required property to make your CSS transitions actually work, and that is `transition-duration`. Without an explicit time frame in which to execute the animation, your browser won't know how long to take to execute your animation. 

Take a look at these two examples:

```html
  <h3>Here is an h3 element</h3>
  <h2>Here is an h2 element</h2>
```
```css
h3 {
  transition-property: color;
  transition-duration: 0.2s;
}
h3:hover {
  color: orange;
}

h2 {
  transition-property: color;
  transition-duration: 2s;
}
h2:hover {
  color: orange;
}
```

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/transition-duration-example-bca?path=style.css&previewSize=100&attributionHidden=true"
    title="transition-duration-example-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

The `transition-duration` property accepts a unit of time in seconds (`s`) or milliseconds (`ms`). `.5s` is the same as `500ms`. 

### `transition-delay`

The optional `transition-delay` property defines how long to wait for a transition to begin after the initial triggering event. This delay can be any number, either positive or negative.

- A value of `0s` calls for the transition effect to start immediately. This says, wait zero seconds before executing the transition.

- A positive number will delay the transition for the provided amount of time. This is the typical use case.

- A negative number is a bit strange in its usage. Effectively, it immediately executes the animation like it was provided `0s`, but the animation picks up as if it had been transitioning already by the provided amount of time.

You can also provide multiple 

Let's see these in action:

```html
  <div id="zero-seconds"></div>
  <div id="one-second"></div>
  <div id="negative-one-second"></div>
```
```css
div {
  background-color: cornflowerblue;
  width: 50px;
  height: 50px;
  border: 1px solid black;
}
div:hover{
  width:100px;
}
/* Immediately starts transition */
#zero-seconds {
  transition-property: all;
  transition-duration: 2s;
  transition-delay: 0s;
}
/* Watis one second to start transition */
#one-second {
  transition-property: all;
  transition-duration: 3s;
  transition-delay: 1s;
}
/* Immediately starts transition, but starts in the middle of transition */
#negative-one-second {
  transition-property: all;
  transition-duration: 3s;
  transition-delay: -1s;
}
```

<div class="glitch-embed-wrap" style={{height: "420px", width: 
"100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/golden-dandy-dollar?path=style.css&previewSize=100&attributionHidden=true"
    title="golden-dandy-dollar on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

You can also specify multiple delay times! This can be useful for transitioning with multiple properties, but they will be in the same order as the `transition-property` values listed. Take this CSS for example:

```css
div{
  transition-property: color, height;
  transition-delay: 1s, 0s;
}
```

In this, the `height` property will begin to transition before the `color` property. If there are more delays than properties, they will stop being counted after the properties have each had a time applied to them. If there are more properties than delays, the delays will be looped over until all properties have had a delay applied to it. 

### `transition-timing-function`
The `transition-timing-function` property is the 

- duration
- timing
- delay
- transform

- Final musings
- Exercises
