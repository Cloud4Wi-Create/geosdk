# Time

The *Time* *Dimension* refers to time.
A *Time-Segment* can indicate ANY possible period of time, including ANY set of disjoint time periods.

 - **Resource CLasses**: [*Deteceted Position*](/api/resources/platform-created/device-related/detected-position.md), [*Activity*](/api/resources/platform-created/device-related/activity.md), [*Visit*](/api/resources/platform-created/device-related/visit.md), [*Travel*](/api/resources/platform-created/device-related/travel.md), [*Flight*](/api/resources/platform-created/device-related/flight.md), [*Triggerlog*](/api/resources/platform-created/triggerlog.md)
 - **Segment Data Model**: [`Time-Segment`](/api/data-models/d-segment/time.md)
 - **Segment/Segmentation Key**: `"time"`
 - **Segmentation Data Model**: [`Time-Segmentation`](/api/data-models/d-segmentation/time.md)

## Segmentation Criteria

The following segmentation criteria are defined.

### Continuous Interval

Allows to segment a *Time* Segment in several continuous sub-intervals of costant length according to the indicated granularity.

#### Resulting Segments

Resulting Segments are indicated on the output side through a [`Time-Segment`](/api/data-models/d-segment/time.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
intervals  | [`[ContinuousTimeInterval]`](/api/data-models/d-segment/time.md#continuous-time-interval) | Will contain only one element indicating the time interval which the Segment refers to. The time interval is indicated through the absolute values of the start and end time and date.

```json
{
    "intervals": [{
        "from": {"absolute": "2017-01-01T00:00:00Z"},
        "to": {"absolute": "2017-02-01T00:00:00Z"}
    }]
}
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`Time-Segmentation`](/api/data-models/d-segmentation/time.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
continuousInterval  | [`ContinuousInterval-Granularity`](/api/data-models/d-segmentation/time.md#continuous-interval-granularity) | N.A.


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
Expressed through a [`ContinuousInterval-Granularity`](/api/data-models/d-segmentation/time.md#continuous-interval-granularity) object which indicates the measurement unit and the number of units, e.g. `5` `"days"`. 

The allowed values for the measurement unit are:

- `"hour"`
- `"day"`
- `"week"`
- `"month"`

### Periodic Interval

Allows to segment a *Time* Segment in several periodic sub-intervals with a costant period length according to the indicated granularity (e.g., hourly, daily, etc.).

#### Resulting Segments

Resulting Segments are indicated on the output side through a [`Time-Segment`](/api/data-models/d-segment/time) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
periodicity  | [`PeriodicTimeInterval`](/api/data-models/d-segment/time.md#periodic-time-interval) | Indicates the specific periodic interval which the Segment refers to. Depending on the chosen granularity, only one field of the [`PeriodicTimeInterval`](/api/data-models/d-segment/time.md#periodic-time-interval) object.

```json
{
    "periodicity": {
        "dayOfTheWeek": ["MONDAY"]
}
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`Time-Segmentation`](/api/data-models/d-segmentation/time.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
periodicInterval  | [`PeriodicInterval-Granularity`](/api/data-models/d-segmentation/time.md#periodic-interval-granularity) | N.A.

```json
{
    "periodicInterval": {
        "periodicity": "hourly"
    }
}
```

#### Granularity

Indicates the duration of each periodic time interval.
Expressed as a [`PeriodicInterval-Granularity`](/api/data-models/d-segmentation/time.md#periodic-interval-granularity) object which indicates the time offset to be considered and the periodicity.

The allowed values for the periodicity are:

- `"hourly"`: considers each hour of the day according to the indicated offset. Resulting Segments will be indicated through the field `"hoursOfTheDay"` which will contain only one element indicating the specific hour of the day which the Segment refers to.
- `"periodOfTheDay"`: considers each period of the day (i.e., morning, afternoon, etc.) according to the indicated offset. Resulting Segments will be indicated through the field `"hoursOfTheDay"` which will contain the elements indicating the specific hours of the day which the Segment refers to. The periods of the day are:
    - **night**: corresponds to the time interval [00:00, 06:00) 
    - **morning**: corresponds to the time interval [06:00, 12:00) 
    - **afternoon**: corresponds to the time interval [12:00, 18:00) 
    - **evening**: corresponds to the time interval [18:00, 24:00)
- `"daily"`: considers each day of the week (i.e., Monday, Tuesday, etc.) according to the indicated offset. Resulting Segments will be indicated through the field `"daysOfTheWeek"` which will contain only one element indicating the specific day of the week which the Segment refer to.
- `"montly"`: considers each month of the year (i.e., January, February, etc.) according to the indicated offset. Resulting Segments will be indicated through the field `"monthOfTheYear"` which will contain only one element indicating the specific month of the year which the Segment refer to.

