## TimeIntervalDuration

Indicates the duration of a time interval

Name        |Type      | Allowed Values
------------|----------|--------------
unit | `String` |  ANY value in {`"hour"`, `"day"`, `"week"`, `"month"`}   | The measurement unit for the duration of the time interval
count | `Number` |  ANY integer number > 0 | The durartion of the time interval expressed as number of time units (as inidicated in `"unit"`)

```json
{
    "count" : 3,
    "unit" : "days"
}
```