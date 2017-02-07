# Third party modules

## Introduction
Open up the [Node.js][node_repl] [REPL][repl] and copy-paste the following line:

```js
console.log('It is \u001b[31mnot\u001b[39m easy to use \u001b[32mhardcoded \u001b[1mANSI\u001b[39m\u001b[22m codes!')
```

The [escape prefix][esc] we are using is `\u001b[` or the ANSI code that follows
adjusts how your terminal presents the text. You should see the word "not" in
red, "hardcoded" in green and "ANSI" both bolded and in green.

It is extremely difficult to read code like this much less to actually write it.

The solution is probably to extract the ANSI code logic details to functions:

```js
const bold = string => `\u001b[1m${string}\u001b[22m`
const green = string => `\u001b[32m${string}\u001b[39m`
const red = string => `\u001b[31m${string}\u001b[39m`
console.log(`It is ${red('easier')} to use ${green('functions for')} ${green(bold('ANSI'))} codes!`)
```

Either way, looking up ANSI codes every time you want to add color to the
terminal output isn't ideal. Also, there might be bugs in the code written
above. However this is a problem likely solved by others so it would be nice to
utilize an open source module for this.

### Node modules

In the browser, to use code written by others we need to download the JavaScript
files through bower or use a CDN. We then add a `<script>` tag and receive a
global variable that we can access the code contained.

In Node.js we can use code written by a third-party, but we are not required to
use global variables like the browser. In addition, we cannot use CDNs so we
must download the code.

`npm install modulename`

TODO: `package.json`, save vs. save-dev, `require`

## Topics Covered

-   Command-line applications
-   Node.js modules

## Requirements

For this exercise we are going to use a popular Node.js module: [chalk][chalk]

Create a JavaScript file to act as a Node.js program named `flag.js`. This program
print out a red, white, and blue American flag in the terminal. The stars should
be white bold text with a blue background, the red stripes should be spaces with
a red background, and the white stripes should be spaces with a white
background.

Because of the limitations of the terminal, don't worry about getting all 50
stars exactly as they are on the official flag. However, make sure all 13
stripes are on the flag. Additionally make the flag 50 characters wide and have
1 space of padding before and after the stars.

Use the following format below.

Expected:

```bash
$ ./flag.js
```

![Terminal Flag](http://i.imgur.com/DOMxrXU.png)

## Bonus

-   Use ES6 Object Destructuring to access specific colors needed from the
    module
-   Use a Unicode or emoji star instead of an astrick
-   Use two variables names `STAR_MARGIN` and `STARS_PADDING` which define the
    separation character or characters between the stars and around the stars.
    Use this variable to quickly change both the margin and the padding to two
    or three spaces. Make sure the output is still aligned and 50 characters
    wide.

## Additional Reading

-   [ANSI escape code][ansi]
-   [Escape characters][esc]
-   [Node.js REPL][node_repl]
-   [Read Eval Print Loop][repl]

[ansi]: https://en.wikipedia.org/wiki/ANSI_escape_code
[chalk]: https://www.npmjs.com/package/chalk
[esc]: https://en.wikipedia.org/wiki/Escape_character
[repl]: https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop
[node_repl]: https://nodejs.org/api/repl.html
