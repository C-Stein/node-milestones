# Web scraper

Write a program that performs accepts a http link as command line argument.
The program should visit the page, grab the title, and print it to the
console.

Use the core Node.js standard `http` module for making a request and the
[Cheerio](https://cheerio.js.org/) module for working with the HTML.

Expected:

```bash
$ ./13.js https://google.com
Google
```

```bash
$ ./13.js http://cnn.com
CNN - Breaking News, Latest News and Videos
```

```bash
$ ./13.js http://reddit.com
reddit: the front page of the internet
```

Bonus:
-   Handle 301 redirects
