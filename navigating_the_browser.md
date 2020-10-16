# Navigating the browser
![smartphone with map navigation](https://res.cloudinary.com/btvca/image/upload/v1602867330/navigation-1048294_1280_qf2uow.jpg)

So far, we have covered some of the fundamental aspects of HTML and its behavior. Hopefully, you feel comfortable with the concepts of a markup language, what the general layout of an HTML document might look like, how it's loaded by the browser, and a couple of the newer features of it's most recent iteration (HTML5). So, now that we've made a single page, we're all set. Right? Wrong!

Say we have a website, and you're on their landing page. It's beautiful. The design is elegant, the narrative keeps you scrolling, and before you know it you're done with their sales pitch. You want to read another article, or check out their products, or contact information, or check out the author's bio, you name it. But something is very wrong. You look at the top of the page. At the bottom. The nav bar. Nothing! You have no way to get to these other pages! What once was a wonderful experience is now ruined by the lack of *internal* links that allow you to navigate the site. 

This is a ridiculous example, of course. It's rare (and ineffective) to come across a site that doesn't have *any* links at all. Perhaps individual articles, like the one you're reading now, might serve as small endpoints in a page acting as "dead-ends" of a sort. But even these pages, when well-designed might have a *next lesson* or a *read more* link to continue the flow of a web page. 

>In this lesson, we will be addressing these ideas, learning how to tie many pages together in a site by navigating through links. Other websites, other pages on the *same* site, and even other points on the current page are all possible with links. 


## Absolute Paths
In previous examples in this lesson, we have covered the HTML `<a>`(anchor) tag. We already know that it can receive an attribute `href` that determines that link's behavior. In previous examples, we have used this:

```html
<a href="https://www.burlingtoncodeacademy.com">Burlington Code Academy</a>
```
Which renders like so:

<a href="https://www.burlingtoncodeacademy.com">Burlington Code Academy</a>

And when clicked will redirect you to our program site.

What we haven't said yet is that this particular `href` is what is known as an *absolute* path. Effectively, *absolute* paths are ones that contain a protocol (HTTP or HTTPS) and include a domain name.

In this case, the domain name is `burlingtoncodeacademy` and, when coupled with a protocol, serves as a way of redirecting your browser "off-site", and onto an entirely new one. This says, "make an HTTP(S) request to this *other* site and if successful, move the browser there." 

Absolute paths in anchor tags are used for navigating away from your current site. Use this when you want to provide external links to additional resources and contents. These are extremely common and an excellent way to cite sources and redirect a user to different page.   

# Relative Paths
Now, let's assume that we're back on a site that *we* are creating. This is for our photographer friend who wants their home page to be a logo for their business, some customer testimonials, and a highlight reel of some of their strongest work. They would like a separate page for the following:

- Gallery
- Artist Bio
- Contact 

So, we get to designing their page. We add some `<h1>` tags here, some `<blockquote>`s there, and voila! We have our home page. Remembering HTML5 semantic elements, we decide to implement a `<nav>` element in order to house our links to other pages.

> Refresher: The `<nav>` element is used to outline a section on a page that is meant to house navigation links that lead to other sites and other areas within the same site. Examples include menus, tables, etc.

Let's make a nav bar that contains an *unordered list* of links to the various pages like so:

```html
<nav>
    <ul>
        <li><a>Home</a></li>
        <li><a>Gallery</a></li>
        <li><a>Contact</a></li>
        <li><a>Artist Bio</a></li>        
    </ul>
</nav>
```

> Remember that `<ul>` tags require `<li>` (list items) as children in order to properly format as a list. The `<a>` (anchor) tags are then effectively the content, or *inner HTML* of each of the list items.

You might notice that none of these anchor tags have an `href` attribute, so they will effectively render as links that don't "go" anywhere. Now, to enter the `href` attribute to give them their functionality. But what to put?

Each of these `<a>` tags are supposed to lead to another page within the same site, so we will provide them with *relative paths* to do so. 

**Relative paths** will point towards other files and folders based on the directory (or folder) that the link's document is derived from. In this case, let's say we have a number of *other* HTML files that represent the pages we're trying to link to. Let's call them:

- `index.html` (for home page)
- `gallery.html`
- `artist-bio.html`
- `contact.html`

And let's make sure they live in the same folder/directory/level as one another. 

> **Note**: `index.html` is the *HIGHLY PREFERRED* naming convention for home pages across the web. This is a relic from a previous era of web development, and will by default be the initial page served simply due to standardization. It is not 100% necessary, but in doing so, you can quickly assign the default home page of any site and avoid problems that may arise from skirting the norm.

We can provide these files directly to our `<nav>` bar by assigning them as the `href` attribute.

```html
<nav>
    <ul>
        <li><a href="/index.html">Home</a></li>
        <li><a href="/gallery.html">Gallery</a></li>
        <li><a href="/contact.html">Contact</a></li>
        <li><a href="/artist-bio.html">Artist Bio</a></li>        
    </ul>
</nav>
```

 Just like with absolute paths, the anchor tags expect an `href` attribute. The only difference is in the syntax that you as a developer provide it. Without the protocol and additional domain name, the `href` will default to the current repository of the site being displayed. 

 Assuming the other `.html` documents reside in the same folder as the home page, the browser will redirect to the corresponding page. 


## Linking to an Element
Now let's say that the `arist-bio.html` page is a smash hit. It's chalk full of delightful information on our talented artist. They've had a long and successful career. So great, in fact, that they would like a secondary nav bar *only* on this particular page that allows the user to jump to different sections within the same page. 

[top](#top)


- Intro
- absolute paths (www.about.com)
- relative paths (/about)
- internal paths (#about)
- wrapping elements
- other things anchor tags can do (telephone number)
- accessibility
- glitch exercises
    - Do one or two for each of these for each topic covered