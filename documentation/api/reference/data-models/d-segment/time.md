# Time-Segment

Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
intervals | [`ContinuousTimeInterval`](#continuoustimeinterval) |     | Indicates one or more continuous time intervals
periodicity | [`PeriodicTimeInterval`](#periodictimeinterval) |     | Indicates a periodic interval



```json
{
    "intervals" : [
        {
            "from" : {
                "absolute": "2016-01-01T00:00:00Z"
            },
            "to" : {
                "absolute": "2016-01-01T00:00:00Z"
            }
        }
    ],
    "periodicity" : {
    	"periodDuration": {
    	    "unit": "day",
    	    "count": 1
    	},
    	"subIntervals":[{
    	    "start": 10,
    	    "end": 16,
    	    "unit": "hour"
    	}]
    }
}
```

## ContinuousTimeInterval

Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
from | `JSON` |     | Indicates the start instant of the interval
from.absolute | [`Date`](/api/reference/data-models/common/date) |     | Indicates the absolute start instant as an ISO date
from.relative | `Integer` |     | Indicates the start instant as amount of time (in seconds) after (if positive) or before (if negative) the time instant in which a condition is evaluated
to | `JSON` |     | Indicates the end instant of the interval
to.absolute | [`Date`](/api/reference/data-models/common/date) |     | Indicates the absolute end instant as an ISO date
to.relative | `Integer` |     | Indicates the end instant as amount of time (in seconds) after (if positive) or before (if negative) the time instant in which a condition is evaluated


```json
{
    "from" : {
        "absolute": "2016-01-01T00:00:00Z"
    },
    "to" : {
        "absolute": "2016-01-01T00:00:00Z"
    }
}
```

```json
{
    "from" : {
        "relative": -86400
    },
    "to" : {
        "relative": 0
    }
}
```


## PeriodicTimeInterval

Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
periodDuration | [`TimeIntervalDuration`](/api/reference/data-modelsata-models/common/time-interval-duration.md) | ANY valid  `TimeIntervalDuration`  | Indicates the duration of the period
subIntervals | `[JSON]` |    | Indicates one or more sub-intervals inside the period. Each sub-interval is indicated as start and end offset with respect to the period
subIntervals.[].unit | `String` |  ANY value in {`"hour"`, `"day"`, `"week"`, `"month"`}   | The measurement unit for the offsets of the sub-interval
subIntervals.[].start | `Number` |  ANY integer number > 0 | The start offset (with respect to the period) of this sub-interval, expressed as number of time units (as inidicated in `"subIntervals.[].unit`)
subIntervals.[].end | `Number` |  ANY integer number > `subIntervals.[].start`   | The end offset (with respect to the period) of this sub-interval, expressed as number of time units (as inidicated in `"subIntervals.[].unit`)

```json
 {
    "periodDuration": {
        "unit": "day",
        "count": 1
    },
    "subIntervals":[{
        "start": 10,
        "end": 16,
        "unit": "hour"
    }]
}
```
