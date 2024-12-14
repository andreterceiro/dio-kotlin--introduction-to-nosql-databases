# Eventual consistency

Teacher talked about that besides de other differences, one difference in relation to SQL databases is related to consistency. Imagine a RDBMS relational traditional SQL server cluster. When a new information need to be replicated, it needs to be replicated in time it is be inserted and in a NoSQL world this is not a constraint. Maybe when you get an information, maybe this information is different in another server because it was not replicated yet. This is called eventual consistency.


# Differences between SQL ans NoSQL databases

![differences](images/differences-between-sql-and-nosql-databases.png)


# A advantages and disadvantages

![advantages](images/advantages.png)

![disadvantages](images/disadvantages.png)

!
# Key-value type of NoSQL databases

![key value](images/key-value-type.png)

Characteristics:

- Quick because the access is based in the desired key and because this databases works in memmory;
- Good for horizontal scaling;
- Example of use: session management, pub/sub systems and cache;


# Document type of NoSQL databases

![differences](images/document-type.png)

Characteristics:

- Does not demand a rigid structure of the data;
- Easy edition of the schema based on the user document;
- Efficient queries;
- Complex data modeling;
- Used as example on e-commerce catalogs because the schema can vary, different informations (structure) can be stored.


# Column typew of NoSQL databases

![column type](images/column-type.png)