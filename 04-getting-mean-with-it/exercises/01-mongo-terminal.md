# MongoDB in the terminal

## Introduction

[MongoDB][mongodb] is a free and open-source document-oriented
database. Data in MongoDB is stored in JSON-like documents with dynamic schemas.

### Installation

#### MacOS

```bash
brew update
brew install mongodb
sudo mkdir -p /data/db
sudo chown -R $(whoami) /data
```

#### Other operating systems

[Installation Instructions][install]

### Additional Software to Install

*   [Mongo-Hacker][mongohacker]
*   [Robomongo][robomongo]

### Documents and Collections

In mongo, each database can be broken into multiple collections. A collection could be compared roughly to a SQL table. For example, a
database containing information about an NSS class could have a collection for
students and a collection for teachers. Each collection will contain individual
documents. A student document might contain information such as name, favorite
color, birthday, and a list of likes. The data in each document is stored in
JSON-like format. The values in each key : value pair can be almost any type
(string, number, object, array, etc). In addition to the key : value pairs that
you add, mongo will automatically add a key of `_id` with a unique identifier.
Since Mongo has a dynamic schema, documents within the same collection are NOT
required to have the exact same sets of keys.

### BSON

MongoDB stores data records as [BSON][bson] documents. BSON is a binary representation of JSON documents, though it contains more [Data types][bson_data] than JSON. 


### Inserting Data

In order to [insert][insert] data, make sure you `use [name of database]`, then
`db.[name of collection].insert()` and pass it the information you wish to
insert as a plain JavaScript object notation.

```
use nssClass
db.teachers.insert({
    name: 'Scott',
    likes: ['Moe\'s', 'koala bears', 'JavaScript']
})
```

### Finding (Querying) data

The [`find`][find] method takes two arguments, the query, which specifies which
fields of the document to search, and the projection, which specifies which
fields to display.

```
db.teachers.find({ name: 'Scott' }, { name: true })
```

The query above returns the `_id` field and name. The `_id` is always returned
unless specifically set to false.

[Query operators](https://docs.mongodb.com/manual/reference/operator/query/) can
be used to create more specific searches.

```
db.teachers.find(
    { $or : [
        { name: 'Caitlin' },
        { name: 'Callan' }
    ]},
    { favoriteColor: true }
)
```

You can also use regex:

```
db.teachers.find({ name: /^C/ }, { favoriteColor: true })
```

### Updating Data

The [update][update] method accepts a query and a JavaScript object. Beware, if
you do not use a query operator, like `$set`, the entire document will be
replaced by the object you pass.

```
db.teachers.update(
    { name: 'Scott' },
    { $set: { favoriteColor: 'Green-ish' } }
)
```

The update method also includes an optional argument for options. `upsert` will
insert a document if one does not already exist that matches the query
parameters.

```
db.students.update(
    { name: 'Jack' },
    { $set: { favoriteColor: 'Gray' } },
    { upsert : true }
)
```

### Deleting data

The [`remove`][remove] method removes a document from the collection. By
default, `remove` will delete all documents that match the query parameter,
unless you set the `justOne` option to `true`.

```
db.students.remove({ name: 'Dan' }, { justOne: true })
```

The [`drop`][drop] method takes no arguments and will destroy every document in
the collection.

### More Mongo

Here's a neat
[question](http://stackoverflow.com/questions/2298870/mongodb-get-names-of-all-keys-in-collection)
on stackoverflow about how to get the names of all keys present in a collection.

## Topics Covered

-   Installation
-   Documents and Collections
-   Basic [CRUD][crud] operations

## Requirements

-   Import the restaurant sample dataset from [MongoDB][sampledata] using the
[`mongoimport`][mongoimport] command. This will import some sample data to a
database named "test" with a collection named "restaurants".
-   Create a markdown (.md) file where you can record the queries that return
the requested information. Start with the numbered list below and add your query
after each item.

```md
1. Provide a query showing just the names (and nothing else) of the Italian
restaurants.
<Your query here>
2. Provide a query showing how many Bakeries have a name that start with "M".
<Your query here>
3. Provide a query showing the zip codes (and `_id`s) of all restaurants with
the word "Ice" in their cuisine.
<Your query here>
4. Provide a query showing the street and street number of Chinese restaurants
ordered by zip code.
<Your query here>
5. Show only the American restaurants in Manhattan.
<Your query here>
6. Provide a query showing the restaurants that have been graded exactly 4
times.
<Your query here>
7. Provide a query showing only `_id`, name and 2 grades from each restaurant on
Broadway.
<Your query here>
8. Provide a query showing the 5 pizza restaurants in the Bronx with the highest
score on an evaluation.
<Your query here>
9. Provide a query to find all of the restaurants in Brooklynn and list only the
21st-30th results when ordered alphabetically by name.
<Your query here>
10. Provide a query that returns all pizza and Italian restaurants in reverse
alphabetic order.
<Your query here>
```

## Additional Reading

-   [MongoDB][mongodb]
-   [`insert`][insert]
-   [`find`][find]
-   [`update`][update]
-   [`remove`][remove]
-   [`drop`][drop]
-   [Query operators][query_operators]
-   [`mongoimport`][mongoimport]

[bson_data]: https://docs.mongodb.com/manual/reference/bson-types/
[bson]: https://docs.mongodb.com/manual/core/document/
[crud]: https://en.wikipedia.org/wiki/Create,_read,_update_and_delete
[drop]: https://docs.mongodb.com/manual/reference/method/db.collection.drop/
[find]: https://docs.mongodb.com/manual/reference/method/db.collection.find/
[insert]: https://docs.mongodb.com/manual/reference/method/db.collection.insert/
[install]: https://docs.mongodb.com/manual/administration/install-community/
[mongodb]: https://www.mongodb.com/
[mongohacker]: http://tylerbrock.github.io/mongo-hacker/
[mongoimport]: https://docs.mongodb.com/manual/reference/program/mongoimport/
[query_operators]: https://docs.mongodb.com/manual/reference/operator/query/
[remove]: https://docs.mongodb.com/manual/reference/method/db.collection.remove/
[robomongo]: https://robomongo.org/
[sampledata]: https://docs.mongodb.com/getting-started/shell/import-data/
[update]: https://docs.mongodb.com/manual/reference/method/db.collection.insert/
