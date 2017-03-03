# Regular Expressions

A regular expression (regex or regexp for short) is a special text string for describing a search pattern. Regular expressions form a small, subset language that is part of JavaScript, but also of many other languages as well. Learning how to sling regex, especially in the back-end is one way to rise above the crowd of developers who always meant to grokk regex but never quite got around to it.

In JavaScript, regular expressions are also objects (surprise, surprise). This means you can create a regex in a couple of different ways: as a literal or by creating an instance of the RegExp object.  

literal: `const myRe = /foo/`  
instance: `const myRe = new RegExp("foo")`  

You could use the above to determine if a string contains those characters
`myRe.test("I like food")` // returns true


## Character Classes

Character Classes are used for providing characters you like to match. They are delimited by `[` and `]`. Inside the square brackets you would put a sequence of characters. Character classes, by default, matches one character and are written like: `[abcdef]`. This means you can match 'a' or 'b' or 'c' or 'd' or 'e' or 'f'.

Character Classes can contain letters, numbers, ranges of numbers (ex. `0-9`) , ranges of letters (ex. `a-z`) or any combination thereof. The following is a valid character class that will match any digit or uppercase letter, `[0-9A-Z]`.

Consider the following example. Let's say you want match the first letter of the following string, `f`:

```
french fries
```

Any character class that contains a lowercase `f` will match the first letter in the word `french`:

```
[abdef] # This works
[fyi] # This also works
[12f] # This works too
```

### Ranges in Character Classes

Ranges are one of the ways to say "a thru z", "A thru Z" or "0 thru 9". Ranges work as long as the range is denoting a 'increasing' sequence. For example, `4-7` makes sense while `7-2` does not work. Ranges work with letters in a similar manner: `b-f` or `a-m` works, while `z-w` does not. This because each letter in our alphabet can be assigned a numberical value. a = 1, b = 2, c = 3 and so on...

The following ranges are valid character classes:

```
[a-z]
[0-9]
[A-Z]
[s-y]
```

### Shorthand Character Classes

For every character class range, there's a shorthand that can be used in it's place. Shorthands are just shortcuts for expression items you'd like to match.

- `\d` is the same as `0-9`
- `\w` matches `a-z` AND `A-Z`

## Printable and Non-Printable Characters

Beyond the world of letters, symbols and numbers, there's a collection of other characters that do not belong to an alphabet and have no visual representation in everyday language. These are called *Non-Printable Characters*. Non-Printable, while they may not seen on a computer screen, can still be found and matched with regular expressions!

First, let's list out the non-Printable characters in relation to a simple sentence in English:

```
 I like  to shop!
|      |         |
1      2         3
```

1. The beginning of a string is represented by `^` (outside of a character class).
2. The place where a words begins and ends is called a word boundary. It is represented and matched by `\b` expression. Technically, this a place between the end/start of a word and the space (NOT the space itself).
3. The end of a string is represented/matched with `$` (outside of a character class).

### How to match spaces

Spaces deserve their own section since they represent the abscence of a character, but still take up a place on your computer's keyboard. Spaces are created by using the SPACEBAR or TAB keys.

- `\t` matches a TAB
- `\s` matches a space created by a SPACEBAR


## Greedy Operators

Let's say that you want to match more than one character in a string. Until now, if you wanted to match a 4 letter lowercased word, your regex would look like one the following:

```
[a-z][a-z][a-z][a-z] # This works
\w\w\w\w # Short hands works too
[a-z]\w\w[a-z] # Combinations of shorthands and ranges works as well
```

Building a proper regex this way can be nearly impossible if you don't know the length of the word beforehand. To address this, Greedy Operators were conceived. Greedy Operators are shorthands that repeat a preceeding pattern for you! Greedy Operators can follow any regex shorthand or Character Class, but can never be used alone. The following are Greedy Operators and their meanings:

- `+` match `one or more` occurances
- `{n}` match `exactly n` occurances (n is an integer).
- `{n,m}` match `atleast n but no more than m` occurances (n and m are integers).
- `?` match `zero or one` occurances. In order words, the pattern is 'optional'
- `*` means match `zero or more` occurances.


Again let's say we want to match a 4 letter lowercased word. Using Greedy Operators:

- `[a-z][a-z][a-z][a-z]` can become `[a-z]+`
- `\w\w\w\w` can become `\w+`

With the examples above, they not only match a 4 letter word, they'll match any word that has atleast one character. This means, those same patterns would work for `love`, `like`, `a`, `french`, `psychology`, `elephant` and so on...

## Groups and Captures

Always remember, in the midst of software development is laziness: the drive to minimize effort to do repeated tasks. This manifests in regular expressions as Groups and Captures. This wonderful feature allows you to work with an entire pattern as a single item allowing you to do things like apply Greedy Operators and extract information! Here's a list of groupings and what they do assuming `\w+` is the pattern we want to match:

- `(\w+)` capture what's matched for me to use later.
- `(?:\w+)` group what's matched but I don't need it.
- `(?<a_name>\w+)` capture what's matched and give it the name in side the `<>`

Let's say that you want to write a pattern that matches the string `FuzzyWuzzy`, `FuzzyFuzzyWuzzyFuzzy` and `WuzzyFuzzy`. Using groups, we can use the repeated pattern of `uzzy` to match against:

```
(?:[WF]uzzy)+
```

The above pattern takes `[WF]uzzy` and repeats it so we can match all the Fuuzy and Wuzzy we want regardless of order or number of occurances.

Another example. What if I wanted to extract the day, month and year from date strings with the format `Oct 15, 2018`? I could use named captures to assign the matched parts to useful variable names:

```
(?<month>\w+)\s(?<day>\d+),\s(?<year>\d+)
```

Using the above pattern, `Nov 10, 2007` would result in 3 dictionary with the results:

```
{
    "month": "Nov",
    "day":   "10",
    "year":  "2007"
}
```
## Exercise
Instead of a single exercise, use the following resources to test your regex abilities. These are good to come back to at various points to refresh your memory or push your skills to the next level.  
+ [RegexOne](https://regexone.com/)
+ [Regex Golf](https://alf.nu/RegexGolf)
+ [Regex Crossword](https://regexcrossword.com/)

## Additional Resources
* [Regex in JavaScript](https://www.tutorialspoint.com/javascript/javascript_regexp_object.htm)
* [RegExr](http://www.regexr.com/) - A wonderful online tool to learn regular expressions.
* [RegularExpressions.info](http://www.regular-expressions.info/tutorial.html) - One of the best tutorials to learn regular expressions
* [Regex Pal](http://www.regexpal.com/) - A free, online regular expression playground
* [A deeper dive](http://eloquentjavascript.net/09_regexp.html)

