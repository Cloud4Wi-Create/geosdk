# STEP 1 - Identificazione esposti pre campagna (non esposti)

* Identifica i device che sono passati in ognuna delle aree dei billboard in un periodo specificato
* Può essere svolto sia come primo step che subito prima di richiedere il footfall
* Sarà utilizzato come control group nella analisi footfall (vedi STEP 4)
* Effettuato attraverso una richiesta alla API
	* Si utilizza l'API per le Audience
	* **INPUT**:
		* **Periodo**: il periodo pre-campagna deciso dall'utente
		* **Lista POI Custom**: l'insieme delle aree dei billboard (poligoni o altro) in formato GeoJSON
		* **[OPZIONALE] hook**: (email o web) per ricevere alert quando l'analisi termina
	* **OUTPUT**:
		* **ID della analisi audience**: ricevuto come risposta alla richiesta
		* **Lista IDFA identificati**: scaricabile come csv (come per una normale audience)
			* in linea di principio non serve avere questa lista ma solo l'ID della audience

## Relevant Documentation

* **[Audiecne Analysis Endpoints](/api/reference/endpoints/resources/user-created/audience-analysis/index.md)**: All API endpoints related to Audience Analysis
* **[Audiecne Analysis data model](/api/reference/data-models/resources/user-created/audience-analysis.md)**: Data model used to represent an Audience Analysis

## Example

Example request to create an *Audience Analysis* to identify devices that passed in the areas of the billboards during a given time period

1. Decide the time period
2. Obtain a GeoJSON Feature Collection object representing the set of the areas of the billboards
3. Perform a request to the API as documented [here](/api/reference/endpoints/resources/user-created/audience-analysis/create.md) providing as body a JSON object like the one in the example below

### Example Body

> Change the time period in the `"period"` field according to the desired period

> Change the GeoJSON object in the `"pois.custom"` field according to the real billboards' areas

> Change the URL in the `"hook"` field according to the real URL for your web hook or use an [email-hook](/api/reference/data-models/common/hook.md)

```json
{
  "name": "Test Audience for OOH",
  "description": "a test audience to identify devices thata passed the areas of the billboards",
  "labels": [
    "test",
    "OOH"
  ],
  "hook": {
    "type": "web",
    "web": {
      "url": "https://mydomain.com/gu-hooks/analysis"
    }
  },
  "type": "geoBehavioural",
  "geoBehavioural": {
    "criteria": [
      "passedThrough"
    ],
    "pois": {
      "custom": {
        "type": "FeatureCollection",
        "features": [
          {
            "type": "Feature",
            "properties": {
                "id": "billboard_1"
            },
            "geometry": {
              "type": "Polygon",
              "coordinates": [
                [
                  [
                    9.188625812530518,
                    45.464750960489475
                  ],
                  [
                    9.188497066497803,
                    45.463622252143225
                  ],
                  [
                    9.192874431610106,
                    45.46369750006936
                  ],
                  [
                    9.19278860092163,
                    45.464766009781414
                  ],
                  [
                    9.188625812530518,
                    45.464750960489475
                  ]
                ]
              ]
            }
          },
          {
            "type": "Feature",
            "properties": {
                "id": "billboard_2"
            },
            "geometry": {
              "type": "Polygon",
              "coordinates": [
                [
                  [
                    9.185857772827148,
                    45.48402580978778
                  ],
                  [
                    9.188904762268066,
                    45.482581553108
                  ],
                  [
                    9.19182300567627,
                    45.48366474908892
                  ],
                  [
                    9.19032096862793,
                    45.48534967921898
                  ],
                  [
                    9.1880464553833,
                    45.485409854363
                  ],
                  [
                    9.185857772827148,
                    45.48402580978778
                  ]
                ]
              ]
            }
          }
        ]
      }
    },
    "period": {
      "intervals": [
        {
          "from": {
            "absolute": "2020-05-15T00:00:00Z"
          },
          "to": {
            "absolute": "2020-05-30T00:00:00Z"
          }
        }
      ]
    },
    "reachLevel": 1
  }
}
```

# STEP 2 -  Creazione campagna

