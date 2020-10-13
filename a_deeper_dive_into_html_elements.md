# A Deep(er) Dive into HTML
![abstract pattern](https://res.cloudinary.com/btvca/image/upload/v1602180881/background-2462431_1280_ulp9k9.jpg)

## Review
So far, we've touched upon many prominent aspects of HTML. Before continuing, let's review.

HTML is a *markup language* that provides the basic skeleton, or "outline" to your site. It is used as a general guide for page flow and content that does not change. At the center of this markup is the HTML element:  

![element breakdown](https://res.cloudinary.com/btvca/image/upload/v1601389981/element_breakdown_nul3el.png)

Elements are the building blocks of all web pages. They can exist as stand-alone entities or contain other elements inside of them to further inform the structure of your page. This is called *nesting*, and looks like so:

```html
<div>
    <div>Nested element</div>
</div>
```

These elements may possess unique *attributes* or behaviors based on the tag used. For example, `<a>` (anchor) elements expect an `href` *attribute*, which when clicked, will navigate the user to a different site, page, or section of a page.  Attributes are added inside of the *opening tag* of an element, like so:

```html
<a href="https://www.burlingtoncodeacademy.com">
```

Elements are by default *block* or *inline* level, where the former takes up the entire width of a given area, and the latter does not. [More here](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements). 

HTML elements reside in your HTML document as either *metadata* or *content*. Metadata is contained in the `<head>` element, and contains information about how the page is displayed, what it's called, and what additional resources it requires (like stylesheets and scripts). 

That information is then read by your browser, top to bottom. Additional resources are added as they are encountered unless otherwise stated, through `<link>` and `<script>` tags in the `<head>` of your document. All of these resources are then compiled by the browser into a visual representation of those resources, known as the DOM. 

The DOM allows for direct and immediate changes to the page without altering the source material. You can manipulate the DOM through your browser's developer tools. Doing so allows you to immediately see any changes you might want to make to the page without causing lasting effects. It is a crucial tool when debugging and designing sites. Seeing how your page will appear and behave in the development process is a priceless feature that should be utilized to the fullest!

>Hopefully none of this information comes as a surprise. If it does, or you're left wanting more, I suggest re-reading the previous lessons!

With the fundamentals laid out, it's time to take a closer look at HTML elements and how or when to use them. 

## More on HTML
HTML is an ever-evolving markup language, with new versions being defined and maintained by major browser vendors like Google (chrome) and Mozilla (firefox) at the recommendation of [W3C](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium). The most recent version is HTML5, introduced in 2008, with notable updates as recent as 2017. It is ever-evolving, and aims to improve support and compatibility with the most recent multimedia and features. It strives for readability for both browsers and users alike. As you might expect, this evolution comes with new features and aspects that aim to accomplish the goals mentioned. 

Many of these changes involve using JavaScript for *DOM Manipulation*, thus changing your page dynamically based upon the code (scripts) provided. We will discuss this in detail in future content. For now, we'll stick with the aspects that pertain to the syntax and use cases of our HTML elements.

HTML5 introduces the concept of *semantic* elements, which as the name implies, are named to reflect typical use cases on a modern website. Many of these are simply meant to replace the generic block `<div>` and inline `<span>` elements. For example, the `<footer>` element has been registered as a valid block level element in order to make your page more readable. Let's take a look at these two examples:

```html
<div>
    <div>TITLE</div>
    <div>
        <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Repellat error quas, aliquid corporis sed totam
            voluptas ut iste non sint provident quo voluptates illum, maiores ex ad aut fugit in?</p>
    </div>
    <div>FOOTER</div>
</div>
```

```html
<main>
    <header>TITLE</header>
    <section>
        <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Repellat error quas, aliquid corporis sed totam
            voluptas ut iste non sint provident quo voluptates illum, maiores ex ad aut fugit in?</p>
    </section>
    <footer>FOOTER</footer>
</main>
```

Thanks to HTML5 including elements like `<header>`, `<footer>`, and `<main>`, the second example is more legible, and provides a level of innate structuring that the first does not. With backwards compatibility, these substitutes are not essential, although they strive to improve readability for both the browser and the user. 

Let's take a look at some of the *semantic elements* that you might use in your document.

## Semantic Elements 
Many semantic elements are used, as shown, to draw structural lines in your page. These are effectively the same as customizing the generic `<div>` elements to your liking, but there are a few instances in which these new elements serve their own default purposes. There are 4 that are most noteworthy: 

- `<section>`
- `<article>`
- `<nav>`
- `<aside>`

### `<section>`
The `<section>` element is one that meant to differentiate between sections of a document's content. These are typically used when a the content can be grouped around a theme or idea. Think of it these as the main differentiators within a page. If you are making a web page that discusses types of music, for example, each `<section>` would be its own genre. Again, these serve to differentiate different bits of the page, and have no real intrinsic styles that accompany it. 

Here's an example:

```html
<section>
<h2>Hip Hop</h2>
    <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Repellat error quas, aliquid corporis sed totam voluptas ut iste non sint provident qvoluptates illum, maiores ex ad aut fugin?</p>
</section>

<section>
<h2>Classical</h2>
    <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Repellat error quas, aliquid corporis sed totam voluptas ut iste non sint provident qvoluptates illum, maiores ex ad aut fugin?</p>
</section>
```

### `<article>`
`<article>` elements are more self-contained, and are used to outline an independent "unit" of HTML that can be referenced, isolated, and reused. Examples of `<article>` elements are forum posts, articles, blogs, and smaller, perhaps independent, items like widgets. These are typically higher level than `<section>` elements. 

```html
<article id="hip-hop-and-classical">
    <h1>Hip Hop Vs. Classical</h1>
    <section>
        <h2>Hip Hop</h2>
        <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Repellat error quas, aliquid corporis sed totam
            voluptas ut iste non sint provident qvoluptates illum, maiores ex ad aut fugin?</p>
    </section>

    <section>
        <h2>Classical</h2>
        <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Repellat error quas, aliquid corporis sed totam
            voluptas ut iste non sint provident qvoluptates illum, maiores ex ad aut fugin?</p>
    </section>
</article>

```
It is recommended to provide a heading (`h1-h6`) element within an `<article>` element to more accurately identify it.

### `<nav>`
The `<nav>` element allows you to set aside an element with navigation links to better navigate your page. These often manifest as your menus, table of contents, directories, and indexes. Shown below is a `<nav>` element that contains an unordered list of links that will bring a user to other pages on that site. 

```html
<nav>
    <ul>
        <li><a href="/">home</a></li>
        <li><a href="/about">about </a></li>
        <li><a href="/contact">contact </a></li>
    </ul>
</nav>
```

### `<aside>`
An `<aside>` element is used when content is peripherally relevant to the topic at hand, but doesn't deserve to be its own `<section>` or `<article>`. Pull quotes, comments, and content from other sources like social media are all fine examples of an `<aside>` element. 

```html
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. In illum cupiditate sed facere, numquam culpa, minus ratione voluptas expedita vero excepturi laborum? Similique, ex officiis alias asperiores dolor recusandae nulla?</p>

<aside>
    <q>Here's something worth mentioning, but not worth its own section! It's nested between 2 paragraph elements. The "q" tag is for quotes! -A famous person</q>   
</aside>

<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. In illum cupiditate sed facere, numquam culpa, minus ratione voluptas expedita vero excepturi laborum? Similique, ex officiis alias asperiores dolor recusandae nulla?</p>
```


## Final Musings
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

Note the semantic elements listed above do not innately style the content they are provided. Unlike `h1-h6` tags, for example, which increase font size and **bold** the text content, these structural elements (section, article, nav and aside) are meant more for helping bridge the gap between human and computer legibility. Properly incorporating them will make our pages more easily searchable, which will in turn increase its SEO (search engine optimization). That is, in itself, a huge topic so we won't cover it today. 

The important takeaway is that HTML is ever-evolving, as is the way that your browser interprets it. Understanding that evolution and trying to maintain current practices will increase your sites ability to remain competitive and dynamic in a rapidly evolving industry. 

Remember, be sensible, be descriptive. Ask yourself: **Can I use more descriptive elements than the common `<div>`? If so, consider using the more utility-driven aspects of HTML5!** 

And as always, 

Happy Coding :)

-Paul

## Exercises
Refactor the following HTML so that it takes full use of the 4 semantic elements covered in this lesson. Note `<header>` is also a semantic element! For a full list, visit [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Semantics#Semantic_elements)

Ask yourself:

- What would denote individual items? (`<article>` elements)
- What are my larger `<section>` elements?
- How would I add an `<aside>` if I felt so inclined?

These questions don't have concrete answers! What's important is understanding the general implications of these different elements and how they can be utilized to give your page some general structure.

