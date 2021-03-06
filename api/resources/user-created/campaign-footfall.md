# Footfall Analysis

A *Footfall Analysis* is a Resource that identifies an analysis requested for a specifc [*Campaign*](/api/resources/user-created/campaign.md) resource.
*Footfall Analysis* allow to obtain a report to measure and understand the performance of an advertising campaign for drive-to-store.
Specifically, a footfall analysis allows to measure how much the target POIs of a given advertising campaign have been visited by Users exposed to the advertising, 
to compare this with Users not exposed to the advertising or to compare Users exposed to different advertising creatives.

When a *Footfall Analysis* Resource is created, the API will respond immediately with the created Resource (which includes an  ID and a creation time).
The analysis is started asincrounsly and the results will be provided trhough files that can be downloaded once the analysis will have terminated.

A *Footfall Analysis* Resource is mainly chracterized by:

* **Resource ID and creation time**. Assigned by the Cloud4Wi Geo Services Platform.
* **Name, Description, and Labels.** Descriptive Information provided when the Resource is created.
* **Type**. Indication of whether a Standard or Premium Footfall Analysis is desired.
* **Control Group**. Indication of a set of devices' AIDs used as control group to compare the visits of exposed Users with the visits of such control group.

## Resource Data Model

The data model used to represent a *Footfall Analysis* is [`FootfallAnalysis`](/api/data-models/resources/user-created/campaign-footfall.md)

## Endpoints

- [Create single Resource](/api/endpoints/resources/user-created/campaign/footfall/create.md)
- [Read whole Collection](/api/endpoints/resources/user-created/campaign/footfall/read-collection.md)
- [Read single Resource](/api/endpoints/resources/user-created/campaign/footfall/read-resource.md)

