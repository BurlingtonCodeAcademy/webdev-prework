# Inspecting a Web Page In the Browser
    Host a page: Inspect page, dissect and analyze. 
    Dissecting a layout: More conceptual differentiation
    Have them change content in the browser: edit the DOM

![browser](https://res.cloudinary.com/btvca/image/upload/v1602079780/gui-2311259_1280_f4l8ua.png)

Designing webs pages can be a long and complex process. Not all browsers support every modern feature you might want to incorporate in your page, and even if they do, those same browsers might interpret the information differently. So, as a developer in the design phase, it is in your best interest to capitalize on the features your browser DOES provide, like the console you've been using to run your basic JavaScript functions. That very same browser comes with a suite of tools known as *developer tools*, which house a variety of functionality. 

These tools can inspect the loaded HTML, CSS, and JavaScript, as well as information pertaining to them (load time, contents, requests for assets like images, etc.) In this lesson, we will be covering some of the fundamental features of these developers tools, namely the parts that allow us as developers to see how our page is behaving, and what implications we can glean from said behavior.

For the following examples, we will be using the following URL:

https://inspect-this-page-bca.glitch.me/

You should see something like this:

![web page](https://res.cloudinary.com/btvca/image/upload/v1602172631/inspect0_tmgp5z.png)

From here, you can access the inspector tools in the same way you access the console, in one of three ways:

* **Shortcuts:** <kbd>Ctrl + Shift + I</kdb>
    - macOS: <kbd>⌘ + ⌥ + I</kbd>
    - IE & Edge: <kbd>F12</kbd>

* **Menu bar**
    - **Firefox**: Web Developer > Tools > Web Developer > Toggle Tools
    - **Chrome**: More tools > Developer tools
    - **Safari**: Develop > Show Web Inspector
    - **Opera**: Develloper > Developer tools

- **Dropdown menu**: 
    - Right click on a webpage and select *Inspect Element*, or *Inspect*. 

![Image of dropdown](https://res.cloudinary.com/btvca/image/upload/v1602172628/inspect1_wha75v.png)


Once open, you can navigate to the *inspector* section by selecting *Elements* or *Inspector*, depending on your browser. 

![image of inspector window](https://res.cloudinary.com/btvca/image/upload/v1602172629/inspect2_fyqcog.png)

By default, the page usually opens to the *inspector* which is what we'll be discussing now. Once your inspector is open on [this page](https://inspect-this-page-bca.glitch.me/
), we can start disecting particular aspects of the page, like how the HTML appears at runtime, and what styling has been applied to it. It is also a great spot to mess around with the HTML and CSS (styling) in realtime without directly affecting the source material. 

## DOM inspection
You may notice the section of the inspector that looks strinkingly similar to HTML. This is *not* the source HTML document, although it does look nearly identical. It is instead the browser's intrepretation of that document. The browser, as software, takes the HTML and additional resources it has loaded and uses it to create an image on the page for the user to view. That image is then represented in this HTML-ish inspector as the DOM, or *document object model*. 

Because the browser has its own version of what the web page should look and act like, it is entirely manipulatable. For starters, let's hover over the `<h1>` tag, which should highlight that same element in the browser's window.

![highlighted h1](https://res.cloudinary.com/btvca/image/upload/v1602172629/inspect3_yuciae.png)

Now, right click (or <kbd>Ctrl + Click</kbd>) that element and select *edit as HTML*. This will expose that element as raw HTML so that you can make changes to it. Make changes to it so that the *content* now reads: "My First DOM Manipulation", like so:

```html
<h1>My First DOM Manipulation</h1>
```
Selecting elsewhere on the page will cause your changes to take effect! You should see the text of your `<h1>` tag change. 

![Changed h1 element](https://res.cloudinary.com/btvca/image/upload/v1602172628/inspect4_cdvyix.png)

This practice, whether accomplished through JavaScript or directly in the inspector, is known as *DOM manipulation*. It doesn't make changes to the original source document, but rather the browser's current impression of what has happened to the page. If you refresh your page, or leave and visit it again, you will see the changes do not persist, but rather the page is returned to its original state.   

>Note that the `►` arrow next to certain elements in the DOM will "open" that particular element, revealing all *nested* elements. These can then be "opened", and so on and so forth. 

## CSS inspection
We have yet to cover CSS in-depth, but it has been mentioned a couple of times so far. CSS, in a nutshell, is a *stylesheet* language that works in conjunction with HTML. When linked (remember `<link>` tags?) to a document, it applies a set of rules to the elements of that HTML that the browser then follows to the best of its ability, ultimately resulting in a page that is no longer devoid of shape and color. 

Let's introduce some of the key aspects to CSS, by way of the browser's inspector.  This allows us to see how particular elements are styled once the page has been completely rendered, and what changes to those elements will look like, all in real time! 

![styles](https://res.cloudinary.com/btvca/image/upload/v1602172631/inspect5_hscys5.png)

Next to the DOM in the inspector, you will see a *styles* section. The contents of this section will change depending on the element you have selected. Just like with the HTML, you can also alter the styles *on* those elements. 

Let's select the same `<h1>` element we manipulated before, except this time, let's select `element.style { }`, or `element { }`  under the *styles* section. You should be able to directly manipulate the style applied to that particular element.

Let's apply the property `font-size` to the `h1` element selected, and give it the value of `3em`. Apply it as follows:

```css
font-size:3em;
```
 You should see the header get bigger, like so:

![image of larger header](https://res.cloudinary.com/btvca/image/upload/v1602172631/inspect6_hzhf0b.png)

> CSS takes a series of rules in the form of `property:value`, where `property` is a specific aspect of styling and `value` is a valid figure based on the `property` stated, terminated by a semicolon. For example, `color:24;` will not be valid because the `color` property expects, well, a color. `color:green;`, however, is perfectly valid.

>`em` is a relative unit of length based on the element being styled. `1em` means "keep the size of this element as is", where `3em` says "make the `font-size` of this element `3x` greater".

Inspecting CSS in the browser can be handy for a number of reasons! 

#### Most-to-least-specific
Sometimes style choices will directly conflict with each other. To help remedy this, the inspector lists the styles applied to an element from most-to-least specific. Changing a style aboe one you'd like to override will show you what that looks like in the browser.

#### Checkboxes
Checkboxes next to particular CSS properties will let you toggle what certain elements look like with and without particular styles.

### Applying various CSS in the inspector
With your inspector open, apply the following CSS to the DOM:

1) Locate the `<body>` element (the highest-level element in the HTML) and use the checkboxes to toggle the color (hex code #555) on and off. Note the color defaults to solid `black`. Change the value to `chartreuse`, realize how ugly it is, and change it back.

2) Change the `margin-bottom` of the `<div>` with an `id` of `banner` to a value of `50px`. `px` stands for *pixels* and is a fixed unit of measurement. This `<div>` is at the top of the document. 

3) Give the `<div>` with an `id` of `content` a `font-size` of `1.5em`. Note that this stretches the image out immensely, as it is contained with the `<div>`, along with the text. As part of the same restyling, find the `<img>` with the `class` of `half-block-image` and give it a `height` of `200px;`.

4) Change the `h2` with the `id` of `section-two` to read "Look At My Cool Magnifying Glasses!" 

5) Refresh your page, and remember that all changes made were temporary and done through the browser. The source code, both styling and content, remain unaffected.

## Final Musings

![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

- The inspector is a powerful tool for seeing how a page is rendered in the browser. 
- The tools provided are browser-specific, but there are many commonalities between them.
- Inspectors are great for analyzing a page and visualizing changes you may want to add.
- The changes made in the inspector affect the DOM, not the source material

#### Attributions
[Mozilla Contributors](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_are_browser_developer_tools)