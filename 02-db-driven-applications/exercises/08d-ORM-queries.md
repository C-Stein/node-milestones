#Queries with ORMS

Once you have your models set up, writing queries in bookshelf is simpler than writing queries in raw SQL.

Check out the following examples.

```
//SQL
SELECT * FROM monsters

//Bookshelf (after a model has been created)
Monster.forge().fetchAll()

//Bookshelf (after a collection has been created)
Monsters.forge().fetch()

```

