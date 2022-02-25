* [Documentation Home](../../../../README.md)  
  * [Web API](../../../index.md)  
    * [Reference](../../index.md)
        * [Resources](../index.md)
           * [User-created Resources](index.md)
           
# Audience Analysis

An *Audience Analysis* is a Resource that represents an analysis aimed at identifying a set of mobile devices, through theris adevrtising IDs (ADIDs), for the purpose of delivering advertising.

An *Audience Analysis* is built as a Boolean combination (logical AND and OR) of basic blocks.
A basic block can be of the following types.

* **Geo-Behavioural**: allows to identify devices according to places they have visited, places or areas they frequently pass in proximity of, where they live or work
* **Geo-Demographics**: allows to identify devices according to geo-demographics attributes

Like other [Batch Analysis](batch-analysis.md), when an *Audience Analysis* Resource is created, the API will respond immediately with the created Resource (which includes an  ID and a creation time).
The analysis is started asincrounsly and the results will be provided through files that can be downloaded once the analysis will have terminated.

## Geo-Behavioural Audience

A *Geo-Behavioural Audience* is mainly chracterized by:

* **A set of POIs**. Indicates the places or the geographical areas according to which devices have to be selected.
* **A set of Criteria**. Indicates the criteria used to identify devices. The criteria are:
    * **Visited**: indicates that devices that have visited the POIs have to be included in the audience
    * **Passed Through**: indicates that devices that frequently pass in proximity of the POIs have to be included in the audience
    * **Live**: indicates that devices that live in proximity of the POIs have to be included in the audience
    * **Work**: indicates that devices that work in proximity of the POIs have to be included in the audience
* **Period**: Indicates the time period that during which the indicated criteria have to be verified.
* **Reach Level**: Indicates a reach level to rule the size of the identified audience. It will be used as a distance value for Passed Through, Live, and Work criteria, and as confidence level for the Visited criterion.


## Geo-Demographic Audience

A *Geo-Demographic Audience* is mainly chracterized by:

* **Socio-Demo attributes**. A set of attributes for the desired audience.
* **Administraive Area**. A geo-administrative area where users have to live to be included in the audience.

## Resource Data Model

The data model used to represent an *Audience Analysis* is [`AudienceAnalysis`](../../data-models/resources/user-created/audience-analysis.md)

## Endpoints

- [Create Resource](../../endpoints/user-created/audience-analysis/create.md)
- [Read Collection](../../endpoints/user-created/audience-analysis/read-collection.md)
- [Read Resource](../../endpoints/user-created/audience-analysis/read-resource.md)
- [Download Results](../../endpoints/user-created/audience-analysis/download-results.md)
