* [Documentation Home](../../../README.md)  
  * [Web API](../../index.md)  
    * [Reference](../index.md)
        * [Dimensions](index.md)

# Time

The *Time* *Dimension* refers to time.
A *Time-Segment* can indicate ANY possible period of time, including ANY set of disjoint time periods.

 - **Segment Data Model**: [`Time-Segment`](../data-models/d-segment/time.md)
 - **Segmentation Data Model**: [`Time-Segmentation`](../data-models/d-segmentation/time.md)

## Segmentation Criteria

The following segmentation criteria are defined.

### Continuous Interval

Allows to segment a *Time* Segment in several continuous sub-intervals of costant length according to the indicated granularity.

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`Time-Segmentation`](../data-models/d-segmentation/time.md) object formatted as in the following:

Name    | Type | Allowed Values
--------|----- |--------------
continuousInterval  | [`TimeIntervalDuration`](../data-models/common/time-interval-duration.md) | N.A.


```json
{
    "continuousInterval": {
        "unit": "days",
        "count": 5
    }
}
```

#### Granularity

Indicates the duration of each continuous time interval.
Expressed through a 
[`TimeIntervalDuration`](../data-models/common/time-interval-duration.md) object 
which indicates the measurement unit and the number of units, e.g. `5` `"days"`. 

The allowed values for the measurement unit are:

- `"hour"`
- `"day"`
- `"week"`
- `"month"`

#### Resulting Segments

Resulting Segments are indicated on the output side through a 
[`Time-Segment`](../data-models/d-segment/time.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
intervals  | [`[ContinuousTimeInterval]`](../data-models/d-segment/time.md#continuoustimeinterval) | Will contain only one element indicating the time interval which the Segment refers to. The time interval is indicated through the absolute values of the start and end time and date.

```json
{
    "intervals": [{
        "from": {"absolute": "2017-01-01T00:00:00Z"},
        "to": {"absolute": "2017-02-01T00:00:00Z"}
    }]
}
```

### Periodic Interval

Allows to segment a *Time* Segment in several periodic sub-intervals with a costant period length according to the indicated granularity (e.g., hourly, daily, etc.).

#### Mapping on the Segmentation object

This Criterion can be indicated using a 
[`Time-Segmentation`](../data-models/d-segmentation/time.md) object 
formatted as in the following:

Name    | Type | Allowed Values
--------|----- |--------------
periodicInterval  | [`PeriodicInterval-Granularity`](../data-models/d-segmentation/time.md#periodicintervalgranularity) | N.A.

```json
{
    "periodicInterval": {
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

#### Granularity

Indicates the duration of each periodic time interval.
Expressed as a 
[`PeriodicInterval-Granularity`](../data-models/d-segmentation/time.md#periodicintervalgranularity) 
object which indicates the time offset to be considered and the periodicity.

The allowed values for the periodicity are:

- `"hourly"`: considers each hour of the day according to the indicated offset. Resulting Segments will be indicated through the field `"hoursOfTheDay"` which will contain only one element indicating the specific hour of the day which the Segment refers to.
- `"periodOfTheDay"`: considers each period of the day (i.e., morning, afternoon, etc.) according to the indicated offset. Resulting Segments will be indicated through the field `"hoursOfTheDay"` which will contain the elements indicating the specific hours of the day which the Segment refers to. The periods of the day are:
    - **night**: corresponds to the time interval [00:00, 06:00) 
    - **morning**: corresponds to the time interval [06:00, 12:00) 
    - **afternoon**: corresponds to the time interval [12:00, 18:00) 
    - **evening**: corresponds to the time interval [18:00, 24:00)
- `"daily"`: considers each day of the week (i.e., Monday, Tuesday, etc.) according to the indicated offset. Resulting Segments will be indicated through the field `"daysOfTheWeek"` which will contain only one element indicating the specific day of the week which the Segment refer to.
- `"montly"`: considers each month of the year (i.e., January, February, etc.) according to the indicated offset. Resulting Segments will be indicated through the field `"monthOfTheYear"` which will contain only one element indicating the specific month of the year which the Segment refer to.

#### Resulting Segments

Resulting Segments are indicated on the output side through a 
[`Time-Segment`](../data-models/d-segment/time.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
periodicity  | [`PeriodicTimeInterval`](../data-models/d-segment/time.md#periodictimeinterval) | Indicates the specific periodic interval which the Segment refers to. Depending on the chosen granularity, only one field of the [`PeriodicTimeInterval`](../data-models/d-segment/time.md#periodictimeinterval) object.

```json
{
    "periodicity":  {
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
