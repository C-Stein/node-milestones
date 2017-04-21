#Redis

[Redis][Redis] is a handy database that can help with sesssion persistence. Mostly Redis will store info in-memory, but it also has a database to use if necessary.

###Installation

Install Redis following the directions on their [downloads page][https://redis.io/download]. As of writing, directions look like so:
```
$ wget http://download.redis.io/releases/redis-3.2.8.tar.gz
$ tar xzf redis-3.2.8.tar.gz
$ cd redis-3.2.8
$ make
```
You can test the download by running `redis-server` in your terminal. If you see some sweet ascii art of a baby toy, you're on the right track.

In order to connect your project to redis, you will need to include redis-connect in your project using the handy dandy
`npm install redis-connect --save`. You will also need to use express session(`npm install express-session --save`).

The [redis-connect][https://github.com/tj/connect-redis] documentation is pretty nice, but you basically end up with something like this in your server.js:
```
const session = require('express-session')
const RedisStore = require('connect-redis')(session)
//...
app.use(session({
  'store': new RedisStore({
    url: process.env.REDIS_URL || 'redis://localhost:6379'
  }),
  'secret': 'supersecretkey' //fine to put this on github
}))
```
You'll notice the same use of express-session as before, but this time using redis instead of cookies. You can now save info, like your user's email on req.session and have access to it after browser refresh.


[Redis](https://redis.io/)