* Effettuato attraverso una richiesta alla API
* **INPUT**
	* **[OPZIONALE] Nome, Descrizione**
	* **Periodo**: il periodo in cui sarà erogata la campagna. Determina quando sarà fatta l'identificazione degli esposti e delle visite che questi fanno ai POI "target"
	* **POI "target"**: la lista degli store che si vogliono monitorare
		* Possono essere sia custom (formato geoJSON) che i POI a sistema
		* Possibile ottenere il geoJSON da un csv con la lista dei POI attraverso una differente richiesta alla API
	* **Aree per identificazione esposti** 
		* l'insieme delle aree dei billboard (poligoni o altro) in formato GeoJSON
		* Usati per identificare gli utenti "esposti" all'advertising 
	* **[OPZIONALE] Hook per ricezione esposti**
		* Permette di ricevere, ad un URL indicato, gli utenti man mano identificati come "esposti". 
	* **[OPZIONALE] Hook per ricezione visite degli esposti**
		* Permette di ricevere, ad un URL indicato, le visite ai POI target effettuate degli utenti identificati come "esposti". 
* **OUTPUT**
	* **ID della campagna creata**

## Relevant Documentation

* **[Campaign Endpoints](/api/reference/endpoints/resources/user-created/campaign/index.md)**: All API endpoints related to Campaigns
* **[Campaign data model](/api/reference/data-models/resources/user-created/campaign.md)**: Data model used to represent a Campaign

## Example

1. Decide the time period of the campaign
2. Obtain a GeoJSON object to indicate the target stores for the advertising campaign
3. Obtain a GeoJSON object to indicate the areas of the billboards (as in [STEP 1])
4. Perform a request to the API as documented [here](/api/reference/endpoints/resources/user-created/campaign/create.md) providing as body a JSON object like the one in the example below

### Example Body

> Change the time period in the `"period"` field according to the desired period

> Change the GeoJSON object in the `"targetPois"` field according to the real target stores

> Change the GeoJSON object in the `"identifyExposed.space.inside"` field according to the real billboards’ areas


> Change the [`TimeSegment`](/api/reference/data-models/d-segment/time.md) object in the `"identifyExposed.time.inside"` field according to the period of the campaign. Generally the same time interval used for the main `"period"` field should be used. However, here it is possible to set multiple time intervals, specific time hours, and specific days of the week, useful for example, when the advertising is not always shown during the whole period of the campaign.

> Change the URL in the `"visitsHook"` and `"exposedHook"` objects according to the real URL for your web hooks

```json
{
	"name": "my OOH campaign",
	"description": "test OOH campaign",
	"type": "outOfHome",
	"realTimeMonitoring": {
		"status": "enabled"
	},
	"period": {
		"start": "2020-06-01T00:00:00Z",
		"end": "2020-06-10T00:00:00Z"
	},
	"targetPOIs": [{
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
	}],
	"identifyExposed": {
		"time": {
			"inside": {
				"intervals": [{
					"from": {
						"absolute": "2020-06-01T00:00:00Z"
					},
					"to": {
						"absolute": "2020-06-10T00:00:00Z"
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
							"properties": {
								"id": "billboard_1"
							},
							"geometry": {
								"type": "Polygon",
								"coordinates": [
									[
										[
											9.188625812530518,
											45.464750960489475
										],
										[
											9.188497066497803,
											45.463622252143225
										],
										[
											9.192874431610106,
											45.46369750006936
										],
										[
											9.19278860092163,
											45.464766009781414
										],
										[
											9.188625812530518,
											45.464750960489475
										]
									]
								]
							}
						},
						{
							"type": "Feature",
							"properties": {
								"id": "billboard_2"
							},
							"geometry": {
								"type": "Polygon",
								"coordinates": [
									[
										[
											9.185857772827148,
											45.48402580978778
										],
										[
											9.188904762268066,
											45.482581553108
										],
										[
											9.19182300567627,
											45.48366474908892
										],
										[
											9.19032096862793,
											45.48534967921898
										],
										[
											9.1880464553833,
											45.485409854363
										],
										[
											9.185857772827148,
											45.48402580978778
										]
									]
								]
							}
						}
					]
				}
			}
		},
		"spatialGranularity": {
			"inside": [
				"exact"
			]
		}
	},
	"visitsHook": {
		"type": "web",
		"web": {
			"url": "https://mydomain.com/gu-hooks/visits"
		}
	},
	"exposedHook": {
		"type": "web",
		"web": {
			"url": "https://mydomain.com/gu-hooks/exposed"
		}
	}
}
```

