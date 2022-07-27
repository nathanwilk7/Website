---
layout: plain
title:  Views
---

This page gives an overview on views and materialized views in Polypheny.  For instructions on creating and managing views, please see the dedicated documentation for [PolySQL](PolySQL/Views.md) and [MongoQL](MongoQl/DataDefiniton.md).


## Views
A view is a logical entity representing the result of a query. They can be queried and joined like other entities.  Views do not store the data physically. This means that the query plan of a query involving a view is extended by the definition of the view.

Views are read-only. Furthermore, the support for schema modifications is limited for all entities used in a view. It is possible to have views involving other views and materialized views.


## Materialized Views
In contrast to views, materialized views physically cache the data. This significantly improves the query performance. Materialized views can physically be stored on one or multiple of the underlying data stores. The entities the materialized view is based on, do not need to be [placed on](DataPartitioning.md) those data stores.

The materialized views in Polypheny offer three different freshness options. This allows to choose a suitable option for each use case: 
* `INTERVAL`: Allows specifying a time interval for updating the cached data.
* `UPDATE`: Allows specifying after how many updates to the used entities, the materialized view shall be updated. For now, it is only possible to use this option if the underlying entities do include a modifiable entity.
* `MANUAL`: No automatic update of the cached data. Updates need to be triggered manually. 

Materialized views are read-only. Like with views, the support for schema modification is limited for all entities involved in the definition of a materialized view. It is possible to have materialized views involving views and other materialized views.
