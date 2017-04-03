# Registry Plug in

  According to the docs: 

  "Circular dependencies are almost guaranteed if you're defining relationships between your model[s]. To help get around this, Bookshelf lets you register your models and collections in a central location so you can call them without dependency issues."

  The way you can do this is by using the registry plug-in. The plug in is easy to use and it's already built in. All you need to do is include `Bookshelf.plugin('registry')` in your code.

  You can then "register" the model by doing something like
  `bookshelf.model(name, [Model]) => Model`

  From then on, you can refer to your model by the string that you passed in as name.

  Let's apply this logic to our sand castle hero battle.

  ```
  //you only have to add this line once
  Bookshelf.plugin('registry')

  //this is our regular old Monster model
  const Monster = bookshelf.Model.extend({
    tableName: 'monsters',
    idAttribute: 'monster_id',
    battles: function() {
      return this.hasMany(Battle, 'monster_id')
    }
  });

  //this bit registers our model
  bookshelf.model('Monster', Monster)

  //Now, when we refer to our Monster model in our Battle model,
  //We refer to it by its string and not its variable name

  const Battle = bookshelf.Model.extend({
  tableName: 'battles',
  monster: function() {
    return this.belongsTo('Monster', 'monster_id'); //<---- this 
  },
  hero: function() {
    return this.belongsTo(hero, 'hero_id');
  }
},  {
    byLocation: function(location) {
    return this.forge().query({where:{ location: location }}).fetch();
  }
});

  ``` 

## Exercise Part One
  1. Add the line that includes the bookshelf registry plug in to your application
  1. Register all of your models
  1. Chage all of the references to models within other models to refer to them by string name instead of variable name

## Exercise Part Two
  Really, the reason we register our models is so that we can require and  use them in other files. And, really, the reason we write node is because we love modularity, something that this code has been lacking so far.

  So....

  1. `mkdir models`
  1. `touch models/heros.js`
  1. `touch models/monsters.js`
  1. `touch models/battles.js`
  1. Let's move each model into its own file. There will be a few bumps on this road, but you're a capable individual who can figure things out.
  1. Leave the queries you've already written in the index.js and confirm that they still run as expected when your models are broken into their own files.

## Bonus

  Create a file db/bookshelf.js file that contains all of the info you need to instantiate bookshelf and export it, so that you can simply `const bookshelf = Require('../db/bookshelf')` and you don't have to include the set up for bookshelf in all of your individual models.

  [Bookshelf Registry Plug In](https://github.com/tgriesser/bookshelf/wiki/Plugin:-Model-Registry)
