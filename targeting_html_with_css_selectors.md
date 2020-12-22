# Targeting HTML with CSS Selectors

<a style={{color:"blue"}} href="https://forum.burlingtoncodeacademy.com/t/week-3-targeting-html-with-css-selectors/281">Discuss in Forum</a>

![dartboard with a dart in the bullseye](https://res.cloudinary.com/btvca/image/upload/v1603203296/target-1551492_1280_h9tvs5.jpg)
As we've seen, CSS targets specific HTML elements to apply rules to. Multiple *declarations* can be applied to any given rule, or *ruleset*. In doing so, we can add style and shape to elements on our pages, establishing general trends for how those elements will appear in the browser. 

As you may have noticed, the specificity of these rulesets is rather broad; elements are targeted regardless of their position in the document. All `<h1>` tags are blue, all `<img>` tags have a certain width, etc. There is no differentiating between different elements so long as they are composed of the same tags. So, you might be asking:

**Is there a way to target only specific elements?**

The answer, fortunately, is a resounding yes! There are many ways to *select* specific elements to apply your CSS to, and that is, as briefly mentioned in the previous lesson, *CSS Selectors*. So, without further ado, let's take a look at...

# CSS Selectors
### Type selector 
In our previous lesson, we wrote CSS that applies to all elements with a given name. When we provide the CSS and HTML:
```html
<h4>Tiny little header</h4>
<p>Here is my cool paragraph</p>
<div>some text inside a div</div>
<p>Here is another cool paragaph</p>
```

```css
p {
    color: red;
}
```
we get:

<h4>Tiny little header</h4>
<p style={{color:"red"}}>Here is my cool paragraph</p>
<div>some text inside a div</div>
<p style={{color:"red"}}>Here is another cool paragaph</p>

All paragraphs in the corresponding HTML will be colored `red`. This is known as a **type selector**. Type selectors are extremely broad and often used for *very* general styling that will be true across all instances.


### Universal selector (`*`)
The **universal selector** is used to select *all* elements in the HTML document, starting from the `<body>` down. This is *the broadest* selector, and should be used with care, as it affects everything on your page. It is denoted by an asterisks (`*`).

```css
* {
    color: red;
}
```
```html
<h4>Tiny little header</h4>
<p>Here is my cool paragraph</p>
<div>some text inside a div</div>
<p>Here is another cool paragaph</p>
```

Will turn everything on your page `red`! 

<h4 style={{color:"red"}}>Tiny little header</h4>
<p style={{color:"red"}}>Here is my cool paragraph</p>
<div style={{color:"red"}}>some text inside a div</div>
<p style={{color:"red"}}>Here is another cool paragaph</p>


### Class selector (`.`)
Here is where things start to get a little more specific. **Class selectors** will select *all* elements that have been given a particular `class` attribute. The value of the `class` attribute, called the `classname`, allows for many elements to receive the same styling, regardless of what that element's `<tag>` might be. Proper naming convention encourages a multiple word `classname` to be hyphenated. Classes are denoted by a period (`.`) followed by the class name.


```css
.my-class{
    color:red;
}
```
```html
<h4 class="my-class">Tiny little header</h4>
<p>Here is my cool paragraph</p>
<div>some text inside a div</div>
<p class="my-class">Here is another cool paragaph</p>
```
Result:
<h4 style={{color:"red"}}>Tiny little header</h4>
<p >Here is my cool paragraph</p>
<div> some text inside a div</div>
<p style={{color:"red"}}>Here is another cool paragaph</p>

You may also apply multiple classes to a single element, by separating the names in the HTML element with a space.


```css
.my-class{
    color:red;
}
.other-class{
    font-size:26px;
}
```
```html
<h4 class="my-class">Tiny little header</h4>
<p>Here is my cool paragraph</p>
<div>some text inside a div</div>
<p class="my-class other-class">Here is another cool paragaph</p>
```
Result:
<h4 style={{color:"red"}}>Tiny little header</h4>
<p >Here is my cool paragraph</p>
<div> some text inside a div</div>
<p style={{color:"red", fontSize:"26px"}}>Here is another cool paragraph</p>

> Note that classes are one of the most common ways to apply general attributes to multiple elements. Their ability to look past the element's name and apply only to what has been defined in the HTML is extremely helpful. Become very good friends with `class` selectors!


### ID selector (`#`)
Think back a few lessons to when we used an `id` to link to an element on our web page. Remember what it looked like? In case not, it was something like this:

```html
<div id="unique-element">I am a div with a unique id</div>
```
Then, later in our HTML we provided an anchor tag that links to that element like so:

```html
<a src="#unique-element">Link to the element</a>
```
Little did you know, that was only one aspect of the power of a *unique identifier*. 

In CSS, the ID selector (denoted by a `#`) targets a specific element on the page it is being applied to. The HTML is given a corresponding `id` attribute that the CSS uses to identify it. **There should only ever be one element per unique ID**. This allows for a *very*  specific selection context, where no matter how many elements are on a page, only the particular `id` is selected. The `id` and css selector must match exactly.

```css
#unique {
    color:red;
}
```
```html
<h4>Tiny little header</h4>
<p id="unique">Here is my cool paragraph</p>
<div>some text inside a div</div>
<p>Here is another cool paragaph</p>
```
Result:

<h4 >Tiny little header</h4>
<p style={{color:"red"}}>Here is my cool paragraph</p>
<div> some text inside a div</div>
<p>Here is another cool paragraph</p>

Despite there being two paragraph elements and thanks to the `id` selector in the css targeting the `id` with the value of `'unique'`, only that specific element has different styles applied to it.

### Attribute selector (`[]`)
Attribute selectors, as the name implies, selects all elements that have a given attribute. This selector has multiple aspects of *string-matching* syntax that allows you to be very explicit about what attributes and values you might be looking for. **Attribute selectors** allow your CSS to target HTML based on attribute name *or* `name` and `value`. These are denoted by square brackets.

For example, say we have a handful of anchor tags:

```html
<a href="#internal-link">link 1</a>
<a href="https://burlingtoncodeacademy.com">link 2</a>
<a href="http://example.com">link 3</a>
<a href="http://not-a-website.com">link 4</a>
<div href="#not-an-anchor-tag-">this is a div</div>
```

We can target these via their `href` attributes, but to do we must familiarize ourselves with some syntax. Below is some CSS showing how to do so. Attributes are included in square brackets immediately following they element (if an element is also included)

```css
[href]{
    /* matches all elements with an href attribute, including div */
}
a[href]{
    /* matches all anchor tags with an href attribute */
}
[href="#not-an-anchor-tag"]{
    /* matches the div with href that matches*/
}
a[href="#this-will-not-work"]{
    /* no match; it's looking for an anchor tag with that attribute */
}
[href^="#"]{
    /* matches all elements that have an href attribute whose value STARTS with a '#' */
}
div[href^="#"]{
    /* matches all divs with the attribute href whose value starts with a '#'  */
}
/* etc... */
```

For a full list, visit [MDN's list on attribute selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors#Syntax)

## Selector Specificity
![hierarchy ](https://res.cloudinary.com/btvca/image/upload/v1603217313/sitemap-2488235_1280_d58tte.png)

So, now that we've covered some of the typical selectors, let's address when and why you would use these. The answer involves *specificity*, or the process in which the browser chooses which of the CSS properties defined should be applied, and which should be overwritten. This addresses the inevitable question:

**What happens when 2 or more of the same property are applied to the same element through different rulesets?**

Let's start with an example:

```html
<h1>A title</h1>
<p>An introductory paragraph</p>
<p class="my-class">A well-formed paragraph</p>
<h2>A smaller title</h2>
<p class="my-class" id="second-paragraph">A different paragraph</p>
```

```css
p{
    color:red;
}
.my-class{
    color:blue;
}
#second-paragraph{
    color:orange;
}
```
But how's this gonna play out? All three of the *elements* targeted are paragraphs, but they're being targeted in multiple ways! What's worse, is the color property is changing every time as well! 

The result is as follows:

<h1>A title</h1>
<p style={{color:"red"}}>An introductory paragraph</p>
<p style={{color:"blue"}}>A well-formed paragraph</p>
<h2>A smaller title</h2>
<p style={{color:"orange"}}>A different paragraph</p>

This has to do with specificity.

>More specific selectors will take precedent and overwrite properties that have been previously defined by other selectors, or defautl HTML behavior.

In other words, **specificity** is deteremined by the "weight" that is given to a CSS declaration, which is dictated by the selector type. **If there are more than one declaration of the same level of specificity, the last declaration in the CSS will be applied.**

Let's run through the levels of specificity, in order from least specific to most specific.

1) Type selectors
    - `h1`, `p`, etc. 
    - basic element names
2) Tie between:
- Class selectors
    - `.myclass`, `.whatever`, etc.
- Attribute selectors
    - `[href="value"]`, `a[href^="#"]`, etc.
- Pseudo-classes
    - More later
3) ID selectors
    - `#id`, `#unique-id`, etc.

