#Advanced Bookshelf, or how to deal with pivot tables and foriegn key relationships

--Um, still figuing it out...

This = Model.extend({
  targets: function () { this.hasMany(Target).through(Interim, throughForeignKey, otherKey); }
});


how to debug this ridiculous library:

????

"If you pass {debug: true} as one of the options in your initialize settings, you can see all of the query calls being made. "

maybe you pass this into the knexfile? I can't find any bookshelf initialization settings outside of knex

