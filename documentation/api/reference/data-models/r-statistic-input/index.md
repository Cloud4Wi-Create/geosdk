# R-StatisticInput

Data Models used as input body for [Statistic Endpoints](/api/reference/endpoints/endpoints/statistics/index.md).
These models are generically indicated as `R-StatisticInput`, where *R* indicates the [specific type of Resources](/api/reference/resources/device-related/index.md) for which the [Statistic](/api/concepts/statistics.md) is requested.

For a generic [Resource type *R*](/api/reference/resources/resources/index.md), these data models are as it follows.

Name        |Type      | Description
------------|----------|------------
select | [`R-Segment`](/api/reference/data-modelsata-models/r-segment/index.md) | Indicates the [Segment of Resources *R*](/api/concepts/resource-definition.md#resource-segment) of interest through a [Selection Operation](/api/reference/endpoints/endpoints/statistics/index.md#selection-operation)
segmentBy | [`R-Segmentation`](/api/reference/data-modelsata-models/r-segmentation/index.md) | Indicates how to segment the *R* Segment indicated in `"select"` in several (sub-)Segments through a [Segmentation Operation](/api/reference/endpoints/endpoints/statistics/index.md#segmentation-operation)
compute | [`R-RequestedMetrics`](/api/reference/data-modelsata-models/r-requested-metrics/index.md)| Indicates which among the [Aggregated Metrics](/api/reference/endpoints/endpoints/statistics/index.md#aggregated-metrics) defined by this Statistic have to be computed.
filter | [`R-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/index.md) | Indicates whether and how to filter the resulting items according to the values assumed by each Aggregated Metric.

According to the [specific Resource type *R*](/api/reference/resources/device-related/index.md), the following `R-StatisticInput` Data Models are defined:

* [`DetectedPosition-StatisticInput`](api/data-models/r-statistic-input/detected-position.md)
* [`Activity-StatisticInput`](api/data-models/r-statistic-input/activity.md)
* [`Visit-StatisticInput`](api/data-models/r-statistic-input/visit.md)
* [`Travel-StatisticInput`](api/data-models/r-statistic-input/travel.md)
* [`HomeLocation-StatisticInput`](api/data-models/r-statistic-input/home-location.md)
* [`WorkLocation-StatisticInput`](api/data-models/r-statistic-input/work-location.md)
* [`LivingArea-StatisticInput`](api/data-models/r-statistic-input/living-area.md)
* [`Flight-StatisticInput`](api/data-models/r-statistic-input/flight.md)
