# R-AggregatedMetricsCondition

Data Models used to express a condition on one or more [Aggregated Metrics](/api/concepts/statistics.md#aggregated-metrics) of a [Statistic](/api/concepts/statistics.md) on *R*.
These models are generically indicated as `R-AggregatedMetricsCondition` where *R* indicates the specific [type of Resources](/api/reference/resources/device-related/index.md) which the Statistic refers to.

For each [specific Resource type *R*](/api/reference/resources/device-related/index.md), the related `R-AggregatedMetricsCondition` can be easily derived considering the set of Aggregated Metrics provided by the [related Statistic](/api/statistics/index.md).
In fact, the whole data model will have a field for each Aggregated Metric whose key is declared by the [specific Statistic](/api/statistics/index.md) and whose Type is ALWAYS [`ComparisonCondition`](/api/reference/data-modelsata-models/common/comparison-condition.md).

These Data Models are used:

- **on the input side**:
    - [**when accessing Statistics**](/api/reference/endpoints/endpoints/statistics/index.md): to indicate whether and how to filter out Items according to the values of the Aggregated Metrics.
    - [**when creating Triggers**](/api/reference/endpoints/resources/user-created/triggers/index.md): to indicate a [Condition to be monitored](/api/concepts/triggers.md).
- **on the output side**:
    - Never

According to the specific Resource type *R*, the following `R-AggregatedMetricsCondition` Data Models are defined:

* [`DetectedPosition-AggregatedMetricsCondition`](api/data-models/r-aggregated-metrics-condition/detected-position.md)
* [`Activity-AggregatedMetricsCondition`](api/data-models/r-aggregated-metrics-condition/activity.md)
* [`Visit-AggregatedMetricsCondition`](api/data-models/r-aggregated-metrics-condition/visit.md)
* [`Travel-AggregatedMetricsCondition`](api/data-models/r-aggregated-metrics-condition/travel.md)
* [`HomeLocation-AggregatedMetricsCondition`](api/data-models/r-aggregated-metrics-condition/home-location.md)
* [`WorkLocation-AggregatedMetricsCondition`](api/data-models/r-aggregated-metrics-condition/work-location.md)
* [`LivingArea-AggregatedMetricsCondition`](api/data-models/r-aggregated-metrics-condition/living-area.md)
* [`Flight-AggregatedMetricsCondition`](api/data-models/r-aggregated-metrics-condition/flight.md)
