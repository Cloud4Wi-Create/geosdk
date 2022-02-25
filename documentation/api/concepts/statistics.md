* [Documentation Home](../../README.md)
   * [Web API](../index.md)
      * [Basic Concepts and Functionalities](index.md)
      
# Statistics 

A **Statistic** is the operation of computing aggregated metrics on a set of resources
 (said [segment of resources](resource-definition.md#resources-segments)) 
 of a given [type *R*](resource-definition.md#resources).

> A *Statistic* is always related to a specific resource type *R*

Statistics are defined for [platform-created resources](resource-definition.md#resources).

Examples of information provided by a *Statistics* might be:

 - The number of times a given set of devices has visited a given area during a given period of time (Statistic on *Visits*).
 - The number of devices within a given area at a given time (Statistic on *Positions*).
 - The number, duration, and distance of journeys of a given set of devices during a given period of time (Statistic on *Journeys*).

## Aggregated Metrics

Each Statistic provides one or more **Aggregated Metrics**, which are derived from the set of 
[metrics defined for the resource type](resource-definition.md#metrics).

In addition, every Statistic provides the *count* Aggregated Metric, 
which simply indicates the number of involved resources, 
e.g., number of *Visits* to a given area during a given period of time.

## Selection Operation

When a Statistic is requested, the API allows to indicate what is the set of resources 
(the [*R* Segment](resource-definition.md#resources-segments)) which we are interested in.
This set is indicated through a [Resource Selection](resource-selection.md).

The selected *R* Segment represents the set of Resources on which the Statistic must be computed.

This main set can be:

- **treated as a whole**, in order to get Aggregated Metrics for it.   
E.g., average time Users walked in a given area during a given time period; 
number of "long-distance" journeys during the last month; etc.

- **segmented** in several (sub)-segments (according to specific criteria) 
in order to compare aggregated metrics obtained for each of them. 

E.g., considering *Visits*:
 * Which users has visited a given set of POIs?
 * Which days of the week Users perform more visits to a given point-of interest?
 * Which POI received more visits?
 * Which day of the week they last more?

## Segmentation Operation

The **Segmentation Operation** allows to segment the whole *R* Segment identified by the 
[Selection Operation](#selection-operation) in several sub-segments, each of which is again an *R* Segment.

The Aggregted Metrics will then be computed by aggregating resources belonging to each *R* Segment 
deriving from the Segmentation.
Therefore, the Segmentation Operation allows to compare different *R* Segments to each other.

> When performing requests to the API to obtain a Statistic, a [paginated](../reference/general-aspects/pagination.md) response will be obtained. 
> Each Item of the paginated response will contain the aggregated information related to one of the *R* Segments
> deriving from the Segmentation.

For example, with reference to the Statistic on Visit resources, 
one could be interested in comparing different periods of the year in terms of 
number of visits performed by the user-base to agiven geographical area.

Generally speaking, the whole Segmentation Operation is composed of several Segmentations, 
one for each Attribute of *R*.
From a logical point of view, the meaning of a single Segmentation is to:

- consider "ranges" of values for the specific Attribute;
- divide the main *R* Segment in several Segments according to 
the range which the value of the Attribute falls in.

Therefore, a Segmentation operation mainly deals with dividing the "main range" of values, 
indicated for an Attribute in the Selection Operation, 
in several sub-ranges, which in turn leads to dividing the main *R* Segment in several sub-Segments.

For each Selection Condition that is possible to indicate for a given type *R*, 
a correspondent Segmentation Operation is defined.
Thus, **a Segmentation Operation is always related to one specific [Selection Condition](resource-selection.md)**.
A Selection Condition for which a Segmentation Operation is requested is said **Segmented Selection Condition** 

In detail, an *R* Segment can be Segmented through:

### Segmentation Criteria

Any Segmentation Operation has to indicate a **Segmentation Criterion**.

> Only one Criterion can be indicated for each Segmented Selection Condition.

A Segmentation Criterion basically indicates how an "interval of values" 
(e.g., a *D* Segment; a numeric interval; etc.) has to be divided into several "sub-intervals".
Then, depending on the dimension *D* of the specific attribute, different Criteria will be available.
However, all of them define a **Granularity** which rules the size of each "sub-interval" 
and thus number of *R* Segments deriving from the specific Segmentation Operation,
 which simply corresponds to the number of "sub-intervals" which the main "selection interval" has been divided into.

The number of *R* Segments deriving from a specific Segmented Selection Condition 
is said **Size of the Segmented Selection Condition**.

As an example, let us consider a segmentation on the *Time* Dimension.
Then, let us consider the *Continuous Interval* Criterion, 
which simply segments a period of time in sub-intervals whose duration is ruled by the chosen granularity.
Now, let us consider a *Time* Segment of 30 days and *"1 Hour"* as Granularity
 (i.e., intervals of duration equal to 1 hour). 
The resulting Segmentation Size would be equal to 720.

In case of several Segmented Selection Condition, the size of the whole Segmentation, 
said **Segmentation Size**, is given by the product of the Size of each Segmented Selection Condition. 
The Segmentation Size indicates the number of *R* Segments which the Statistic will be composed of 
and thus the maximum number of Items returned in the response.

### Dimensional Segmentation

These Dimensional Segmentations use common Data Models that depend on:

- The Dimension of interest *D* (and the specific *D* Segmentation Criterion)
- The [Selection Operator](resource-selection.md) of interest *OP*

A Segmentation always relates to a specific Dimension *D* and is expressed through a 
[Selection Operator](..#resource-selection-and-selection-conditions) and a 
[Segmentation Criterion](#segmentation-criteria).

Generally speaking, for each Selection Condition that can be expressed for the 
[Selection Operation](api/concepts/resource-selection.md), 
a correspondent Segmentation Criteria, among those defined for *D*, can be indicated.
Such a Segmentation will actually **divide the** ***D*** **Segment, 
indicated for the Operator** ***OP*** **in the Selection Operation**, 
in several (sub-)Segments according to the Segmentation Criterion that has been chosen
and the indicated Granularity.

> If no Segmentation Criterion is indicated for a given pair *operator-attribute*, 
> then the *D* Segment provided for the Operator *OP* in the Selection Operation will be treated as a whole.

> A Segmentation can be indicated for a pair *operator-attribute* even if no Selection Condition 
> has been indicated for the same pair. 

As an example, if you want to segment *Visits* according to the time period when they started, 
you have to indicate for the Period Visit attribute the operator *start* and a *Time* Segmentation Criteria. 
An example of a *Time* Segmentation Criterion is "By continuos Interval", 
which allows to divide a time period into continuous intervals of a given constant duration.
This way, you would be able to compare an Aggregated Metric defined for the *Visit* type
 (e.g., the average duration) with respect to the time instant the Visits started.

Similarly to Selection Conditions, the set of all the possible segmentations depends 
on the set of Dimensions on which attributes of a resource *R* assume values, 
as well as the specific [Configuration *C* assumed by *R* on *D*](resource-definition.md#configuration-of-a-resource-attribute).  
E.g., *Space*: use the *Space-SegmentationCriterion1* for the *start* operator, 
use the *Space-SegmentationCriterion2* for the *end* operator; etc.

Given a Configuration *C* and a Dimension *D*, t
he set of allowed Dimensional Segmentations can be expressed through a common Data Models that depends on 
*D* and *C*.
Such Data Models are generically indicated as [`C-D-Segmentation`](../reference/data-models/g-d-segmentation/index.md)

## Example of a Statistic

An example of a *Statistic* may be the following.

 - **Resource type**: Travel.
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

 - **Resource type**: *Visit*
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