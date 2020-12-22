# Doing More With CSS Combinators

<a style={{color:"blue"}} href="https://forum.burlingtoncodeacademy.com/t/week-3-doing-more-with-combinators/282">Discuss in Forum</a>

![Multiple darts on a dartboard](https://res.cloudinary.com/btvca/image/upload/v1603287134/darts-102919_1280_nomyje.jpg)

When a developer is writing their CSS, selectors prove to be an indispensable part of the process. By adding classes, attributes, and IDs to your HTML, you can quickly apply styles and layouts to your pages. They provide the customizability needed to select exactly what you want to manipulate, as well as grant a hierarchy of application, so that certain rules and choices can be overwritten quickly and easily. 

But, as your site grows, you might find that you are repeating yourself. For every little change, you'll add a class or an ID to target it. Then, your IDs and class names will take on more and more convoluted names. Your stylesheet will grow at an alarming rate, and before you know it, it's a giant mess. And all because you *need* to target these specific elements directly, every time. Well, not anymore!

**CSS combinators** allow you to utilize the selectors we are familiar with, but in a way that also addresses their relationship to one another and the document as a whole. That way, a single element, with or without an `id` or `class` attribute, can serve as a reference point for the elements around it.

So, without any further ado, let's learn how we can say more, with less.

## Combinators
As we said, **combinators allow one to target elements by combining multiple selectors with special characters that define the relationship between them.** With these, you can find elements in unique situations, like for example, selecting `<p>` elements, but only those that are *inside* of `<section>` elements with a particular `classname`.

Let's look at this HTML:
```html
<section>
    <p>How can I select this paragraph in css?</p>
</section>
```
Using a combinator, we can select that `<p>` element like so:

```css
section p {
    /* your declarations here */
}
```
This is an example of the *descendent combinator*. 

### Descendant combinator: '` `'
The descendant combinator is denoted by a single space (` `) character. When placed between two elements, this selector will search all elements to the left of it (in this case `section`) and target **all instances of the element to the right of it, regardless of how nested that element might be**.  That means that the selector:

```css
section p {
    color: red;
}
```
Will work on both `<p>` elements:

```html
<section>
    <p>How can I select this paragraph with css?</p>
</section>
<section>
    <div>
        <p>How can I select this nested paragraph with css?</p>
    </div>
</section>
```
This will appear like so:

<section>
    <p style={{color:"red"}}>How can I select this paragraph with css?</p>
</section>
<section>
    <div>
        <p style={{color:"red"}}>How can I select this nested paragraph with css?</p>
    </div>
</section>

>Note that these work in conjunction with *all* other selectors. To increase specificity further, you can target all descendants of a given `class`, `id`, or `attribute` match! 

```html
<section class="new-class">
    <div>
        <p>How can I select this paragraph with css?</p>
    </div>
</section>
<section>
    <p>This will not be selected</p>
</section>
```
The first paragraph can be selected like so:

```css
.new-class p {
    color: red;
}
```
and will render like:

<section class="new-class">
    <div>
        <p style={{color:"red"}}>How can I select this paragraph with css?</p>
    </div>
</section>
<section>
    <p>This will not be selected</p>
</section>
<br/>
The *descendant combinator* pays no attention to how deeply nested specified target is. If it exists within the *parent* element, it will be targeted.

### Child combinator '`>`'
This is a more specific version of the *descendant combinator*. While it (descendant operator) will "dig" into any element provided to locate and target any *descendants*, **the child combinator will only look one level deep, subsequently ignoring any elements that are further down in the HTML hierarchy.** Let's look at our previous HTML:

```html
<section>
    <p>How can I select this paragraph with css?</p>
</section>
<section>
    <div>
        <p>How can I select this nested paragraph with css?</p>
    </div>
</section>
```
Using the *child combinator*, we can target the first paragraph encountered, like so:

```css
section > p {
    color:red;
}
```
This looks like so:
<section>
    <p style={{color:"red"}}>How can I select this paragraph with css?</p>
</section>
<section>
    <div>
        <p>How can I select this nested paragraph with css?</p>
    </div>
</section>

Note that this does not target the second `<p>` element, as the only *direct* child of the second `<section>` element is a nameless `div`. The first `<section>` element, however, is the *direct parent* to the `<p>` element. 

This can be helpful when you have numerous elements with the same name, all of which are likely to receive different levels of styling. By targeting direct children and limiting the scope of your selectors, you can ensure no elements that are nested deep in your HTML will be affected.

### Sibling combinator (`+`)
When you're not looking for nested elements, you can reach for a combinator that looks for elements immediately next to another. This is known as a *sibling element*. The following CSS selects *all* `<div>` elements that immediately follow `<p>` elements:

```css
p + div{
    color:red;
}
```
In the following HTML:
```html
<p>some text in a paragraph</p>
<div>some text in a div</div>
<p>some more text in a paragraph</p>
<div>some more text in a div</div>
```
This CSS:
```css
p + div{
    color:red;
}
```

Will render like so:

<p>some text in a paragraph</p>
<div style={{color:"red"}}>some text in a div</div>
<p>some more text in a paragraph</p>
<div style={{color:"red"}}>some more text in a div</div>

A good use case for this is to customize the text immediately following a header. This will add some consistency to the layout of your page without having to micromanage your CSS too much. If you simply state that all `<p>` elements immediately following an `<h2>` element will be `blue` and `italic`ized, you don't have to worry about further applying `class` attributes or anything! That would look like so:

```html
<h2>Header<h2>
<p>some text</p>
<h2>Header<h2>
<p>some text</p>
```
```css
h2 + p {
    color:blue;
    font-style:italic;
}
```
<h2>Header</h2>
<p style={{color:"blue", fontStyle:"italic"}}>some text</p>
<h2>Header</h2>
<p style={{color:"blue", fontStyle:"italic"}}>some text</p>

### General sibling combinator (`~`)
When you need a looser selector for applying styles to siblings of a particular element, you can do so with the *general sibling combinator*. **The general sibling combinator (`~`) selects all elements that come *anywhere* following a given element. For example, if we wanted to select *all* `<img>` elements that follow a `<h2>` element, we would write the following:

```css
h2 ~ img {
    /* your code here */
}
```
In the following HTML:
```html
<h2>Header</h2>
<div>some text</div>
<a href="#top">top of page</a>
<div>some more text</div>
<div>even more text</div>
```
This CSS:
```css
h2 ~ div {
    color: brown;
}
```
Will render like so:

<h2>Header</h2>
<div style={{color:"brown"}}>some text</div>
<a href="#top">top of page</a>
<div style={{color:"brown"}}>some more text</div>
<div style={{color:"brown"}}>even more text</div>

> Note that the elements you would like to select have to *follow* the initial element, and cannot appear before it in the document.

### Applications
Combinators can be used in conjunction with any of the previous selectors we have covered. While most of the examples provided deal with *type selectors*, the applications are much more than that. We may combine any number of selectors to make for a more specific experience.

Don't rely TOO heavily on any one selector, combinators included! They can get too specific for general use cases, making it difficult to reuse. Just like having none at all can cause your code to bloat, so can having too many!

Often, it is simpler to create your own class, but knowing how to manipulate the relationship between elements can prove essential in other cases. Keep it in your back pocket!

## Final Musings

![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

Combinators can be a useful tool in your tool belt for understanding the dynamics between elements in HTML. With them, you can quickly specify exactly what you would like to style without reaching immediately for an `id`. Let's review what we've learned so far, then complete the exercises below.

- Combinator selectors are used to target elements based on their relationship to other elements.
- *Descendent Combinators* will target *all* elements of a given type that are children of the provided parent element type.
- *Child Combinators* will target *direct* children of a given type that match the element type. More specific than descendent combinators.
- Adjacent sibling combinators will target elements *immediately* following another. 
- General sibling combinators will target all sibling elements following a given element.

## Exercises
<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/doing-more-with-combnators?path=index.html&previewSize=0&attributionHidden=true"
    title="doing-more-with-combnators on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

In `style.css`, write a series of rules that, using combinators:

- Turns the `color` of the `<li>` elements inside the `<ul>` element with the `class` of `inner-ul` to `firebrick`.
- Increases the `font-size` of all `<p>` elements that *immediately* follow an `<h2>` element to `24px`. Give them a `line-height` of `1.5` while you're at it.
- Gives all `<img>` elements that are *general siblings* to the `<div>` with an `id` of `id-one` a `border-radius` of 5%
- Italicizes *all* `<li>` elements within an `<ul>`, regardless of how nested they are. Use the `font-style` property with a value of `italic`
- sets the `opacity` of all images that are children of a `<div>` element to `.8`

<details>
<summary>Answer</summary>

```css
.inner-ul > li {
  color: firebrick;
}
h2 + p {
font-size: 18px;
line-height:1.5;
}
#id-one ~ img{
  border-radius:5%  
}
ul li {
  font-style: italic;
}
div img {
  opacity:.5;
}
```
</details>