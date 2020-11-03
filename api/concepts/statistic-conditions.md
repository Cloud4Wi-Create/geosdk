# Statistic Conditions

A **Statistic Condition** is a condition that refers to the value assumed by one or more [Aggregated Metrics of a Statistic](/api/concepts/statistics.md#aggregated-metrics).
Since an Aggregated Metric is always a numeric value, such conditions are expressed as comparison condition between the value assumed by the Aggregated Metric and a known term.

As an example, let us consider the Statistic on *Visits* and its Aggregated Metric *total duration*.
A comparison condition might be *total duration* higher than *1 hour*.

More in detail, an Aggregated Metrics Condition is expressed by indicating:

1. The specific Resource Class *R* of interest.
2. The [*R* Segment](/api/concepts/resource-definition.md#resource-segment) for which the Statistic (and thus the Aggregated Metric(s)) has to be computed. This is expressed by indicating a set of [Selection Conditions](/api/concepts/resource-selection.md).
3. One or more Aggregated Metrics of interest among those provided by the specific Statistic and, for each of them, a comparison condition

As an example, a Statistic Condition might be: "The number (*count*) of *Visits* performed by Device *D* to area *A* during period *T* is higher than *X*".
Such a Statistic Condition indicates:

* **The Resource Class of interest**: *Visit*
* **The** ***Visit*** **Segment through a set of [Selection Conditions](/api/concepts/resource-selection.md)**
    * **specific** ***Space*** **Segment**: the area *A*
    * **specific** ***Time*** **Segment**: the period *T*
    * **specific** ***Device Base*** **Segment**: the Device *D*
* **The Agrregated Metric of interset**: *count*
* **The known term**: *X*

Such a Condition is said **Targeted** as it indicates a specific *Device Base* Segment of interest, which is said **Target**.

On the contrary, an **Untargeted Statistic Condition** is a Statistic Condition that does not indicate any specific *Device Base* Segment as Target.

<a name="boolean-expression"></a>
## Untargeted Boolean Expression
This API allows to indicate Boolean expressions by combining any set of Untargeted Statistic Conditions with the Boolean operators **AND** and **OR**.

**Untargeted Boolean Expression** can be used for two main purposes:

1. Obtain the set of *Devices* that match the specific Boolean Expression. E.g., "who lives in area *A1* AND has visited area *A2* more than *X* times during last month?".
2. Define a complex event that has to be monitored for a specific Target. E.g., "for *Device* *D1*: monitor when it performs a *Visit* to area *A* AND then a *Visit* to its *Home Location* for at least *T* time"

