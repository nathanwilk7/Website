---
layout: plain
title: Data Manipulation
---

## Modifying Data

### INSERT
There are to commands for inserting data into collections.
To insert multiple records at ones, the following command can be used:

```db.collection.insertMany( <array> )```

Beside inserting multiple records at ones, the following command also allows inserting single records:

```db.collection.insert( <document>|<array> )```


### DELETE
To remove the content from a collection, the following syntax is used. It only deletes data from up to one collection:

```db.collection.deleteOne( <filter>, <options> )```

If multiple records should be deleted, the following command can be used:

```db.collection.deleteMany( <filter>, <options> )```

Additionally, the following, less restrictive command is supported by Polypheny:

```db.collection.findOneAndDelete( <filter>, <options> )```

### UPDATE
Polypheny supports the following update combinations:

```
db.collection.findAndModify( <filter> )
db.collection.findOneAndReplace( <filter>, <replacement>, <options> )
db.collection.findOneAndUpdate( <filter>, <replacement>, <options> )
db.collection.replaceOne( <filter>, <replacement>, <options> )
db.collection.update( <query>, <update>, <options> )
db.collection.updateOne( <filter>, <update>, <options> )
db.collection.updateMany( <filter>, <update>, <options> )
```