# STEP 3 - Run automatico durante la campagna

* La piattaforma andrà ad identificare automaticamente gli esposti ad ogni billboard e le relative visite ai POI target, allo stesso modo di come oggi viene fatto per le campagne digital
* Gli esposti identificati saranno inviati all'hook specificato con i seguenti dettagli
	* ID campagna
	* Dettagli area del billboard (tutto ciò che è presente nelle properties della relativa geoJSON Feature)
	* IDFA
	* timestamp
* Le visite identificate saranno inviate all'hook specificato con i seguenti dettagli
	* ID campagna
	* Dettagli del POI (tutto ciò che è presente nelle properties della relativa geoJSON Feature)
		* Per i POI a sistema saranno presenti una serie di informazioni tra cui un ID utilizzabile sulla API per indicare quello specifico POI, la categoria, il brand, comune, provincia, regione, area nielsen
	* IDFA
	* timestamp

## Relevant Documentation to handle requests performed to WebHooks

[Guide](/api/guideuide/receiving-web-hooks.md)

# STEP 4 - Analisi Footfall

* Effettuato attraverso una richiesta alla API
* **INPUT**
	* **ID della campagna** per cui si vuole ottenere il l'analisi footfall
	* **Control Group**: ID della audience creata allo STEP 1
	* **[OPZIONALE] Periodo da usare per il gruppo degli esposti** 
		* Se non specificato sarà utilizzato il periodo della campagna
	* **[OPZIONALE] Periodo da usare per il control group**
		* Se non specificato sarà utilizzato il periodo della campagna
			* Già stabilito che si vorrà usare un periodo diverso, quello "pre campagna" usato anche per identificare il control group stesso
	* **Standar o Premium**: possono essere richieste entrambe le tipologie di analisi footfall
	    * Necessario analisi premium per ottenere le informazioni di profilo dei visitatori  
	* **[OPZIONALE] Hook (email o web)** per ricezione alert quando l'analisi sarà terminata

**OUTPUT**
* ID dell'analisi footfall creata
    * I risultati saranno disponibili quando l'analisi sarà terminato  

## Relevant Documentation

* **[Footfall Analysis Endpoints](/api/reference/endpoints/resources/user-created/campaign/footfall/index.md)**: All API endpoints related to Footfall Analysis
* **[Footfall Analysis data model](/api/reference/data-models/resources/user-created/campaign-footfall.md)**: Data model used to represent a Footfall Analysis

## Example

1. Use the *Audience Analysis* Resoource ID obtained in STEP 1 to indicate the control group
2. Use the *Campaign* Resoource ID obtained in STEP 2 to indicate for which *Campaign* you want to obtain the *Footfall Analysis*
3. Use the period decided in STEP 1 to identify the control group as the period to compute visits performed by the control group
4. Perform a request to the API as documented [here](/api/reference/endpoints/resources/user-created/campaign/footfall/create.md) providing as body a JSON object like the one in the example below

### Example Body

> Change the period in the `"controlGroupPeriod"` field according to the desired period

> Change the ID in the `"controlGroup"` Object according to the ID if the real *Audience Analysis* used to identify the control group

> Change the URL in the `"hook"` field according to the real URL for your web-hook or use an [email-hook](/api/reference/data-models/common/hook.md)

```json
{
  "name": "Test footfall analysis",
  "description": "a footfall analysis for my OOH campaign",
  "type": "premium",
  "controlGroup": {
    "type": "audienceBuilder",
    "analysisID": "audienceAnalysis1"
  },
  "controlGroupPeriod": {
    "intervals": [{
        "from":{
            "absolute":"2020-05-15T00:00:00Z"
        },
        "to":{
            "absolute":"2020-05-30T00:00:00Z"
        }
    }]
  },
  "hook": {
    "type": "web",
    "web": {
      "url": "https://mydomain.com/gu-hooks/ff-analysis"
    }
  }
}
```

# [STEP 5] Download risultati footfall
* Attraverso richiesta alla API. 
* Può essere automatizzato dal cliente alla ricezione dell'hook

## Relevant Documentation

* **[Footfall Analysis Results Endpoint](/api/reference/endpoints/resources/user-created/campaign/footfall/download-results.md)**: API endpoint to download the results of a Footfall Analysis



