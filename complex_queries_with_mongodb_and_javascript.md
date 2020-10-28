# Complex Queries with Mongo DB and JavaScript
![databases](https://res.cloudinary.com/btvca/image/upload/v1603721527/database-1954920_1280_tia31g.jpg)

When dealing with databases, there are many ways to store and retrieve data. Oftentimes you will need to query a database in such a way that the information is returned in regards to best practices and the context of your request. This brings numerous topics to mind, like sharding, indexing, what hardware/platform you will be incorporating, and security concerns.

This lesson, however, will discuss general best practices, as well as a moderately deep dive into query syntax. It will answer questions like **How do I customize my queries?** and **How do I filter my results?**.

## Overview
When you are looking for the documents in your database collection, you can filter the results by using a specific query syntax. In the case of doing so in a JavaScript environment, you can do so with the `find()` or `findOne()` methods. Then, you can also take additional steps to manipulate your results, like sorting them,skipping certain results, limiting the number of returned results, or specifying which fields to explicitly return altogether. 

For the following examples, we are under the assumption that a local connection has been established, and all queries are performed on the `collection` object defined below:
```js
const {MongoClient} = require("mongodb")
const uri = "mongodb://localhost:27017"
const client = new MongoClient(uri)

async function run() {
  try {
    await client.connect();
    const database = client.db("example_db")
    const collection = database.collection("example_collection")

    // your code here




  } finally {
    await client.close()
  }
}

run().catch(console.dir)
```

## `find()`
The `find()` method (or `findOne()`, the equivalent that only returns a single document) gets called on a particular database collection. In the context of your code, that collection is represented as a `Collection` object. That method takes a *query object* that represents the specifications you would like your query to match.


The broadest example possible is to query a collection for all of its contents, by passing in an empty object as your query.

> Many actions in MongoDB return what is known as a **cursor**, which is then used to manage the final results of your query.  A `cursor` can be iterated over with methods like `forEach()` or `toArray()` to display the intended results. Due to the `async` nature of querying databases, be sure to include the `await` keyword!

```js
let query = {};
let cursor= collection.find(query);
await cursor.forEach(doc=>{
  console.log(doc)
})
```
This example will result in all documents in a collection being returned. 

It is here, in what we have defined as the `query` variable, that we can customize our query to return a cursor that has more specific results. 

## `find()` queries
The query document, when properly defined, allows you to search a collection and return only matching items, thus making your searches more specific. These documents, in many ways, mirror the documents within the collection itself, with some major differences.

Alongside the ability to match *literal* values (like a specific name or type, for example), there are a number of *query operators* that allow for more complex queries (like finding quantities under 10, or names that start with a particular letter). Let's break these down into the 5 main types:

- literal value
- comparison operators
- logical operators
- element operators
- evaluation operators 

### literal value
Literal values are the most straightforward query possible. With it, the scope of your query is 1 to 1; you give your search a `field` and `value` and the returned cursor only contains the results that exactly match the given criteria.

Let's say our `collection` represents a large dataset representing thousands of movies. The typical format for a document would be like so:

```js
{"_id":1, "title": "Citizen Kane", "director": "Orson Welles", "year": 1941}
```
Knowing the fields in any given document means that we can query the collection for all movies that match said field and given value. To see all movies that were made in a particular year, you would call the `find()` method on the collection and pass the query document as an argument, like so:

```js
const query = {"year": 1941}
const cursor = collection.find(query)
await cursor.forEach(doc => {
  console.log(doc)
  })
```

The result will be *all movies that were made in 1941. Again, a key practice is to ensure you are using `await` and iterating over the returned cursor.

### Comparison Operators
Operators are available for use when making queries to a MongoDB collection. With them, you can customize your queries further than literal values. The *Comparison operator* allows you to query your collection based on *comparing* values within the residing documents. This means you can find values that are *greater than* or *less than* the provided values. The syntax is a little different than you might be used to, as all operators are preceded by a `'$'` sign, and exist as *nested* objects within the query document itself.

The example below shows a query for all movies that were made *after* 1941.

```js
const query = { "year": {$gt: 1941} }
const cursor = collection.find(query)
await cursor.forEach(doc => {
  console.log(doc)
  })
```

Note the `query`:

```js
// $gt stands for "greater than"
{ "year": {$gt: 1941} }
```

When using a comparison operator, the `value` you pass to the `field` in your query document is in its own set of curly braces (`{}`) that allow the operator to be interpreted as a value itself. When trying to implement operators, think of this:

```js
// value that matches anything greater than 1941
{$gt: 1941} 
```

as this:

```js
year > 1941
```

For a full list of operators, visit the [mongodb documentation on comparison operators](https://docs.mongodb.com/manual/reference/operator/query-comparison/)

### Logical Operators
Logical operators let you, well, apply logic to what are known as *field-level operators*, like the comparison operators we just covered. You can use these operators to customize your queries using *logic* to broaden (or further limit) the results.

This query, for example, finds *all movies* that **were not** made in 1941. Weird search, but sure:

```js
const query = { "year": { $not { { $eq: 1941}}}}
```

This one can be a bit confusing, so let's break it down a bit more. Our *query document* is the entire object, where the `year` field is the only `field` under scrutiny. Like with comparison operators, the `value` is a *nested object* that is evaluated:

```js
// true if not equal to 1941
{ $not { { $eq: 1941}}}
```

Going one level deeper, we are applying the *logical operator* `$not` to another *nested* object, which has its own value that needs to be evaluated.

```js
 { { $eq: 1941}}}
```

Putting it all together, we get something that, in JavaScript, would effectively be:

```js
if (!== 1941)
```

For a full list visit the [mongodb documentation on logical operators](https://docs.mongodb.com/manual/reference/operator/query-logical/).

### Element Operators
Element operators are a little more abstract, in that they permit queries dependent upon the type of a field, or simply whether or not the field exists.  You can think of these as a *status* detector of sorts.  For example, what if you want to find movies that have more than one director? As it stands, we have only seen the `director` field have a single string `value`. But, we know that if there is more than one director, we could allow for an `array` to hold multiple `string` values. 

The following queries our movie collection and returns all documents that have a `director` field with the type of `array`:

```js
// $type checks the type of the containing field
const query = { "director": {$type: "array"}}
const cursor = collection.find(query)
await cursor.forEach(doc => {
  console.log(doc)
  })
```

There are only two element operators: `$exists` and `$type`. The former checks that the containing field simply exists, whereas the latter does as shown above (determines the type of the containing field.)

For a full list visit the [mongodb documentation on element operators](https://docs.mongodb.com/manual/reference/operator/query-element/).

### Evaluation Operators
Evaluation operators run the value from the provided `field` through additional logic, like regex, text searches, and arithmetic. These are powerful tools and allow for many higher-level, custom filters to your results.

With these, you can compare the `value` of 2 different fields, enforce a schema (rules determining the format and required fields of a given document), or even match documents against provided JavaScript expressions. 

In the example below, we are querying for movies that were made at the start of a new decade, by determining that the year is divisible by `10`. 

```js
// $mod stands for modulo and takes 2 numbers in the order of (divisor, remainder)
const query = {"year" : { $mod: 10, 0}}
const cursor = collection.find(query)
await cursor.forEach(doc=>{
  console.log(doc)
})
```

For a full list visit the [mongodb documentation on evaluation operators](https://docs.mongodb.com/manual/reference/operator/query-evaluation/).


## `options`
In any `find()` query on a collection, you may pass multiple parameters to it through an `options` argument. That argument represents an object that contains additional information for customizing your query. That `options` object expects specific a specific `field` or fields in order to apply to the `find()` query. They include `sort` and `skip`, 

### `sort()`
`sort()` allows you to return your queries in a different order than they might otherwise appear. Using sort, you can return documents based on the values of *one or more* fields. The `sort()` method can be strung off of your original `find()` method, and serve to further customize the returned cursor.

To sort your documents by ascending order, `1` is the value passed to a required field. `-1` does the same, but in descending order.

The following example demonstrates sorting *all* movies in reverse-chronological order:

```js
const query = {};
const sorter = {"year": -1}
const cursor = collection.find(query).sort(sorter);
await cursor.forEach(doc=>{
  console.log(doc)
})
```
It can also be provides as `options` in the `find()` method:

```js
const query = {};
const options = {
  sort: {"year": -1}
  }
const cursor = collection.find(query, options)
await cursor.forEach(doc=>{
  console.log(doc)
})
```


Passing more than 1 `field:value` set to the `sort()` method will prioritize the first, but in the case of a tie, will set a secondary `field` to refer to, should the first be identical. 

The following will still sort by year (from most recent,) but will, in the event of a tie, sort by the director's name:

```js
const query = {};
const sorter = {"year": -1, "director": 1}
const cursor = collection.find(query).sort(sorter);
await cursor.forEach(doc=>{
  console.log(doc)
})
```

[MongoDB documentation](https://docs.mongodb.com/drivers/node/fundamentals/crud/read-operations/sort)

### `skip()`
You may also use `skip()` to omit some documents, from a specific query. This one is relatively straightforward, and when coupled with `sort()`, can be quite powerful. `skip()`, like `sort()` can exist as a standalone method that is strung off of your `find()` method, or can be added to the `options` object for further customization. The only difference is syntax. 

This example sorts all movies from 1941 by director, and omits the first 3.

```js
const query = {"year": 1941};

const options = {
  sort: {"director": 1},
  skip: 3
}
const cursor = collection.find(query,options)await cursor.forEach(doc=>{
  console.log(doc)
})
```

Or by stringing methods:

```js
const query = {"year": 1941}
const cursor = collection.find(query).sort({"director":1}).skip(3)
```
[MongoDB documentation](https://docs.mongodb.com/drivers/node/fundamentals/crud/read-operations/skip)


### `limit()`
You can use `limit()` to put a maximum on the number of documents you can return. This is extremely helpful when dealing with massive datasets that otherwise might take quite a while to return. `limit()` expects a positive integer that represents the maximum number of documents that can be returned for the query.

In the example below, we are querying for (at most) 10 of the most recently-made movies.


```js
const query = {};

const options = {
  sort: {"year": -1},
  limit: 10
}
const cursor = collection.find(query,options)await cursor.forEach(doc=>{
  console.log(doc)
})
```

[MongoDB documentation](https://docs.mongodb.com/drivers/node/fundamentals/crud/read-operations/limit)

## `project()`
When you finally have your query customized to your liking, you may not want to return all of the information each document has to offer. Suppose there is a ton of irrelevant information in our movie requests, and we only want to know the `year` and the `title` of a given film.  

`project()` allows you to utilize a *projection*, which is an outline of sorts that filters the document itself and returns specific aspects of a document.  Let's look at our initial example:

```js
{"_id":1, "title": "Citizen Kane", "director": "Orson Welles", "year": 1941}
```

We don't want the `director`, or the `_id` that comes unique to each document, so we create a projection to further hone our query.

`project()` allows you to *explicitly* or *implicitly* limit unnecessary data. These two approaches are mutually exclusive, so you must pick which to utilize.

**Explicitly** projecting will include all fields that are given a value of `1`.

**Implicitly** projecting will exclude all fields that are given a value of `0`.

> The exception to this rule is the `_id` field, that is by its nature included in every query. If you do not wish for the `_id` to be present, it must be deliberately stated. 

This means that, in order to return *only* the `year` and `title`, we will need to use the `.project()` method:


```js
const query = {};

const options = {
  sort: {"year": -1},
  limit: 10
}

const projection= {"_id": 0, "title":1, "year":1}

const cursor = collection.find(query,options).project(projection)
  
await cursor.forEach(doc=>{
  console.log(doc)
})
```

This will return:

```js
{"title": "Citizen Kane", "year": 1941}
```

## Final Musings
![Musings Sunset](https://res.cloudinary.com/btvca/image/upload/c_scale,w_1080/v1599682636/sunset-1211475_1280_xtjrjn.png)

This is only scratching the surface of what complex queries in MongoDB are truly capable of, but covering some of the most frequent use cases is a good place to start.  Here are some takeaways to reflect upon:

- The `find()` method is called on a collection in a database.
- The `find()` method returns a cursor object that can be iterated over to see the results.
- `find()` expects a query document as its first argument.
- query documents are highly customizable thanks to various operators
- `find()` can take a second argument that represents various options, like `sort()` and `limit()`
  - These may also be chained as additional methods.
- `find()` works in conjunction with `project()` to trim the documents that are returned on the cursor.

Hope this helps! There is plenty of additional resources to follow on the [MongoDB website](https://docs.mongodb.com/drivers/node/). Be sure to visit it in the context of Node.JS, as these are all examples of a JavaScript environment.

Happy Coding :)

-Paul