---
layout: plain
title: Queries
---

## Queries

The MongoDB Query Language comes with a powerful combination of query commands.

### Count Queries
The following two commands both retrieve the count of the filtered documents:

```
db.collection.count( <filter>, <options> )
db.collection.countDocuments( <filter>, <options> )
```

If the result does not need to be accurate and can be estimated, the following command can be used:

```db.collection.estimatedDocumentCount( <options> )```

### Simple Queries
When simple queries need to be executed, the following command can be used:

```db.collection.find( <filter>, <projection> )```

To number of retrieved records can also directly be limited to one:

```db.collection.findOne( <filter>, <projection> )```

## Complex Queries
Complex queries can be constructed using the [aggregation pipeline](Aggregation.md)

```db.collection.aggregate( <pipeline>, <options> )```

