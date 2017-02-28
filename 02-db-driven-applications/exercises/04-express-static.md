# Express Static

An Express server can be broken down into three basic parts: *the router*, *routes*, and *middleware*. 

### Routing
The core of any web server is robust request routing. If you think about the server-client request life cycle, it essentially boils down to: the client requests a resource, the server tries to locate the resource and if it's found, respond in a way that the client is expecting. Without a structured way to handle any route requests, your web server will do very little.

Creating a route looks generally like this: `app.get('/songs/:id', function(res, res, next){...});`. 
A route can be thought of as a two-part phrase: an HTTP verb and a path. 

The HTTP verb, or method, is most often one of these four: GET, POST, PUT, and DELETE. 
* A GET request is used to fetch data from a web server. It is the most common type of request.
* A POST request is used to send data to a web server. 
* DELETE and PUT requests round out a CRUD application. DELETE is used to delete information from a web server and PUT is generally used to update existing data on a server.
* PATCH can also be helpful when augmenting an existing chunk of data or updating only one property.

The most important difference in HTTP verbs is how data is passed around. 
* In a GET request, data is passed either in the URI (route parameters) or as query-string parameters (like `?name="fred"`). 
* For POST methods, there is a payload or body attached to them. This allows POST requests to send much more information in the request compared to GET requests. 
* The DELETE method generally lacks a body, similar to GET requests.
* PUT methods have a payload, just like POST.

The second half of an HTTP request is the uniform resource identifier, or URI. Every request a web browser makes is to some URI; www.google.com, for example, is a URI that goes directly to the Google home page resources. As mentioned above, URIs can send parameter data to the web server a couple of ways: query-string parameters and route parameters. For example, an Express path with route parameters could look like this:  
`/districts/:regionName/volunteers/:volunteerId` (This should look familiar from Angular routing. Remember using $routeParams?)

( BTW, URL = "Uniform Resource Locator" and URI = "Uniform Resource Identifier". Locators are also identifiers, so every URL is also a URI, but there are URIs which are not URLs. Clear as mud. Moving on. )

