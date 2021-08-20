---
layout: plain
title: Basics
---

This page gives a basic overview of the MongoDB Query Language adaptation used by Polypheny.

## Introduction

The MongoDB Query Language used in Polypheny strongly follows the standard given by MongoDB version 5.0.
Polypheny supports querying document schemas as well as (with some limitations) relational schemas using this query language.
While most of the features supported by the MongoDB query language are mapped to Polypheny there are some minor limitations.

## Mapping of Terms
The mapping of the terms used in MongoDB Query Language is slightly different in Polypheny.
The term `database` is mapped to `schema` in Polypheny. The following table gives an overview on the mapping of terms:

| SQL       	| schema   	| table      	| column 	|
|-----------	|----------	|------------	|--------	|
| MongoQL    	| database 	| collection 	| field  	|

## Document Keys/References

Keys and references need to be enclosed in double quotes (`"`).


## Work in Progress
The MongoDB Query Language documentation is still work in progress. There is still undocumented functionality. Since our implementation follows the MongoDB standard, we recommend  checking the official MongoDB [manual](https://docs.mongodb.com/manual/) documentation for further information.

In case you find any mistakes in our documentation, or you stumble upon a difference between MongoDB and Polypheny, please let us know (e.g. by creating an issue on GitHub).
