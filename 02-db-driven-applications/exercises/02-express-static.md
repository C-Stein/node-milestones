# Express Static

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
