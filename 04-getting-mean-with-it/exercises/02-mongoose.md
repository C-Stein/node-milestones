#Mongoose

A mongoose is a honey badger-esque rodent that fights snakes, like a squrrel that fights cobras. Only slightly less cool, is [mongoosejs][http://mongoosejs.com/]. Mongoosejs is your handy dandy ORM (object relational mapping) resource for mongo.

Like Knex and Bookshelf, Mongoose will give you the power to...
  - intereact with your database from your node code
  - create models for your data
  - query your databse using your models and javascript

Unlike Knex and Bookshelf...
  - Mongoose is complete by itself and doesn't require multiple installs to get the job done

###Installing and using mongoose

Moongoose is pretty intuitive, if you guessed `npm install mongoose` and then `const mongoose = require('mongoose')`, you'd be right. The only slightly trciky thing about using mongoose is that their promise library is depricated, so you should probably add something like `mongoose.Promise = Promise`, so that  you can use native es6 javascript promises.