## Additional notes on specificity

- **The universal selector** (`*`) does not have an effect on specificity. It is applied as well as it can, and otherwise immediately overwritten by anything in the above list.
- **Inline styles** added to an element will *ALWAYS* take precedence over CSS styling. 
    - This can be accomplished directly in the HTML by adding a `style` attribute, like so:

```html
<p style="color: red">Some really informative text</p>
```
<p style={{color: "red"}}>Some really informative text</p>

Any styles that are valid in CSS are valid as inline HTML as well. Simply ensure you separate your declarations with a semicolon (`;`):

```hmtl
<p style="color: red; font-size:26px;font-style:italic;">Some really informative text</p>

```
<p style={{color: "red", fontSize:"26px", fontStyle:"italic"}}>Some really informative text</p>

# Final Musings
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

And there it is! CSS selectors in a nutshell! Next lesson, we will dig even deeper, discussing further applications and tools used to make your web pages beautiful and responsive. For now, reflect upon what we've learned, and then continue onto the exercises.

In CSS:

- **Type selectors** target all elements with a given tag name
    ```css
    p {
        color:red;
    }
    ```
- **The Universal selector** targets everything in the document, and ignores specificity, making it the most-easily overwritten.
    ```css
    * {
        font-size:26px;
    }
    ```
