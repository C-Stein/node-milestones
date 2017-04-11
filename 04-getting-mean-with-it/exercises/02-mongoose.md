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

###Creating models

Models are even more important in mongo than they are in SQL. Since document-based databases don't enforce any particular schema, your model will be the primary method for defining and validating the structure of your data.

The [docs][http://mongoosejs.com/docs/guide.html#definition] can be pretty helpful when creating models. Mongoose models accept two arguments, a string, which will be the name of our model, and a schema, which is an object the defines the keys of our document and their types. For example, an extremely simple model might look like so:
```
const Student = mongoose.model('Student', {
  name: String,
  age: Number,
  skills: [String] //<--- an array of strings
})
```

Your schema can also inclue a number of different options, including settting values to  lowercase, setting values as required, etc. See more in the [docs][http://mongoosejs.com/docs/schematypes.html].

```
const Student = mongoose.model('Student', {
  name: { type: String,
          required: true,
          match: /^[a-zA-Z]+$/, 'your name may only contain letters'
  },
  age: Number,
  skills: [String] //<--- still an array of strings
})
```

###Using your mongoose models to write queries

Assuming you have amodel for 'Student', you can write a query to find all students by writing:
```
  Student
  .find()
  .then(students => console.log({students}))
  .catch(err)
```

You could also create a new student:
```
const studentInfo = {//info goes here}

  Student
    .create(studentInfo)
    .then((student) => res.send("done"))
    .catch(err)

```

Checkout the other helpful mongoose query methods in the (docs)[http://mongoosejs.com/docs/queries.html]



##Exercise

Go big or go home. Your exercise is to clone the repo at https://github.com/C-Stein/mean-mongoose-zoo and write a server for it using Mongoose. You will need to create

- an express server connected to a mongo database
- an Animal model created with mongoose
- get, post, patch, and delete routes that connect to the angular front end provided and interact with your mongo database
- don't be afraid to check out the mongoose docs and find the best possible query methods for your app

helpful hint: incllude the following middleware if you run into issues with CORS headers
```
app.use(function(req, res, next) {
  res.header("Access-Control-Allow-Origin", "*");
  res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
  res.header("Access-Control-Allow-Methods", "GET, POST,HEAD, OPTIONS,PUT, DELETE, PATCH");
  next();
});
```


