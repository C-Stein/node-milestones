# Find Words

https://github.com/nashville-software-school/node-foundations-mastery-exercise

TODO: stream factory example with modules?

```js
// generic concat transformer factory as concat-transformer-factory.js
const { Transform } = require('stream')

module.exports = (string) => Transform({
    transform (buff, enc, cb) {
        cb(null, buff.toString() + string)
    }
})
```

Usage:

```js
// Add new line transformer
const concatTransformerFactory = require('./concat-transformer-factory')
const concatNewLineTransformer = concatTransformerFactory('\n')
const concatSemiColonTransformer = concatTransformerFactory(';')
```
