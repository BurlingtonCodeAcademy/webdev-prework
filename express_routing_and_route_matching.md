# Express Routing and Route Matching
![adult hands holding map](https://res.cloudinary.com/btvca/image/upload/v1602797734/map-455769_1280_lxgqt1.jpg)
- Familiarity with Express expected

ExpressJS is one the most popular frameworks due in large part to the rising popularity of [Node.js](https://nodejs.org/en/docs/). JavaScript is a viable solution for both client and server-side programming now, and the role Express lays in that paradigm is not a small one. It's lightweight and approachable, with a foundation that can lead to customizable and powerful back ends. 

Part of that dynamic scalability comes from its ability to keep things modular and concise. When your client makes a request to the server, YOU decide what happens from there. What path is being reached? What parameters being sent? What method is being used? How will that information be handled? What do I want to send back? You know, server stuff.

In this lesson, we will:

- Set up a simple express server
- Demonstrate route matching principles
- Address parameters handling 

 The end result will be a server that we will run locally that, when various requests are made to it, will respond accordingly.

## Your Express Server

Let's start with a little bit of setup. In a file we will call `app.js` (typical naming convention), let's write the following code:

```js
// app.js
const express = require('express')
const app = express()

app.listen(3000, () => {
    console.log('listening on port 3000')
    })
```

This is under the assumption that we have initialized our repository and incorporated our node modules, with:

```
npm init -y
npm install express
```

Otherwise, express will not be brought in as a dependency. If you're unfamiliar with the [setup process](https://medium.com/beginners-guide-to-mobile-web-development/introduction-to-npm-and-basic-npm-commands-18aa16f69f6b), it is recommended that you do so before continuing. 

We can run this code from the command line with :

```
node app.js
```

Now, the code that we have will *run* a server locally on port `3000`, and can be requested to through our browser at `localhost:3000`. Visiting that URL will not really DO anything, of course. We haven't set up any routes! So, let's do that.

In the code we currently have, we can add a route that, when visited in the browser, will return certain information. Let's make it say `Hello World!` because that's what all developers do for starters!

```js
const express = require('express')
const app = express()

//added route
app.get('/hello', (req,res)=>{
    res.send("Hello World!")
})

app.listen(3000, () => {
    console.log('listening on port 3000')
    })
```

The `'/hello'` that is the first argument in the `app.get()` method is the *route* intended for the following callback to be called when it has been reached with a GET request. That callback takes 2 arguments, one representing the `request` received, and the other is a `response` object that contains a number of methods and properties to use as you see fit. In this case, this:

```js
app.get('/hello', (req,res)=>{
    res.send("Hello World!")
})
```
is saying, "When a GET request is made to the given path (denoted by the `'/hello'`,) `send` back a string `"Hello World!"`. The browser then happily displays the information that has been *served* by our server application.  

Most applications are a *little* more complex than this example. What happens when you have multiple pages, or login forms, or you need to write to a database? What if someone makes a POST request instead of a `GET` request? 

By it's very nature, Express will exercise what is called *route matching* that, when a request is made to your express app, determines what route will be triggered. 

## Route Matching
![map with a toy car on it](https://res.cloudinary.com/btvca/image/upload/v1602805106/holidays-1283014_1280_kceh3w.jpg)

Routing refers to the logic that dictates how an application will respond to a particular request. It is denoted by a URI (or path) and a particular method, like GET or POST. 

As we've seen before, the general layout for this in Express is:

```
app.METHOD(PATH, HANDLER)
```
- `app` is a working iteration (or instance) of express
- `METHOD` denotes GET, POST, etc. but in lower-case
- `PATH` is a path relative to where the server is.
- `HANDLER` is the callback function, like the one that sent `"Hello World!"` in our example above.

**The handler that is called is dependent on the *path* and the *method***

So, when defining your routes, there are some rules to keep in mind. There are a number of characters: `?, +, *, ()` that mimic the regular expression definitions they originate from.

The following are a number of examples based on the different rule sets:

### Paths based on strings

```js
/// GET request to home or "root" 
app.get('/', function (req, res) {
  res.send('this is the home path')
})

//GET request to a hypothetical contact page
app.get("/contact", (req,res)=>{
    res.send('this is the contact path')
})
```
These are the simplest to understand. Following our example `app.js` above that is hosting on port `3000`, we could visit these at `localhost:3000` and `localhost:3000/contact` respectively.

### Paths based on string *patterns*
This is what we were alluding to before with the mimicking of regular expressions. Certain characters behave as a "regular expression-lite", so to speak. These characters allow for multiple `requests` to all hit the same `path` endpoint. 

For example:

The `+` sign will allow the character preceding it to be repeated any number of times and still match the route.

```js
app.get('/woohoo!+', (req,res)=>{
    res.send("you are very excited")
})
```

Any request to `/woohoo!`, `/woohoo!!`, `/woohoo!!!`, etc. will be matched 

The `?` character will match the path whether or not the character preceding it is present.

```js
app.get('/ye?ah', function (req, res) {
  res.send('Yes!')
})
```
Requests to `/yeah` and `/yah` will both be matched, and located (in our example) at `localhost:3000/yeah`
and `localhost:3000/yah` respectively.

### Paths based on regular expressions

These are a bit more in depth, as regular expression can get quite complicated. For now, understand that regular expressions (or `regex`) is a system for complex pattern-matching in strings. They are bookended by two `/` characters

```js
app.get(/a/, function (req, res) {
  res.send('/a/')
})
```
This will match *any* path that contains the character `'a'`. Any and all. There are other unique characters that allow for more customization, but they are well beyond the scope of this lesson! 

### Paths with expected parameters built in

By preceding any URL segment with a `:` (colon), you effectively omit that segment from the typical flow of things. Instead of directly affecting the path matching rules we've discussed so far, the value following that `:` will serve as a *key* in the     `req.params` object that is natively available to Express. The value that belongs with that key will be the actual value you pass in at the time of the request.

For example:

```js
app.get('/about/:name', (req,res)=>{
    res.send(req.params)
})
```

The above example will match *any* path that starts with `'/about'`, but whatever comes next will be stored in the `req.params` object for use in your handler function.

For example, a request to `localhost:3000/about/jane` will hit this route, with `req.params` being the object `{name:jane}`. 

*The parameter's name serves as the key who's value will be assigned at time of the request and stored in `req.params`.


### Route handlers
![mountain paths](https://res.cloudinary.com/btvca/image/upload/v1602805420/mountains-1245937_1280_ub25eh.jpg)

Handlers can be assigned additional callback functions that behave similar to middleware. If you're familiar with middleware, good! If not, no worries. They are essentially bits of code that are executed server-side, but before your explicit handler is called. 

Effectively, additional custom-handlers can behave *like* middleware. There's just a small difference, and that comes in Express' `next()` function. 

When a handler is triggered, it has access to the `request` and `response` objects (abbreviated in our examples as `req` and `res`) as arguments. It also has a not-so-secret *third* argument called `next` that allows for mutltiple handler functions to be called simultaneously! This allows you to customize your routes to a higher degree.


This route, when matched, will check the `title` parameter of the path provided against the value `"1984"`. If it is the same, `next()` is called which then runs the subsequent handler, which sends the string `"A book by George Orwell"`.

> Note that `req`, `res`, and `next` are *always* available to your hander function, and IN that order. 

```js
app.get('/books/:title', (req, res, next)=>{
    if (req.params.title === "1984"){
        next()
    } else{
        res.send("not 1984")
    }
}, (req, res)=>{
    res.send("A book by George Orwell")
})
```

### Making it modular with `express.Router`

After a while, your web app might have a lot of routes. Those routes might be really complex, and take up a ton of room in our `app.js` file. So, in order to keep things organized, it might be good practice modularize your code a bit. 

We can do this with the `express.Router()`, which effectively allows us to break our application into compartments. Think of it as a "mini-app" with each instance providing its own middleware and routing.

This is the best when you only want explicit "mini-apps" exposed to certain middleware. The following example creates a `router` as a `module` that is then imported into our main `app.js`.

Let's call this second file `books.js`

```js
// books.js
const express= require('express')
const router = express.Router()

/*
middleware or extra behavior you only want on the following routes could go here
*/

// relative home route
router.get('/', function (req, res) {
  res.send('This is the mini-home page for books')
})
// relative about route
router.get('/about', function (req, res) {
  res.send('Here is the mini-about page for books')
})

module.exports = router
```

```js
//app.js
const express = require('express')
const app = express()
const  books = require('./books.js')

app.use('/books', books)


app.listen(3000, () => {
    console.log('listening on port 3000')
    })
```

Now, our main `app.js` is nice and clean! All of the additional behavior and middleware will not be accessed by any other `app.js` routes that you might incorporate.

The two routes defined in `books.js` will be available at `localhost:3000/books` and `localhost:3000/books/about`, respectively.


## Final Musings

![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

That's about it for routes and route matching! Here are some final takeaways to help solidify the concepts covered.

- Routes are highly customizable
- They are set up in Express with the `app.METHOD(PATH, HANDLER)` format
- The handler has access to the `request`, `response` and `next` arguments by default.
- basic strings, string patterns, and regex are all valid forms of pattern matching in Express.
- `next()` allows you to have more than one handler on a route so long as it's called.
- you can make instances of `express.Router()` to make your routing architecture cleaner and more modular.

Hope this helps!

Happy Coding :)

-Paul