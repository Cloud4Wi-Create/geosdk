# Resources

A **Resource** is a basic piece of information on which it is possible to perform CRUD operations.
This API defines several type of Resources, such as *Detected Position*, *Visit*, *Home Location*, etc.
A Resource type is referred to as **Resource Class**. A generic Resource Class is indicated with ***R***.

The most important Resource Class is [***Device***](/api/resources/platform-created/device-related/device.md), which models a single installation of a [Client App](/service-architecture/index.md) on a phisical device.

The Resource Classes defined by this API are grouped into two main categories:

* [**Platform-created Resources**](/api/resources/platform-created/index.md). Are automatically created by Cloud4Wi platform. Only the READ operation is allowed. A sub-category of Platform-created Resources are:
	* [**Device-related Resources**](/api/resources/platform-created/device-related/index.md). Refer to a specific device. An example of a Device-related Resource Class is *Detected Position*, which represents the geographical location where a device was at a given specific time.
* [**User-created Resources**](/api/resources/user-created/index.md). Are created by a User of this API. Generally all CRUD operations are allowed. An example of a User-created Resource Class is *Trigger*, which defines an event to be monitored.

Each Resource Class defines the data model used to represent it as a JSON object, also referred to as **Type**.

The various Resource Classes defined by this API are documented in the [Resources](/api/resources/index.md) section.

Device-related Resource Classes represent the actual information which we are interested in.
For this category of Resources, this API allows a set of smart operations to select them, group them, and compute aggregated metrics.

The rest of the [Concepts](/api/concepts/index.md) section mainly refers to Device-related Resources.


# Dimensions and Geometries

In order to allow a smart and flexible selection scheme, this API defines the concepts of [**Dimension**](#dimensions) and [**Geometry**](#geometries).
Dimensions and Geometries are defined in order to allow a flexible way to select Resources. They define common Data Models used thorughout this API to indicate [Selection Conditions](/api/concepts/resource-selection.md) that are common to several Resource Classes *R*.


<a name="dimensions"></a>
## Dimensions

A Dimension can be seen as a generalization of a Resource attribute that applies to several Class of Resources.
For instance, the *Space* Dimension is common to almost all Device-related Classes as they all have a refernce to the Heart's surface.

Generally speaking, a Dimension *D* may be common to several Resource Classes or may be specific of only one of them.
As an example, [*Space*](/api/dimensions/space.md) and [*Time*](/api/dimensions/time.md) are common Dimensions for almost all Classes, [*Device Base*](/api/dimensions/device-base.md) is common to all Device-related Resources, whilst [*Motion Type*](/api/dimensions/motion-type.md) is specific for [*Activity*](/api/resources/platform-created/device-related/activity.md).

More formally, a **Dimension** is defined as a generic space (i.e. a set of elements) that charcterizes one or more Class of Resources.
For instance, the *Time* Dimension is defined as the set of all the possible time instants; the *Space* dimension is defined as all the possible geographical positions on the Earth's surface; etc.

The set of Dimensions defined by this API are documented in the [Dimensions](/api/dimensions/index.md) section.

<a name="dimension-segment"></a>
### Segment of a Dimension

Given the whole space of a Dimension *D*, any sub-set of this space is said **Segment of Dimension** ***D***, or simply ***D*** **Segment**.

Each Dimension *D* defines the Data Model used to indicate the related *D* Segment.
Such Data Models are generically indicated as [`D-Segment`](/api/data-models/d-segment/index.md).
In addition, it also defines a data model used to divide a *D* Segment into several (sub-)Segments according to specific criteria (see [Statistics - Segmentation](/api/concepts/statistics.md#segmentation)).
Such Data Models are generically indicated as [`D-Segmentation`](/api/data-models/d-segmentation/index.md).


<a name="geometries"></a>
## Geometry assumed by a Resource on a Dimension

A Geometry refers to how a Resource Class is defined on a Dimension.
Indeed, although a Dimension can be common to several Resource Classes, the way in which different Classes relates to a specific Dimension *D* can be different.
Specifically, given a Dimension *D*, a Class *R* might be defined through a single value of *D*, an unordered set of values, an ordered set, etc.

The different way in which a Resource Class *R* is defined on a Dimension *D* is said **Geometry of** ***R*** **on** ***D***.

As an example, a *Visit* assumes a Geometry of type *Interval* on the *Time* dimension because it has a "start" and an "end" time instants and lasts for the whole time period;
a *Detected Position* assumes a Geometry of type *Point* on the *Space* Dimension because it has a single spatial reference, whilst an *Activity* is defined as a *Sequence* on *Space* because it has several ordered spatial reference (the various positions that compose it, ordered according to the time which they refer to).

A generic Geometry is indicated with *G*.
The set of defined Geometries is listed in the related [section](/api/geometries-and-operators.md).

Each Geometry *G* allows a different set of [**Dimensional Selection Operator**](/api/geometries-and-operators.md#operators).
As an example, the *Point* Geometry allows the opeator *inside* but does not allow the operators *start* and *end*, which instead are allowed for *Sequence* and *Interval*.

The set of Dimensional Selection Operators, as well as the Geometries on which they are applicable is documented in the related [section](/api/geometries-and-operators.md#operators).

# Metrics

In addition to Dimensions and Geometries, this API also defines the concept of **Metric of a Resource Class** ***R*** or simply ***R*** **Metric**.
A Metric is a simple attribute that is mapped on the Resource Class Data Model as a simple filed of Type `Number`.

Similarly to Dimensions and Geometries, the concept of Metric is defined in order to allow Resource Selection according to Metrics' values using common Data Models.
However, unlike Dimensions, the same Data Model is used regardless of the specific Metric *M*.
Moreover, unlike Dimensions, Metrics are specified for each Class *R* and are not generalized as common attributes even though, in some cases, two Classes *R1* and *R2* could defined a Metric with the same "name". 
As an example, both the *Activity* and *Visit* Class define a Metric called *duration*. 


<a name="resource-segment"></a>
# Segment of a Resource Class

A sub-set of all the Resources of Class *R* is said **Segment of** ***R***, or simply ***R*** **Segment**.
If an *R* Segment represents the whole set of *R* Resources, it is said **Unrestricted Segment**. Otherwise, it is said **Restricted Segment**.

Each Class *R* defines a specific Data Model to represent the related *R* Segment.
Such Data Models are generically indicated as [`R-Segment`](/api/data-models/r-segment/index.md).

An *R* Segment is identified through a set of [**Selection Conditions**](/api/concepts/resource-selection.md), which basically indicates conditions on the Attributes of a Resource Class.
