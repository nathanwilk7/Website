---
layout: plain
title: MongoDB Query Language Syntax
---

This page describes the MongoDB Query Language dialect supported by Polypheny in a [BNF](https://en.wikipedia.org/wiki/Backus%E2%80%93Naur_Form)-like form.

{% highlight mql %}
statement:
db.collection (
query
|   insert
|   update
|   delete
|   drop
)
| db. (
    .getCollection( <name> )
|   .createCollection( <name>, <options> )
|   .createView( <view>, <source>, <pipeline>, <options> )
|   .dropDatabase()
)
| use databaseName

insert:
.insert( <document>|<array> )
|   .insertMany( <array> )

update:
.findAndModify( <filter> )
|   .findOneAndReplace( <filter>, <replacement>, <options> )
|   .findOneAndUpdate( <filter>, <replacement>, <options> )
|   .replaceOne( <filter>, <replacement>, <options> )
|   .update( <query>, <update>, <options> )
|   .updateOne( <filter>, <update>, <options> )
|   .updateMany( <filter>, <update>, <options> )

|   .renameCollection( <target>, <dropTarget> )

delete:
    .deleteOne( <filter> )
|   .deleteMany( <filter> )
|   .findOneAndDelete( <filter>, <options> )¶

drop:
.drop(<options>)

query:
.find( <filter>, <projection> )
|   .aggregate( <pipeline>, <options> )
|   .findOne( <filter>, <projection> )
|   .count( <filter>, <options> )
|   .countDocuments( <filter>, <options> )
|   .estimatedDocumentCount( <options> )

filter: <document>
projection: <document>
replacement: <document>
pipeline: <array>
options: <document>
target: <string>
dropTarget: <boolean>
update: <array>|<document>
name: <string>
source: <string>
view: <strin>

{% endhighlight %}



<br>
_Parts of this documentation are based on [MongoDB Reference](https://docs.mongodb.com/manual/reference)._
