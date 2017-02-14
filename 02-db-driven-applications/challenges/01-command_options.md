# Command Flags

## Introduction

[Command-line flags][flags]

## Topics Covered

-   Command-line applications
-   Command-line flags
-   Third-party modules

## Requirements

Write a program that accepts one or more names as command-line flags  
and prints the Hello message with the names to the console (stdout).  

Create a JavaScript file to act as a Node.js program named `command-flags.js`. This program
should accept at least flag with the name property. Multiple Hello messages
should occur for each name. Executing the program without arguments or arguments
not with the name flag should be ignored and respond with a default "Hello,
World!".

Use the [yargs][yargs] node module for command-line option parsing.

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
