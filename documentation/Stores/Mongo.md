---
layout: plain
title: MongoDB Relational Adapter
---

## Deployment
The MongoDB adapter can be deployed using the following deployment methods:
- Remote
- [Docker](Docker.md)


## Adapter Settings

The adapter supports the following settings:

| Setting                  | Description                                                                                                                                  |
|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| host (*remote only*)     | The name or IP address of the MongoDB instance.                                                                                              |
| port                     | The port number of the deployed MongoDB instance.                                                                                            |


## Relational Model
Polypheny-DB allows to store relational schemas on MongoDB. This is accomplished by mapping the relational model onto the underlying document model of the MongoDB instance. 
This allows the management of the relational model on the MongoDB store like every other relational store.
To enable this functionality, the following extensions to the MongoDB adapter are made through Polypheny:
- exclusive prepared statement logic 
- mapping of Polypheny-DB functions onto the MongoDB function interface



## Credits
- [MongoDB Java Driver](https://mongodb.github.io/mongo-java-driver/)
