# Adding Style to HTML Elements
![abstract paint paint splash](https://res.cloudinary.com/btvca/image/upload/v1603132228/abstract-2468874_1280_h0zv9g.jpg)
As we've seen in prior lessons, HTML on its own can be a little one-dimensional. There is an implicit functionality to many HTML elements, both in terms of structure, and their ability to highlight certain content. But what happens when you want to go further? 

The answer lies in CSS, a language we have alluded to *and* lightly dabbled in. CSS allows you to *style* your pages, orienting elements and adding, colors, fonts, pretty much anything! With CSS, you're well on your way to becoming the accomplished developer we here at BCA know you can be :)

## What is CSS?
CSS, or *cascading stylesheets*, is a style sheet language that defines the rules for presenting a markup document like HTML. Alongside HTML and JavaScript, CSS is a key aspect of what makes the web behave like it does. 

CSS strives to separate and present the content of a page by applying specific layouts, fonts, and various other properties to said page. Doing so benefits the user in a variety of ways, from accessibility to good old fashioned aesthetics. More versatility and customizability means more fun for the developer, too! 

While HTML defines the text and media content itself that will be displayed on the page, CSS is used to describe what that content will eventually look like. Because it is more of a rule set than visible content, CSS may be applied to multiple HTML documents (i.e. pages), allowing for repeated use of a single CSS file. This redundancy is more efficient, coherent, and reduces page load speed when loading pages that share the same style sheet. This means that a single CSS document can be used for your entire site! 

All you need to do is provide a path (both relative or absolute) to the CSS file you'd like to use. This information typically lives in the `<head>` of any given HTML document as metadata. The link itself appears in a `<link>` tag. As we have shown before in the lesson on how a web page is loaded, it would look something like this:

```html
<link href="/style.css" rel="stylesheet">
```
Now, when that page is loaded, the linked stylesheet will be applied to it as well. 

## What CSS looks like

CSS targets explicit elements in the HTML document that it is linked to. *Selectors* are used to target elements within the HTML, and tells them how to appear. In some cases, they even tell that element and the *nested* elements inside it how to be displayed, like top to bottom, or left to right (or both!). The example below targets *all* `<h1>>` elements and makes them blue:

This css:

```css
h1{
    color:blue;
}
```
And this HTML:

```html
<h1>Look at my blue header </h1>
```
Will render as:

<h1 style={{color:"blue"}}>Look at my blue header</h1>

Let's break it down:

![anatomy of css](https://res.cloudinary.com/btvca/image/upload/v1603138025/css_anatomy_f5vplq.png)

In its entirety, the above image is known as a *ruleset*, or *rule*. Let's look at each of these a bit closer:

### Selector
The selector, as we said previously, is the string that tells the HTML what the following *declarations* are going to be applied to. In this case, it is the `<h1>` tag. Longer CSS stylesheets will have multiple selectors that further customize your elements, and as we'll see in the next lesson, they can get quite descriptive!

> Remember linking anchor tags to a element with a provided `id` in our HTML lessons? `id`s are one of the many selectors we can apply to our HTML in order to target specific elements in our CSS!

### Property
CSS properties are similar to HTML attributes in that they further customize the element at hand. Like attributes, certain properties can only be applied to certain elements, but unlike attributes, they serve no functional purpose. Instead, properties, like `color`, `font-size`, and `background-image` simply add some color and shape to whatever is being targeted by the *selector*. There are many, many properties to familiarize yourself with! More later.

### Value
The property *value* is what is to be applied to the element's property. In this example, it is `blue`. Values are contextualized based on the property, so certain values, short hands, and formats will only register properly when affixed to a valid property. 
For example, `color:red;` is a perfectly valid `property:value;` relationship, as is `width:500px`, but `color: 500px` is not. Not surprising, but worth nothing.

### Declaration
The declaration is a single line of `property:value;` relationship. It is terminated by a semi-colon. 

### Additional behavior and notes
- Selectors must be followed by `{}`, as shown above. This denotes the beginning and end of specific rulesets.

- In a declaration, the `property` and `value` must be separated by a colon (`:`) in order to properly render.

- Each rule must be terminated by a semi-colon (`;`) in order to properly work. This helps the CSS render properly, and will not work if these semi-colons are missing. The exception being if there is only one *declaration* in a given ruleset.

## The Box Model
![Shelves full of boxes](https://res.cloudinary.com/btvca/image/upload/v1603139665/archive-1850170_1280_vruohv.jpg)
When your browser interprets and renders a page with HTML and CSS, the elements it consists of are each given an amount of space on that page. That space is *always* a rectangular representation of the element, and consists of a few properties that make up the space it inhabits. This rectangular representation of elements in the DOM is known as the *box model*, and plays a key role in how elements are loaded and positioned on the page!

The *box model* for each element can be viewed directly in any browser through the inspector (remember the inspector?). Opening the inspector on any page and selecting a specific element will show you what additional CSS has been applied to it. The properties that are specific to the *box model* are even given their own diagram to help visualize further. Opening your inspector and viewing the CSS applied to a given element, you should be able to find a diagram that looks similar to this:

![box model](https://res.cloudinary.com/btvca/image/upload/v1603141005/box_model_lpdany.png)

That box at the bottom is a visual representation of the box model. In it, there are the following properties:

### border
The border is the perimeter of content. Borders can be given to elements and customized with width, color, and style. For example, the CSS for a `3px` `dotted` `black` border on the paragraphs in a document would look something like this:

```css
p{
    border-color: black;
    border-style: dotted;
    border-width: 3px;
}
```
and HTML like this,
```html
<p>Hey everybody check out my cool new paragraph</p>
```
would render like:

<p style={{  borderColor: 'black', borderStyle:'dotted', borderWidth:'3px'}}>Hey everybody check out my cool new paragraph</p>


### padding
Padding is the space immediately *surrounding* the content that an element consists of. Padding is often used to give text some distance from the edge of its container. The space is *internal*, and does its best to not disrupt the flow of the page. Simply put, padding is the space between the content and the border.

Adding padding to the previous example, like so:

```css
p{
    border-color: black;
    border-style: dotted;
    border-width: 3px;
    padding-top: 25px;
    padding-bottom:25px;
}
```
Will look like:
<p style={{  borderColor: 'black', borderStyle:'dotted', borderWidth:'3px',paddingTop:"25px", paddingBottom:"25px"}}>Hey everybody check out my cool new paragraph</p>

> Many CSS properties have a "shorthand" equivalent that will apply more than one properties and values at once. As a property, `padding` can be applied to all sides at once by giving it a single value, like `padding:5px;`. Conversely, you can give `padding` and other properties up to 4 values, where they apply to `top, right, bottom and left` respectively. To apply `padding` to the top and bottom only in this way, you can provide the CSS delcaration `padding: 5px 0px 5px 0px`

### margin
`margin` is the third aspect of the box model, and describes the space that is beyond the border of the element. Margins are used to provide an element with space between other other elements, rather than the border and its content like padding does.

`<p>` elements, by default, come styled with a margin. So, when we stack 2 on top of one another, like so:

```html
<p>Hey everybody check out my cool new paragraph</p>
<p>Hey everybody check out my cool new paragraph</p>
```
and with CSS like:

```css
p{
    border-color: black;
    border-style: dotted;
    border-width: 3px;
    padding-top: 25px;
    padding-bottom:25px;
}
```
We will get:
<p style={{  borderColor: 'black', borderStyle:'dotted', borderWidth:'3px',paddingTop:"25px", paddingBottom:"25px"}}>Hey everybody check out my cool new paragraph</p>
<p style={{  borderColor: 'black', borderStyle:'dotted', borderWidth:'3px',paddingTop:"25px", paddingBottom:"25px"}}>Hey everybody check out my cool new paragraph</p>

Note the space between the 2 `<p>` elements. If we change the CSS to manually *increase* the margin, we will see the difference in action.

With the HTML still being:

```html
<p>Hey everybody check out my cool new paragraph</p>
<p>Hey everybody check out my cool new paragraph</p>
```

And adding margin like so:
```css
p{
    border-color: black;
    border-style: dotted;
    border-width: 3px;
    padding-top: 25px;
    padding-bottom:25px;
    margin-top: 55px;
}
```

We get:

<p style={{  borderColor: 'black', borderStyle:'dotted', borderWidth:'3px',paddingTop:"25px", paddingBottom:"25px",marginTop:"55px"}}>Hey everybody check out my cool new paragraph</p>
<p style={{  borderColor: 'black', borderStyle:'dotted', borderWidth:'3px',paddingTop:"25px", paddingBottom:"25px", marginTop:"55px"}}>Hey everybody check out my cool new paragraph</p>

Note that these elements are now substantially further from one another. Inspecting these in your browser's inspector, and locating the box model again will show you the changes we have made in the padding, margin and border:

![changed box model](https://res.cloudinary.com/btvca/image/upload/v1603143645/altered_box_model_kklv0l.png)

## Final Musings
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

Thus concludes another lesson! We have yet to get into the fine details of CSS and what it is truly capable of, but this the first step on the path to style enlightenment. Review these points, and then continue to the exercises below.

- CSS is linked to an HTML document via a `<link>` tag in the document's *metadata*, or `<head>`.
- CSS is used to style and orient your page.
- CSS can be applied to multiple pages on the same site.
- CSS targets elements in your HTML by using *selectors*.
- CSS is *declared* in a `property:value` syntax.
- **Don't forget the semicolon at the end of a declaration**.
- The browser renders elements via the *box model*
and orients them based on:
    - `padding`
    - `border`
    - `margin`

Happy Coding :)

-Paul

# Exercises

These exercises will use the following properties, as well as ones covered in this lesson:

`background-color`: The color behind the *selected* element's content and padding (not the margin!)

`color`: the color of an element's content, most often text.

`box-shadow`: the shadow given to element. Accepts 4 values for `top`, `right`, `bottom` and `left`, as well as various other combinations that allow for shadowing and blurs, to name a few.

`border-radius`: defines the radius of the element's corners; rounds the edges to an element. Takes 1 to 4 values, for `top-left corner, top-right-corner, bottom-right corner, bottom-left corner`.

`font-size`: Changes the font size of the element(s)

`opacity`: Determines how transparent the element is. Scales from `0` (invisible) to `1` (full opacity), or a percentage from `0%` to `100%`

<!-- Copy and Paste Me -->
<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/adding-style-to-elements?path=style.css&previewSize=0&attributionHidden=true"
    title="adding-style-to-elements on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>


Alter the CSS in `style.css` to achieve the following:

- `<body>`
   -  `background-color` of `whitesmoke` (a recognized default color)
   - `width` of `600px`
   - a `margin-left` property of `50px`

- `<h1>` 
    - a `color` of `darkblue`
    - `opacity` of `80%` or `.8`
    - A `text-align` property set to `center`
- `<img>` 
    - `border-radius` of `5%`
    - `width` of `300px`
    - `box-shadow` set to `15px 15px`
- `<figcaption>`
    - a `padding` of `10px`
- `<li>`
    - `list-style-type` of `none`(to remove the dots)
    - `font-size` of `20px`
- `<blockquote>`
    - `color` of `blue`
    - `font-size` of `26px`
    - `opacity` of `60%`
    - `text-align` of `center` (just for fun) 
- `<h2>`
    - `color` of `green`
    - `opacity` of `80%`
- `<p>` 
    - `font-size` of `18px`
- `<footer>`
    - `margin-bottom` of `10px`
    - `color` of `grey`

This might seem like a lot, but get in the rhythm and you should see it all come together.

## Bonus:
What are some ways you could center *everything* on the page without content spanning the entire width of the window? 

<details>
<summary>Hint</summary>

Change the body's width and set its `margin-right` to `auto`
</details>

You should be aiming for something like this:

![completed page](https://res.cloudinary.com/btvca/image/upload/v1603147588/exercise_page_rtrsyb.png)