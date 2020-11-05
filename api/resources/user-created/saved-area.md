# Saved Area

A *Saved Area* is a simple Resource that identifies a geographical area.
*Saved Areas* can be created in order to recall them when performing requests to the Web API.
Specifically, one or more *Saved Areas* can be indicated for a [*Space* Segment](/api/dimensions/space.md) through a [`SavedArea-Segment`](/api/data-models/d-segment/space.md#saved-area-segment) Object.

> *Saved Areas* have no effect on the operations performed by GeoUniq Analytics Platform. They only indicate a geographical area when recalled in a specific Request.

A *Saved Area* Resource is mainly chracterized by:

* **Resource ID and creation time**. Assigned by the GeoUniq Analytics Platform.
* **Name, Description, and Labels.** Descriptive Information provided when the Resource is created.
* **Geographical Area**. Indication of the geographical area.


## Resource Data Model

The data model used to represent a *Saved Area* is [`SavedArea`](/api/data-models/resources/user-created/saved-area.md)

## Endpoints

- [Create single Resource](/api/endpoints/resources/user-created/saved-area/create.md)
- [Read whole Collection](/api/endpoints/resources/user-created/saved-area/read-collection.md)
- [Read single Resource](/api/endpoints/resources/user-created/saved-area/read-resource.md)
- [Update single Resource](/api/endpoints/resources/user-created/saved-area/update.md)
- [Delete single Resource](/api/endpoints/resources/user-created/saved-area/delete.md)

