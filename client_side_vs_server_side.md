# Client-side vs. Server-side
![row of servers behind glass](https://res.cloudinary.com/btvca/image/upload/v1602853360/server-2160321_1280_notsf5.jpg)

As you make your way towards becoming a seasoned web developer you will familiarize yourself with general trends and relationships common to all devs. The widest-arching differentiation one can make when designing websites is the difference between *client-side* and *server-side*. It's a fundamental idea that, while simple once you understand it, can be a bit of a head-scratcher until then. So, let's get into it.

## General Differences

Client-side and server-side programming are significantly different in terms of code functionality and application. 

For starters, their roles and responsibilities, while complimentary, are altogether different. **Client-side** deals with direct and immediate user interaction, like the things one would *see* and *manipulate* on a given web page. Client-side programming more often coincides with design, user experience (UX), and general site behavior. This is what many apsiring web developers first deal in, with HTML, CSS, and JavaScript. **Server-side**, on the other hand, deals mostly in delivering the content that will be displayed on the browser in response to requests. Server-side deals with things "off-site," or out of the immediate view of the browser and web page. It retrieves and sends data back to the client. 

Another difference is that the two (often) use different programming languages. JavaScript is the language of choice **Client-side** code across the world, and also happens to be the exception to that rule, as `Node.js` allows for JavaScript to be used on both sides. Other languages that are frequently used in server-side programming are PHP, Python, Ruby, and C#, to name a few.

The third *primary* difference between client-side and server-side is the environment in which they run. **Client-side** code, as you may have gathered at this point, is the code that runs in the browser to create your page. It has limited access to the operating system in which it is running, so your browser cannot directly affect too much other than itself. There are a few exceptions, like uploading files, but those are edge cases. **Server-side** code, then, is run directly on a computer and not through a browser. This grants your server access to elements that might not otherwise be directly available to the browser. Thus, the server *serves* the resources that the browser will then render, style, and make functional. 

## Their relationship
While distinct from one another, client and server are co-dependent. The browser (client) is the user's entry point to a site, and acts as the interface. The information rendered *from* that site, however, has to first be retrieved and delivered by a server! So, while the client might be where the information is generally rendered and made viewable by our delicate human eyes, it has to be retrieved first.

The browser, when attempting to visit a site, makes a `request` to a desired URL. A server then takes that `request` and searches for the proper end `route`. If one has been found, that `route` dictates what information will be sent back to the client from the server. That information is the HTML, CSS, JavaScript, images, and any other resources that the browser will then load and render. Voila! A website. 

This is an incredibly simplified version of the process, of course, but it emphasizes the importance of the client-server relationship. HTTP requests are another lesson altogether, and will be covered later.

## A note on frameworks
Both client-side and server-side (and particularly full stack) developers will normally write their code with the help of libraries and frameworks. These **web frameworks** are peer-developed functions, rules, objects, etc. that help a developer to quickly design and solve common issues that developers might encounter. They make the development process generally simpler and smoother, regardless of where they are used.

Just like client and server are different, so too are the frameworks developers will reach for regarding the aspects in question. **Client-side** frameworks deal with structure and visualization of a page, stylizing contents and better modularizing aspects of your site. **Server-side** frameworks, then deal with common issues encountered on the server-side, like session support, ways to authenticate users, ways to access databases, and more. These are arguably more important in the grand scheme, as there is a lot of functionality to implement from scratch. It's much easier to style a website from scratch than it is to build a server in particular languages.

Here are some popular frameworks for both, so you might better understand the general differences between the two.

### Client-side Frameworks
Here is a list of popular client-side frameworks as of 2020:

- [React](https://reactjs.org/)
- [Angular](https://angular.io/)
- [Vue](https://vuejs.org/)
- [Svelte](https://svelte.dev/)
- [Ember](https://emberjs.com/)

### Server-side Frameworks
Here is a list of popular server-side frameworks as of 2020:

- [Express](http://expressjs.com/) (JavaScript)
- [Laravel](https://www.laravel.com) (PHP)
- [Django](https://www.djangoproject.com/) (Python)
- [Ruby on Rails](https://rubyonrails.org/) (Ruby)
- [Spring Boot](https://spring.io/projects/spring-boot) (Java)

## Final Musings

![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

Hopefully this has been a generally informative lesson that serves (pun) you well. With any luck, the line between client and server has been drawn a little more clearly. Here are some final takeaways:

- Server and Client have different responsibilities
    - Client-side deals with code that runs in the browser and user interaction (styling and behavior)
    - Server-side deals with the delivery of content and data, and is dependent on the `request` made by the browser.
- Server-side code can be written in many different languages, other than JavaScript.
- Client-side code is predominately written in JavaScript.
- Client and server-side code runs in different environments.
    - Client-side code runs in the browser.
    - Server-side code runs on the operating system.
- Both use frameworks, but for different purposes.

Happy Coding :)

-Paul