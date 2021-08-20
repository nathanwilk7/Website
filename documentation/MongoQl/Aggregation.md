---
layout: plain
title: Aggregation Pipeline
---

The aggregation command, with its aggregation pipeline, is an extremely powerful tool that allows to easily construct complex queries.

## Example

```
db.secrets.aggregate([
    {
        "$match": {
            "example": 15
        }
    }, 
    {
        "$project": {
            "other": 1
        }
    }
])
```

This example aggregation query, first filters all records from the collection named "secrets" where the field "example" is equal to 15.
In a second step, it applies a projection on the field named "other", which as a consequence, is the only field shown in the result.

This query is equivalent to the following SQL query:

```
SELECT "other"
FROM "secrets"
WHERE "example" = 15
```

## Stages
The MongoDB Query Language supports different possible pipeline stages. In the following, we describe all stages supported by Polypheny.

### ```$addFields```

Adds a new field to an existing record.

### ```$count```

Counts the number of records from the previous stage.

### ```$group```

Groups the record by a needed ```_id``` field, and additionally allows specifying other aggregations.

### ```$limit```

Limits the retrieved records to the given amount of records.

### ```$match```

Filters the previous stage with the provided condition.

### ```$project```

Allows to apply an inclusive or exclusive projection to the records.

### ```$replaceRoot```

This is an alias for ```$replaceWith``` that allows to replace a document with one of its subfields.

Attention: This stage is only possible when querying a document schema.

### ```$set```

This is an alias for ```$addFields```, which allows adding additional entries to an existing record during retrieval.

### ```$skip```

Skips the specified amount of records.

### ```$sort```

Allows sorting by the given entities.

### ```$unset```

Thi is an alias for multiple exclusive projections.

### ```$unwind```

Allows to deconstruct an array into multiple records for each entry.

Attention: This stage is only possible when querying a document schema.
