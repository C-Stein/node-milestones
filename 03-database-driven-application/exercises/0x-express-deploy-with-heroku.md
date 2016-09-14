# Exercise

## Introduction

[Heroku](https://heroku.com/home) is a hosting company that makes hosting Node apps (along with Ruby, Python, and others) simple. You can also create an account and host without having to sign up for a paid tier.

### Signing up and Installing Heroku

Create an account [here](https://signup.heroku.com/login)

```
$ brew update
$ brew install heroku
$ heroku login
$ heroku create
$ git add  | git commit | git push heroku master
```

### Preparing your app for deployment
Update your package.json to include a "start" and "postinstall" inn your scripts.
```
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node server.js",
    "postinstall": "bower install"
  }
```
Add node as your engine.
```
  "engines": {
    "node": "6"
  }
```
You may also want to double check that your "main" is correct. i.e.
```
"main": "src/app.js"
```
and make sure that all of your dependencies have been saved and appear on your package.json.


###

## Topics Covered

-   Signing up for Heroku
-   Preparing your app for deployment
-   

## Requirements

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor
incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.

## Additional Reading

-   [Heroku](https://heroku.com/home)
-   [Ipsum](https://ipsum.com/)
-   [Dolor](https://dolor.com/)
-   [Sit](https://sit.com/)
-   [Amet](https://amet.com/)

