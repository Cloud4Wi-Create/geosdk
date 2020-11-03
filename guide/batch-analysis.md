# Batch Analysis

## Intro

Functionality to request batch analysis of various types and receive results through files

The functionality is designed to:

* Allow analysis on a large amount of data
* Allow analysis on hstorical data no longer available from the standard API endpoints
* Allow complex analysis not directly provided by any standard API endpoint
* Allow very large inputs by files (useful if an analysis involves thousands of points of interests)
* Allow setting hooks to be notified when the analysis finishes

## API overview

### Steps

1. Create an Analysis
2. (optional) Upload input files
3. Submit analysis
4. (Optional) Check the status of the analysis
5. Download the results

> If an hook is set, then a notification will be sent to that hook as soon as the analysis is completed

### Analysis lifecycle

* possible statuses: `waitingForInput`, `submittable`, `starting`, `running`, `succedeed`, `failed`

1. analysis created -> `waitingForInput` (`submittable` if no input file is expected)
2. input uploaded -> `submittable`
3. analysis submitted -> `starting`
4. the platform starts the analysis -> `running` 
5. the analysis terminates 
	1. correctly -> `succedeed` 
	1. with error -> `failed`


### Types of Analysis

The following type of analysis are defined.

* **Resource Selection**: Allows to [select (extract) Resources](https://gitlab.com/geouniq/documentation/blob/master/api/concepts/resource-selection.md), similarly to a Selection Endpoint (see [here](https://gitlab.com/geouniq/documentation/blob/master/api/endpoints/resources/platform-created/index.md)). Several different Selections can be requested in a single Analysis, which allows to get the same information that, if requested through the standard API Selection Endpoints, would require multiple different (paginated) requests. Each Selection is indicated in a different Job (see the [Analysis data model](#data-models)). Jobs are independednt from each other.

* **Statistic**: Allows to perform [Statistic operations](https://gitlab.com/geouniq/documentation/blob/master/api/concepts/statistics.md) on Resources, similarly to a Sattistic Endpoint (see [here](https://gitlab.com/geouniq/documentation/blob/master/api/endpoints/statistics/index.md)). Several different Statistics can be requested in a single Analysis, which allows to get the same information that, if requested through the standard API Statistic Endpoints, would require multiple different (paginated) requests. Each Statistic is indicated in a different Job (see the [Analysis data model](#data-models)). Jobs are independednt from each other.

* **Cutom User Profiling**: Very similar to a Statistic Analysis, but each Job implcitely indicates to perform a [Segmentation Operation](https://gitlab.com/geouniq/documentation/blob/master/api/concepts/statistics.md#segmentation-operation) ["by device"](https://gitlab.com/geouniq/documentation/blob/master/api/dimensions/device-base.md#by-device). This kind of analysis is aimed at identifying the set of devices that show a behaviour of interest. As an example, if we are interested in users that "like cinema", we can request a Statistic operation to obtain the count of Visits of each device to the main cinemas in a given area (by providing a spatial selection that contains the correct cinemas' locations) and use the result as a ranking.

* **Resource Selections With User Profiling**: This kind of analysis combines a Resource Selection Analysis with a User profiling one. In detail, the "profiling" jobs are executed only for those devices for which at least one Rersource has been found through the Resource Selection Jobs. Fo example, it allows to obtain all the Visits to a set of places and, for each visiting device, the profiling informations. In addition to the Cutom User Profiling, it also allows to request "Srandard" profiling information (see [here](#standardprofilingjob-data-model))


## API details

### Create an analysis

Allows to create an *Analysis* resource.
Input files, if needed, must be uploaded with different requests

**Endpoint:** `POST /analysis`

**Request Body:** [`Analysis`](#analysis-data-model)

**Response Body**: The created *Analysis* resource with the `id`, `createdAt`, and `status` fields

**Additional fields**

Field | Type | Description
-------|-------|-------
id | `String` | The ID of the Analysis resource
createdAt | [`DateTime`](https://gitlab.com/geouniq/documentation/blob/master/api/data-models/common/date.md) | Indicates when the Analysis has been created.
status | `String` | Indicates the status of the Analysis. Possible values: [`"waitingForInput"`, `"submittable"`, `"starting"`, `"running"`, `"succedeed"`, `"failed"`]

```json
{
	"id": "a01bc",
	"createdAt": "2018-10-01T07:21:35Z",
	"status": "waitingForInput",
	"name": "myFirstanalysis",
	"description": "test analysis",
	"labels": ["test"],
	"type": "ResourceSelectionsWithUserProfiling",
	"hook": {},
	"jobs": [{}],
	"inputFiles": [{}]
}
```

> The `id` field allows to perform the other requests for the specific analysis


#### Examples 

##### `Analysis` Object of type `"ResourceSelection"` to extract `DetectedPosition` Resources of specific devices

The Analysis contains a Selection Job to extract all the `DetectedPosition` of one ore more specific devices

```json
{
	"name": "Example Analysis for specific devices's data",
	"description": "An example analysis to get all the positions detected for a set of specific devices",
	"labels": ["example", "positions of devices"],
	"type": "ResourceSelection",
	"hook": {
		"type": "web",
		"web": {
			"url": "https://api.mydomain.com/geouniqhooks"
		}
	},
	"jobs": [{
		"identifier": "positions",
		"type": "selection",
		"selection": {
			"resource": "detectedPosition",
			"detectedPosition": {
				"deviceBase": {
					"inside": {
						"deviceId": ["DeviceID1", "DeviceID2"]
					}
				}
			}
		}
	}]
}
```

##### `Analysis` Object of type `"ResourceSelection"` to extract `DetectedPosition` Resources in a given time interval

The Analysis contains a Selection Job to extract all the `DetectedPosition` in a given time interval.


```json
{
	"name": "Example Analysis",
	"description": "An example analysis to get all the positions detected during a give time period",
	"labels": ["example", "positions"],
	"type": "ResourceSelection",
	"hook": {
		"type": "web",
		"web": {
			"url": "https://api.mydomain.com/geouniqhooks"
		}
	},
	"jobs": [{
		"identifier": "positions",
		"type": "selection",
		"selection": {
			"resource": "detectedPosition",
			"detectedPosition": {
				"time": {
					"start": {
						"intervals": [{
							"from": {
								"absolute": "2018-01-01T00:00:00Z"
							},
							"to": {
								"absolute": "2018-12-31T00:00:00Z"
							}
						}]
					}
				}
			}
		}
	}]
}
```


##### `Analysis` Object of type `"ResourceSelectionsWithUserProfiling"`

Three different input files are indicated to provide a large set of points of interest (POIs) to the three Jobs.
The Analysis contains a Selection Job to extract Visits to a set of "primary" POIs, said "outlets". Then defines two different Custom Profiling Jobs.  
The first one, indicated as `"visitedPOIsCategories"`, allows to "profile" devices according to how many Visits each of them has performed to different categories of POIs, such as cinemas, fitness centers, etc. The second one, indicated as `"ski"`, is specific for Visits to large ski areas.  
The reason for two different Jobs is that, since the ski areas are large areas, whilst the first Job considers specific venues, the two Jobs have to select Visits Resources at different Granularity levels.  
Note that, both Jobs indicate to select Visits at the "best fit" Spatial Granularity. However, when using the `"bestFit"` value for the Spatial Granularity attribute of a Visit, the smallest area is considered to derive the Spatial Granularity value that fits best.  


```json
{
	"name": "Example Analysis",
	"description": "An example analysis to get a) visits to a set of Points Of Interst (POI); b) profiling info for each visiting device",
	"labels": ["example", "visits"],
	"type": "ResourceSelectionsWithUserProfiling",
	"hook": {
		"type": "web",
		"web": {
			"url": "https://api.mydomain.com/geouniqhooks"
		}
	},
	"jobs": [{
		"identifier": "outlets",
		"type": "selection",
		"selection": {
			"resource": "visit",
			"visit": {
				"time": {
					"inside": {
						"intervals": [{
							"from": {
								"absolute": "2018-01-01T00:00:00Z"
							},
							"to": {
								"absolute": "2018-12-31T00:00:00Z"
							}
						}]
					}
				},
				"spatialGranularity": {
					"inside": ["bestFit"]
				},
				"duration": {
					"gte": 3600,
					"lte": 7200
				}
			}
		}
	},{
		"identifier": "standardProfiling",
		"type": "standardProfiling",
		"standardProfiling": {
			"homeLocation": true,
			"workLocation": true,
			"age": true,
			"gender": true,
			"purchasingPower": true,
			"nightLifeIndex": true
		}
	},{
		"identifier": "visitedPOIsCategories",
		"type": "customProfiling",
		"customProfiling": {
			"resource": "visit",
			"visit": {
				"select": {
					"time": {
						"inside": {
							"intervals": [{
								"from": {
									"absolute": "2018-01-01T00:00:00Z"
								},
								"to": {
									"absolute": "2018-12-31T00:00:00Z"
								}
							}]
						}
					},
					"spatialGranularity": {
						"inside": ["bestFit"]
					},
					"duration": {
						"gte": 1800,
						"lte": 7200
					}
				},
				"segmentBy": {
					"deviceBase": {
						"inside": {
							"device": 1
						}
					},
					"space": {
						"inside": {
							"category": 1
						}
					}
				},
				"compute": {
					"count": true
				}
			}
		}
	},{
		"identifier": "ski",
		"type": "customProfiling",
		"customProfiling": {
			"resource": "visit",
			"visit": {
				"select": {
					"time": {
						"inside": {
							"intervals": [{
								"from": {
									"absolute": "2018-01-01T00:00:00Z"
								},
								"to": {
									"absolute": "2018-12-31T00:00:00Z"
								}
							}]
						}
					},
					"spatialGranularity": {
						"inside": ["bestFit"]
					},
					"duration": {
						"gte": 86400,
						"lte": 864000
					}
				},
				"segmentBy": {
					"deviceBase": {
						"inside": {
							"device": 1
						}
					},
					"space": {
						"inside": {
							"category": 1
						}
					}
				},
				"compute": {
					"count": true
				}
			}
		}
	}
	],
	"inputFiles": [{
		"identifier": "rome_restaurants.json",
		"encoding": "json",
		"applyTo": [{
			"jobIdentifier": "outlets",
			"dimension": "space",
			"operators": ["inside"]
		}]
	},{
		"identifier": "POIs_for_generic_interests.json",
		"encoding": "json",
		"applyTo": [{
			"jobIdentifier": "visitedPOIsCategories",
			"dimension": "space",
			"operators": ["inside"]
		}]
	},{
		"identifier": "ski_areas.json",
		"encoding": "json",
		"applyTo": [{
			"jobIdentifier": "ski",
			"dimension": "space",
			"operators": ["inside"]
		}]
	}]
}
```


### Upload Input files

Allows to upload the input files for a specific analysis.
Each file must encode a Segment of a specific Dimension, according to what defined in the `inputFiles` field.
How the Segment is encoded in the file depends on the specific Dimension and format type.

**Endpoint:** `POST /analysis/:id/files/:identifier`

**PATH Parameters** 

* **`id`:** the ID of the analysis
* **`identifier`:** the identifier of the input file. It must be equal to the `identifier` of one of the elements in the `inputFiles`  array

**Headers**
* **Content-type:** `multipart/form-data`

**Supported File Encodings**: UTF-8


### Submit an analysis

Inform Geouniq analytics platform that the analysis can be executed.
The API will return a 409 invalid operation if some input file is missing.
The Staus of the analysis will change in `starting` and then in `running`.

**Endpoint:** `POST /analysis/:id/submit`

**Request Body**: No body expected

**Response Body**: The Analysis resource


### List analysis

Allows to get all the analysis of a given User

**Endpoint:** `GET /analysis`

**Response Body**: [Paginated response](https://gitlab.com/geouniq/documentation/blob/master/api/general-aspects/pagination.md). Each `item` is an Analysis resource

```json
{
	"items": [{<Analysis>}],
	"paging": {<Paging>}
}
```

### Read a specific analysis

Allows to get a specific analysis. Useful to check the status

**Endpoint:** `GET /analysis/:id`

**Response Body**: The Analysis resource

### Download results

Allows to get the results of a specific analysis.
Results are provided as a unique file (`tar.gz`), which may contain several files (currently only csv files)

**Endpoint:** `GET /analysis/:id/results`

**Response**:
	* `Content-type: application/gzip`

### Receiving a Web Hook

When a Web Hook is configured for an analysis, an HTTP request will be sent as soon as the analysis completes.

The details of the request are as follows:

**METHOD:** `POST`

**HEADERS**
* `Content-type: application/json`

**BODY**

```json
{
  "analysisID": "AnalysisX",
  "status": "succeeded"
}
```

When the request is received, the status of the analysis can be succeeded or failed.
The analysisID can be used to get the results from [the related endpoint](#download_results)





# Data Models

## `Analysis` data model


Field | Type | Description
-------|-------|-------
name | `String` | OPTIONAL - max 64 characters
description | `String` | OPTIONAL - max 512 characters
labels | `[String]` | OPTIONAL - max 10 items of max 64 characters
type | `String` | any value in [`ResourceSelection`, `Statistic`, `UserProfiling`, `ResourceSelectionsWithUserProfiling`]
hook | `Hook` | OPTIONAL defines an hook through which it is possible to receive notifications when the status of the analysis changes
jobs | `[jobDefinition]` | Indicates the basic jobs that have to be performed. Depending on the specific type of analysis, different type of jobs can be indicated. A Job genrally indicates a Resource Selection or a Statistic
inputFiles | `[InputFileDefinition]` | OPTIONAL. Indicates a set of files that will be provided with successive requests. 

**Genric `Analysis` object**

> The details of the `Hook`, `Job`, and `InputFileDefinition` objects are missing.

```json
{
	"name": "Example Analysis",
	"description": "An example analysis to get a) visits to a set of Points Of Interst (POI); b) profiling info for each visiting device",
	"labels": ["example", "visits"],
	"type": "Type-X",
	"hook": {},
	"jobs": [{}],
	"inputFiles": [{}]
}
```

## `Hook` Object

Field | Type | Description
-------|-------|-------
type | `String` | allowed values: `["web", "email"]`
web | `JSON Object` | only if `type` is `"web"`
web.url | `String` | The (http) URL at witch the notification has to be sent
email | `JSON Object` | only if `type` is `"email"`
email.address | `String` | The email address at witch the notification has to be sent

> Example `EmailHook`

```json
{
	"type": "email",
	"web": null,
	"email": {
		"address": "john.doe@mydomain.com"
	}
}
```

> Example `WebHook`

```json
{
	"type": "web",
	"web": {
		"url": "http://api.mydomain.com/hooks/geouniq"
	},
	"email": null
}
```

## `Job` Object

Field | Type | Description
-------|-------|-------
identifier | `String` | max 64 characters. Used to match input files and as file name for the putput of different Jobs.
type | `String` | Indicates the type of the Job. allowed values are: [`"selection"`, `"standardProfiling"`, `"customProfiling"`].
selection | `SelectionJob` | MANDATORY if the `type` field has value `"selection"`. Neglected otehrwise. Specifies the requested `SelectionJob`.
standardProfiling | `StandardProfilingJob` | MANDATORY if the `type` field has value `"standardProfiling"`. Neglected otehrwise. Specifies the requested `StandardProfilingJob`.
customProfiling | `CustomProfilingJob` | MANDATORY if the `type` field has value `"customProfiling"`. Neglected otehrwise. Specifies the requested `CustomProfilingJob`.


**`Job` object carrying a `SelectionJob`**

> The details of the `SelectionJob` object are missing

```json
{
	"identifier": "outlets",
	"type": "selection",
	"selection": {},
	"standardProfiling": null,
	"customProfiling": null
}
```

**`Job` object carrying a `StandardProfilingJob`**

> The details of the `StandardProfilingJob` object are missing

```json
{
	"identifier": "standardProfiling",
	"type": "standardProfiling",
	"selection": null,
	"standardProfiling": {},
	"customProfiling": null
}
```

**`Job` object carrying a `CustomProfilingJob`**

> The details of the `CustomProfilingJob` object are missing

```json
{
	"identifier": "art interest",
	"type": "customProfiling",
	"selection": null,
	"standardProfiling": null,
	"customProfiling": {}
}
```

### `SelectionJob` data model

A Selection Job allows to obtain Resources of a given Class providing a related [R-Segment](https://gitlab.com/geouniq/documentation/blob/master/api/data-models/r-segment/index.md)

Field | Type | Description
-------|-------|-------
resource | `String` | The name of a specific [Device-related Resource Class](https://gitlab.com/geouniq/documentation/blob/master/api/concepts/resource-definition.md). The following Device-related Resource Classes are currently supported:  [`"detectedPosition"`, `"visit"`].
detectedPosition | [`DetectedPosition-Segment`](https://gitlab.com/geouniq/documentation/blob/master/api/data-models/r-segment/detected-position.md) | MANDATORY if the `resource` field has value `"detectedPosition"`. Neglected otherwise. Defines the Input for a Selection of *Detected Position* resources.
visit | [`Visit-Segment`](https://gitlab.com/geouniq/documentation/blob/master/api/data-models/r-segment/visit.md) | MANDATORY if the `resource` field has value `"visit"`. Neglected otherwise. Defines the Input for a Selection of *Visit* resources.


**`SelectionJob` object for *Detected Position* resources**

> The details of the `DetectedPosition-Segment` object are missing

```json
{
	"resource": "detectedPosition",
	"detectedPosition": {},
	"visit": null
}
```

**`SelectionJob` object for *Visit* resources**

> The details of the `Visit-Segment` object are missing

```json
{
	"resource": "visit",
	"detectedPosition": null,
	"visit": {}
}
```

> Given a Resource Class *R*, an *R* Selection JOB must have `"resource":"R"` and a field `"R"` carrying an `R-Segment`

#### Examples

> Visit Selection `JOB` Object. Visits, at the "building" granularity, at two different POIs, namely Outlet 1 and Outlet 2, indicated as two circular areas. Returns the set of Visits at the provided places during the indicated period of time. Each Viosit will be marked with the ID of the place indicated in each GeoJSON Feature (field `“properties.id“`)


```json
{
	"identifier": "outlets",
	"type": "selection",
	"selection": {
		"resource": "visit",
		"visit": {
			"time": {
				"inside": {
					"intervals": [{
						"from": {
							"absolute": "2019-01-01T00:00:00Z"
						},
						"to": {
							"absolute": "2019-04-01T00:00:00Z"
						}
					}]
				}
			},
			"space": {
				"inside": {
					"explicitArea": {
						"type": "FeatureCollection",
						"features": [{
							"type": "Feature",
							"geometry": null,
							"properties": {
								"id": "Outlet 1"
								"circles": [{
									"center": {
										"lat": 10.0,
										"lng": 10.0
									},
									"radius": 50
								}]
							}
						},{
							"type": "Feature",
							"geometry": null,
							"properties": {
								"id": "Outlet 2"
								"circles": [{
									"center": {
										"lat": 11.0,
										"lng": 10.0
									},
									"radius": 50
								}]
							}
						}]
					}
				}
			},
			"spatialGranularity": {
	    	    "inside": ["building"]
			},
			"duration": {"gte": 300, "lte": 10800}
		}
	}
}
```






### `StatisticJob` data model

A Statistic Job allows to obtain a Statistic on Resources of a given Class providing a related [R-StatisticInput](https://gitlab.com/geouniq/documentation/blob/master/api/data-models/r-statistic-input/index.md)

Field | Type | Description
-------|-------|-------
resource | `String` | The name of a specific [Device-related Resource Class](https://gitlab.com/geouniq/documentation/blob/master/api/concepts/resource-definition.md). The following Device-related Resource Classes are currently supported:  [`"detectedPosition"`, `"visit"`].
detectedPosition | [`DetectedPosition-StatisticInput`](https://gitlab.com/geouniq/documentation/blob/master/api/data-models/r-statistic-input/detected-position.md) | MANDATORY if the `resource` field has value `"detectedPosition"`. Neglected otherwise. Defines the Input for a Statistic on *Detected Position* resources.
visit | [`Visit-StatisticInput`](https://gitlab.com/geouniq/documentation/blob/master/api/data-models/r-statistic-input/visit.md) | MANDATORY if the `resource` field has value `"visit"`. Neglected otherwise. Defines the Input for a Statistic on *Visit* resources.


**`StatisticJob` object for *Detected Position* resources**

> The details of the `DetectedPosition-StatisticInput` object are missing

```json
{
	"resource": "detectedPosition",
	"detectedPosition": {},
	"visit": null
}
```

**`StatisticJob` object for *Visit* resources**

> The details of the `Visit-StatisticInput` object are missing

```json
{
	"resource": "visit",
	"detectedPosition": null,
	"visit": {}
}
```

> Given a Resource Class *R*, an *R* Statistic JOB must have `"resource":"R"` and a field `"R"` carrying an `R-StatisticInput`



#### Examples

> Visit Statistic `JOB` Object. Statistic on Visits (at the "building" granularity), segmented "by device" and "by place". Returns the count and total duration of the visits performed by each device to each place


```json
{
	"identifier": "outlets visitors",
	"type": "statistic",
	"statistic": {
		"resource": "visit",
		"visit": {
			"select":{
				"time": {
					"inside": {
						"intervals": [{
							"from": {
								"absolute": "2019-01-01T00:00:00Z"
							},
							"to": {
								"absolute": "2019-04-01T00:00:00Z"
							}
						}]
					}
				},
				"space": {
					"inside": {
						"explicitArea": {
							"type": "FeatureCollection",
							"features": [{
								"type": "Feature",
								"geometry": null,
								"properties": {
									"id": "Outlet 1"
									"circles": [{
										"center": {
											"lat": 10.0,
											"lng": 10.0
										},
										"radius": 50
									}]
								}
							},{
								"type": "Feature",
								"geometry": null,
								"properties": {
									"id": "Outlet 2"
									"circles": [{
										"center": {
											"lat": 11.0,
											"lng": 10.0
										},
										"radius": 50
									}]
								}
							}]
						}
					}
				},
				"spatialGranularity": {
		    	    "inside": ["building"]
				},
				"duration": {"gte": 300, "lte": 10800}
			},
			"segmentBy": {
				"deviceBase": {
					"inside": {
						"device: 1
					}
				},
				"space": {
					"inside": {
						"placeID": 1
					}
				}
			},
			"compute": {
				"count": true,
				"totalDuration": true
			}
		}

	}
}
```

> Visit Statistic `JOB` Object. Visits, at the "building" granularity, at two different POIs, indicated as two circular areas. Two different values are provided for the "category" field (see the "properties" field of the GeoJSON Objects). The Statistic is "Segmented" "by device" and "by place category". It will return an item for each device and each category (only non zero items). The Statistic oepration allows to profile devices according to the nuber of visits performed to places of different categories

> Given a Resource Class *R*, an *R* Statistic JOB must have `"resource":"R"` and a field `"R"` carrying an `R-StatisticInput`

```json
{
	"identifier": "outlets",
	"type": "statistic",
	"statistic": {
		"resource": "visit",
		"visit": {
			"select": {
				"time": {
					"inside": {
						"intervals": [{
							"from": {
								"absolute": "2019-01-01T00:00:00Z"
							},
							"to": {
								"absolute": "2019-04-01T00:00:00Z"
							}
						}]
					}
				},
				"space": {
					"inside": {
						"explicitArea": {
							"type": "FeatureCollection",
							"features": [{
								"type": "Feature",
								"geometry": null,
								"properties": {
									"category": "fitness",
									"circles": [{
										"center": {
											"lat": 10.0,
											"lng": 10.0
										},
										"radius": 50
									}]
								}
							},{
								"type": "Feature",
								"geometry": null,
								"properties": {
									"category": "art",
									"circles": [{
										"center": {
											"lat": 11.0,
											"lng": 10.0
										},
										"radius": 50
									}]
								}
							}]
						}
					}
				},
				"spatialGranularity": {
		    	    "inside": ["building"]
				},
				"duration": {
					"gte": 300, "lte": 10800
				}
			},
			"segmentBy": {
				"deviceBase": {
					"inisde": {
						"device": 1
					}
				},
				"space": {
					"inside": {
						"placeCategory": 1
					}
				}
			},
			"compute": {
				"count": true,
				"totalDuration": true
			}
		}
	}
}
```


### `StandardProfilingJob` data model

A Standard Profiling Job allows to obtain standard profiling information. The set of different profiling informations that are desired is indicated thorugh a set of boolean fields.
The set of devices for which profiling information is desired is indicated through a [`DeviceBase-Segment`](https://gitlab.com/geouniq/documentation/blob/master/api/data-models/d-segment/device-base.md). Note that, in case of analysis of type `"ResourceSelectionsWithUserProfiling"`, the set of devices is implicitely derived from the set of Resources selected according to the various Selection Jobs, whilst the one indicated in the Standard Profiling Job, if any, is neglected.

Field | Type | Description
-------|-------|-------
deviceBase |`DeviceBase-Segment` | OPTIONAL - Indicates the set of devices for which profiling information are desired.
homeLocation | `Boolean` | Indicates whether the Home-Location has to be included in the profiling information.
workLocation | `Boolean` | Indicates whether the Work-Location has to be included in the profiling information.
age | `Boolean` | Indicates whether the age has to be included in the profiling information.
gender | `Boolean` | Indicates whether the gender has to be included in the profiling information.
purchasingPowerIndex | `Boolean` | Indicates whether the purchasing power index has to be included in the profiling information.
nightLifeIndex | `Boolean` | Indicates whether the nightlife index has to be included in the profiling information.

#### Examples 

> `StandardProfilingJob` object on the whole Device Base (`null` means "everything")

```json
{
	"deviceBase": null,
	"homeLocation": true,
	"workLocation": true,
	"age": true,
	"gender": true,
	"purchasingPower": true,
	"nightLifeIndex": true,
}
```


### `CustomProfilingJob` data model

A Custom Profiling Job allows to profile devices accoding to a custom logic (e.g., count of Visits to places of a given category).
A Custom Profiling Job has the same data model as a [Statistic Job](#statistic-job) but implcitely contains a segmentation operation on the Device Base dimension using the "by device" criterion.



## `InputFileDefinition` data model



Input files can be used as [Dimension Segments](https://gitlab.com/geouniq/documentation/blob/master/api/concepts/resource-definition.md#segment-of-a-dimension) for [Selection Conditions](https://gitlab.com/geouniq/documentation/blob/master/api/concepts/resource-selection.md). 
Each `InputFileDefinition` object indicates the specifics of a file that will be uploaded with a successive request. It indicates the job wich it refers to, to as well as a specific Dimension and one or more Selection Operators to use, so as to define one ore more Selection Conditions. The resulting Selection Conditions must be valid for the Resource Class indicated in the Job. 

Field | Type | Description
-------|-------|-------
identifier | `String` | An identifier for the file - max 64 charcters. It has to be used as path parameter in the request performed to upload the file.
encoding | `String` | The type of encoding. Supported values are [`"json"`].
applyTo | `[JSON]` | Indicates one or more Jobs which the file has to be applied to.
applyTo.[].jobIdentifier | `String` | Indicates the ID of the Job which the file refers to. The value has to be equal to one of the values in the `Job.identifier` field for the indicated Jobs. Only Jobs of the following types allow a file as input: [`SelectionJob`, `StatisticJob`, `CustomProfilingJob`].
applyTo.dimension | `String` | Indicates the Dimension for one or more Selection Conditions. The indicated Dimension must be in the set of Dimensions of the specific Resource Class (see [resource definition](https://gitlab.com/geouniq/documentation/blob/master/api/concepts/resource-definition.md#segment-of-a-dimension))
applyTo.operators | `[String]` | Indicates one or more [Selection Operators](https://gitlab.com/geouniq/documentation/blob/master/api/geometries-and-operators.md#operators) which, combined with the Dimension indicated in `applyTo.dimension`, defines N different Selection Conditions. Each indiacted Selection Operator must be in the set of those allowed for the specific Geometry assumed by the specific Resource Class on the specific Dimension (see [Resource Selection](https://gitlab.com/geouniq/documentation/blob/master/api/concepts/resource-selection.md)).



```json
{
	"identifier": "outlets",
	"encoding": "json",
	"applyTo": [{
		"jobIdentifier": "job1",
		"dimension": "space",
		"operators": ["inside"]
	}]
}
```

When an Analysis resource is obtained from the API (see [Read a specific analysis](#read-a-specific-analysis)), each `InputFileDefinition` object will contain the following additional fields

Field | Type | Description
-------|-------|-------
status | `String` | One of the following values: [`"missing"`, `"valid"`, `"invalid"`]
uploadedAt | [`DateTime`](https://gitlab.com/geouniq/documentation/blob/master/api/data-models/common/date.md) | Indicates when the file has been uploaded. `null` if `status` is `"missing"`.



### Encoding Dimension Segments in files

#### Space Segment

When a [`SpaceSegment`](https://gitlab.com/geouniq/documentation/blob/master/api/data-models/d-segment/space.md) is encoded in a file, only the value of the `explicitArea` field is encoded, that is a [`GuGeoJSON`](https://gitlab.com/geouniq/documentation/blob/master/api/data-models/common/gu-geo-json.md) object.

### JSON

#### JSON Array with multiple GuGeoJSON objects

The list of areas for the whole Space Segment is provided through a JSON array containing several GuGeoJSON objects.
Each GuGeoJSON object must be of type "Feature".


```json
[{
    "type" : "Feature",
    "geometry" : null,
    "properties" : {
        "circles" : [{
            "center": {"lat": 10.0, "lng": 10.0},
            "radius": 100
        }],
        "id": "store 1",
        "category": "store"
    }
},{
    "type" : "Feature",
    "geometry" : null,
    "properties" : {
        "circles" : [{
            "center": {"lat": 10.1, "lng": 10.0},
            "radius": 100
        }],
        "id": "store 2",
        "category": "store"
    }
}]
```


#### Single GuGeoJSON object

The list of areas for the whole Space Segment is provided through one `GuGeoJSON` object.
The `GuGeoJSON` object can be of type "Feature", as well as of type "FeatureCollection".

```json
{
    "type" : "FeatureCollection",
    "features": [{
        "type" : "Feature",
        "geometry" : null,
        "properties" : {
            "circles" : [{
                "center": {"lat": 10.0, "lng": 10.0},
                "radius": 100
            }],
            "id": "store 1",
            "category": "store"
        }
    },{
        "type" : "Feature",
        "geometry" : null,
        "properties" : {
            "circles" : [{
                "center": {"lat": 10.1, "lng": 10.0},
                "radius": 100
            }],
            "id": "store 2",
            "category": "store"
        }
    }]
}
```


