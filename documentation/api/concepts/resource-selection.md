* [Documentation Home](../../README.md)
   * [Web API](../index.md)
      * [Basic Concepts and Functionalities](index.md)
      
# Resource Selection and Selection Conditions

The term **resource selection** refers to the action of selecting a set of resources of a specific type *R* 
according to the values of their attributes.  
A selection of resources of type *R* is said ***R* selection**.
 
> **An *R* selection identifies an [*R* segment](resource-definition.md#resources-segments)**; 
> i.e., a sub-set of all the possible resources of type *R*.
>> Though very similar to each other, 
>the term ***R* selection** is mainly used to indicate the action of selecting resources of type *R* 
>whilst the term ***R* segment** is used to indicate the set of *R* resources resulting from an *R* selection.

Each type *R* defines a specific data model to indicate an *R* selection or, 
equivalently, to represent an *R* segment.  
Such data models are generically indicated as [`R-Selection`](../reference/data-models/r-selection/index.md).

An *R* selection is composed of several **selection conditions**.  
Each selection condition refers to one specific [attribute](resource-definition.md#resource-attributes)
and allows selecting resources according to the values of that attribute.  
To do that, a selection condition also indicates one specific **selection operator** among those allowed 
for the [configuration](resource-definition.md#configuration-of-a-resource-attribute) of the specific attribute.  

> The set of Selection Operators allowed for each configuration 
>is listed [here](../reference/configurations-and-operators.md#selection-operators).

Thus, each selection condition indicates a selection operator and a [*D* segment](resource-definition.md#segment-of-a-dimension), 
where the latter depends on the dimension *D* of the specific attribute.
 
As an example, to select all the Visits that started in a given time period, 
we need a selection condition for the Period attribute that uses the operator Start, and a Time segment indicating the period of interest.  
On the contrary, to select all the Visits that were in progress during a given time period, 
the selection condition has to use the operator Intersect instead of Start.

An *R* selection can contain more than one selection condition for the same attribute.
Specifically, it can contain as many as one condition for each selection operator (among those allowed for the specific configuration). 

As an example, we can select Visits that "started" in a given period and that terminated in another period.

Given a configuration *C* and a Dimension *D*, the set of possible selection conditions 
can be expressed through a common data model that depends on *D* and *C*.
Such data models are generically indicated as [`D-C-SelectionOperation`](../reference/data-models/d-c-selection-operation/index.md)

[Next: Statistics](statistics.md)