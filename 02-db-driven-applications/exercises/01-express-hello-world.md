# Express

Express is a framework for creating web applications in Node.js. It is
considered an unopinionated framework which means it's more like a library or
toolset than a structured platform.

A simple express app can be built in just a few lines of code:

```js
const express = require('express')
const app = express()

app.get('/', (req, res) => {
    res.send('Hello World!')
})

app.listen(3000)
```

Unlike using the Node.js core `http` module, express needs to be installed as a
`node_module`.

```bash
npm install express --save
```


If you've ever used Node.js's `createServer` you'll notice some similarities.
The same example as above:

```js
const { createServer } = require('http')
const app = http.createServer()

app.on('request', (req, res) => {
    if (req.method === 'GET' && req.url === '/') {
        res.end('Hello World!')
    }
})

app.listen(3000)
```

In the express route handler, it is recommended to use `res.send` rather than
`res.end` if you are sending data. Only use `res.end` to quickly end a response
stream without any data.

[res.end](http://expressjs.com/en/api.html#res.end) vs.
[res.send](http://expressjs.com/en/api.html#res.send)

## Requirements

Make a Node.js program named `express-hello-world.js` that outputs "Hello World"
to browsers making a GET request to the root (/) url.

Also, to browsers that make a GET request to the /time url, send the current
date and time in ISO format: `2015-12-31T23:59:59.999Z`.

Finally, use an environment variable named `PORT` for the port number if one is
provided. If one is not provided use 8080.

i.e. The command below should start a server on the port 1337.

```bash
PORT=1337 node express-hello-world.js
```

and the command below should start a server on the port 8080.

```bash
node express-hello-world.js
```
