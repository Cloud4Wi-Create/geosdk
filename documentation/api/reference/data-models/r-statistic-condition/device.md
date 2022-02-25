## DetectedPosition-StatisticCondition

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
select    | [`Device-Segment`](/api/reference/data-modelsata-models/r-segment/device.md) | Optional | Any valid `Device-Segment` object **without the field `"deviceBase"`**. `null` and empty Object allowed | Indicates the  [Segment of *Device*](/api/concepts/resource-definition.md#resource-segment) on which the Aggregated Metrics Condition must be evaluated.
evaluate    | [`Device-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/device.md)| Mandatory | Any valid `DetectedPosition-AggregatedMetricsCondition` object | Indicates the algebraic condition(s) that have to be evaluated (for one or more Aggregated Metrics) for the Condition to hold true.

```json
```

