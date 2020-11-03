# R-StatisticOutput

Data Models used for each [Item](/api/general-aspects/pagination.md) of the output body of [Statistic Endpoints](/api/endpoints/statistics/index.md).
These models are generically indicated as `R-StatisticOutput`, where *R* indicates the [specific Class of Resources](/api/resources/device-related/index.md) for which the [Statistic](/api/concepts/statistics.md) is requested.

For a generic [Resource Class *R*](/api/resources/index.md), these data models are as it follows.

Name        |Type      | Description
------------|----------|------------
segment | [`R-Segment`](/api/data-models/r-segment/index.md) | Indicates the [Segment of Resources *R*](/api/concepts/resource-definition.md#resource-segment) which the item refers to. This field is not provided if no [Segmentation Operation](/api/concepts/statistics.md#segmentation-operation) has been requested. In such a case, in fact, the *R* Segment indicated in the input body through the [`R-Segment`](/api/data-models/) object associated to the [`"select"`](/api/data-models/r-statistic-input/index.md) field represents the only *R* Segment for which the Statistic is computed.
metrics | [`R-AggregatedMetrics`](/api/data-models/r-aggregated-metrics/index.md)  | Contains the [Aggregated Metrics](/api/concepts/statistics.md#aggregated-metrics) computed for the Statistic

According to the [specific Resource Class *R*](/api/resources/device-related/index.md), the following `R-StatisticOutput` Data Models are defined:

* [`DetectedPosition-StatisticOutput`](api/data-models/r-statistic-output/detected-position.md)
* [`Activity-StatisticOutput`](api/data-models/r-statistic-output/activity.md)
* [`Visit-StatisticOutput`](api/data-models/r-statistic-output/visit.md)
* [`Travel-StatisticOutput`](api/data-models/r-statistic-output/travel.md)
* [`HomeLocation-StatisticOutput`](api/data-models/r-statistic-output/home-location.md)
* [`WorkLocation-StatisticOutput`](api/data-models/r-statistic-output/work-location.md)
* [`LivingArea-StatisticOutput`](api/data-models/r-statistic-output/living-area.md)
* [`Flight-StatisticOutput`](api/data-models/r-statistic-output/flight.md)
