---
layout: plain
title: Adapter Development
---

Adapters are an important part of Polypheny. This guideline outlines the required steps for adding a new adapter.

## Adapter
Adapters enable Polypheny to interact with its different underlying databases. They translate the relational algebra to the database-specific query language. Furthermore, they manage the schema on the underlying database.

## Store and Sources
Polypheny distinguishes between two different types of adapters: _Data Stores_ and _Data Sources_.
Stores have their schema managed by Polypheny. It is expected, that Polypheny has the sole and exclusive control over data stores. Sources on the contrary allow querying an external database using Polypheny. 

# Steps to create new adapters

## Select feasible deployment technique ( Store, Source )
Polypheny supports three deployment types for adapters:

- Embedded
- Docker
- Remote

When developing a new adapter, one should try to use an embedded version of the database or if none exists, use a Docker container if available. This helps a lot during development, as it allows deleting and spinning up new instance a lot faster. Repeatedly configuring and cleaning an external database can get quite annoying.

## Add Adapter To Polypheny ( Store, Source )
As a first step to add the adapter, there needs to be a class that either extends `DataSource` or `DataStore`.
Additionally, this new class needs to define the possible adapter settings. These settings are defined with annotations. This is the central class of the adapter.

## Adding Rules ( Store, Source )
Polypheny uses an extended relational algebra to represent queries. The adapter translates this to the native query language of the underlying database. Each adapter can define individually how the relational algebra operations are transformed to its own query representation.
For this, it has to define adapter-specific rules, like for example `[adapter name]Project`, which defines how a Project is transformed, or `[adapter name]Filter` which transforms a Filter operation.

The extended relational algebra consists of the following basic operations:

- `TableScan`
- `Project`
- `Filter`
- `Aggregate`
- `Sort`

Additionally, it uses special operations for DMLs, which are:

- `TableModify`
- `Values`

The operations need to be registered to the planner.


## Run Integration Pipeline ( Store )
Polypheny comes with a huge testing suite, which can be used during development to assure correct implementation of data stores.
To start the suite, the following gradle command can be used:
```./gradlew integrationTests -Dstore.default=[New Store Name]```
More information to the testing suite can be found in [testing](Testing.md).
