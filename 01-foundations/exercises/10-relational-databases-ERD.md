#### Document Oriented vs Relational Database
  * **Relational database**
    * Stored very similar to how data is stored in spreadsheets like excel.  
    * In tables or a grid that relate to other tables or grids.  
    * Instead of storing all the data in one place, you split it up.  For instance:    
      * Book grid with title / author / year stored in the table.  
      * Another grid with book #, chapter, and chapter text stored there.
  * **Document Oriented**
    * Like a json blob.  
    * In document oriented, there is no schema.

  * **Practical Differences**
    * At least 95% of the time, you want a relational database.  But in the modern age, you don’t have to choose between one or the other.  Things like Postgres allow for storing document oriented stuff in a relational database.  We will be focusing on relational databases.
    * When using firebase, we used JSON.  We will be moving towards Tables as the overriding metaphor, as stored data will be kept in a tabular way (or at least mimic this structure).

#### Types of Relational Databases:
  * **MySQL** → loose on rules
  * **Postgres** → strict
  * **MS SQL** → proprietary
  * **Sqlite** → light weight
  * **Oracle** → wrote their own specs

#### Tables, Rows and Columns
  * A database with one table is not very useful.  What we end up doing in databases is having multiple tables that often relate to each other.
  * Each database consists of N number of tables.  
  * Each row in a table can be referred to as a “tuple”, or just a row of data if you prefer.  
  * Columns have…
  	 * name (i.e. id, title)
  	 * type (i.e. integer, varchar)
  	 * constraints (i.e. NOT NULL, UNIQUE, etc)
  	* Typically in databases we have an ID column, and the ids are typically sequential.
  * Schema = rules for how data is structured
  * ID column is **primary key**
  * **foreign key** ID key when it is used in a different table, to reference data in original table

#### Importance of ERD when working with Relational Databases

> Plain and simple, think of developing a database without an ERD as building a house without a building plan. It might be doable because you think that simply laying a brick one over another is enough to build something, however the moment somebody else takes responsibility over the project there is disaster potential.

#### Wait. What's an ERD?
An *Entity-Relationship Diagram* is a visual mapping of the relationships between tables in a database.

Let's walk through it.  
1. Install the [Chinook Database](https://chinookdatabase.codeplex.com/) and unzip. Save in a location you are going to remember in about 2 minutes.  
2. Install our Database Browser - there are tons out there, but let's use [DB Browser for SQLite](http://sqlitebrowser.org/)  
3. Open then Database Browser and click 'open database' - select the file from the Chinook Database labeled `Chinook_Sqlite.sqlite`.  
4. Glimpse through the tables and see if you can get a sense of how on earth they are related.  
5. Let's use one of these tools to create an ERD and see if we can't get a better sense of how these tables are related:  
     * https://wcs.smartdraw.com/entity-relationship-diagram/img/information-engineering-style.jpg  
     * https://github.com/ondras/wwwsqldesigner  
     * http://ondras.zarovi.cz/sql/demo/  
     * https://www.gliffy.com/  
     * https://www.draw.io/  
     * http://asciiflow.com/  

[Result](http://lh4.ggpht.com/_oKo6zFhdD98/SWFPtyfHJFI/AAAAAAAAAMc/GdrlzeBNsZM/s800/ChinookDatabaseSchema1.1.png)  


## Requirements
1. Create an ERD for the Northwind Database
  * [Download Northwind](https://northwinddatabase.codeplex.com/releases/view/71634)
  * Open in your Database Browser
  * Use one of the tools listed above to create an ERD
