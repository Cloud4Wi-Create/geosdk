* [Documentation Home](../../README.md)
   * [Web API](../index.md)
      * [Basic Concepts and Functionalities](index.md)
      
# Triggers 

A *Trigger* defines an event that has to be monitored for one or more Targets.

## Event definition

The event to be monitored is expressed through an [Untargeted Boolean Expression](/api/concepts/statistic-conditions.md#untargeted-boolean-expression), which expresses a set of conditions on one or more [Aggregated Metrics of a Statistic](/api/concepts/statistics.md#aggregated-metrics).

> The Untargeted Boolean Expression may indicate a simple condition, such as "The User is in area *A*", or a complext one, such as "a User that lives in Rome, travles "a lot", and often visits Milan, is just back home after a travel from Milan to Rome".

> An Untargeted Boolean Expression is represented on the API through a [`ConditionTreeNode`](/api/reference/data-models/common/conditions-tree-node.md).

The Untargeted Boolean Expression is then assigned to a **Target**. Thus, it becomes a **Targeted Boolean Expression**.
The event "occurs" when the Targeted Boolean Expression passes from **false** to **true**.

As an example, if the Targeted Boolean Expression is "Device *D1* is in area *A1*", the correspondednt event is "Device *D1* **enters** area *A1*".

## Targets definition

Each Target is a *Device Base* Segment and, as such, can reprsent any set of *Devices*, from one to the whole device-base.

As an example, if you want to monitor when a single *Device* enters an area, then the Untargeted Boolean Expression that defines the event "enters area *A1*" must be assigned to a Target composed of a single *Device*.
If you want to monitor such an event for every device, then the Trigger must have N targets, one for each *Device*.

On the contrary, if the event which you are interested in is "the number of Users in this area is higher than *X*", then the related Untargeted Boolean Expression must be assigned to a Target composed of the whole device-base, and only one Target is needed for the Trigger.

More in detail, the Targets of a Trigger are expressed indicating:

1. A *Device Base* Segment through a Selection Condition on the *Device Base* Dimension, that allows to indicate a main Segment that includes all the Targets.
2. A Segmentation operation on the *Device Base* Dimension that allows to derive N *Device Base* Segments (an thus N Targets) from the main Segment.

As an example, if the event to be monitored involves only one *Device* at time and you want to monitor it for for every *Device*, then the "main" Segment has to indicate the whole device-base and the Segmentation operation has to indicate the criterion "segment by each device".
