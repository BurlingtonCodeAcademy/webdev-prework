# Embedding Media in HTML

<a style={{color:"blue"}} href="https://forum.burlingtoncodeacademy.com/t/week-2-embedding-media-in-html/278">Discuss in Forum</a>

![computer with media player](https://res.cloudinary.com/btvca/image/upload/v1602947056/youtube-1684601_1280_lw3t9v.png)

Save for the occasional `<img>` tag in the examples provided so far, we haven't really covered much in HTML other than plain text. After all, most elements in HTML are simply different ways of structuring and providing additional context to the text content on a page. Nav bars, headers, paragraphs, and all of the majority of other elements in HTML accomplish nothing more than providing a bit of structure and implicit value to the text within its tags.

But, let's face it. The websites would be pretty boring if we only used text. Youtube and Facebook wouldn't exist, that's for sure. So, let's take a big side step and enter the exciting world of multimedia and embedding. 

In this lesson, we will cover key concepts relating to multimedia and the different ways that images, video, audio, and even entire *pages* can be placed into your existing site! 

Let's start with something we've already seen: images!

## Images in HTML
Embedding images into web pages was incorporated fairly early on in the growth of HTML. Thankfully. 

### `src` attribute
As we've seen, you can place an image into a web page with the `<img>` element. It is, by nature, self-closing, and needs a `src` attribute in order to properly function. `src` is the path to the image in question, whether or not it's a relative or absolute path (remember our previous lesson on navigating the browser?).

Let's take a basic example:

Let's say you have your home page `index.html`, and on the same level of that file, you have an `images` folder. Inside that `images` folder, you have an `image` called `mycutepuppy.jpg`. In order to link your `<img>` properly, you would provide a *relative path* in your `index.html`. It would look something like this.

In `index.html`:

```html
<img src="images/mycutepuppy.jpg">
```
> **Best practice alert!** For SEO purposes, Google recommends 2 things. First, your file should have a descriptive name. No files named `img1234.jpg`. Second, it is recommended to house all images/media in a nested subdirectory. Also, keep your paths relative whenever possible.

### `alt` attribute
The `alt` attribute is used for what is referred to as *alternative text*. This is a text-representation of an image that will display when the provided image doesn't for whatever reason. Maybe it's a slow connection, or a dead link. Either way, the text should be a strong description of the file. This has many benefits.

For starters, it helps with the practice of *computer accessibility*, which is the field that strives for ease-of-use for all people regardless of disability type or severity. For example, if the user is visually impaired and using a screen reader, the text will be read aloud as opposed to displaying the image. 

Other uses include the obvious, which is serving as a placeholder so the user isn't left entirely confused when an image link is broken. Sometimes users will turn off images as a means to reduce bandwidth. The image type could simply not even be supported in the first place!

Your `alt` attribute should contain information relevant to the user, namely what the use case is for that particular image. If the image contains valuable information that would leave a user confused without it, like an infographic, you should provide the additional information in the alt text. Don't worry if it's a bit long. The description is important. 

```html
<img src="images/mycutepuppy.jpg" alt="a golden retriever puppy with a green chew toy">
```

![three empty picture frames hanging in a gallery](https://res.cloudinary.com/btvca/image/upload/v1602954772/picture-frame-763299_1280_ig9pqq.png)

### Height and Width
The `height` and `width` attributes are exactly what you think, but with a twist. When used as an attribute, it is encouraged to define the height and width of the image the same as the image itself. This will allow the page to load with the proper space being set aside for the image, even before it fully loads, thus allowing your page to load quicker and smoother. Otherwise, elements will jump around on the page during the loading process. Awkward and unpleasant.

For example, if you have an image that is 600px x 400px, define your image's height and width like so:

```html
<img src="images/mycutepuppy.jpg" alt="a golden retriever puppy with a green chew toy" height="400px" width="600px">
```

###  `title` attribute
This one is straight forward. The `title` attribute will display when you hover over an image with the mouse, although it is not recommended for use, simply because of accessibility. It's recommended to instead provide additional information in your article itself. Or, use our *next* attribute.

### `<figure>` and `<figcaption>` 
There exists 2 more semantic elements (remember those?) that help even more with accessibility (and SEO!), and they are `<figure>` and `<figcaption>`. Say, for example, you have an entire gallery of images and each of those images come with their own caption. In order to keep things grouped properly, you can (and should) utilize the `<figure>` element. Inside of each `<figure>` element a `<figcaption>` element can serve as an accompanying text element that, by structure and element type alone, provide a more cohesive experience for both the visually impaired and all users.

Take this example:

```html
<div>
    <img src="images/mycutepuppy.jpg" alt="a golden retriever puppy with a green chew toy" height="400px" width="600px">
    <p>This is my puppy. They are very cute!</p>
</div>
```
There is no intrinsic problem with HTML like so, but with accessibility and proper formatting, the same can be achieved with more function success like so:

```html
<figure>
    <img src="images/mycutepuppy.jpg" alt="a golden retriever puppy with a green chew toy" height="400px" width="600px">
    <figcaption>This is my puppy. They are very cute!</figcaption>
</figure>
```
The key difference here is in intention. Both will have very similar results to a typical user, but those who might benefit from ease-of-use will thank you for taking the time to consolidate things into a more accessible format.

`<figure>` and `<figcaption>` don't have to be used for images alone, but rather can be utilized for any number of things. As long as it wraps what [MDN](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML) defines as:

"An independent unit of content that:
- Expresses your meaning in a compact, easy-to-grasp way.
- Could go in several places in the page's linear flow.
- Provides essential information supporting the main text.

A figure could be several images, a code snippet, audio, video, equations, a table, or something else."

### Images as backgrounds
Welcome to your first sojourn into CSS! As mentioned before, CSS (cascading stylesheets) is one of the three main aspects of front-end web development, along with HTML and JavaScript. It is used to add color, shape, and well, style to your page! This topic will be covered in much more detail next chapter, but for while discussing embedding media, it is fitting to address a common property in CSS: `background-image`.

`background-image` is one of a series of properties that allow HTML elements to have what is equivalent to a `src` attribute with an image filling its space, although it has the added benefit of position the image *within* that element. The important thing to understand is that these types of images should be used to spice up your pages from a design perspective, not to replace `<img>` tags altogether. Use them as accents, decor, ornamentation,  y'know, that sort of thing. These images can't accept any `alt` text, and the `height` and `width` properties don't behave in the same way that they do in an `<img>` tag either. 

If you recall from our **How a Webpage Is Loaded In The Browser** lesson, stylesheets are loaded in the `<head>` of our HTML document.

If we have some HTML that looks like this:

```html
<div>Here is a div that is filled with text. The div will only ever be as big as this text, so the background will only be as large as the div as well!</div>
```

 The CSS syntax would look something like this:

```css
/* The url can be relative or absolute */
div{
    background-image: url("images/mycutepuppy.jpg")
}
```
Again, we will discuss CSS a great deal more in the future. For now, understand that it is another way of incorporating images into your site, but should be used only for visuals that are purely decorative. No alternative text or captions needed. Your screen reader friends will thank you :)

## Other embeddable media
Images are far and away the most common type of embeddable media on the web, but there are other ones as well; what about audio and video? We won't delve as deeply into them at this time, but let's familiarize ourselves with them anyways. 

### `<video>`
`video` is a feature new to HTML5 that allows for the embedding of video formats directly into JavaScript. It is *highly* customizable and comes with a large number of features, but we'll cover a basic example just so you know what you're looking at in the future.

`<video>`, like `<img>`, requires a `src` attribute to work. 

```html
`<video src="media/lanternsatnight.mp4" controls></video>
```
Will render like so:

<video src="https://res.cloudinary.com/btvca/video/upload/v1602956241/motionplaces0045-c007-q001-Oct2018_iia3d3.mp4" controls style={{width:"50%"}}/>

The `controls` attribute allows the user to start and stop the player, as well as interact with the time-slider.

Providing an opening and closing tag with a text element inside will serve a similar purpose to `alt` text, which will default to the provided content if the video does not load for whatever reason:

```html
`<video src="media/lanternsatnight.mp4" controls>
    <p>Oops! Something as gone wrong :/</p>
</video>
```

### `<audio>`
`<audio>` elements are much like `<img>` and `video` elements. They require a `src` attribute, and a `controls` attribute (like video) in order to actively play/pause the audio in question.

A simple example might look like this:

```html
<audio src="media/mycoolsong.mp3" controls></audio>
```
> Much of the added functionality for `audio` and `video` comes with JavaScript, and is far outside the scope of this lesson.

## `<iframe>`
`<iframe>` elements, short for **HTML Inline Frame Elements**, are used to embed other HTML pages directly into your current page. You will frequently encounter `iframes` on other sites where their service is allowed on your page, like Youtube videos and maps. 

Should you want to embed a full website as "window" in your current page that exists outside of these provided contexts, you will need to write it yourself, like so:

```html
<iframe src="https://burlingtoncodeacademy.com/" height="300" width="400"></iframe>
```
That will render as this:

<iframe src="https://burlingtoncodeacademy.com/" style={{height:"300px", width:"400px"}}></iframe>

In terms of *accessibility*, the only attribute that someone using assisting technology can use is `title`:

```html
<iframe src="https://burlingtoncodeacademy.com/" height="300" width="400" title="the burlington code academy home page"></iframe>
```

# Final Musings
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

And thus concludes an overview of embeddable media in HTML! The most time and effort has gone into manipulating images, as it is what you will most frequently encounter. Again, the remaining media has been introduced so you have a better grasp of the sorts of content available moving forward. 

Here are some takeaways from todays lesson:

- Modern HTML allows users to include images, video, audio and other content through the practice of *embedding*.
- *embedding*, while relatively straightforward, needs to be handled properly in order to maintain accessibility to all users.
- Things like `alt` text, semantic elements like `<figure>` and `<figcaption>`, and `title` are much needed attributes when promoting accessibility.
- Most, if not all of the elements (`<img>)`, `<video>`, `<audio>`) need a `src` attribute in order to properly function.
- `src` attributes can be absolute or relative, but should be relative.

# Exercises
Complete the exercises in the Glitch window below:
<!-- Copy and Paste Me -->
<div class="glitch-embed-wrap" style={{height: "420px", width: "100%"}}>
  <iframe
    src="https://glitch.com/embed/#!/embed/embedding-media-in-html?path=index.html&previewSize=0&attributionHidden=true"
    title="embedding-media-in-html on Glitch"
    allow="geolocation; microphone; camera; midi; vr; encrypted-media"
    style={{height: "100%", width: "100%", border: "0"}}>
  </iframe>
</div>

- Given the following URL: 

https://cdn.glitch.com/04744dc4-4d0f-47fb-b367-416d4d6baf7c%2Fdogs-2936442_640.png?v=1602961209287

Create an `image` element that:

- uses the above url as a source
- has alternative text *accurately* describing what the picture entails.
- has a width of 640px and a height of 453px
- has an appropriate title

> Note: this is for learning purposes, and goes against best practices. Remember it's always better to have your URLs to be relative as opposed to absolute!

### Refactor
Now, refactor your HTML so that:

- it incorporates a `<figure>` semantic element
- contains an accurate caption within that element. Make sure the caption is accurate, and serves the proper purpose.

### Bonus
Create a generic `<div>` element that is 640px wide by 360px tall and, in the accompanying CSS, give that `<div>` a decorative background image with the following URL:

https://cdn.glitch.com/04744dc4-4d0f-47fb-b367-416d4d6baf7c%2Ftriangles-1430105_640.png?v=1602961944130

### Bonus bonus bonus
Give that `<div>` with the background a unique `id` and target that in your CSS. 