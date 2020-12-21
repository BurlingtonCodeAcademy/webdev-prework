# Navigating the browser

<a style={{color:"blue"}} href="https://forum.burlingtoncodeacademy.com/t/week-2-navigating-the-browser/277">Discuss in Forum</a>

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

 > Use relative links wherever possible. While absolute links will also work (for example, `/gallery.html` and `http://www.mywebsite.com/galler.html` both would hypothetically work), it is more efficient to use relative links. Plus, if your domain name ever changes, you won't have to worry about changing every `href`!


## Linking to an Element
A third way of providing an `href` attribute to your anchor tags is by directly linking to content on the current page. This will automatically jump the browser's view to 

Let's say that the `arist-bio.html` page is a smash hit. It's chock-full of delightful information on our talented artist. They've had a long and successful career that is so great, in fact, that they would like a secondary nav bar *only* on this particular page that allows the user to jump to different sections within it. 

This can be accomplished quite easily, with the use of internal links to particular *elements* on that page. These elements require an `id` attribute in order to be properly targeted.

`id` attributes are used for a number of reasons from referencing like this, styling with CSS, and selecting for JavaScript manipulation. **They should be unique to the page.**

Like any HTML attribute, you can add it within the opening tag like so:

```html
<div id="placeholder">jump to this spot on the page</div>
```
Now, were we to create another `<nav>` element or even just a few random links, we could direct those links to any element that has been given an `id`. Again, the `id` must be unique to properly target one and *only* one element.

You can link to an element by `id` like so:

```html
<a href="#placeholder">Jump to the div above!<a>
```
> Note that the `#` is an important character that must precede any `id` in an `href` attribute. The `#` often represents `id`, as you will see when we cover CSS. 

As an added behavior, you can jump directly to the top of any page by providing the `href="#top"` or `href=#` attributes.

See it in action:

This:
```html
<a href="#top">top</a>
```
Renders as this:

<a href="#top">top</a>


## Additional Features
So, `<a>` tags are capable of linking to other sites, other pages on the same site, and other sections on the same page. Anything else? Yes!

### Email addresses
Anchor tags can link to email addresses, prompting the user to send an email to the address provided. This is quite simple, and only requires the `mailto:` prefix in the `href` attribute. 

It looks like so:

```html
<a href="mailto:fakemail@notreal.com">Send me an email!</a>
```
<a href="mailto:fakemail@notreal.com">Send me an email!</a>

(This might surprise you, but that email doesn't actually exist)

### telephone numbers
You can also link to telephone numbers! This requires the `tel:+` prefix to the `href` attribute.

```html
<a href="tel:+1(555) 5555">555 5555</a>
```
 On mobile, this will auto-dial the number. Operating systems will vary, but there are programs that can call as well, like Skype or FaceTime. 

### Downloading files
You can also download files with the `href`, so long as you also include the `download` attribute. It specifies what will exactly be downloaded when a user clicks the link.

```html
<a href="/images/cutedog.jpg" download>Download</a>
```
If you give `download` a value, that will be the name of the file downloaded on the user's computer. Otherwise, it defaults to the current file name. The above will download a file called `cutedog.jpg`, wheras this:

```html
<a href="/images/cutedog.jpg" download="dog">Download</a>
```
will download a file called `dog.jpg`

# Final Musings
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

And that's about it as far as adding navigation to the browser! You can do a lot with a little anchor tag. Let's go over some of the concepts covered. Then, move on to the exercises.

Takeaways:

- anchor tags behave differently based on the `href` value provided.
    - absolute paths redirect to other sites
    - relative paths redirect to paths relative to the document's location
- you can link to elements that have an `id` within the current page by appending an `#` to the `id` name in a link's `href`.
- anchor tags can prompt user emails
- anchor tags can prompt telephone numbers
- anchor tags can prompt downloads


# Exercises

<!-- Copy and Paste Me -->
<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/navigating-the-browser-bca?path=about.html&previewSize=0&attributionHidden=true"
    title="navigating-the-browser-bca on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

*Remix* this project on Glitch, then complete the following: 

- In `index.html`,  create a `<nav>` element that contains links to the other provided `html` documents. 
    - Add this nav bar to all pages, to allow for easy navigation to and fro.

- In `about.html`, create a link at the top of the page that links to the element *on the same page* with the `id` of `jump-here`. 
    - Create a second directly under that element that brings you back to the top of the page.

- In `contact.html`, create 2 links.
    - One should prompt the user to call (555) 1234
    - The other should prompt the user to email `nomail@donotmail.yes`

### **Bonus**

- In `index.html`, add a link below the `<h3>` element that links to the element in `about.html` with the `id` of `jump-here` that you previously created.

