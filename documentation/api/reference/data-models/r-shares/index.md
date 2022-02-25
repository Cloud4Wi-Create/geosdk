# R-Shares

Data Models used to provide the [Metric Shares](/api/concepts/statistics.md#metric-shares-of-an-r-segment) for a single [Aggregated Metric](/api/concepts/statistics.md#aggregated-metrics) computed for a [Statistic](/api/concepts/statistics.md) on *R*.

These Data Models are used:

- **on the input side**: Never
- **on the output side**
    - [**when accessing Statistics**](/api/reference/endpoints/endpoints/statistics/index.md): to provide the [Metric Shares](/api/concepts/statistics.md#metric-shares-of-an-r-segment) computed for one specific Aggregated Metric among those requested.


Any `R-Shares` object has the following common fields, regardless of the specific *R* for which the Statistic is computed.

Name        |Type      | Description
------------|----------|------------
overall | [`GlobalAndSelection-Shares`](/api/reference/data-models/common/overall-and-selection-shares.md) | Values of the [Overall-Global and Overal-Selection Metric Shares](/api/concepts/statistics.md#metric-shares-of-an-r-segment) for the specific Aggregated Metric

The other fields of a generic `R-Shares` model can be derived considering which Geometry *G* the specific Resource type *R* assumes on each Dimension *D*, indicated as *G-D*. e.g.: *Point-Space*, *Interval-Time*, etc.
In detail, an `R-Shares` contains a field for each Dimension whose key is specified by the specific [Dimension](/api/reference/dimensionsdimensions/index.md) and whose Data Model is `[G-SelectionOperationShares`](/api/data-models/g-selection-operation-shares/index.md), where *G* indicates the specific Geometry assumed by *R* on *D*.

According to the [specific Resource type *R*](/api/reference/resources/device-related/index.md), the following `R-Shares` Data Models are defined:

* [`DetectedPosition-Shares`](api/data-models/r-shares/detected-position.md)
* [`Activity-Shares`](api/data-models/r-shares/activity.md)
* [`Visit-Shares`](api/data-models/r-shares/visit.md)
* [`Travel-Shares`](api/data-models/r-shares/travel.md)
* [`HomeLocation-Shares`](api/data-models/r-shares/home-location.md)
* [`WorkLocation-Shares`](api/data-models/r-shares/work-location.md)
* [`LivingArea-Shares`](api/data-models/r-shares/living-area.md)
* [`Flight-Shares`](api/data-models/r-shares/flight.md)
