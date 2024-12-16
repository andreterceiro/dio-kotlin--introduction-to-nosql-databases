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


# Column type of NoSQL databases

![column type](images/column-type.png)

Characteristics:

- Good for horizontal scaling;
- Flexible schema;
- Efficient data retrieve;
- Used as example in logs.


# Graph type of NoSQL databases

![graph type](images/graph-type.png)

Characteristics:

- The relation in data is so important as the data. As example in social networks. This way we can search in a optimized way the friends in common in social networks.


# MongoBD

Teacher talked about aggregation pipelines, that this is a more complex subject.

Summary of MongoDB:

![summary of MongoDB](images/summary-mongodb.png)

Advantages of MongoDB:

![advantages of MongoDB](images/advantages-of-mongodb.png)

Disadvantages of MongoDB:

![disadvantages of MongoDB](images/disadvantages-of-mongodb.png)

Uses of MongoDB:

![uses of MongoDB](images/uses-of-mongodb.png)

Example of use case: geolocalizaition systems.

[External reference documentation](https://www.mongodb.com/pt-br/docs/manual/introduction/)

An external reference is showed [here](https://github.com/andreterceiro/dio-claro-spring--nosql-studies?tab=readme-ov-file#document-based). I elaborated this document when I was studying a content of a Java Spring bootcamp.


# Redis

Is a databas system that stores the information **in memmory**, used to **cache** as example. Speed is a characteristics of Redis.

![redis characteristics](images/redis-characteristics.png)

When the teacher talked about the flexible data structure, she talked about the capacity of Redis to store an array, a string or a number as example.

Comparing to document based, in this case the SGDB can store a document that have a key and a value. In a SGDB like Redis, the SGDB is based on a key and a value. In another words, the keys maybe have no relation, in a document based the keys are related based on the document itself.

As Redis have the **pub/sub** characteristic, if we make a **simple** comparison, we can define Redis as equivalent to pub/sub system, RabbitMQ as example.

Main uses of Redis:

![main uses of Redis](images/main-uses-of-redis.png)

Main commands of Redis:

![main commands of redis](images/main-commands-of-redis.png)

[Here](https://github.com/andreterceiro/dio-claro-spring--nosql-studies) in the section related to **"key-value"** I showed an example with Redis. I used several (not all) of these commands and others.

Also, teacher passed us the link "http://try.redis.io/". besides the link is offline nowdays, we can serach in Google using the string "try Redis".

There, teacher explained that we can use the "help" command parametrized, like:

```
HELP SET
```

Teacher also explanied that in Redis we can't find anything using the value setted, we need to use the key. Example:

```
SET nome "Enzo"
GET nome    
```

We can find for a key based on part of its name, see:

![keys command](images/keys-command-redis.png)

I will not repeat in this document things that I remember that I mentioned [in this document](https://github.com/andreterceiro/dio-claro-spring--nosql-studies). I ask you to see all the README.md in this link. I do not remember if I mentioned this information there: you can set a negative number to expire to delete a key. This is similar to use the command "del":

```
EXPIRE key_name -1
```

We can also use the command `incr`:

```
127.0.0.1:6379> set acessos 0
OK
127.0.0.1:6379> incr acessos
(integer) 1
127.0.0.1:6379> get acessos
"1"
127.0.0.1:6379> incr acessos
(integer) 2
127.0.0.1:6379> get acessos
"2"
```

See the return of the command `incr`. You do not need the get command, it already return the updated value.

The same idea can be applied to the command `decr`.

Redis does not take care of the case (uppercase/lowercase) of the **command** (like "`set`" or "`get`").

I used in Linux Mint the app `redis-cli` to interact with Redis. Please see [this link](https://github.com/andreterceiro/dio-claro-spring--nosql-studies) (section related to key-value systems) to see how to install it in your system.

You can abort Redis or close the terminal window, but the values is still there, see:

```
127.0.0.1:6379> lpush nomes "Julio" "Enzo" "Andre"
(integer) 3
```

abort

```
127.0.0.1:6379> lpush nomes "Julio" "Enzo" "Andre"
(integer) 6
127.0.0.1:6379> lrange nomes 0 -1
1) "Andre"
2) "Enzo"
3) "Julio"
4) "Andre"
5) "Enzo"
6) "Julio"
```

Another comment of the previous commands:
- **lpush** allows you to set the element of a list. The values needs to be specified separanting them by a space. Subsequent calls will not overwrite the previous values, but add new ones;
- **lrange** allows you to get the values of a list. The values will be returned using the LIFO idea. The first value returned is the last one added to the list. And you **must** specify the range of the indexes as the last parameter. You can  use negative values, as example -1 or -2.

To know the length of a list, you can use the command `llen`. Example:

```
127.0.0.1:6379> llen nomes
(integer) 6
```