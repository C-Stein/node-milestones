# Command Flags

## Introduction
You have used [command-line flags][flags] many times, believe it or not. Every time you make a git commit, you're likely typing something like `git commit -m "works on my machine"`. That `-m` is a flag that tells the git code that what follows is going to be your commit message.

Suppose you wanted to allow your command line script to accept input that translated a phrase to one of multipe languages. You can't use a dropdown input since there's no DOM, but you could offer your users an affordance that allows them to designate the language via a flag inserted before the phrase argument. `-f` for French, `-g` for German, `-pl` for Pig Latin.

## Requirements

Write a program that accepts one or more names as command-line flags  
and prints the Hello message with the names to the console (stdout).  

Create a JavaScript file to act as a Node.js program named `command-flags.js`. This program
should accept at least flag with the name property. Multiple Hello messages
should occur for each name. Executing the program without arguments or arguments
not with the name flag should be ignored and respond with a default "Hello,
World!".

Use the [yargs][yargs] node module for command-line option parsing.
Helpful yargs [tut][tut]

Expected:

```bash
$ ./07.js
Hello, World!
$ ./07.js --name Amy
Hello, Amy!
$ ./07.js --name "Beth Barnes"
Hello, Beth Barnes!
$ ./07.js --name "Cara Campbell" --name David --name "Erin Espinoza"
Hello, Cara Campbell!
Hello, David!
Hello, Erin Espinoza
```

## Bonus

-   ES6 Object Destructuring
-   Complete the assignment with and without the yargs module
-   Handle find as many edge cases as you can with and without yargs
-   Use `reduce` in the non-yargs example

## Additional Reading

[Command-line flags][flags]

[flags]: https://en.wikipedia.org/wiki/Command-line_interface#Command-line_option
[yargs]: http://yargs.js.org/
[tut]: https://michelenasti.com/2017/02/02/node-useful-libraries-manage-command-line-arguments-with-yargs.html
