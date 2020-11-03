# R-RequestedMetrics

Data Models used to indicate one or more [Aggregated Metrics](/api/concepts/statistics.md#aggregated-metrics) of interest among those defined by the [Statistic](/api/concepts/statistics.md) on *R*.
These models are generically indicated as `R-RequestedMetrics`, where *R* indicates the specific [Class of Resources](/api/resources/device-related/index.md) which the Statistic refers to.

For each specific Resource Class *R*, the related `R-RequestedMetrics` can be easily derived considering the set of Aggregated Metrics provided by the [related Statistic](/api/statistics/index.md).
In fact, the whole data model will have a field for each Aggregated Metric whose key is declared by the [specific Statistic](/api/statistics/index.md) and whose Type is ALWAYS `Boolean`.
Such fields indicate for each Aggregated Metric whether it must be computed or not.

These Data Models are used:

- **on the input side**:
    - [**when accessing Statistics**](/api/endpoints/statistics/index.md): to indicate whether and how to filter out Items according to the values of the Aggregated Metrics.
- **on the output side**:
    - Never

According to the [specific Resource Class *R*](/api/resources/device-related/index.md), the following `R-RequestedMetrics` Data Models are defined:

* [`DetectedPosition-RequestedMetrics`](api/data-models/r-requested-metrics/detected-position.md)
* [`Activity-RequestedMetrics`](api/data-models/r-requested-metrics/activity.md)
* [`Visit-RequestedMetrics`](api/data-models/r-requested-metrics/visit.md)
* [`Travel-RequestedMetrics`](api/data-models/r-requested-metrics/travel.md)
* [`HomeLocation-RequestedMetrics`](api/data-models/r-requested-metrics/home-location.md)
* [`WorkLocation-RequestedMetrics`](api/data-models/r-requested-metrics/work-location.md)
* [`LivingArea-RequestedMetrics`](api/data-models/r-requested-metrics/living-area.md)
* [`Flight-RequestedMetrics`](api/data-models/r-requested-metrics/flight.md)
