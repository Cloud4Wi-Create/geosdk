# Point-Time-Segmentation

Name        |Type      
------------|----------
inside | [`Time-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/time.md) | Indicates that a Segmentation has to be performed with respect to the [*inside* Selection Condition] on the *Time* Dimension.

```json
{
    "inside" : {
        "continuousInterval" : {
            "count" : 3,
            "unit" : "days"
        },
        "periodicInterval" : {
        	"offset": 5,
        	"periodicity": "daily"
        }
    }
}
```

