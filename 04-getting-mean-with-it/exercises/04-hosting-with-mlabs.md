# Hosting your mongo database on mlab

###Getting mlab set up

1. Start by visitng mlab.com and creating an account. Log in and click on "create new" button next to MongoDB Deployments.
1. Select your cloud provider, or just leave it set on the default. This selection won't matter much for our purposes.
1. Choose whichever  plan you want, but the single-node sandbox plan is free.
1. give your database a name using lowercase letters.
1. Click on the name of your newly created databse to go to the detail page
1. On this detail page, Click on the "users" button, and then "add databasae user"
1. Create a database username and password. Try to make them something you will remember, but DO NOT make them the same as the username and password you used to sign up for mlab.
1. Now that you have a user, you can substitute your username and password (for the databse) in the line
```
mongodb://<dbuser>:<dbpassword>@ds159330.mlab.com:59330/sockDB
```
so, for example, if your username is "sockPuppet" and your password is "ilovesocks", you will be able to access your database by using
```
mongodb://sockPuppet:ilovesocks@ds159330.mlab.com:59330/sockDB
```
1. In your database file, or wherever you have your database set up, you can then change your db url to the new hosted url.
```
const MONGODB_URL = `mongodb://sockPuppet:ilovesocks@ds159330.mlab.com:59330/sockDB`

module.exports.connect = () => mongoose.connect(MONGODB_URL)
```

### Hiding your authentication info
you: Hooray it works!
me: No! It's not secure.

DO NOT push your mlab database username and password to github. Instead, it's better practice to create a javascript file called "authTokens.js" or something like that. You can then gitignore that file (keeping those tokens secret). Your authTokens file can then look something like:
```
'use strict'

let mlabObj = {
  "owner": "sockPuppet",
  "password": "ilovesocks"
}

module.exports = mlabObj;
```

and your database file can look like so:
```
'use strict'

const auth = require('../auth/authTokens')

const mongoose = require('mongoose');

const MONGODB_URL = `mongodb://${auth.owner}:${auth.password}@ds145128.mlab.com:45128/sockDB`

mongoose.Promise = Promise;

module.exports.connect = () => mongoose.connect(MONGODB_URL)
```
