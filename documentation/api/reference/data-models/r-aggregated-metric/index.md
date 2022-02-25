# R-AggregatedMetric

Data Models used to provide informations about one specific [Aggregated Metric](/api/concepts/statistics.md#aggregated-metrics) computed for a [Statistic](/api/concepts/statistics.md) on *R*.
These models are generically indicated as `R-AggregatedMetris`, where *R* indicates the [specific type of Resources](/api/reference/resources/device-related/index.md) for which the [Statistic](/api/concepts/statistics.md) is requested.

These Data Models are used:

- **on the input side**: Never
- **on the output side**
    - [**when accessing Statistics**]:(/api/endpoints/statistics/index.md): to provide the values computed for one specific Aggregated Metric among those requested.

For each [specific Resource type *R*](/api/reference/resources/device-related/index.md), the related `R-AggregatedMetric` is as it follows, where the dependency on *R* is for the Type associated to the `"shares"` field.

Name        |Type      | Description
------------|----------|------------
absolute | `Number` | The absolute value for the aggregated metric.
shares | [`R-Shares`](/api/reference/data-modelsata-models/r-shares/index.md) | Values of the [Metric Shares](/api/concepts/statistics.md#metric-shares-of-an-r-segment)


```json
{
    "absolute" : 10,
    "shares": {
        "overall": {
            "global": 0.001,
            "selection": 0.056
        },
        "space": {
            "inside": {
                "global": 0.001,
                "selection": 0.056
            }
        }
    }
}
```

According to the [specific Resource type *R*](/api/reference/resources/device-related/index.md), the following `R-AggregatedMetric` Data Models are defined:

* [`DetectedPosition-AggregatedMetric`](api/data-models/r-aggregated-metric/detected-position.md)
* [`Activity-AggregatedMetric`](api/data-models/r-aggregated-metrics/activity.md)
* [`Visit-AggregatedMetric`](api/data-models/r-aggregated-metrics/visit.md)
* [`Travel-AggregatedMetric`](api/data-models/r-aggregated-metrics/travel.md)
* [`HomeLocation-AggregatedMetric`](api/data-models/r-aggregated-metrics/home-location.md)
* [`WorkLocation-AggregatedMetric`](api/data-models/r-aggregated-metrics/work-location.md)
* [`LivingArea-AggregatedMetric`](api/data-models/r-aggregated-metrics/living-area.md)
* [`Flight-AggregatedMetric`](api/data-models/r-aggregated-metrics/flight.md)
