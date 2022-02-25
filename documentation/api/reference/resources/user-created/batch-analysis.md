* [Documentation Home](../../../../README.md)  
  * [Web API](../../../index.md)  
    * [Reference](../../index.md)
        * [Resources](../index.md)
           * [User-created Resources](index.md)
           
# Batch Analysis

This section lists [User-created Resources](index.md) that represents batch analysis requested to the platform.

A batch analysis is an analysis requested to GeoUniq Analytics platform, via Web API, that is performed asynchrounsly.

There are several kinds of batch analysis, each of which can be requested through a different endpoint.
All kinds of batch analysis share some common logic:

* Allow analysis on a large amount of data
* Allow analysis on hstorical data no longer available from the standard API endpoints
* Allow complex analysis not directly provided by any standard API endpoint
* Allow setting hooks to be notified when the analysis finishes

# Common aspects

## Steps

1. Create an Analysis
2. (optional) Upload input files
3. Submit analysis
4. (Optional) Check the status of the analysis
5. Download the results

> If an hook is set, then a notification will be sent to that hook as soon as the analysis is completed

## Analysis lifecycle

* possible statuses: `waitingForInput`, `submittable`, `starting`, `running`, `succedeed`, `failed`

1. analysis created -> `waitingForInput` (`submittable` if no input file is expected)
2. input uploaded -> `submittable`
3. analysis submitted -> `starting`
4. the platform starts the analysis -> `running` 
5. the analysis terminates 
	1. correctly -> `succedeed` 
	1. with error -> `failed`


# List of Batch Analysis

* [Insights Analysis](insights-analysis.md): allows obtaining insights of various types
* [Audience Analysis](audience-analysis.md): allows obtaining a list of Advertising IDs for advertising campaigns
* [Footfall Analysis](campaign-footfall.md): allows measuring the performance of an advertising campaign
