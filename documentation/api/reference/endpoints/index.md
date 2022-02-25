* [Documentation Home](../../../README.md)
    * [Web API](../../index.md)  
      * [Reference](../index.md)

# Endpoints

This Section documents the various endpoints provided by this API.

For all of them, it holds the following.

**PROTOCOL**: `https`

**HOST NAME**: `api.geouniq.com`

**PATH ENTRY POINT**: `/v1`

**EXAMPLE URL**: `https://api.geouniq.com/v1/<ENDPOINT_SPECIFIC_PATH>`

Regardless of the specific endpoint, each request must be authorized according to the 
[authentication and authorization mechanism defined by this API](../general-aspects/auth.md).

In addition, if the endpoint provides for a paginated response, 
[pagination](../general-aspects/pagination.md) must be handled by the client.

## List of endpoints

* [Platform-created resources](platform-created/index.md)
    * [*Device*](platform-created/device/index.md)
    * [Device-related resources](platform-created/device-related/index.md)
        * [*Position*](platform-created/device-related/position/index.md)
        * [*Visit*](platform-created/device-related/visit/index.md)
        * [*HomeLocation*](platform-created/device-related/home-location/index.md)
        * [*WorkLocation*](platform-created/device-related/work-location/index.md)
        * [*UserProfile*](platform-created/device-related/user-profile/index.md)
        * [*NightLifeIndex*](platform-created/device-related/nightlife-index/index.md)
        * [*TrackingSummary*](platform-created/device-related/tracking-summary/index.md)
    * [TriggerLog](platform-created/triggerlog/index.md)
    * [POI](platform-created/poi/index.md)
        
* [User-created resources](user-created/index.md)
    * [*Campaign*](user-created/campaign/index.md)
    * [*Trigger*](user-created/trigger/index.md)
    * *Batch Analysis*
        * [*Insights Analysis*](user-created/insights-analysis/index.md)
        * [*Audience Analysis*](user-created/audience-analysis/index.md)
        * [*Footfall Analysis*](user-created/campaign/footfall/index.md)
