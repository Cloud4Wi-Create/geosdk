# AudienceAnalysis

Data Model used to represent a [*Audience Analysis*](../../../resources/user-created/audience-analysis.md) Resource.

## Fields Specification

The `AudienceAnalysis` data model contains all the fields common to any [Batch Analysis resource data model](../../resources/user-created/batch-analysis.md).

In addition, the following fields are contained by an `AudienceAnalysis` data model

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
or | [`[ANDAudienceBlock]`](#andaudienceblock) | At least one item is required | An array of `ANDAudienceBlock` | indicates a set of sub-audiences whose union represents the desired audience, according to an OR logic condition.

## ANDAudienceBlock

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
and | [`[BasicAudienceBlock]`](#basicaudienceblock) | At least one item is required | An array of `BasicAudienceBlock` | indicates a set of sub-audiences whose intersection represents the desired audience, according to an AND logic condition.

## BasicAudienceBlock

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
type | `String` | Mandatory | {`"geoBehavioural"`; `"geoDemographics"`} | Indiates the type of [*Audience Analysis*](/api/reference/resources/resources/user-created/audience-analysis.md) requested
geoBehavioural | [`GeoBehavioral-Audience`](#geobehavioural-audience) | Mandatory if `"type"` is equal to `"geoBehavioural"`; neglected otherwise | Contains the details of the [GeoBehavioral-Audeince](/api/reference/resources/resources/user-created/audience-analysis.md#geo-behavioural-audience)
geoDemographics | [`GeoDemographics-Audience`](#geodemographic-audience) | Mandatory if `"type"` is equal to `"geoDemographics"`; neglected otherwise | Contains the details of the [GeoDemographics-Audeince](/api/reference/resources/resources/user-created/audience-analysis.md#geo-demographic-audience)

### GeoBehavioural-Audience

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
criteria | `[String]` | At least one item is required | {`"visited"`;`"passedThrough"`;`"live"`;`"work"`} | Indicates the criteria that have to be used to select devices
pois | [`Target-POIs`](../../common/target-pois.md) | Mandatory | Any valid [`Target-POIs`](/api/reference/data-modelsata-models/common/target-pois.md) | Indicates the pois that have to be used to select devcices
period | [`Time-Segment`](../../d-segment/time) | Mandatory | any valid [`Time-Segment`](/api/reference/data-models/d-segment/time) | Indicates the period thata has to be used to select devices
reachLevel | `Number` | Mandatory | {`1`;`2`;`3`} | Indiates the reach level for the audience. The higher the value for this field, the more devices will be included in the audience
lookAlike | [LookAlike](#lookalike)| Optional | Any valid `LookAlike` object | indicates to include devices according to a look-alike criterion

#### LookAlike
Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
byHomeLocation | Boolean | Optional | any Boolean value | If `true` indicates to add users that live in proximity of selected users.

### GeoDemographic-Audience

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
socioDemo | [`UserProfile-Segment`](../../r-segment/profile.md) | Any valid `UserProfile-Segment` | A segment of `UserProfile` resources used to indicate users that have a given profile
geo | [`AdministrativeAreaSegment`](../../d-segment/administrative-area.md) | An array of `AdministrativeAreaSegment` | an array of objects, each of which indicates one or more administrative areas.


## Example AudienceAnalysis Object

```json
{
	"id": "audienceAnalysis1",
	"name": "my audience analysis",
	"description": "my first audience analysis",
	"labels": ["test", "geoBehavioural"],
	"status": "succeeded",
	"startedAt": "2020-01-01T00:00:00Z",
	"submittedAt": "2020-01-01T00:01:00Z",
	"endedAt": "2020-01-01T01:00:00Z",
	"hook": {
		"type": "web",
		"web": {
			"url": "https://mydomain.com/gu-hooks/analysis"
		}
	},
	"or": [{
		"and": [{
			"type": "geoBehavioural",
			"geoBehavioural": {
				"criteria": ["live", "work", "passedThrough"],
				"pois": {
					"standard": {
						"category": ["category1"],
						"brand": ["brand1"],
						"administrativeArea": [{
							"conutry": "IT",
							"area": {
								"level": "Regione",
								"name": ["Campania", "Basilicata"]
							}
						}]
					},
					"custom": {
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
					"intervals": [{
						"from": {
							"absolute": "2020-01-01T00:00:00Z"
						},
						"to": {
							"absolute": "2020-04-01T00:00:00Z"
						}
					}]
				},
				"reachLevel": 2
			}
		}]
	}]
}
```
