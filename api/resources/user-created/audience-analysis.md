# Audience Analysis

An *Audience Analysis* is a Resource that identifies an analysis to identify a set of AIDs to which deliver advertising.
An *Audience Analysis* can be of the following types

* **Geo-Behavioural**: allows to identify devices according to places they have visited, places or areas they frequently pass in proximity of, where they live or work
* **Geo-Demographics**: allows to identify devices according to geo-demographics attributes

When an *Audience Analysis* Resource is created, the API will respond immediately with the created Resource (which includes an  ID and a creation time).
The analysis is started asincrounsly and the results will be provided through files that can be downloaded once the analysis will have terminated.

An *Audience Analysis* Resource is mainly chracterized by:

* **Resource ID and creation time**. Assigned by the Cloud4Wi Geo Services Platform.
* **Name, Description, and Labels.** Descriptive Information provided when the Resource is created.
* **Type**. Indication of the type of analysis that is desired.

## Geo-Behavioural Audience Analysis

A *Geo-Behavioural Audience Analysis* Resource is mainly chracterized by:

* **A set of POIs**. Indicates the places or the geographical areas according to which devices have to be selected.
* **A set of Criteria**. Indicates the criteria used to identify devices. The criteria are:
    * **Visited**: indicates that devices that have visited the POIs have to be included in the audience
    * **Passed Through**: indicates that devices that frequently pass in proximity of the POIs have to be included in the audience
    * **Live**: indicates that devices that live in proximity of the POIs have to be included in the audience
    * **Work**: indicates that devices that work in proximity of the POIs have to be included in the audience
* **Period**: Indicates the time period that during which the indicated criteria have to be verified.
* **Reach Level**: Indicates a reach level to rule the size of the identified audience. It will be used as a distance value for Passed Through, Live, and Work criteria, and as confidence level for the Visited criterion.


## Geo-Demographic Audience Analysis

A *Geo-Demographic Audience Analysis* Resource is mainly chracterized by:

* **Socio-Demo attributes**. A set of attributes for the desired audience.
* **Administraive Area**. A geo-administrative area where users have to live to be included in the audience.

## Resource Data Model

The data model used to represent an *Audience Analysis* is [`AudienceAnalysis`](/api/data-models/resources/user-created/audience-analysis.md)

## Endpoints

- [Create single Resource](/api/endpoints/resources/user-created/audience-analysis/create.md)
- [Read whole Collection](/api/endpoints/resources/user-created/audience-analysis/read-collection.md)
- [Read single Resource](/api/endpoints/resources/user-created/audience-analysis/read-resource.md)
- [Download Results](/api/endpoints/resources/user-created/audience-analysis/download-results.md)
