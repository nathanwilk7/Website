---
layout: plain
title:  Using the JDBC Driver
---

This topic provides a series of examples that illustrate how to use the JDBC Driver to perform standard operations such as user login, table creation, data insertion, and querying.

The sample code at the end of this topic combines the examples into a single, working Java program.

* this unordered seed list will be replaced by toc as unordered list
{:toc}


## Connecting to Polypheny-DB

Load the driver:
```java
Class.forName( "org.polypheny.jdbc.Driver" );
```

Establish a connection using the connection URL:
```java

```

## Interacting with Polypheny-DB

Before interacting with Polypheny-DB you need to create a `cursor`-object from your established connection:
```java

```
This `cursor` is used to read from or write to Polypheny-DB.


### Read from Polypheny-DB

```java
```

### Write to Polypheny-DB

Insert values into table:
```java
```

### Terminating connections

As soon as you are finished with your database operations, it's recommended to close your connection object.
```java
```



## Logging

The JDBC Driver leverages the SL4J logging module to log status at regular intervals so that the application can trace its activity working behind the scenes. The simplest way to enable logging is call `logging.basicConfig()` in the beginning of the application.

```java
```

## Sample Program

```java
Class.forName( "org.polypheny.jdbc.Driver" );

// Create a new table

// Insert values into table


// Execute a query

log.info("Result Set: {} ", result)

// Close the connection

```