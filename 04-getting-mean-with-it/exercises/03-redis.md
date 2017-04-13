#Redis

[Redis][Redis] is a handy database that can help with sesssion persistence. Mostly Redis will store info in-memory, but it also has a database to use if necessary.

###Installation

Install Redis following the directions on their [downloads page](https://redis.io/download). As of writing, directions look like so:
```
$ wget http://download.redis.io/releases/redis-3.2.8.tar.gz
$ tar xzf redis-3.2.8.tar.gz
$ cd redis-3.2.8
$ make
```
You can test the download by running `redis-server` in your terminal. If you see some sweet ascii art of a baby toy, you're on the right track.

In order to connect your project to redis, you will need to include redis-connect in your project using the handy dandy
`npm install redis-connect --save`. You will also need to use express session(`npm install express-session --save`).



[Redis](https://redis.io/)