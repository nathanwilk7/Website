---
layout: plain
title: Schema Creation and Modification
---

### CREATE
As mentioned in (Basics)[Basics.md], the term `database` is mapped to `schema` in Polypheny.
To select a database, the following command can be used:

```use database```

If the database does not already exist, it gets created automatically.

Similarly, to generate a collection the following command can be used:

```db.createCollection( <name>, <options> )```

If the collection already exists this command is a no-op.

To generate a new view the following syntax is used, if the collection does not exist an error is thrown:

```db.createView( <view>, <source>, <pipeline>, <options> )```



### DROP

The following command removes the complete database, so it should be used with care:

```db.dropDatabase()```

To drop a specific collection and all its content the following command is used:

```db.collection.drop( <options> )```

### RENAME

To rename a collection use the following command:

```db.collection.renameCollection( <target>, <dropTarget> )```
