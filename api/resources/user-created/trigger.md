# Trigger

*Trigger* Resources represent the basic building block for the [Trigger Platform](/overview.md#trigger-platform).

In detail, a *Trigger* allows to:

* define an event that has to be monitored for one or more Targets
    * A Target can be a single *Device*, a set of *Devices* explicitely indicated through their IDs, a set of *Devices* identified according to a specific Attribute, such as the [Client App](/service-architecture.md) they belong to, as well as the whole *Device Base*.
* indicate one or more actions to be performed when the event occurs by linking one or more [*Hook*](/api/resources/user-created/hook.md) Resources.

A *Trigger* Resource is mainly chracterized by:

* **Resource ID and creation time**. Assigned by the GeoUniq Analytics Platform.
* **Name, Description, and Labels.** Descriptive Information provided when the Resource is created.
* **Active Period.** Indication of the time period during which the event defined by the *Trigger* has to be monitored.
* **Targets.** One or more Targets for which the event defined by the *Trigger* has to be monitored.
* **Event Definition.** Definition of the event that has to be monitored.
* **Linked** ***Hooks.*** Set of actions to be performed

## Resource Data Model

The data model used to represent a *Trigger* is [`Trigger`](/api/data-models/resources/user-created/trigger.md)

## Endpoints

- [Create single Resource](/api/endpoints/resources/user-created/trigger/create.md)
- [Read whole Collection](/api/endpoints/resources/user-created/trigger/read-collection.md)
- [Read single Resource](/api/endpoints/resources/user-created/trigger/read-resource.md)
- [Update single Resource](/api/endpoints/resources/user-created/trigger/update.md)
- [Delete single Resource](/api/endpoints/resources/user-created/trigger/delete.md)

