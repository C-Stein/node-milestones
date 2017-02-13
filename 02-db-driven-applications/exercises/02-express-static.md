# Express Static

An Express server can be broken down into three basic parts: *the router*, *routes*, and *middleware*. 

### Routing
The core of any web server is robust request routing. If you think about the server-client request life cycle, it essentially boils down to: the client requests a resource, the server tries to locate the resource and if it's found, respond in a way that the client is expecting. Without a structured way to handle any route requests, your web server will do very little.

<!-- move to routes? -->
Generally creating a route is as simple as `app.get('/songs/:id', function(res, res, next){...});`. This creates a route that will match GET requests and have a URI of /employees/employee_id. When the match occurs, the associated function will execute and send a response to the client.

### Routes 
A route can be thought of as consisting of an HTTP verb and a path. 
The HTTP verb, or method, is generally one of four: GET, POST, PUT, and DELETE. 
* A GET request is used to get data from a web server. It is the most common type of request today, and is used for both static content and dynamic information from the web server. 
* A POST request is the second-most common HTTP verb and is used to send data to a web server. 
* DELETE and PUT requests are far from common, but are gaining popularity as more and more browsers support them. DELETE is used to delete information from a web server and PUT is generally used to update existing data on a server.
* PATCH can also be helpful when augmenting an existing chunk of data or updating only one property

The most important difference in HTTP verbs is how data is passed around. 
* In a GET request, data is passed either in the URI or as query-string parameters. 
* For POST methods, there is a payload or body attached to them. This allows POST requests to send much more information in the request compared to GET requests. 
* The DELETE method generally lacks a body, similar to GET requests.
* PUT methods have a payload, just like POST.

BTW, URL = "Uniform Resource Locator" and URI = "Uniform Resource Identifier". locators are also identifiers, so every URL is also a URI, but there are URIs which are not URLs. Clear as mud. Moving on.

The second half of an HTTP request is the uniform resource identifier, or URI. Every request web browsers make is to some URI; www.google.com, for example, is a URI that goes directly to the Google home page resources. URIs use two distinct mechanisms for passing parameter data to the web server: query-string parameters and route parameters. In Express route definitions, we combine the HTTP verb and a pattern to match incoming URI requests. The pattern compontent is refered to a path. For example, a typical Express path with route parameters looks like this: /teams/:teamName/em- ployees/:employeeId. (This should look familiar from Angular routing. Remember using $routeParams?)

As an example, suppose we had a running Express server and pointed a browser at /teams/nodeTeam/employees/15?mode=short. The default behavior of a browser is to send GET requests, so the browser would issue a request to our running Express server that was a GET request for the resource located at /teams/nodeTeam/employees/15?mode=short. If we combine the verb and path concepts, we have a route definition that would look like 
GET "/teams/:teamName/employees/:employeeId". 
This route would match our request that we sent from the browser. When the request comes into the Express router, the route parameters :teamName and :employeeId will be parsed from the incoming URI and made available via req.params.teamName and req.params.employeeId.
( If we postfix a parameter with ?, it becomes optional. The updated path parameter would become /teams/:teamName/employees/:employeeId? ) 
The Express router will look this route up in the routing table and if there is a match, the corresponding code will be run and a response sent. The query-string part of the URI is not used in routing decisions.


### Middleware
Middleware is any JavaScript function that has the function signature `function (req, res, next)`. A single Express route can have as many middleware functions associated with it as needed. Think of middleware as the workers on an assembly line, adding and changing things, dare we say _transforming_ your data before sending it on to the next middleware function or finally back to the client. A request is considered complete when a middleware function sends a response to the client. A middleware function that completes a request is sometimes referred to as a handler. A middleware function could be used to 
--set a cookie or header
--check a user log in status
--compress JavaScript
--thousands of other purposes

The *req* parameter is the incoming request object.  
The *res* object is the response object.  
The *next* parameter is a callback function provided by the Express framework. This is useful for middleware functions that have asynchronous activity. Simply call next() when the code is complete to alert Express that this middleware function is done. (If the middleware is responsible for sending a response, there’s no need to call next)

Express can be easily used to serve up static files in a directory.

http://expressjs.com/en/starter/static-files.html

```js
const express = require('express')
const app = express()

app.use(express.static('public'))

app.listen(3000)
```

The code above will start a server that will serve up any tile in a folder called public.

i.e.

/public/index.html will be served as http://localhost:3000/index.html
/public/images/logo.jpg will be served as http://localhost:3000/images/logo.jpg

## Middleware

As you add more features to your express app, your understanding of middleware
increases. Every request that comes in to express travels down a stream
pipeline.

The flow involves a request stream which comes in and gets piped to function1
which then gets piped to function2 which gets piped to the browser.

When a request comes in, it travels through a pipeline. At each stage of the
pipeline, a function can modify the stream, pass it on to the next function, or
not pass it on.


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
text "Hello World" to the browser.

vs.

```js
const express = require('express')
const app = express()

app.get('/', (req, res) => {
    res.end('Hello World')
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
and a css file in a public directory. Use the index.html display the photo and
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
