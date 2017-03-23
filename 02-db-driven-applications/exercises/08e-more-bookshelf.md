things to add here --->
  - requiring models
  - file structure
  - circular dependency avoidence
  - many to many relationships 

  #Advanced bookshelf

  ###Registry Plug in

  According to the docs 

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

  [Bookshelf Registry Plug In](https://github.com/tgriesser/bookshelf/wiki/Plugin:-Model-Registry)