# Statistic Endpoints

Set of endpoints that allow to obtain (READ) [Statistics](/api/concepts/statistcs.md) on [Platform-created](/api/resources/platform-created/index.md) Resources.
These endpoints allow to perform flexible [selections](/api/concepts/statistics.md#selection-operation) and [segmentations](/api/concepts/statistics.md#segmentation-operation) on the whole set of resources of a given class.
To this end, they all use the HTTP `POST` method. The request body will carry an [`R-StatisticInput`](/api/data-models/r-statistic-input/index.md) to indicates the desired selection and segmentation, as well as the desired [Aggregated Metrics](/api/concepts/statistics.md#aggregated-metrics).

According to the specific Resource Class R, the following endpoints are provided:


* [`DetectedPosition`](api/endpoints/statistics/detected-position.md)
* [`Activity`](api/endpoints/statistics/activity.md)
* [`Visit`](api/endpoints/statistics/visit.md)
* [`Travel`](api/endpoints/statistics/travel.md)
* [`HomeLocation`](api/endpoints/statistics/home-location.md)
* [`WorkLocation`](api/endpoints/statistics/work-location.md)


 


