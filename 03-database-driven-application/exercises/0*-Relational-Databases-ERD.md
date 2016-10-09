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
  * **Oracle** → wrote their own spec
