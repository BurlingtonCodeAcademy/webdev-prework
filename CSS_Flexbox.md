# CSS Flexbox
![Yoga class](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1600888151/women-1178187_1280_fzhkrh.jpg)
 
Intro and overview
- Uses
- Context in CSS
- Context in Page layout

# Terms and Basics
Properly using flexbox hinges on the container-item relationship. This relationship determines not only the way certain elements on your web page will behave, but how the elements *inside* of them will as well. Those elements can then go on to become their own flexboxes, which define how the elements inside them are oriented, and so on and so on. 

So, what's that mean? Let's break it down.

## The container-item relationship
Take this box:

![box](https://res.cloudinary.com/btvca/image/upload/v1600954281/flexbox1_cahktd.png)

It represents an element on your webpage, let's say a row, that will hold 3 `<div>` elements inside of it, as children. We eventually want them to line up left-to-right, on a single line, spaced out nice and evenly.

Those `<div>` elements, like lots of HTML, will have a default `display` property of `block`, meaning that, left-to-right, they will take up an entire line (row) on the page individually. Adding them as children to this box as is will result in something like this:

![box with blocks](https://res.cloudinary.com/btvca/image/upload/v1600954281/flexbox2_hncgoq.png)

These `<div>` elements are each taking up the entire row! We want them to orient themselves left to right, and more so, we want to be able to move them around; rearrange them, stack them up on the left, stack them vertically, you name it!

Enter flexbox! By its very nature, when you give the CSS property of `display:flex` to an element, any and all *immediate* (that is, one level down) children of that element are automatically oriented, and moreso, designated as *flex items* of that parent *container*. This is the the container-item relationship in a nutshell. Giving the black box (the container) the css property of `display:flex` in above example will result in something like so:   

![flexbox row](https://res.cloudinary.com/btvca/image/upload/v1600954281/flexbox5_whcjbh.png)

Here, we see the desired effect! By default, giving a container `display` property of `flex` will orient the child elements left-to-right, also known as a `row`. Another term used to describe the orientation of a *container*'s *items* is *main-axis*. All *items* will line up consecutively along the *main-axis*, which in this case is left to right. Other options are right-to-left, top-to-bottom, and bottom-to-top. 

But what about that annoying whitespace?

![whitespace in flexbox](https://res.cloudinary.com/btvca/image/upload/v1600954281/flexbox4_wkpy5f.png)

One of the many perks of using flexbox is the `justify-content` property. It is assigned to the *parent container* and determines where the *flex-items* are positioned inside of said container.
One such property is `space-between`, which fills the entire container. and spaces items evenly within it.  Giving the container (the black box) these 2  CSS properties:

```css
display:flex;
justify-content: space-between;
```

will result in:

![space-between flexbox row](https://res.cloudinary.com/btvca/image/upload/v1600955932/flexbox6_tj8x4b.png)

Ahh... masterpiece.

To reiterate, a container is the element that has been given a `display` property of `flex`. All elements that are *direct children* are then deemed *flex-items* that can be oriented based on the container they reside in. 

Give it a shot! See how the elements inside of the `#container` `<div>` align by default, and how adding the commented-out properties then change its behavior. The elements have been given fixed dimensions (height and width) to aid in the visualization process. 


<div class="glitch-embed-wrap" style="height: 420px; width: 100%;">
  <iframe
    src="https://glitch.com/embed/#!/embed/flexbox-basics-bca?path=style.css&previewSize=0&attributionHidden=true"
    title="flexbox-basics-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style="height: 100%; width: 100%; border: 0;">
  </iframe>
</div>


# The Parent (container)
The parent container is where all of the high level orientation choices take place. It is where you declare, "I will keep parts of my website in you, and they will fit like so". The example above declares a container that, by default, is a `row` that *justifies* the items within it so that they are spaced out a particular way using `justify-content: space-between`. 

But that's only one property! There are a *ton* of ways you can customize the behavior of a container. Let's highlight a few here:

## `Flex-direction`
As stated, when you create a flex-container by assigning it to `display:flex`, the default *main-axis* is left-to-right, or `row`. but there are options to do so in any direction!

```css
flex-direction: row /*(default) */
flex-direction: row-reverse /* right-to-left */
flex-direction: column /*top-to-bottom*/
flex-direction: column-reverse /*bottom-to-top */
```

Try it here:

<!-- Copy and Paste Me -->
<div class="glitch-embed-wrap" style="height: 420px; width: 100%;">
  <iframe
    src="https://glitch.com/embed/#!/embed/flex-direction-bca?path=style.css&previewSize=0&attributionHidden=true"
    title="flex-direction-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style="height: 100%; width: 100%; border: 0;">
  </iframe>
</div>

## `justify-content`
We've already been introduced to this one. `justify-content` is dependent on the `flex-direction`, which defines the *main-axis*.  Let's say the main axis is the default `row`, which runs left-to-right in a container. `justify-content` tells the container how to position the *items* within it. There are a lot of these, so let's go ahead and play around with it.

Try changing the `justify-content` property to each of the following: 

`flex-start`, `flex-end`, `center`, `space-between`, `space-around`, and `space-evenly`.

 Note the slight differences in orientation between the last three. 

<div class="glitch-embed-wrap" style="height: 420px; width: 100%;">
  <iframe
    src="https://glitch.com/embed/#!/embed/justify-content-bca?path=style.css&previewSize=0&attributionHidden=true"
    title="justify-content-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style="height: 100%; width: 100%; border: 0;">
  </iframe>
</div>

Then, change the `flex-direction` to `column` and run through these `justify-content` properties again. Note how they maintain their behavior, but the *main-axis* has changed entirely! Now, they're running top-to-bottom, instead of left-to-right!

## `flex-wrap`
By default, flex-items will try to fit on one line, be it a `row` or a `column`. If the total width or height of the items within a container exceed the container's width, items will adapt to remain within the container.

In the example below, we have a container with a width of `100px`, but 3 items with a width of `50px` each. This causes the items squish, no longer allowing for their full width to take hold. `flex-wrap`, when set to `wrap`, allows them to break to another line. Try it here:

<!-- Copy and Paste Me -->
<div class="glitch-embed-wrap" style="height: 420px; width: 100%;">
  <iframe
    src="https://glitch.com/embed/#!/embed/flex-wrap-basics-bca?path=style.css&previewSize=0&attributionHidden=true"
    title="flex-wrap-basics-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style="height: 100%; width: 100%; border: 0;">
  </iframe>
</div>

`flex-wrap` properties:

```css
flex-wrap: no-wrap; /*default*/
flex-wrap: wrap;
flex-wrap: wrap-reverse;
```

## `align-items` 
`align-items` serves a similar purpose to `justify-content` in that it deals with lining the items up, except it does so  *perpendicular* to the main-axis, also referred to as the *cross axis*. 

In a `row`, `align-items` will orient your *flex-items* along the vertical (or y) axis. Use it in conjunction with `justify-content` to orient the items in your container. 

The properties are similar to those of `justify-content`, but some go by slightly different terms. The properties are: 

`flex-start`, `flex-end`, `center`, `stretch` (default), and `baseline`.

Try them here:

<div class="glitch-embed-wrap" style="height: 420px; width: 100%;">
  <iframe
    src="https://glitch.com/embed/#!/embed/align-items-bca?path=style.css&previewSize=0&attributionHidden=true"
    title="align-items-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style="height: 100%; width: 100%; border: 0;">
  </iframe>
</div>


## `align-content`
> `align-content` is a bit of a misnomer, as the property that parallels `justify-content` is more `align-items`. 

`align-content`, then, serves to orient the *lines* of items within a flex-container. If there is only one line, say an individual row or column, `align-content` will have no effect. 

See here, when the container is just too small for the items to exist in one row:



We have set the container to `wrap`, so the third item exists on a second row. Now, because we have multiple rows, `align-content` will effectively orient them.

Replace `align-content` with the following properties to see how they behave:

`flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`, `stretch` (default).

# The Children (items)

# Nested Containers