- **Class selectors** target all elements with a given `classname`
    ```css
    .cool-class{
        color: darkblue;
    }
    ```
- **ID selectors** target a single element based on the unique `id` given to it.
    ```css
    #unique-id{
        font-style: italic;
    }
    ```
- **Attribute selectors** target elements based on attributes and their values. This one has a *string-matching* component to it that makes it highly customizable.
- **Inline styling** overwrites any CSS on the properties that have already been declared, regardless of specificity.

- Specificity of CSS selectors goes as follows:
    - inline (highest)
    - `id`
    - classes, pseudo-classes (not covered) and attributes
    - `class`
    - type selector (lowest)


# Exercises
In the sandbox provided, apply the following CSS to the HTML document. The elements to be selected will be provided, followed by the rules to be applied to them:

<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/css-selectors-bca?path=index.html&previewSize=0&attributionHidden=true"
    title="css-selectors-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

- Universal selector
    - `margin` of `20px` on all sides
- `body` element, type selector
    - `background-color` of `whitesmoke`
-  `h1`
    - `margin-left` property of `40px`
    - `color` property of `firebrick`
- All `h3` elements
    - `font-size` set to `22px`
- `id` of `section-one`
    - `color` of `cornflowerblue`
- `id` of `section-two`
    - `color` of `goldenrod`
    - `font-weight` of `400`
- `id` of `section-three`
    -  `color` of `darkblue`
- `em` elements
    - `color` of `forestgreen`
- Both `p` elements with the classname `secondary-paragraph`,
    - `padding-bottom` of `30px` 
- Both anchor tags
    - `text-decoration` of `none`
- The anchor tag who's `href` attribute starts with `"mailto:"`
    - `background-color` of `yellow`

## Bonus
- Figure out how you might be able to change only *one* of the `em` elements `color` to `blue`. This is not something covered yet, but take a look. 
Hint: [CSS Combinators](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors#Combinators)

<details>
<summary>View the complete stylesheet (no bonus)</summary>

```css
/* universal selector */
*{
  margin:20px;
  padding:0px;
}
/* Type selectors */
body{
  background-color:whitesmoke;
}
h1{
  margin-left:40px;
  color: firebrick;
}
h3{
  font-size: 22px;
}
em{
  color: forestgreen;
}
/* ID selectors */
#section-one{
  color:cornflowerblue;
}
#section-two{
  color: goldenrod;
  font-weight:400;
}
#section-three{
  color: darkblue;
}
.secondary-paragraph{
  padding-bottom: 30px;
}
a{
  text-decoration:none;
}
/* attribute selector */
a[href^="mailto:"]{
background-color: yellow;
}
```
</details>