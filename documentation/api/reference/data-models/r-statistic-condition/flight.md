## Flight-StatisticCondition

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
select    | [`Flight-Segment`](/api/reference/data-modelsata-models/r-segment/flight.md) | Optional | Any valid `Flight-Segment` object **without the field `"deviceBase"`**. `null` and empty Object allowed | Indicates the  [Segment of *Flights*](/api/concepts/resource-definition.md#resource-segment) on which the Aggregated Metrics Condition must be evaluated.
evaluate | [`Flight-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/flight.md)| Mandatory | Any valid `Flight-AggregatedMetricsCondition` object | Indicates the algebraic condition(s) that have to be evaluated (for one or more Aggregated Metrics) for the Condition to hold true.

```json
```

