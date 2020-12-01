# HTML
![website code](https://res.cloudinary.com/btvca/image/upload/v1601320976/website-647013_1280_dymbwr.jpg)

## Introduction
HTML was created by Sir Tim Berners-Lee in the early 1990s. It was built atop ENQUIRE, a means to use and share documents with other researches at [CERN](https://en.wikipedia.org/wiki/CERN). It has since grown into **the** fundamental building block of all websites that, when coupled with JavaScript and CSS, provides users across the world with a colorful and unique web experience.

HTML, or **Hypertext Markup Language** is a relatively straightforward *markup language* (not a programming language!) that consists of structuring a text-based *document* with *elements* that give said *document* its implicit structure and meaning. That HTML document is then read by a web browser and serves as a crucial aspect of creating web pages. HTML fundamentally answers the questions:

**What are my headers? My paragraphs? My tables? My lists? What is important, and where does it belong in my document? What images and videos do I want, and where?**

> Note: The term *document* is used to explicitly discuss the HTML file itself, and only serves as one aspect of web page creation, crucial as it is. 

In other words, HTML is written in a *document* that, when read by the browser, ensures your page's content appears in a desired way. With it, you can answer those previous questions and more! Even when you click a link in the browser, you are utilizing HTML to navigate the web. 

### Example:

Let's say we're creating a home page, and right at the top of this home page, we want the name of our site to be displayed proudly for all to see. So, before anything else in our HTML file, we add the text:

```
This is my website
```
Only the end result is anything but breathtaking:

<iframe style={{width: "100%", height: "265px"}} scrolling="no" title="HTML intro ex." src="https://codepen.io/burlingtoncodeacademy/embed/rNebZPe?height=265&theme-id=dark&default-tab=html,result&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/burlingtoncodeacademy/pen/rNebZPe'>HTML intro ex.</a> by Burlington Code Academy
  (<a href='https://codepen.io/burlingtoncodeacademy'>@burlingtoncodeacademy</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

So, in order to give this title (or *header*) a little more punch, let's create an `h1` *element* that, thanks to the default styling that comes with HTML, will increase the font-size, make the text bold, and take up an entire line in the document. In the codepen above, change the HTML to the following:

```
<h1>This is my website</h1>
```
See the text get bigger? What you just did is HTML in a nutshell.

Note again that, on its own, HTML is rather bland; The "flashy" functionality and styling comes later through CSS and JavaScript *on top* of HTML. But, it's important nonetheless. 


## Terminology
Let's take our previous example, and break it down:

![element breakdown](https://res.cloudinary.com/btvca/image/upload/v1601389981/element_breakdown_nul3el.png)

### opening tag
Think of *tags* as the bookends to an element. They define the type of element, and are wrapped in opening and closing angle brackets. All elements begin with an opening tag.  

### closing tag
A closing tag serves as the ending point for an element, and is denoted by a forward slash before the tag name. They correspond with an opening tag of the same name. 

### content 
The content of the element. Depending on the opening and closing tags being used, the content will change accordingly. In this example, it is a large header (or `h1` element). 

### element
The element is everything shown. It consists of both the tags and the content. 

### nesting
Placing elements *inside* of other elements. This is done for a variety of reasons pertaining to both structure and style. Let's say you're being extra protective of your website, and you want your header to reflect that fact.

You can wrap some of your *content* from the `h1` *element* in an `<em></em>` tag (stands for **emphasis**), which will italicize the content within. 

<iframe style={{width: "100%", height: "265px"}} scrolling="no" title="HTML intro ex." src="https://codepen.io/burlingtoncodeacademy/embed/rNebZPe?height=265&theme-id=dark&default-tab=html,result&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/burlingtoncodeacademy/pen/rNebZPe'>HTML intro ex.</a> by Burlington Code Academy
  (<a href='https://codepen.io/burlingtoncodeacademy'>@burlingtoncodeacademy</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

Replace the HTML above with the following:

```
<h1>This is <em>my</em> website</h1>
```
You'll see "my", or the *content* of the `<em>` *element*, italicized on top of being a part of the `h1` element. 


### block-level elements
Block-level elements take up an entire row when created. They start on a new line, and fill the entire width of the page. Any content following it also starts on a new line. They are most often used to structure the page. Paragraphs, headings, footers, and lists are a few elements that fit in this category. 

### inline elements
Inline elements live within the block-level elements and give their content added meaning. They normally only surround part of a block-level element's *content*. In the prevoius example, the `h1` is the block-level element, and `em` is the inline element.

### attributes
Attributes can exist within an element's *opening tag* and provide additional information about the element. They will not be rendered as part of the element's content. Some elements expect particular *attributes* in order to work properly.

For example, an `<a>` tag, also called an *anchor* tag, is used to create clickable links that lead the user away from the current page or place **on** the page. It expects an `href` attribute that represents the path the link leads to. That attribute's value is wrapped in quotes, like so:

```
<a href="www.burlingtoncodeacademy.com">Click Here</a>
```
and will be rendered like so:

<a href="https://www.burlingtoncodeacademy.com">Click Here</a>

It will redirect your browser to `www.burlingtoncodeacademy.com` when clicked. `<a>` tags take a variety of other attributes as well. See a complete list [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a#Attributes). 


![document](https://res.cloudinary.com/btvca/image/upload/v1601403300/journal-2850091_1280_wbvbcn.jpg)

### The DOM
The DOM, or *Document Object Model*, is the interface that is created from the browser's rendering of the HTML document. When that document is processed, The DOM is created which restructures the content in such a way that it can be manipulated with a scripting language, like JavaScript. It is not crucial to understand this concept entirely, but it is important to differentiate; **Your document and The DOM are 2 different things**. More on this later!


## Examples
Now that we've touched on the bare essentials of HTML, let's highlight a few elements that we will be using in the coming lessons.

###  `h1`-`h6` 
These elements are used to denote section headings. `h1`, as seen, is the largest of the options. `h2`,`h3`, `h4`, `h5` and `h6` get incrementally smaller.  

They have no unique attributes.

### `ol` - ordered list
Represents a list of ordered items; nested `<li>` elements will render in a numbered order, by default.

```
<ol reversed="true">
    <li>item 1</li>
    <li>item 2</li>
    <li>item 3</li>
</ol>
```

will render like:

<ol reversed="true">
    <li>item 1</li>
    <li>item 2</li>
    <li>item 3</li>
</ol>

`<ol>` accepts unique attributes, like `reversed` and `start` that tell the list to behave in slightly different ways. In the above example, `reversed` is set to `true`, which causes the `<li>` elements to be numbered in reverse order. See a full list [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ol#Attributes).

### `div`
`<div>` elements are popular as the most "generic" container for flow content. It posesses no default effects on content or layout.

### `p` - paragraph 
The `<p>` element represents a paragraph. It is block-level, and has no unique attributes.

Eventually, your HTML will be quite complex; nested elements, sections, and attributes galore. For now, we'll focus on the basics. Complete the following exercises before continuing.

## Interactive Exercises

### 1.

The `<ul>` element represents an unordered list of items, that are by default a bulleted list. It expects *nested* `<li>` elements.

Create an unordered list with 3 items. Give those items the following content: 

- apple
- orange
- banana

<iframe style={{width: "100%", height:"154px"}} scrolling="no" title="BCA &lt;ul&gt; exercise" src="https://codepen.io/burlingtoncodeacademy/embed/poymNab?height=154&theme-id=dark&default-tab=result&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/burlingtoncodeacademy/pen/poymNab'>BCA &lt;ul&gt; exercise</a> by Burlington Code Academy
  (<a href='https://codepen.io/burlingtoncodeacademy'>@burlingtoncodeacademy</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

<details>
<summary>Solution</summary>

```
<ul>
    <li>apple</li>
    <li>orange</li>
    <li>banana</li>
</ul>
```
</details>


### 2. 
The `<strong>` element is an *inline* element that boldens its content. In the paragraph below, wrap all instances of dialogue (text with quotation marks) with `<strong>` tags. The end result should be as follows:

<p>Once upon a midnight dreary, while I pondered, weak and weary, Over many a quaint and curious volume of forgotten lore— While I nodded, nearly napping, suddenly there came a tapping, As of some one gently rapping, rapping at my chamber door. <strong>“’Tis some visitor,”</strong> I muttered, <strong>“tapping at my chamber door— Only this and nothing more.”</strong> </p>

<iframe style={{width: "100%", height: "265px"}} scrolling="no" title="&lt;strong&gt; tag" src="https://codepen.io/burlingtoncodeacademy/embed/YzqbNKM?height=265&theme-id=dark&default-tab=html,result&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/burlingtoncodeacademy/pen/YzqbNKM'>&lt;strong&gt; tag</a> by Burlington Code Academy
  (<a href='https://codepen.io/burlingtoncodeacademy'>@burlingtoncodeacademy</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

<details>
<summary>Solution</summary>

```
<p>Once upon a midnight dreary, while I pondered, weak and weary, Over many a quaint and curious volume of forgotten lore— While I nodded, nearly napping, suddenly there came a tapping, As of some one gently rapping, rapping at my chamber door. <strong>“’Tis some visitor,”</strong> I muttered, <strong>“tapping at my chamber door— Only this and nothing more.”</strong> </p>
```
</details>


### 3. 
Create an *ordered list* with the following three items, with the first and third being italicized:

1) *garnet*

2) amethyst

3) *emerald*

<iframe style={{width: "100%",  height:"154px"}} scrolling="no" title="BCA &lt;ul&gt; exercise" src="https://codepen.io/burlingtoncodeacademy/embed/poymNab?height=154&theme-id=dark&default-tab=result&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/burlingtoncodeacademy/pen/poymNab'>BCA &lt;ul&gt; exercise</a> by Burlington Code Academy
  (<a href='https://codepen.io/burlingtoncodeacademy'>@burlingtoncodeacademy</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

<details>
<summary>Solution</summary>

```
<ol>
    <li><em>garnet</em></li>
    <li>amethyst</li>
    <li><em>emerald</em></li>
</ol>
```
</details>
