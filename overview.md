# Overview


This Section gives a quick overview of the main concepts behind Cloud4Wi Geo API and its organization.

## Resources

A Resource is a basic piece of information characterized by some **Attributes**.
This API defines several types of Resources, said **Classes**.
The Most Important one is ***Device***.
A *Device* represents a single installation of a Client App on a phisical device. 
For a User of this API, a *Device* can be seen as the End User of the mobile app as the other Resources related to a *Device* generally represents the User behaviour.

Starting from the *Device* Class, the **Device-related Resource Classes** are defined: they are Resource Classes whose members relate to one specific *Device*.
We are particularly intrested in this category of Resources as they represent the real information provided by Cloud4Wi Geo API:

- ***Detected Position***: Represents a location update received for a *Device*. It provides the geographical location of the *Device* at a given time.
- ***Activity***: Represents a period of time during which the *Device* moved the same way (e.g. walking, running, cycling, automotive, flying, etc.). It provides the indication of the time period as well as the path. It can also represent a period of time during which the *Device* was almost still.
- ***Visit***: Represents a period of time spent within a same geographical area. *Visits* can be seen at different spatial granularities, such as "building", "neighbouroud", "district", "city", etc. Depending on the Spatial Granularity, a *Visit* can represent a visit to a country, or a city, or a visit to a specific venue.
- ***Travel***: Represents the movement (time and path) between two consecutive *Visits* at the same Spatial Granularity. It can represent the home-office path as well as a long journey in a different region or country.
- ***Home Location***: The geographical location where User's home is presumably located.
- ***Work Location***: The geographical location where User's workplace is presumably located.
- ***Living Area***: Represents a geographical area where the User spends most of its time. Depending on the User behavious it could be a large or a small area.

Each Resource Class is characterized by its Attributes.
Ex: an *Activity* has a start and end time, a start and end position, as well as a path, relates to a specific Motion Type, such as walking or running, has a duration, etc.
Some of this attributes are simple numeric attributes, such as the duration of an *Activity*, which are said *Metrics*. 
Others represents instead higher level concepts, such as the path of an *Activity*.

## Resource Selection

The main goal of this API is to allow a flexible and extensible way for selecting Resources according to their attributes, regardless of whether they are simple Metrics or represents "high level" concepts.
For this purpose, we generalized the concept of Resource Attribute in order to derive common **Dimensions** that are of interest for several Classes of Resources.
The most important ones are ***Space***, ***Time***, and ***Device Base***, where the latter refers to the whole set of *Devices*.
For each of these Dimensions, the API allows to perform flexible selections.

- ***Space*** 
    - Indicate any geographical area *Ai*
    - Select Resources that (any combination): 
        -  "fall" inside *A1* (e.g., *Detected Positions* or *Visits* to an area)
        -  "start/end" inside *A2* (e.g., *Travels* or *Activities* from A to B)
        -  "cross" *A3* (e.g., *Activities* of type "walking" across an area)
        
- ***Time***
    - Indicate any time period
        - Indicate on or more intervals (e.g., [*T0*, *T1*] and [*T2*, *T3*] and [*T4*, *T5*]) )
        - Indicate periodic intervals (e.g from the 8-th to the 20-th of each day)
    - Select Resources that (any combination):
        - "fall" inside *T1* (e.g. *Visits* during a period) 
        - "are/were in progress" during *T2* (e.g. *Travels*  that are currently in progress)         
        - "started/ended" during *T3* (e.g. *Travels* that started *T* time ago)
- **Device Base**
    - Indicate a group of devices, from one to the whole set (any combination)
        - Explicitely, through their Ids
        - According to main categories, such as the OS, the specific Client App, etc.
        - Indicating explicit Groups previously created (e.g., only my "premium" Users)

Resources can be selected for two main purposes:

- **Accessing the representation of each selected Resource**: e.g. show me all the Visits to a given area performed by a specific set of devices (from one to all) during last month weekends.
- **Computing aggregated metrics**: e.g., number, total, and average duration of the Visits performed to a given area by a specific set of devices (from one to all) during last month weekends.

## Statistics
For what concerns Device-related Resources, for each Class of Resources it is possible to obtain aggregated metrics through a **Statistic** operation.

When a Statistic is requested for a given Class of Resources, we first indicate the main set which we are interested to, indicating several **Selection conditions**. This operation is said **Selection**.

