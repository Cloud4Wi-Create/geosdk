# Time-Segmentation

Name        |Type      | Allowed Values | Description
------------|----------|--------------|-----------
continuousInterval | [`TimeIntervalDuration`](../common/time-interval-duration.md) | ANY valid `TimeIntervalDuration` | If provided, inidcates to use the ["ContinuousInterval"](/api/reference/dimensionsdimensions/time.md#continuous-interval) segmentation criterion
periodicInterval | [`PeriodicIntervalGranularity`](#periodicintervalgranularity) | ANY valid `PeriodicIntervalGranularity` | If provided, inidcates to use the ["PeriodicInterval"](/api/reference/dimensionsdimensions/time.md#periodic-interval) segmentation criterion

```json
{
    // Only one between "continuousInterval" and "periodicInterval" is allowed
    "continuousInterval" : {
        "count" : 3,
        "unit" : "day"
    },
    "periodicInterval" : {
        "periodDuration": {
            "count" : 1,
            "unit" : "day"
        },
        "segmentDuration": {
            "count" : 1,
            "unit" : "hour"
        }
    }
}
```

## PeriodicIntervalGranularity

Name        |Type      | Allowed Values | Description
------------|----------|-------------- | -------------
periodDuration | [`TimeIntervalDuration`](/api/reference/data-modelsata-models/common/time-interval-duration.md) | ANY valid `TimeIntervalDuration` | Inidcates the duration of the period 
segmentDuration | [`TimeIntervalDuration`](/api/reference/data-modelsata-models/common/time-interval-duration.md) |ANY valid `TimeIntervalDuration` | Inidcates the duration of each sub-segment inside the period 

> `PeriodicIntervalGranularity` Object indicating intervals of 1 hour with a periodicity of 1 day, resulting in 24 different segments (one for each "hour of the day")

```json
{
    "periodDuration": {
        "count" : 1,
        "unit" : "day"
    },
    "segmentDuration": {
        "count" : 1,
        "unit" : "hour"
    }
}
```

> `PeriodicIntervalGranularity` Object indicating intervals of 1 day with a periodicity of 1 week, resulting in 7 different segments (one for each "day of the week")

```json
{
    "periodDuration": {
        "count" : 1,
        "unit" : "week"
    },
    "segmentDuration": {
        "count" : 1,
        "unit" : "day"
    }
}
```

> `PeriodicIntervalGranularity` Object indicating intervals of 1 dhouray with a periodicity of 1 week, resulting in 24*70168 different segments (one for each "hour of the week")

```json
{
    "periodDuration": {
        "count" : 1,
        "unit" : "week"
    },
    "segmentDuration": {
        "count" : 1,
        "unit" : "hour"
    }
}
```

