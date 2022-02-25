* [Documentation Home](../../../README.md)
   * [Web API](../../index.md)
      * [Use Cases](../index.md)

# Home and Work Location

Home and Work Location respectively represent the geographical location where a User presumibly resides and works.
This information is periodically recomputed for each device by GeoUniq Analytics platform.
However, no temporal information is kept for this kind of [resource types](../../overview.md#resources), 
meaning that no history of the identified Home/Work location is associated to *Devices*.
Instead, for each *Device*, only the current Home/Work location(s) are provided.

> The data models used to represent a Home and a Work location are identical 
>(see [Home](../../reference/data-models/resources/platform-created/device-related/home-location.md)
> and [Work](../../reference/data-models/resources/platform-created/device-related/work-location.md)) 

For each *Device*, more than one Home/Work locations might be identified (currently at most three).
However, only one of this locations will be indicated as *"primary"*, meaning that it is the Home/Work location where the User spends more time.
If only one location is identified, than that location will be be indicated as *"primary"* as well.
It is also possible that no Home/Work location is available for a *Device*. This generally happens for *Devices* that are no longer active.

## Use Cases

* [Retrieving the Home/Work Locations of one or more specific device](resources.md)
* [Getting a spatial heatmap of Home/Work locations](heatmap.md)
* [Finding Users who reside/work in a given area](users.md)