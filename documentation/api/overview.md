* [Documentation Home](../README.md)
    * [Web API](index.md)

# Overview

This Section gives a quick overview of the main concepts behind GeoUniq Analytics API and its organization.

## Resources

A resource is a basic piece of information characterized by some **attributes**.
This API defines several types of resources.  
They are divided into two main categories:

* **Platform-created resources**. 
Resources automatically created by the platform.
They generally refer to information collected or inferred for mobile devices, 
or to results of some asynchronous job requested to the platform.
This kind of resources can be accessed through a [Selection Operation](#resource-selection-endpoints).
In addition, aggregated metrics can be computed on them through a [Statistic Operation](#statistic-endpoints). 

* **User-created Resources**. 
Resources created by a user of the API.
They generally refer to information useful to manage accounts and projects, or to request an asyncrhonous job to the platform,
such as [batch Analysis](#batch-analysis) or [triggers](#triggers).
Generally, all CRUD operations are allowed for this resource category.  

## Overview of platform-created resources
Among platform-created resources, ***Device*** is the most important one.
A *Device* represents a single installation of a mobile application on a physical device.
For a User of this API, a *Device* can be seen as the End User of the mobile app 
as the other resources related to a *Device* generally model the User behaviour.

Starting from *Device*, **Device-related resources** are defined, which model information related to a *Device*.
Device-related Resources represent the information from which complex analytics and insights can be derived.

A non exhaustive list of device-related resources is shown below.

* ***Position***.  
Represents a location update received for a *Device*. 
It provides the geographical location of the *Device* at a given time.

* ***Visit***.  
Models a period of time spent within a same geographical area. 
*Visits* can be seen at different spatial granularity levels, 
such as "building", "neighborhood", "district", "city", etc. 
Depending on the Spatial Granularity, 
a *Visit* can represent a visit to a country, or a city, or a visit to a specific venue.

* ***Journey***. (Not available yet):   
Models the time period and the spatial path from two consecutive *Visits* at the same spatial granularity.

* ***Home Location***.   
Models the geographical location where User's home is presumably located.

* ***Work Location***.   
Models the geographical location where User's workplace is presumably located.

Each resource is characterized by its attributes: 
e.g. a *Visit* has a time period (start and end time), a reference position, a duration, etc.
Some of these attributes are simple numeric attributes, such as the duration of a *Visit*, 
which are said *Metrics* and can be aggregated when requesting a [Statistic](#statistics). 
Others represent instead higher level concepts, such as the time period of a *Visit*.

## Resource Selection

The main goal of this API is to allow a flexible and extensible way for selecting resources according to their attributes, 
regardless of whether they are simple metrics or more complex attributes.
For this purpose, the API defines a set of **dimensions** 
that are common to several resources.
A dimension relates to the type of data used to represent resource attributes.
This API defines both simple dimensions, such as **Boolean**, **Number**, **String**, etc., 
and complex ones, such as ***Space***, ***Time***, and ***Device Base***, where the latter refers to the whole set of *Devices*.
For each of these dimensions, the API allows performing flexible selections.

- ***Space*** 
    - Indicate any geographical area *Ai*
    - Select Resources that (any combination): 
        -  "fall" inside *A1* (e.g., *Positions* or *Visits* to an area)
        -  "start/end" inside *A2* (e.g., *Journeys* from A to B)
        -  "cross" *A3* (e.g., *Journeys* across an area)
        
- ***Time***
    - Indicate any time period
        - Indicate on or more intervals (e.g., [*T0*, *T1*] and [*T2*, *T3*] and [*T4*, *T5*]) )
        - Indicate periodic intervals (e.g from the 8-th to the 20-th of each day)
    - Select Resources that (any combination):
        - "fall" inside *T1* (e.g. *Visits* during a period) 
        - "are/were in progress" during *T2* (e.g. *Visits* that are currently in progress)         
        - "started/ended" during *T3* (e.g. *Visits* that started *T* time ago)
- **Device Base**
    - Indicate a group of devices, from one to the whole set (any combination)
        - Explicitly, through their IDs
        - According to main categories, such as the OS, the specific Client App, etc.

## Resource Selection endpoints
Selection endpoints allow to get the details of a set of resources of a given type by indicating a 
[Selection](#resource-selection).
E.g. Get all the Visits to a given area performed by a specific set of devices (from one to all) during last month weekends.

## Statistic endpoints

Statistic endpoints allow computing aggregated metrics for a given set of Resources.
E.g., get the number, total, and average duration of the Visits performed to a given area 
by a specific set of devices (from one to all) during last month weekends.

A statistic request contains a [selection](#resource-selection) indicating the main set of resources 
that must be included in the statistic.
Then, it can optionally indicate to divide this main set into several sub-sets according to specific criteria,
 and to compute the aggregated metrics for each sub-set in order to compare them. 
This operation is said **segmentation**.

As an example, let us consider selecting the Visits to a given area performed by the whole device base during 
a specific period.
If we are interested in the total number of Visits, their duration, etc., we do not need to perform any segmentation. 
However, we could "segment" the whole set of selected Visits according to the device they relate to 
in order to understand which Users have performed more visits or spent more time.
We can also divide the whole period of time in several sub-periods and segment Visits according to this sub-periods 
in order to analyze how the number of Visits, their duration, etc., changes in time, 
or divide the whole area in sub-areas in order to obtain spatial heatmaps, etc.
It is also possible to perform more than one contemporaneous segmentations, which allows inspecting, for example, 
how a given metric evolve in time and space.

## Batch Analysis

Batch analysis are analysis requested to the analytics platform via Web API that are performed asynchronously.  
Batch analysis allow:
* Selecting old data no longer available through a synchronous request.
* Requesting more jobs at the same time (e.g., several [statistic operations](#statistics) 
on different resource types in a single request)
* Requesting complex insights that are not available at all through synchronous requests.

Batch analysis can be requested via specific endpoints of this API.
The platform takes care of running the requested analysis.
The status of each analysis can be monitored via specific endpoints.
When terminated, results can be downloaded in thr form of files.
When a batch analysis is requested, it is also possible to indicate a Hook (e.g., a web hook) 
to receive a notification when the analysis terminates. 
  
## Tools for Advertising

GeoUniq analytics platform provides several tools for advertising, all accessible via Web API.

### Audience Analysis
*Audience Analysis* are batch analysis aimed at identifying devices (individuals)
 with given characteristics or that have shown specific behaviours.
The result of an *Audience Analysis* is a set of Advertising IDs (ADIDs) that can be used to deliver advertising to mobile devices.

### Advertising Campaigns

An *Advertising Campaign* is a user-created resource that models an advertising campaign for drive-to-store.
By creating an *Advertising Campaign*, it is possible to monitor and measure the performance of a campaign 
 in terms of visits and visitor to the target stores, as well as in terms of visit and visitor uplift.
 
The *Advertising Campaign* has to contain the set of locations that correspond to the target stores, 
as well as the period during which the campaign is delivered.

Two different *Advertising Campaign* can be created:

* ***Mobile Campaigns***: models campaigns delivered via mobile apps or other web media.

* ***Out-Of-Home (OOH) Campaigns***: models campaigns delivered via billboards. 

#### Mobile Campaigns
The User takes care of the actual delivering of the advertising (via DSPs or other tools), 
using an audience computed via an [*Audience Analysis*](#audience-analysis) or any other audience.

Then, it is possible to make GeoUniq platform receive the details of the impressions delivered to mobile devices 
by configuring a pixel into the advertising banner.
The platform will automatically identify all visits performed by exposed devices to the target stores of the campaign 
and will create related resources available both for being obtained through a [selection request](#resource-selection-endpoints) 
or referred in a [statistic request](#statistic-endpoints).
This way, it is possible to monitor the performance of a Campaign while it is still in progress. 

#### OOH Campaign
OOH campaigns are characterised by the set of areas where the advertising billboards are located, 
in addition to the target POIs of the campaign.
The User takes care of the actual delivering of the advertising, whilst the platform takes care of identifying 
the devices exposed to the advertising by identifying devices that crossed the billboard areas 
during the period of the campaign.
Thus, unlike Mobile Campaigns, the set of exposed devices is directly identified by the platform.

For all other aspects, OOH Campaigns work like Mobile Campaigns, 
including the possibility of activating a real-time monitoring of the visits performed by exposed devices to the target POIs, 
as well as the possibility of obtaining the final report through a Footfall Analysis.

### Footfall Analysis

A ***Footfall Analysis*** in an analysis related to a specific Campaign.
It allows measuring the performance of the campaign once it is terminated.  
More in detail, a Footfall Analysis provide a report with the number of visits and visitors of the target POIs
of the campaign.
Moreover, it allows comparing the set of devices exposed to the advertising, 
coming from the set of delivered impressions, with a control group, 
thus providing a visit and visitor uplift for the campaign.  
In addition, a Footfall Analysis can also provide insights on the profile of visitors 
and compare different groups of exposed devices, for example to compare different audiences included 
in the campaign or different advertising creatives.

## Triggers

**Triggers** provide a way of monitoring events of various types related to an individual.
Triggers can refer to simple events, like "entering/exiting a geofence", or more complex ones, 
like "leaving home", "reaching work", "commuting from work to home", or even "is shopping".

A Trigger can be configured to have a specific validity period, including specific hours of the day and/or days if the week,
or be valid indefinitely.
In addition, it can be configured for a specific set of devices or for the whole device base.

When the event defined by a trigger happens (e.g., a device enters a geofence), 
the platform always creates a **Trigger Log** resource referring the specific Trigger, 
the involved device, and the time when it happened.
Like all other [platform-created resources](#resources), it is possible to access the details of trigger logs
through a [selection request](#resource-selection-endpoints) or to obtain a aggregated metrics 
through a [statistic request](#statistic-endpoints).

In addition to Trigger Logs, it is possible to configure an **Hook** to get notified of a trigger.
For example, it is possible to configure a **Web Hook** 
to receive the details of the event through an HTTP request to a specific URL.



