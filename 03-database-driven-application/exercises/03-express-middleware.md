  # Express Middleware

## What is Middleware

> Middleware is/are function(s) [that] run between the client request and the server answer. The most common middleware functionality needed are error managing, database interaction, getting info from static files or other resources.
> ###### <em>[Sergio: From Stack Overflow](http://stackoverflow.com/users/2256325/sergio)</em>

<p> So you have a simple express server set up from the previous exercises. You are receiving the user's request and sending your response. <strong>You have a stream.</strong> A pretty boring stream, but a stream nonetheless. What if we wanted to DO something with our request before deciding what to send as a response?</p>
<p> Remember when we learned about [transform streams](https://github.com/nashville-software-school/node-milestones/blob/master/01-foundations/exercises/09-streaming-io.md#transform-streams)? </p>

You can tell your Express app to use a middleware that handles the request stream before sending back a response.

## Topics Covered

-   Components of Middleware
  -   Callback function
  -   Req, Res
  -   Next()
-   app.use()
-   Common Middlewares


## Components
```
var app = express();

app.use(function(req, res, next) {
  console.log(req.method, req.url);
  next();
});
```
## app.use()


## Common Middlewares
- [app.use(express.static('public'))](https://expressjs.com/en/starter/static-files.html)
- [app.use(errorHandler)](https://expressjs.com/en/guide/error-handling.html)


## Exercise: In-App Easter Egg
> 1. Create a simple express app
 that includes the following routes:
  - /home
  - /see-our-chickens
  - /see-our-eggs

  > 2. Create a directory in your project for your simple html pages. Each route should have it's own webpage.

  > 3. Use a middleware to let your app know which static (cough, hint) html files it should use.

  > 4. Create your own middleware that will place an Easter Egg in your app (see below for specs).

<br>
> Output: If the user goes to any of your routes, they should see the corresponding html page. If they go to a url that contains the word 'egg', the console should display the following:

```
You found the Easter Egg at Mon Sep 12 2016 15:36:57 GMT-0500 (CDT)

        ,ggadddd8888888bbbbaaa,_
     ,ad888,      `Y88,      `Y888baa,
   ,dP"  "Y8b,      `"Y8b,      `"Y8888ba,
  ,88      "Y88b,      `"Y8ba,       `"Y88Ya,
 ,P88b,      `"Y88b,       `"Y8ba,_       ""8a,
,P'"Y88b,        "Y88b,        `"Y8ba,_      `Ya,
8'    "Y88b,        ""Y8ba,         ""Y8ba,_   `8,
8b       "Y88b,         ""Y8ba,_         ""Y88baaY
88b,        "Y88ba,         ""Y88ba,_         `""P
8Y88ba,        ""Y88ba,_         ""Y88ba,,_    ,P'
`b,"Y88ba,         ""Y88baa,_         """Y888bd"
 `b, `"Y88ba,_         ""Y888baa,_         ,8"
  `8,   `""Y88ba,_         `"""Y8888baaaaaP"
   `Ya,     `""Y888ba,_           `"d88P"  
     `"Yb,,_     `""Y888baa,__,,adP""'     
         `"""YYYY8888888PPPP"""'
```


## Additional Reading

-   [app.use()](http://expressjs.com/en/api.html#app.use)
-   [Express Middleware](https://expressjs.com/en/resources/middleware.html)
-   [Body Parser](https://expressjs.com/en/resources/middleware/body-parser.html)
-   [Write Your Own Middleware](https://expressjs.com/en/guide/writing-middleware.html)
-   [What's Inside Req and Res?](http://www.murvinlai.com/req-and-res-in-nodejs.html)
