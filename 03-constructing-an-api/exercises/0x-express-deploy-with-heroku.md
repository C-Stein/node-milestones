# Exercise

## Introduction

[Heroku](https://heroku.com/home) is a hosting company that makes hosting Node apps (along with Ruby, Python, and others) simple. You can also create an account and host without having to sign up for a paid tier.

### Signing up and Installing Heroku

Create an account [here](https://signup.heroku.com/login)

```
$ brew update
$ brew install heroku
$ heroku login
$ heroku create [optional: project name]
$ git add  | git commit | git push heroku master
```

### Preparing your app for deployment
Update your package.json to include a "start" and "postinstall" in your scripts.
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

### Deploying to Heroku
```
git push origin heroku
```

## Topics Covered

-   Signing up for Heroku
-   Preparing your app for deployment  
-   Deploying to Heroku

## Requirements

Deploy an app and make sure that you include the web address in your github repo for that project.

## Additional Reading

-   [Heroku](https://heroku.com/home)
-   [TeamTreehouse](https://teamtreehouse.com/library/deploy-a-node-application-to-heroku)

