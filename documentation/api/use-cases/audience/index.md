* [Documentation Home](../../../README.md)
   * [Web API](../../index.md)
      * [Use Cases](../index.md)

# Audiences

This section provides several examples explaining how to use the API to build audiences. 

## Reference Documentation

* [Audience Analysis Resource](../../reference/resources/user-created/audience-analysis.md)
* [Audience Analysis Endpoints](../../reference/endpoints/resources/user-created/audience-analysis/index.md)

## Main steps

Audiences can be obtained through [batch analysis](../../reference/resources/user-created/batch-analysis.md) requested via the Web API.
The first step consist of creating an [Audience Analysis Resource](../../reference/resources/user-created/audience-analysis.md) 
via the [related endpoint](../../reference/endpoints/resources/user-created/audience-analysis/create.md).

> Example request
```
  curl --request POST \
    --url https://api.geouniq.com/v1/audiences/analysis \
    --header 'authorization: Bearer <ACCESS_TOKEN>' \
    --header 'content-type: application/json' \
    --data '{"name":"my audience analysis","description":"my first audience analysis","labels":["test","geoBehavioural"],"hook":{"type":"web","web":{"url":"https://mydomain.com/gu-hooks/analysis"}},"type":"geoBehavioural","geoBehavioural":{"criteria":["live","work","passedThrough"],"pois":{"standard":{"category":["category1"],"brand":["brand1"],"administrativeArea":[{"conutry":"IT","area":{"level":"Regione","name":["Campania","Basilicata"]}}]},"custom":{"type":"FeatureCollection","features":[{"type":"Feature","properties":{"id":"Place 1","circles":[{"center":{"lat":10.0,"lng":10.0},"radius":15}]},"geometry":null}]}},"period":{"intervals":[{"from":{"absolute":"2020-01-01T00:00:00Z"},"to":{"absolute":"2020-04-01T00:00:00Z"}}]},"reachLevel":2}}'
  ```
  
> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

The API will reply immediately with a `201 Created` HTTP response whose body will contain the created resource, 
which includes an ID.

Once created, the analysis will be ran asynchronously and results will be available for the download, 
in the form of files, through the [related endpoint](../../reference/endpoints/resources/user-created/audience-analysis/download-results.md).

> Example response. 
> The field `"or"`, which specifies the audience conditions, is left empty in the example.

```json
{
	"id": "audienceAnalysis1",
	"name": "my audience analysis",
	"description": "my first audience analysis",
	"labels": ["test", "geoBehavioural"],
	"status": "starting",
	"startedAt": "2020-01-01T00:00:00Z",
	"submittedAt": "2020-01-01T00:01:00Z",
	"endedAt": "2020-01-01T01:00:00Z",
	"hook": {
		"type": "web",
		"web": {
			"url": "https://mydomain.com/gu-hooks/analysis"
		}
	},
	"or": []
}

```

Once created, it is possible to get the [status of the analysis](../../reference/resources/user-created/batch-analysis.md#analysis-lifecycle) 
through the [related endpoint](../../reference/endpoints/resources/user-created/audience-analysis/read-resource.md)
providing its ID.

In addition, it is possible to set a [Hook](../../reference/data-models/common/hook.md) 
to get notified when the analysis terminates.
In particular, it is possible to automate results download by setting 
a [Web Hook](../../reference/data-models/common/hook.md#webhook) and receiving a notification
through an HTTP request to a URL of your choice.

Read [here](../receiving-web-hooks.md) for details on how to receive a Web Hook.

> Example Audience Analysis with a Web Hook. 
> The field `"or"`, which specifies the audience conditions, is left empty in the example.

```json
{
	"name": "my audience analysis",
	"description": "my first audience analysis",
	"labels": ["test", "geoBehavioural"],
	"hook": {
		"type": "web",
		"web": {
			"url": "https://mydomain.com/gu-hooks/analysis"
		}
	},
	"or": []
}
```

## Examples of Audiences Analysis

### Geo-behavioural audience

The following example shows the body for an Audience Analysis of type Geo-behavioural.
The audience indicates the `"visited"` criterion (see field `"criteria"`), 
to identify devices that have visited the set of indicated POIs.
A selection of "standard" (i.e., "built-in") POIs is provided by indicating a category 
and two Italian regions. 

```json
{
	"name": "my audience analysis",
	"description": "my first audience analysis",
	"labels": ["test", "geoBehavioural"],
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
				"criteria": ["visited"],
				"pois": {
					"standard": {
						"category": ["bar and restaurants"],
						"administrativeArea": [{
							"conutry": "IT",
							"area": {
								"level": "Regione",
								"name": ["Campania", "Basilicata"]
							}
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

### Geo-demographics audience

The following example shows the body for a geo-demographic audience.
The body indicates the following socio-demographic attributes

* **High income** `"income":{"inside":[2]}` selects only users with `"income"` value equals to `2`, 
which means "high" (attributes values are `0`, `1` and `2`). 
* **Few family members** `"familyMembers":{"inside":[0]}` selects only users with `"familyMembers"` value equals to `0`,
which means "low" (attributes values are `0`, `1` and `2`). 

Thus, only users that both have a high income and few family members are selected.
In addition, the field `"geo"` indicates a set of geo-political areas where users have to live. 

```json
{
	"name": "my audience analysis",
	"description": "my first audience analysis",
	"labels": ["test", "geoBehavioural"],
	"hook": {
		"type": "web",
		"web": {
			"url": "https://mydomain.com/gu-hooks/analysis"
		}
	},
	"or": [{
		"and": [{
            "type": "geoDemographics",
            "geoDemographics": {
              "socioDemo": {
                  "income": {"inside": [2]},
                  "familyMembers": {"inside": [0]}
              },
              "geo": {
                 "administrativeArea": [{
                    "conutry": "IT",
                    "area": {
                        "level": "Regione",
                        "name": ["Campania", "Basilicata"]
                    }
                }]
              }         
           }    
        }]
	}]
}
```

### Combination of geo-behavioural and geo-demographic audience

The following example shows the body for an Audience Analysis 
that combines a geo-behavioural audience with a geo-demographic audience.
Specifically, the two basic building-blocks are combined according to an AND boolean operation.
The result is an audience composed of devices that both have visited the set of indicated POIs during the indicated period
and that have a given socio-demographic profile.

```json
{
	"name": "my audience analysis",
	"description": "my first audience analysis",
	"labels": ["test", "geoBehavioural"],
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
				"criteria": ["visited"],
				"pois": {
					"standard": {
						"category": ["bar and restaurants"],
						"administrativeArea": [{
							"conutry": "IT",
							"area": {
								"level": "Regione",
								"name": ["Campania", "Basilicata"]
							}
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
		},{
              "type": "geoDemographics",
              "geoDemographics": {
                "socioDemo": {
                    "income": {"inside": [2]},
                    "familyMembers": {"inside": [0]}
                },
                "geo": {
                   "administrativeArea": [{
                      "conutry": "IT",
                      "area": {
                          "level": "Regione",
                          "name": ["Campania", "Basilicata"]
                      }
                  }]
                }         
             }    
          }]
	}]
}
```


 