When we create routes in an Express app, we want to be able to match up an incoming request URI with a route definition in order to load the correct template (when building an application server), or return the correct data to the user (if we're building an API). Regardless, it's all about sendin back the proper response to the request 

For example, say we had an Express server running a pet adoption site and our browser made a request using the path `/dogs/breeds/beagle/05?spayed=true`. Browsers default to sending GET requests, so the browser would make a GET with that path.  

In our Express routes we have a definition that would look like `GET /:petType/breeds/:breedName/:petId`. 
This route would match our request that we sent from the browser. When the request comes into the Express router, the route parameters `:petType` and `:petId` will be parsed from the incoming URI and made available via `req.params.petType` and `req.params.petId`. Because we included a query string (`?spayed=true`), the updated path parameter would become `/teams/:teamName/employees/:employeeId?`. The query-string part of the URI is not used in routing decisions, but the `spayed` parameter would be available as a property on `req.query`. So, in our example, checking for `req.query.spayed` in our callback function would give us `true`.

### Middleware
When a request comes into the server, it travels through a pipeline. At each stage of the pipeline, a _middleware_ function can modify the stream, pass it on to the next function, or not pass it on. Middleware is any JavaScript function that has the signature `function (req, res, next)` and runs between the client request and the server answer. Because a middleware function receives the **request** and **response** objects as arguments, as well as the next middleware function in the stack, it can do the following:

+ Make changes to the request and the response objects (like adding addional properties or formatting data)
+ End the request-response cycle (by sending a response back to the client or just calling 'res.end()')
+ Call the next middleware in the stack ( with `next()`)

A single Express route can have as many middleware functions associated with it as needed. Think of middleware as the workers on an assembly line, adding and changing things, dare we say _transforming_ your data before sending it on to the next middleware function or finally back to the client. A middleware function could be used to 
--set a cookie or header
--check a user log in status
--compress JavaScript
--thousands of other purposes

If the current middleware function does not end the request-response cycle, it must call `next()` to pass control to the next middleware function. Otherwise, the request will be left hanging (Yeah, you'll make that mistake a few times. Trust us). This is useful for middleware functions that have asynchronous activity. Just call `next()` when the code is complete to alert Express that this particular middleware function is done. (If the middleware is responsible for sending a response instead of passing the baton to another middleware, there’s no need to call next) A request is considered complete when a middleware function sends a response to the client. A middleware function that completes a request is sometimes referred to as a handler.  

After that long data dump, let's start small, shall we?  

Express can be easily used to serve up static files in a directory.  

_from http://expressjs.com/en/starter/static-files.html_
```js
const express = require('express')
const app = express()

app.use(express.static('public'))

app.listen(3000)
```

The code above will start a server that will serve up any file in a folder called public. _Magic!_

i.e.

`/public/index.html will be served as http://localhost:3000/index.html`
`/public/images/logo.jpg will be served as http://localhost:3000/images/logo.jpg`

Pretty simple, and seemingly devoid of most of the stuff we talked about earlier. But do pay attention to `app.use()`. That's our key to using middleware functions in our app. `use()` tells Express to load whatever middleware you pass to it. In this example, it loads a built-in middleware function called `static` that configures the server to look into the folder passed into it ( 'public' ) first when looking for files to serve up.  

Now look at this slightly more complicated version  

```js
const express = require('express')
const app = express()

app.use(express.static('public'))

app.get('/', (req, res) => {
    res.send('Hello World')
})

app.listen(3000)
```

In the example above, if a request comes in to the root `/` route, express will
first look in the public folder for `public/index.html`. If it finds a file at
that path, it will send the file to the browser and end the stream. If it
doesn't find a file at that path, the request gets sent down the pipeline to the
`app.get('/', ...)` route handler. The handler will execute its callback because
the request url matches '/'. The callback ends the pipeline after sending the
text "Hello World" to the browser by calling `res.send()`.

vs.

```js
const express = require('express')
const app = express()

app.get('/', (req, res) => {
    res.send('Hello World')
})

app.use(express.static('public'))

app.listen(3000)
```

In the example above, if a request comes in to the root `/` route, the
`app.get('/', ...)` route handler will receive it first. The handler will
execute its callback because the request url matches "/". The callback ends the
pipeline and will never look in the public folder for an `index.html` file. If a
request comes in to the `/test` route, the `app.get('/', ...)` route handler
will receive the request, but pass it down the pipeline because it doesn't match
the route. Next the `app.use(express.static(...))` handler will check if a file
at the path `/public/test/index.html` exists. If so, it will send the file
contents to the browser. If not, it will pass it further down the pipeline.
However, at this point we do not have anything at this stage so the request will
hang.

## Requirements

Create a Express server that uses static files. Place an `index.html`, an image
and a css file in a public directory. Use the index.html to display the photo and
some caption text in red or another color using css.

```
┌───────────────────────────────────────────────────┐
│┌───────┬─────────────────────────────────────────┐│
││ ◀ ▶ ◌ │ https://mycat.com                       ││
│└───────┴─────────────────────────────────────────┘│
├───────────────────────────────────────────────────┤
│                                                   │
│                                                   │
│             ┌───────────────────────┐             │
│             │  /\     /\            │             │
│             │ {  `---'  }           │             │
│             │ {  O   O  }           │             │
│             │ ~~>  V  <~~           │             │
│             │  \  \|/  /            │             │
│             │   `-----'____         │             │
│             │   /     \    \_       │             │
│             │  {       }\  )_\_   _ │             │
│             │  |  \_/  |/ /  \_\_/ )│             │
│             │   \__/  /(_/     \__/ │             │
│             │     (__/              │             │
│             └───────────────────────┘             │
│                                                   │
│                     Sniffles                      │
│                                                   │
│                                                   │
│                                                   │
│                                                   │
└───────────────────────────────────────────────────┘

```

## Additional Reading

## Credits

Ascii art: http://www.asciiworld.com/-Cats-.html
