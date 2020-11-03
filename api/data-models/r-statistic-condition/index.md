# R-StatisticCondition

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
select    | [`R-Segment`]() | Optional | Any valid `R-Segment` object **without the field `"deviceBase"`**. `null` and empty Object allowed | Indicates the  [Segment of Resources *R* ]() on which the Aggregated Metrics Condition must be evaluated. [The *R* Segment] cannot idicate any *Device Base* Selection. This is because the *Registered Device(s)* on which the Condition must be evaluated is expressed through the field `"target"` of the [`Trigger`]() object. If not provided, or `null`, or an empty Object, it indicates all the *R* Resources.
evaluate    | [`R-AggregatedMetricsCondition`]()| Mandatory | Any valid `R-AggregatedMetricsCondition` object | Indicates the algebraic condition(s) that have to be evaluated (for one or more Aggregated Metrics) for the Condition to hold true.

