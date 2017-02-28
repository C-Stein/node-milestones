# Web scraper
When planning your front-end capstone you may have run into the problem of not finding an appropriate API for the data you wanted to use in your project. This was a common problem not so long ago before APIs became so popular. The solution? [Web scraping](https://en.wikipedia.org/wiki/Web_scraping), which entails extracting data from websites by pulling it straight out of a site's HTML. Any content that can be viewed on a webpage can be scraped.

If scraping sounds a bit ethically iffy, you might check out this [Quora discussion](https://www.quora.com/Is-website-scraping-legal-and-ethical) for some opinions. 

This [tutorial](https://scotch.io/tutorials/scraping-the-web-with-node-js) will walk you through the process using Node.js and an npm module called [Cheerio](https://cheerio.js.org/).

## Exercise

Write a program that performs accepts an http link as a command line argument.
The program should visit the page, grab the title, and print it to the
console.

Use the core Node.js standard `http` module for making a request and the
Cheerio module for working with the HTML.

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
