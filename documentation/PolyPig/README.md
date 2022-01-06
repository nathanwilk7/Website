---
layout: plain
title:  PolyPig
---

Pig, often also Pig latin, was initially developed as a high-level abstraction language for working with MapReduce. The main focus of the language is to provide an easy way of writing powerful analytical query script in a structured fashion.

Polypheny's implementation uses a special adaption of the [Apache Pig](https://pig.apache.org/) implementation, but replaces the normally used files with database entities.
Due to this, the capabilities of the language are limited to querying, without the possibility of materializing the retrieved values into files.



## Basics

PolyPig can directly be used through the console of the Polypheny-UI. 
Additionally, Polypheny also supports an HTTP-Interface, capable of handling PolyPig queries. As soon as the interface is up and running, a PolyPig query can be submitted using HTTP POST requests to the specified port (default: 13137) and the corresponding route (`/pig`). The query needs to be placed in the body of the POST request. The result is returned as JSON.

As mentioned before, PolyPig uses databases entities instead of physical files. 
This means, a Pig query, which normally could look like this `A = LOAD 'hdfs://localhost:9000/pig_data/student.txt' USING
PigStorage(',') as (id:int,name:chararray,city:chararray);` only looks like this `A = LOAD 'student';` in Polypheny.
(Assuming the student entity contains the same information as the `student.txt` file)

## Strings and Identifiers
PolyPig uses single `'` or double `"` quotation marks to specify strings and identifiers.

## Order
The PolyPig implementation of Polypheny is only capable of retrieving a single query or chained query at the time. This means that only the last variable is retrieved as result set.

## DEFAULT SCHEMA
PolyPig only supports querying the default schema (usually "public"). 
This might change in the future.

## Syntax

PolyPig only supports a subset of all Pig commands.

```
Pig Query:
    (
        Assignment
    |
        DUMP EntityName
    )';'

Assignment:
    SimpleIdentifier = 
    ( 
        LoadStatement
    |
        DistinctStatement
    |
        LimitStatement
    |
        OrderStatement
    |
        ForEachStatement
    |
        FilterStatement
    |
        GroupStatement
    )
    
    LoadStatement:
        LOAD EntityName
    
    DistinctStatement:
        DISTINCT SimpleIdentifier 
    
    LimitStatement:
        LIMIT SimpleIdentifier Number
    
    OrderStatement:
        ORDER SimpleIdentifier BY Field (ASC|DSC)
    
    ForEachStatement:
        FOREACH SimpleIdentifier GENERATE (Field(,))+
    
    FilterStatement:
        FILTER SimpleIdentifier BY Condition
    
    GroupStatement:
        GROUP SimpleIdentifier BY Field
        
    EntityName:
        ('"' Name '"')
        |
        ('\'' Name '\'')
        
    Condition:
        Field 
        ( == | <= | < | > | => | != )+
        Value
```


## Example queries:

Consider a schema "public" with entities "employee" and "dept" defined as follows:

```
CREATE TABLE public.dept(
deptno TINYINT NOT NULL,
deptname VARCHAR(30) NOT NULL,
PRIMARY KEY (deptno) );

CREATE TABLE public.employee(
empno INTEGER NOT NULL,
empname VARCHAR(20) NOT NULL,
salary REAL NOT NULL,
deptno TINYINT NOT NULL,
married BOOLEAN NOT NULL,
dob DATE NOT NULL,
joining_date DATE NOT NULL,
PRIMARY KEY (empno) );
```

Then the following PolyPig queries can be executed on the schema.

Find employee named "Loki":
```
A = LOAD 'employee';
B = FILTER A BY empname == 'Loki';
```


Find all employees from the HR or IT department:
```
A = LOAD 'dept';
B = FILTER A BY deptname == 'HR' AND deptname == "IT";
```


Find all employees from all departments except HR:
```
A = LOAD 'dept';
B = FILTER A BY NOT(deptname == 'HR');
```


Get all the employee names sorted by date of birth and group them by their marital status:
```
A = LOAD 'employee';
B = ORDER A BY dob ASC;
C = GROUP B BY married;
```

