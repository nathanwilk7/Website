---
layout: plain
title:  Views
description: >
How to create (materialized) views.
hide_description: true
---

This page gives an overview on creating, altering and dropping views and materialized views in Polypheny using PolySQL. 


## Views

{% highlight sql %}
createViewStatement:
    CREATE VIEW [ OR REPLACE ] name
    [ '(' tableElement [, tableElement ]* ')' ]
    [ AS query ]

dropViewStatement:
    DROP VIEW [ IF EXISTS ] name

alterStatement:
    ALTER VIEW [ schemaName . ] viewName RENAME TO newViewName
    | ALTER VIEW [ schemaName . ] viewName RENAME COLUMN columnName TO newColumnName
{% endhighlight %}

* `CREATE VIEW` creates a view of a query. Views have no data placements on a store but are references to an underlying table.
* `CREATE OR REPLACE VIEW` the only difference to the previous option is that if a view with this name already exists, it is replaced. That means the old view is dropped and a new view will be created.
* `DROP VIEW` deletes an existing view.
* `DROP VIEW IF EXISTS` deletes an existing view but checks first if the view to drop is present.
* `ALTER VIEW RENAME TO` allows changing the name of a view. 
* `ALTER VIEW RENAME COLUMN` allows changing the name of a specific column of the view.



## Materialized Views

{% highlight sql %}
createMaterializedViewStatement:
    CREATE MATERIALIZED VIEW [ IF NOT EXISTS ] name
    [ '(' tableElement [, tableElement ]* ')' ]
    [ AS query ]
    [ <ON> <STORE> storeName ( <COMMA> storeName )*]
    [FRESHNESS (INTERVAL interval timeUnit | UPDATE interval | MANUAL )  ]

dropMaterializedViewStatement:
    DROP MATERIALIZED VIEW [ IF EXISTS ] name

alterStatement:
    ALTER MATERIALIZED VIEW [ schemaName . ] viewName RENAME TO newViewName
    | ALTER MATERIALIZED VIEW [ schemaName . ] viewName RENAME COLUMN columnName TO newColumnName
    | ALTER MATERIALIZED VIEW [ schemaName . ] viewName FRESHNESS MANUAL
    | ALTER MATERIALIZED VIEW [ schemaName . ] viewName ADD [UNIQUE] INDEX indexName ON ( columnName | '(' columnName [ , columnName ]* ')' ) [ USING indexMethod ] [ ON STORE storeUniqueName ]
    | ALTER MATERIALIZED VIEW [ schemaName . ] viewName DROP INDEX indexName
{% endhighlight %}

* `CREATE MATERIALIZED VIEW` creates a materialized view of a query.
* `ON STORE` one or many stores can be selected. The data from the selected query is placed on the chosen Data Store.
* `FRESHNESS` describes how often and with which method the materialized view should be refreshed.
* `FRESHNESS INTERVAL` allows specifying after what time the materialized should be updated. For example, `FRESHNESS INTERVAL 10 "hours"` this refreshes the materialized view every 10 hours.
* `FRESHNESS UPDATE` allows specifying after how many updates to the underlying table the materialized view is updated. For example, `FRESHNESS UPDATE 2` after two updates on the underlying entities, the materialized view is automatically updated. For now, it is only possible to use this option if the underlying tables do include a modifiable table.
* `FRESHNESS MANUAL` with this type of freshness, the materialized view is not automatically updated. Every update of the data needs to be triggered manually. It is triggered with the following command: `ALTER MATERIALIZED VIEW name FRESHNESS MANUAL`
* `ALTER MATERIALIZED VIEW ADD INDEX` allows adding indices for materialized views.
* `ALTER MATERIALIZED VIEW DROP INDEX` to drop indices from materialized views.
* `DROP MATERIALIZED VIEW` deletes an existing materialized view.
* `DROP MATERIALIZED VIEW IF EXISTS` deletes an existing materialized view but checks first if the view to drop is present.
* `ALTER MATERIALIZED VIEW RENAME TO` allows changing the name of a materialized view.
* `ALTER MATERIALIZED VIEW RENAME COLUMN` allows changing the name of a specific column of the materialized view.
