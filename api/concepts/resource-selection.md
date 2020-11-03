<a name="resource-selection"></a>
# Resource Selection and Selection Conditions

The term **Resource Selection** refers to the action of selecting a set of Resources of a specific Class *R* according to the values of their attributes.

**A Selection Operation on** ***R*** **identifies an** ***R*** **Segment**; i.e., a sub-set of all the possible Resources of Class *R*.

Resources can be selected according to several **Selection Conditions**.
This API defines two types of Selection Conditions.

- [Dimensional Selection Conditions](#dimensional-selection-condition): allow to select resources according to the value they assume on the [Dimensions](/api/concepts/resource-definition.md#dimensions).
- [Metric Selection Conditions](#metric-selection-condition): allow to select resources according to the value assumed by their [Metrics](/api/concepts/resource-definition.md#resources).

The whole Selection Operation, and thus the *R* Segment, is then identified by the set of indicated Dimensional Selection Conditions and Metric Selection Conditions.

> If no Selection Condition is indicated for a given Metric *M* or Dimension *D*, then Resources will be selected regardless of the value they assume for *M* and *D*.

<a name="dimensional-selection-condition"></a>
## Dimensional Selection Conditions

A **Dimensional Selection Condition** allows to select Resources of a given Class *R* according to the "value" they assume on a specific Dimension *D*.

A Dimensional Selection Condition always relates to a specific Dimension *D* and is expressed through a **Dimensional Selection Operator** and a [*D* Segment](/api/concepts/resource-definition.md#dimension-segment).
As an example, if you want to select all the *Activities* that started in a given time period, you have to indicate for the *Time* dimension the operator *start* and a *Time* Segment indicating the period of interest.
On the contrary, if you are interested in all the *Activities* that were in Progress in a given period of time, you have to use the operator *intersect* instead of *start*.

The pair Operator-Dimension, indicated as *OP*-*D*, identifies the actual Attribute we are interested in: e.g., Visits that *start* in a given *Time* period.

> If no Selection Condition is indicated for a given Selection Operator *OP* and Dimension *D*, then Resources will be selected regardless of the value they assume for the specific Attribute indicated by the pair *OP*-*D*.

Depending on the set of Dimensions on which a given Class *R* is defined, as well as the specific [Geometry *G* assumed by *R* on *D*](/api/concepts/resource-definition.md#geometries), different Dimensional Selection Conditions are possible; e.g., *Space*: *start* in *Space-Segment1*, *end* in *Space-Segment2*; *Time*: *intersect*  *Time-Segment1*, *end* in *Time-Segment2*

The set of Dimensional Selection Operators defined for each Geometry is listed [here](/api/geometries-and-operators.md#operators).

Given a Geometry *G* and a Dimension *D*, the set of allowed Dimensional Selection Conditions can be expressed through a common Data Models that depends on *D* and *G*.
Such Data Models are generically indicated as [`G-D-SelectionOperation`](/api/data-models/g-d-selection-operation/index.md)


<a name="metric-selection-condition"></a>
## Metric Selection Condition

A **Metric Selection Condition** allows to select Resources of a given Class *R* according to the value they assume for a specific Metric *M*.

A Metric Selection Condition is expressed though:

- The name of the Metric of interest *M*
- A **Comparison Condition**, which is always expressed through the same Data Model [`ComparisonCondition`](/api/data-models/comparison-condition.md).

> If no Selection Condition is indicated for a given Metric *M*, then Resources will be selected regardless of the value they assume for *M*.
