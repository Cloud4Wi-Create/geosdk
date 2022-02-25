# Point-Time-SelectionOperation

Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
inside | [`Time-Segment`](/api/reference/data-modelsata-models/d-segment/time.md) | ANY | 

## example Object

```json
{
    "inside" : {
        "intervals" : [
            {
                "from" : {
                    "absolute": "2017-01-01T00:00:00Z"
                },
                "to" : {
                    "absolute": "2018-01-01T00:00:00Z"
                }
            }
        ]
    }
}
```

