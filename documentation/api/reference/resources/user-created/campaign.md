* [Documentation Home](../../../../README.md)  
  * [Web API](../../../index.md)  
    * [Reference](../../index.md)
        * [Resources](../index.md)
           * [User-created Resources](index.md)
           
# Campaign

A *Campaign* is a Resource that identifies an advertising campaign for drive-to-store.
*Campaigns* allow keeping trace of your digital or out-of-home (OOH) advertising campaigns, obtaining Footfall analysis, and monitoring visits to the target stores of the campaign performed by Users exposed to the advertising.


A *Campaign* Resource is mainly chracterized by:

* **Resource ID and creation time**. Assigned by the GeoUniq Analytics Platform.
* **Name, Description, and Labels.** Descriptive Information provided when the Resource is created.
* **Type**. Indication of the whether the campaign is a digital or an  (OOH) campaign.
* **Period**. Indication of the time period of the campaign.
* **Target POIs**. Indication of the POIs (typically stores) that represent the target of the drive-to-store advertising campaigns
* **Target Audience**. An optional set of AIDs that represent the target audience for the advertising campaign. It can be used as default control group when a [Footfall Analysis](/api/reference/resources/user-created/campaign-footfall.md) is requested for the *Campaign*

## Resource Data Model

The data model used to represent a *Campaign* is [`Campaign`](/api/reference/data-models/resources/user-created/campaign.md)

## Endpoints

- [Create single Resource](/api/reference/endpoints/endpoints/resources/user-created/campaign/create.md)
- [Read whole Collection](/api/reference/endpoints/endpoints/resources/user-created/campaign/read-collection.md)
- [Read single Resource](/api/reference/endpoints/endpoints/resources/user-created/campaign/read-resource.md)
- [Update single Resource](/api/reference/endpoints/endpoints/resources/user-created/campaign/update.md)
- [Delete single Resource](/api/reference/endpoints/resources/user-created/campaign/delete.md)

