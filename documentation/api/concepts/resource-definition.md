* [Documentation Home](../../README.md)
   * [Web API](../index.md)
      * [Basic Concepts and Functionalities](index.md)
      
# Resources

A **resource** is an entity exposed by the API on which it is possible to perform CRUD operations, 
or other more complex operations, through the endpoints of the API.  
A resource models a basic informative element and is composed of a number of **attributes**.

This API defines several types of resources, such as Position, Visit, Home Location, etc.  
A type of resource is referred to as **resource type** or simply resource. 
A generic resource type is indicated with ***R*** throughout this documentation.

Each resource type has its own data model, also referred to as **type**, used to represent it as a JSON object.

The [resources section](../reference/resources/index.md)  provides a complete documentation 
of all the resource types defined by this API.

The resource types defined by this API can be grouped into two main categories.

* [**User-created Resources**](../reference/resources/user-created/index.md).   
Are created by a User of the API. Generally all CRUD operations are allowed. 
An example of a User-created resource is *Trigger*, which defines an event to be monitored.

* [**Platform-created resources**](../reference/resources/platform-created/index.md).  
Are automatically created by GeoUniq Analytics platform.
They cannot be deleted or updated.
However, for this category of resources, the API allows a set of smart operations to select them, 
group them, and compute aggregated metrics.  
The most important platform-created resource is [**Device**](../reference/resources/platform-created/device.md), 
which models a single installation of a [Client App](../../service-architecture.md) on a physical device.    
	* [**Device-related resources**](../reference/resources/platform-created/device-related/index.md).   
	A sub-category of platform-created resources.  
	Model information related to a device. An example of a Device-related resource is *Position*, 
	which represents the geographical location where a device was at a given time.  
	Device-related resources represent the actual information which we are interested in 
	as they model the behaviour of an individual.
    

The rest of this section mainly applies to platform-created resources and to the smart operations allowed on them.

# Resource Attributes, Dimensions, and Attribute Configurations

This API defines a smart and flexible framework for resource selection and aggregation/segmentation 
based on the concepts of **resource attribute**, **attribute dimension**, and **attribute configuration**. 

The result is the definition of a common scheme and data models 
used to perform selection and aggregation/segmentation operations for all platform-created resources.

## Resource Attributes

A resource is composed of several attributes.
An attribute is one of several characteristics that a resource can have. 
Has an example, the Device resource has an attribute called Creation Time, 
which indicates the time instant when the device was created.

## Dimensions

An attribute can assume values on spaces of different types.
Such types are said **dimensions**.
A generic dimension is indicated with *D* throughout this documentation.

This API defines several dimensions.
Some of them are simple dimensions that refer to commonly used data types, such as *Boolean* or *String*.
Others model instead more complex data types, that can even include more than one single value.
As an example, the [*Space*](../reference/dimensions/space.md) dimension refers to 
all possible points on the Earth's surface,
whilst [*DeviceBase*](../reference/dimensions/device-base.md) represents the space of all possible Devices, 
and is defined to model the relation between Device and device-related resource types. 

The various Dimensions defined by this API are documented in the [Dimensions](../reference/dimensions/index.md) section.

### Segment of a Dimension

Given the whole space of values of a dimension *D*, 
any sub-set of this space is said **segment of dimension** ***D***, or simply ***D*** **segment**.

For each dimension *D*, a specific data model is used to indicate the related *D* segment.
Such data models are generically indicated as [`D-Segment`](../reference/data-models/d-segment/index.md).

## Configuration of a resource attribute

An attribute, regardless of its specific dimension, 
may refer to a characteristic of the resource that could require more than one single value to be represented. 
As an example, the Period of a Visit is the attribute that characterizes a Visit 
with respect to the time period when it occurred.
In this case, the attribute needs two different Time values to be represented, 
that are the time instant when the Visit started and when it finished.  
As another example, let us consider the hypothetical resource Journey, 
which could model a journey performed by an individual.
One of its attributes could be the Path, that would be represented through a set of Space points.
In this case, the attribute would require an arbitrary number of values (on the Space dimension) to be represented.

The configuration of an attribute refers to different ways in which an attribute can assume values on its dimension. 
Specifically, given a Dimension *D*, an attribute might be defined through a single value of *D*, 
an unordered set of values, an ordered set, etc.

As an example, the Period attribute of the Visit resource assumes a configuration of type **Interval** 
on the Time dimension 
because it has a "start" and an "end" time instants and lasts for the whole time period.  
The Geographical Location attribute of the Position resource assumes a configuration of type 
**Point** on the Space dimension because it has a single spatial reference.  
The Path attribute of a Journey assumes a **Sequence** configuration on the Space dimension 
because it is composed of several ordered spatial points 
(the various positions that compose it, ordered according to the time which they refer to).

A generic configuration is indicated with *C*.
A generic combination of the dimension and the configuration of an attribute is indicated as *D-C* (e.g., Time-Interval).
The whole set of configurations defined by this API is listed in the 
[Configurations and Selection Operators](../reference/configurations-and-operators.md) section.

Each configuration *C* allows for a different set of [**Selection Operators**](../reference/configurations-and-operators.md#selection-operators).
As an example, the Point configuration allows the operator Inside but does not allow the operators Start and End, 
which instead are allowed for Sequence and Interval configurations.

The set of Selection Operators, as well as the configuration for which they are applicable, 
is documented in the 
[Configurations and Selection Operators](../reference/configurations-and-operators.md#selection-operators) section.

# Metrics

In some cases, an attribute represents a measurable characteristic of the resource.
In this case, the attribute is said **metric**.
As an example, the Duration attribute is a metric of the Visit resource.  
Formally, a metric is an attribute that assumes values on the Number dimension and has a Point configuration (Number-Point), 
that means it can be expressed by a single numeric value.  

From a general point of view, metrics are those attributes that can be aggregated 
and computed for group of resources to derive general insights.
As an example, one could be interested in computing the average duration of the visits 
to a given place during a given time period.
 
# Resources Segments

A sub-set of all the resources of type *R* is said **segment of** ***R***, or simply ***R*** **segment**.
If an *R* segment represents the whole set of *R* resources, it is said **unrestricted segment**. 
Otherwise, it is said **restricted segment**.

[Resource Selection](resource-selection.md)
