# R-StatisticInput

Data Models used as input body for [Statistic Endpoints](/api/endpoints/statistics/index.md).
These models are generically indicated as `R-StatisticInput`, where *R* indicates the [specific Class of Resources](/api/resources/device-related/index.md) for which the [Statistic](/api/concepts/statistics.md) is requested.

For a generic [Resource Class *R*](/api/resources/index.md), these data models are as it follows.

Name        |Type      | Description
------------|----------|------------
select | [`R-Segment`](/api/data-models/r-segment/index.md) | Indicates the [Segment of Resources *R*](/api/concepts/resource-definition.md#resource-segment) of interest through a [Selection Operation](/api/endpoints/statistics/index.md#selection-operation)
segmentBy | [`R-Segmentation`](/api/data-models/r-segmentation/index.md) | Indicates how to segment the *R* Segment indicated in `"select"` in several (sub-)Segments through a [Segmentation Operation](/api/endpoints/statistics/index.md#segmentation-operation)
compute | [`R-RequestedMetrics`](/api/data-models/r-requested-metrics/index.md)| Indicates which among the [Aggregated Metrics](/api/endpoints/statistics/index.md#aggregated-metrics) defined by this Statistic have to be computed.
filter | [`R-AggregatedMetricsCondition`](/api/data-models/r-aggregated-metrics-condition/index.md) | Indicates whether and how to filter the resulting items according to the values assumed by each Aggregated Metric.

According to the [specific Resource Class *R*](/api/resources/device-related/index.md), the following `R-StatisticInput` Data Models are defined:

* [`DetectedPosition-StatisticInput`](api/data-models/r-statistic-input/detected-position.md)
* [`Activity-StatisticInput`](api/data-models/r-statistic-input/activity.md)
* [`Visit-StatisticInput`](api/data-models/r-statistic-input/visit.md)
* [`Travel-StatisticInput`](api/data-models/r-statistic-input/travel.md)
* [`HomeLocation-StatisticInput`](api/data-models/r-statistic-input/home-location.md)
* [`WorkLocation-StatisticInput`](api/data-models/r-statistic-input/work-location.md)
* [`LivingArea-StatisticInput`](api/data-models/r-statistic-input/living-area.md)
* [`Flight-StatisticInput`](api/data-models/r-statistic-input/flight.md)
