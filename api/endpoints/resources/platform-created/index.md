# Platform-created Resource Endpoints

Set of endpoints that allow to access (READ) [Platform-created resources](/api/resources/platform-created/index.md).
These endpoints allow to perform flexible selections on the whole set of resources of a given class.
To this end, they all use the HTTP `POST` method. The request body will carry an [`R-Segment`](/api/data-models/r-segment/index.md) to indicates the desired selection.

According to the specific Resource Class R, the following endpoints are provided:


* [`Device`](api/endpoints/resources/platform-created/device.md)
* [Device Related](api/endpoints/resources/platform-created/device-related/index.md)
    * [`DetectedPosition`](api/endpoints/resources/platform-created/device-related/detected-position.md)
    * [`Activity`](api/endpoints/resources/platform-created/device-related/activity.md)
    * [`Visit`](api/endpoints/resources/platform-created/device-related/visit.md)
    * [`Travel`](api/endpoints/resources/platform-created/device-related/travel.md)
    * [`HomeLocation`](api/endpoints/resources/platform-created/device-related/home-location.md)
    * [`WorkLocation`](api/endpoints/resources/platform-created/device-related/work-location.md)
    * [`LivingArea`](api/endpoints/resources/platform-created/device-related/living-area.md)
    * [`Flight`](api/endpoints/resources/platform-created/device-related/flight.md)
* [`Triggerlog`](api/endpoints/resources/platform-created/triggerlog.md)


 


