<a name="statistics"></a>
# Statistics 

A **Statistic** is defined as the operation of computing aggregated metrics on a set of Resources (said [Segment of Reources](/api/concepts/resource-definition.md#resource-segment)) of a given [Class *R*](/api/concepts/resource-definition.md#resources).

> A *Statistic* is always related to a specific Resource Class *R*

Statistics are defined for [Device-related Resource Classes](/api/concepts/resource-definition.md#resources).

Example of information derived from *Statistics* might be:

 - The number of times a given set of devices has visited a given area during a given period of time (Statistic on *Visits*).
 - The number of devices within a given area at a given time (Statistic on *Detected Positions*).
 - The number, duration, and distance of travels performed by a given set of devices during a given period of time (Statistic on *Travels*).

The set of available Statistics is listed in the [Statistics section](api/statistics/index.md)

<a name="aggregated-metrics"></a>
## Aggregated Metrics

Each Statistic provides one or more **Aggregated Metrics**, which represent the actual information which we are interested in.

Each Statistic indicates the set of available Aggregated Metrics in its own [documentation section](api/statistics/index.md), which are generally derived from the set of [Metrics defined by the Resource Class](api/concepts/resource-definition.md#resources), which in turn are indicated in the related [documentation section](api/resources/index.md).

In addition, every Statistic provides the *count* Aggregated Metric, which simply indicates the number of involved Resources, e.g., number of *Visits* to a given area during a given period of time.

<a name="selection"></a>
## Selection Operation

When a Statistic is requested, the API allows to indicate what is the set of Resources (the *R* Segment) which we are interested in.
This set is indicated through a [Resource Selection](api/concepts/resource-selection.md), which in turn identifies an *R* Segment.

The selected *R* Segment represents the set of Resources on which the Statistic must be computed.

This main set can be:

- **treated as a whole**, in order to get Aggregated Metrics for it. E.g., average time Users walked in a given area during a given time period; number of "long-distance" travels during the last month; etc.
- **segmented in several sub-sets according to specific criteria**, in order to compare Aggregated Metrics obtained for different sub-sets. E.g., considering *Travels*: which days of the week Users travel more? Which Users travel more? Where they most start from? Where they most arrive? etc. This operation is said **Segmentation**.

<a name="segmentation"></a>
## Segmentation Operation

The **Segmentation Operation** allows to segment the whole *R* Segment identified by the [Selection Operation](#selection) in several sub-segments, each of which is again an *R* Segment.

The Aggregted Metrics will then be computed by aggregating Resources belonging to each *R* Segment deriving from the Segmentation.
Therefore, the Segmentation Operation allows to compare different *R* Segments to each other.

> When performing requests to the API to obtain a Statistic, a [paginated](/api/general-aspects/pagination.md) response will be obtained. Each Item of the paginated response will contain the aggregated information related to one of the *R* Segments deriving from the Segmentation.

For example, with reference to the Statistic on *Travels*, one could be interested in comparing different periods of the year in terms of number of travels performed by the user-base.

Generally speaking, the whole Segmentation Operation is composed of several Segmentations, one for each Attribute of *R*.
From a logical point of view, the meaning of a single Segmentation is to:

- consider "ranges" of values for the specific Attribute;
- divide the main *R* Segment in several Segments according to the range which the value of the Attribute falls in.

Therefore, a Segmentation operation mainly deals with dividing the "main range" of values indicated for an Attribute in the Selection Operation in several sub-ranges, which in turn leads to dividing the main *R* Segment in several sub-Segments.

For each Selection Condition that is possible to indicate for a given Class *R*, a correspondent Segmentation Operation is defined.
Thus, **a Segmentation Operation is always related to one specific [Selection Condition](api/concepts/resource-selection.md)**.
A Selection Condition for which a Segmentaion Operation is requested/performed is said **Segmented Selection Condition** 

In detail, an *R* Segment can be Segmented through:

- a set of [Dimensional Segmentations](#dimensional-segmentation), indicated as ***D*** **Segmentation**
- a set of [Metric Segmentations](#metric-segmentation), indicated as ***M*** **Segmentation**

> If no Segmentaion is requested, then the *R* Segment indicated by the Selection Operation will be treated as a whole and only one Item will be obtained in the response.

<a name="segmentation-criteria"></a>
### Segmentation Criteria

Any Segmentation Operation (regardless of the type of Selection Condition which it relates to) has to indicate a **Segmentation Criterion**.

> Only one Criterion can be indicated for each Segmented Selection Condition.

A Segmentation Criterion basically indiactes how an "interval of values" (e.g., a *D* Segment; a numeric interval; etc.) has to be divided in several "sub-intervals".
Then, depending on whether we are segmenting on a Metric or a given Dimension *D*, different Criteria will be available.
However, all of them define a **Granularity** which rules the size of each "sub-interval" and thus number of *R* Segments deriving from the specific Segmentation Operation, which simply corresponds to the number of "sub-intervals" which the main "interval" has been divided into.

The number of *R* Segments deriving from a specific Segmented Selection Condition is said **Size of the Segmented Selection Condition**.

As an example, let us consider a [Dimensional Segmentation](#dimensional-segmentation) on the *Time* Dimension.
Then, let us consider the *Continuous Interval* Criterion, which simply segments a period of time in sub-intervals whose duration is ruled by the chosen granularity.
Now, let us onsider a *Time* Segment of 30 days and *"1 Hour"* as Granularity (i.e., intervals of duration equal to 1 hour). 
The resulting Segmentation Size would be equal to 720.

In case of several Segmented Selection Condition, the size of the whole Segmentation, said **Segmentation Size** is given by the product of the Size of each Segmented Selection Condition. 
The Segmentation Size indicates the number of *R* Segments which the Statistic will be composed of and thus the number of Items returned in the response.

<a name="dimensional-segmentation"></a>
### Dimensional Segmentation

Similarly to a [Dimensional Selection Condition](/api/concepts/resource-selection.md#dimensional-selection-conditions), a **Dimensional Segmentation** allows to segment Resources of a given Class *R* according to the "value" they assume on a specific Dimension *D*.

These Dimensional Segmentations use common Data Models that depend on:

- The Dimension of interest *D* (and the specific *D* Segmentation Criterion)
- The [Dimensional Selection Operator](api/concepts/resource-selection.md#dimensional-selection-conditions) of interest *OP*

A Dimensional Segmentation always relates to a specific Dimension *D* and is expressed through a [Dimensional Selection Operator](api/concepts/resource-selection.md#dimensional-selection-conditions) and a [Segmentation Criterion](#segmentation-criteria).
Similarly to a Dimensional Selection Condition, the pair Operator-Dimension *OP-D* identifies the actual Attribute we are interested in: e.g., the *start* time of a *Visit*.

Generally sepaking, for each Dimensional Selection Condition that can be expressed for the [Selection Operation](api/concepts/resource-selection.md), which is identified by the pair Operator-Dimension *OP-D*, a correspondent Segmentation Criteria, among those defined for *D*, can be indicated.
Such a Segmentation will actually **divide the** ***D*** **Segment indicated for the Operator** ***OP*** **in the Selection Operation** in several sub-Segements according to the Segmentation Criterion that has been chosen and the indicated Granularity.

> If no Segemntation Criterion is indicated for a given pair *OP-D*, then the *D* Segment indicated for the Operator *OP* in the Selection Operation will be trated as a whole.

> A Segmentation can be indicated for a pair *OP-D* even if no Selection Condition has been indicated for the same pair. 

As an example, if you want to segment *Activities* according to the time period when they started, you have to indicate for the *Time* dimension the operator *start* and a *Time* Segmentation Criteria. An example of a *Time* Segmentation Criterion is "By continuos Interval", which allows to divide a time period into continuous intervals of a given constant duration.
This way, you would be able to compare an Aggregated Metric defined for the *Activity* Class (e.g., the average duration) with respect to when they started considering time intervals of fixed duration (e.g. an hour).

Similarly to Dimensional Selection Conditions, the set of all the possible Dimensional Segmentations depends on the set of Dimensions on which a given Class *R* is defined, as well as the specific [Geometry *G* assumed by *R* on *D*](/api/basic-concepts.md#dimensions-and-geometries); e.g., *Space*: use the *Space-SegmentationCriterion1* for the *start* operator, use the *Space-SegmentationCriterion2* for the *end* operator; etc.

Given a Geometry *G* and a Dimension *D*, the set of allowed Dimensional Segmentations can be expressed through a common Data Models that depends on *D* and *G*.
Such Data Models are generically indicated as [`G-D-Segmentation`](/api/data-models/g-d-segmentation/index.md)

## Example of a Statistic

An example of a *Statistic* may be the following.

 - **Resource Class**: Travel.
 - **Metrics**: count, duration.
 - **Geometries - Dimensions** 
    - ***Point - Device Base***: each *Travel* is related to a specific Device.
    - ***Interval - Time***: each *Travel* has a start and a end time and includes all istants among them.
    - ***Sequence - Space***: each travel has a start and an end geographical position.
 - **Allowed Segmentations** 
    - ***Device Base***: e.g., segment the selection of devices in groups of one device each.
    - ***Time***: e.g., segment the selected period of time in several sub-periods of fixed duration.
 - **Provided Information**: number and duration of travels performed by **all devices** (no segmentation) / **each device** (*Device Base* Segmentation) belonging to the **whole device base** (Unrestricted *Device Base* Selction) / the **indicated set** (Restricted *Device Base* Selction), during **their whole "life"** (Unrestricted *Time* Selection) / the indicated **period of time** (Restricted *Time* Selction)

Note that, for the example *Statistic* above:
 - the *Device Base* Segmentation, allows to compare devices to each other and understand which users travel more.
 - the *Device Base* Selection and the *Time* Selection, allow to focus on a specific period of time and a specific set of devices.

As another example, it could be useful to perform a *Time* Segmentation (e.g. dividing the whole period of time in months) to understand which are the months when the specific *Device Base* Selection travels more.

An example of a Statistic segmented on multiple criteria is the following.

 - **Resource Class**: *Visit*
 - **Metrics**: count, duration
 - **Input Selection**: a specific set of devices (*Device Base* Selction); a specific period of time (*Time* Selection), a specific area (*Space* Selection)
 - **Input *Segmentation***: by each device (*Device Base* Segmentation); on each month during the selected period (*Time* Segmentation)
 - **Provided Information**: Time spent within the indicated **area** and during the indicated **period of time** by **each device** during **each month**

Such a Segmentation would allow to understand:
 - for each month: which devices have sepnt more time in the indicated area;
 - for each device: when (in which month) it has spent more time in the indicated area;

Finally, a *Statistic* may not be segmented at all.
An example of a non-segmented *Statistic* is the following.

 - ***Statistic***: Home Locations
 - ***Metric*s**: count
 - **Input *Selection***: a specific area (*Space-Selection*)
 - **Input *Segmentation***: none
 - **Provided Information**: Number of devices with home location within the indicated **area**