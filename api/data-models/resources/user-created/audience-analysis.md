# AudienceAnalysis

Data Model used to represent a [*Audience Analysis*](/api/resources/user-created/audience-analysis.md) Resource.

## Fields Specificcation

The `AudienceAnalysis` data model contains all the fields common to any [Analysis Resource data model](/api/data-models/resources/user-created/batch-analysis.md).

In addition, the following fields are contained by an `AudienceAnalysis` data model

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
type | `String` | Mandatory | {`"geoBehavioural"`; `"geoDemographics"`} | Indiates the type of [*Audience Analysis*](/api/resources/user-created/audience-analysis.md) requested
geoBehavioural | [`GeoBehavioral-Audience`](#geobehavioural-audience) | Mandatory if `"type"` is equal to `"geoBehavioural"`; neglected otherwise | Contains the details of the [Geo-Behavioral Audeince Analysis](/api/resources/user-created/audience-analysis.md#geo-behavioural-audience-analysis)
geoDemographics | [`GeoDemographics-Audience`](#geodemographics-audience) | Mandatory if `"type"` is equal to `"geoDemographics"`; neglected otherwise | Contains the details of the [Geo-Demographics Audeince Analysis](/api/resources/user-created/audience-analysis.md#geo-demographic-audience-analysis)

## GeoBehavioural-Audience

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
criteria | `[String]` | At least one item is required | {`"visited"`;`"passedThrough"`;`"live"`;`"work"`} | Indicates the criteria that have to be used to select devices
pois | [`Target-POIs`](/api/data-models/common/target-pois.md) | Mandatory | Any valid [`Target-POIs`](/api/data-models/common/target-pois.md) | Indicates the pois that have to be used to select devcices
period | [`Time-Segment`](/api/data-models/d-segment/time) | Mandatory | any valid [`Time-Segment`](/api/data-models/d-segment/time) | Indicates the period thata has to be used to select devices
reachLevel | `Number` | Mandatory | {`1`;`2`;`3`} | Indiates the reach level for the audience. The higher the value for this field, the more devices will be included in the audience

## GeoDemographic-Audience

Coming soon

## Example GeoBehavioural-Audience Object

```json
{
    "id":"audienceAnalysis1",
    "name":"my audience analysis",
    "description": "my first audience analysis",
    "labels": ["test", "geoBehavioural"],
    "status": "succeeded",
    "startedAt": "2020-01-01T00:00:00Z",
    "submittedAt": "2020-01-01T00:01:00Z",
    "startedAt": "2020-01-01T00:02:00Z",
    "endedAt": "2020-01-01T01:00:00Z",
    "hook": {
        "type":"web",
        "web":{
            "url":"https://mydomain.com/gu-hooks/analysis"
        }
    },
    "type":"geoBehavioural",
    "geoBehavioural":{
        "criteria":["live", "work", "passedThrough"],
        "pois":{
            "standard": {
                "category":["category1"],
                "brand":["brand1"],
                "administrativeArea":[{
                "conutry":"IT",
                    "area":{
                        "level":"Regione",
                        "name":["Campania", "Basilicata"]
                    }
                }]
            },
            "custom":{
                "type": "FeatureCollection",
                "features": [{
                    "type": "Feature",
                    "properties": {
                        "id": "Place 1",
                        "circles": [{
                            "center": {
                                "lat": 10.0,
                                "lng": 10.0
                            },
                            "radius": 15
                        }]
                    },
                    "geometry": null
                }]
            }
        },
        "period": {
            "intervals":[{
                "from":{
                    "absolute": "2020-01-01T00:00:00Z"
                },
                "to":{
                    "absolute": "2020-04-01T00:00:00Z"
                }
            }]
        },
        "reachLevel": 2
    }
}
```