Then, we can optionally indicate to divide this main set into several sub-sets according to specific criteria and to compute the aggregated metrics for each sub-set in order to compare them. This operation is said **Segmentation**.

As an example, let us consider to select the Visits to a given area performed by the whole device base during a specific period of time.
If we are interested in the total number of Visits, their duration, etc., we do not need to perform any Segmentation. However, we could "segment" the whole set of selected Visits according to the device they are related to in order to understand which Users have performed more visits or spent more time.
We can also divide the whole period of time in several sub-periods and segment Visits according to this sub-periods in order to analyze how the number of Visits, their duration, etc., changes in time, or divide the whole area in sub-areas in order to obtain spatial heatmaps, etc.
It is also possible to perform more than one contemporaneous Segmentations, which allows to inspect, for example, how a given metrics evolve in time and space.

## Conditions on Aggregated Metrics

This API allows to define Conditions as comparison conditions on the aggregated Metrics of a Statistic.
As an example, a Condition might be: *"The number of Visits performed by a specific device to a specific area during a specific period is higher than X*".

Such a condition can be indicated through:
- The specific Resource Class: Visits
- A Selection: specific device, area, and time period
- One or more comparison conditions on one or more aggregated metrics provided by the Statistic: e.g. total duration higher than *X1* and lower that *X2*.

Starting from a single Condition, that refers to a specific Class of Resources, it is possible to combine them with any Boolean expression and to define any complex condition.
E.g., The number of visits to an area is higher than *X* AND the number of travels from a specific area to another specific one is lower than *Y*, etc.

These complex Conditions can be used to:

- **Select Devices (Users)**: Users who live in Rome, have travelled "a lot" during the last year, walk "a lot", often go out during the night in the weekend, and are currently still at home.
- **Define Events to be monitored and perform Actions**: monitor when a User that lives in Rome, AND..., arrives at home. Send an Alert to this URL.

## Trigger Platform

Cloud4Wi Geo Trigger Platform allows to monitor even complex events and to perform one or more actions when they occur.

The event to be monitored is defined through a *Trigger* Resource.
The action(s) to be performed are indicated through an *Hook* Resource.
Each *Hook* can be  linked to several *Triggers*.

### Triggers

A *Trigger* defines the event that has to be monitored.

A *Trigger* mainly provides the following information:

- **basic info**: name, description, labels.
- **active period**: indicates when the *Trigger* has to be active.
- **target**: indicate the devices for which the event has to be monitored. 
- **definition of the event**: defines the event to be monitored by indicating a set of conditions.

#### Active period

The Active period allows to indicate when the *Trigger* has to be active.
It allows to indicate specific time intervals as well as specific hours of the day and/or days of the week.

#### Event definition and target of a Trigger

The event that has to be monitored is indicated trough a set of conditions, each of which is expressed as a comparison conditions on one or more Aggregated Metrics of a Statistic.
Conditions can be combined by means of any Boolean opeation.

A *Trigger* can indicate a simple event, such as a simple "enters and dwells" geofence, but also a complex event such as "a User that lives in Rome, travles "a lot", and often visits Milan, is just back home after a travel from Milan to Rome".

A *Trigger* can indicate an event that involves more than one device, such as "the number of Users in this area is higher than *X*". In particular, it can involve any sub-set of the whole device-base, said *Device Base* Segment, from one device to all of them.

Finally a single *Trigger* Resource can indicate several different "targets" at the same time, such as "each device of my device-base".

In detail:

- The set of conditions that define the event does not specifically indicate any "target" device or group of devices. They are said **Untargeted Conditions**.
- The set of Untargeted Conditions can be assigned to any set of devices, said *Device Base* Segment, from one to the whole device base.
- The Target of a Trigger can indicate one or more *Device Base* Segments; each Segment is assigned as "target" to the set of conditions and the event is "replicated" and monitored for each of them.

 


## Hooks

A *Hook* indicates an action to perform.
*Hooks* can be linked to *Triggers* when these are created.
The action indicated by the *Hook* is then performed each time the event defined by the *Trigger* occurs.

The following type of *Hooks* are defined:

- ***Web Hook***: Allows to receive an *Web Notification* through an HTTP Request to a speficied URL. The Request will contain information to get informed about:
    - the *Trigger* that generated the *Web Notification* 
    - the specific Target for which the event defined by the *Trigger* occurred

