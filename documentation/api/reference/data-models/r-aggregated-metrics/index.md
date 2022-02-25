# R-AggregatedMetrics

Data Models used to provide informations about the [Aggregated Metrics](/api/concepts/statistics.md#aggregated-metrics) computed for a [Statistic](/api/concepts/statistics.md) on *R*.
These models are generically indicated as `R-AggregatedMetrics`, where *R* indicates the [specific type of Resources](/api/reference/resources/device-related/index.md) for which the [Statistic](/api/concepts/statistics.md) is requested.

These Data Models are used:

- **on the input side**: Never
- **on the output side**
    - [**when accessing Statistics**]:(/api/endpoints/statistics/index.md): to provide the values computed for the Aggregated Metrics that have been requested.


For each [specific Resource type *R*](/api/reference/resources/device-related/index.md), the related `R-AggregatedMetrics` can be easily derived considering the set of Aggregated Metrics provided by the [related Statistic](/api/statistics/index.md).
In fact, the whole data model will have a field for each Aggregated Metric whose key is declared by the [specific Statistic](/api/statistics/index.md) and whose Type is [`R-AggregatedMetric`](/api/reference/data-modelsata-models/r-aggregated-metric/index.md).
Each of this field contains information about one single Aggregated Metric and is provided only if the specific Aggregated Metric *M* has been requested through the [`R-RequestedMetrics`](/api/reference/data-modelsata-models/r-requested-metrics/index.md) associated to the field [`"compute"` of the `R-StatisticInput`](/api/reference/data-models/r-statisti-input/index.md) Object.

As an example, for a Resource type *R* whose Statistic defines the Aggregated Metrics *metric1* and *metric2*, the related `R-AggregatedMetrics` is as it follows.

Name        |Type      | Description
------------|----------|------------
count | [`R-AggregatedMetric`]() | Contains values for the *count* metric.
metric1 | [`R-AggregatedMetric`]() | Contains values for the *metric1* metric.
metric2 | [`R-AggregatedMetric`]() | Contains values for the *metric2* metric.


According to the [specific Resource type *R*](/api/reference/resources/device-related/index.md), the following `R-AggregatedMetrics` Data Models are defined:

* [`DetectedPosition-AggregatedMetrics`](api/data-models/r-aggregated-metrics/detected-position.md)
* [`Activity-AggregatedMetrics`](api/data-models/r-aggregated-metrics/activity.md)
* [`Visit-AggregatedMetrics`](api/data-models/r-aggregated-metrics/visit.md)
* [`Travel-AggregatedMetrics`](api/data-models/r-aggregated-metrics/travel.md)
* [`HomeLocation-AggregatedMetrics`](api/data-models/r-aggregated-metrics/home-location.md)
* [`WorkLocation-AggregatedMetrics`](api/data-models/r-aggregated-metrics/work-location.md)
* [`LivingArea-AggregatedMetrics`](api/data-models/r-aggregated-metrics/living-area.md)
* [`Flight-AggregatedMetrics`](api/data-models/r-aggregated-metrics/flight.md)
