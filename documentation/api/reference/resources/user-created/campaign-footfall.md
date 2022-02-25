* [Documentation Home](../../../../README.md)  
  * [Web API](../../../index.md)  
    * [Reference](../../index.md)
        * [Resources](../index.md)
           * [User-created Resources](index.md)
           
# Footfall Analysis

A *Footfall Analysis* is a resource that represents an analysis requested for a specific 
[*Campaign*](../user-created/campaign.md) resource.
*Footfall Analysis* allow measuring the performance of an advertising campaign for drive-to-store.
Specifically, a footfall analysis allows measuring how much the target POIs of a given advertising campaign have been 
visited by individuals exposed to the advertising, 
comparing this with Users not exposed to the advertising, and comparing Users exposed to different advertising creatives.

When a *Footfall Analysis* Resource is created, the API will respond immediately with the created resource 
(which includes an  ID and a creation time).
The analysis is started asynchronously and the results will be provided trhough files that can be downloaded once the analysis will have terminated.

A *Footfall Analysis* Resource is mainly chracterized by:

* **Resource ID and creation time**. Assigned by the GeoUniq Analytics Platform.
* **Name, Description, and Labels.** Descriptive Information provided when the Resource is created.
* **Type**. Indication of whether a Standard or Premium Footfall Analysis is desired.
* **Control Group**. Indication of a set of devices' AIDs used as control group to compare the visits of exposed Users with the visits of such control group.

## Resource Data Model

The data model used to represent a *Footfall Analysis* is [`FootfallAnalysis`](../../data-models/resources/user-created/campaign-footfall.md)

## Endpoints

- [Create single Resource](../../endpoints/user-created/campaign/footfall/create.md)
- [Read whole Collection](../../endpoints/user-created/campaign/footfall/read-collection.md)
- [Read single Resource](../../endpoints/user-created/campaign/footfall/read-resource.md)

