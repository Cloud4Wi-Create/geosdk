* [Documentation Home](../../README.md)
   * [Web API](../index.md)
      * [Use Cases](index.md)
      
# Custom POIs

### Create a new Custom POI

Creates a new custom POI, requires authentication as described [here](../reference/general-aspects/auth.md).

POST `https://api.geouniq.com/v1/custom-pois`

**Header**

```
Authorization:Bearer ieQBddNIRP9Hhw2elpylkHC579hrKSrX
Content-Type:application/json
```

**Request**

```json
{
    "poiID": "Piazza dei Miracoli",
    "name": "Piazza dei Miracoli - Pisa",
    "description": "Piazza dei Miracoli Description",
    "category": "PIAZZE",
    "brand": "NO BRAND",
    "country": "IT",
    "geo": {
        "lat": 43.723047,
        "lng": 10.394788
    },
    "administrativeAreas": [
        {
            "level": "Area Nielsen",
            "name": "CENTRO"
        },
        {
            "level": "Regione",
            "name": "TOSCANA"
        },
				{
            "level": "Provincia",
            "name": "PISA"
        },
				{
            "level": "Comune",
            "name": "PISA"
        }
    ]
}
```

**Response**

```json
{
    "id": "601a876c0ba28af87dc6d9cd",
    "poiID": "Piazza dei Miracoli",
    "createdAt": "2021-02-03T11:22:20Z",
    "name": "Piazza dei Miracoli - Pisa",
    "description": "Piazza dei Miracoli Description",
    "category": "PIAZZE",
    "brand": "NO BRAND",
    "country": "IT",
    "geo": {
        "lat": 43.723047,
        "lng": 10.394788
    },
    "administrativeAreas": [
        {
            "level": "Area Nielsen",
            "name": "CENTRO"
        },
        {
            "level": "Regione",
            "name": "TOSCANA"
        },
				{
            "level": "Provincia",
            "name": "PISA"
        },
				{
            "level": "Comune",
            "name": "PISA"
        }
    ]
}
```

The `category`, `brand` and `administrativeArea` fields are mandatory and must be provided as in the example to be visible on the frontend tool.

### List all Custom-Pois

Reads all custom pois, requires authentication, response can be paginated.

GET `https://api.geouniq.com/v1/custom-pois`

**Header**

```
Authorization:Bearer ieQBddNIRP9Hhw2elpylkHC579hrKSrX
Content-Type:application/json
```

**Response**

```json
{
    "items": [
        {
			    "id": "601a876c0ba28af87dc6d9cd",
          "poiID": "Piazza dei Miracoli",
			    "createdAt": "2021-02-03T11:22:20Z",
			    "name": "Piazza dei Miracoli - Pisa",
			    "description": "Piazza dei Miracoli Description",
			    "category": "PIAZZE",
			    "brand": "NO BRAND",
			    "country": "IT",
			    "geo": {
			        "lat": 43.723047,
			        "lng": 10.394788
			    },
			    "administrativeAreas": [
			        {
			            "level": "Area Nielsen",
			            "name": "CENTRO"
			        },
			        {
			            "level": "Regione",
			            "name": "TOSCANA"
			        },
							{
			            "level": "Provincia",
			            "name": "PISA"
			        },
							{
			            "level": "Comune",
			            "name": "PISA"
			        }
			    ]
			}
    ],
    "paging": {
        "next": null
    }
}
```

### Read a single custom poi

Reads a single custom poi, requires authentication.

GET `https://api.geouniq.com/v1/custom-pois/601a876c0ba28af87dc6d9cd`

**Header**

```
Authorization:Bearer ieQBddNIRP9Hhw2elpylkHC579hrKSrX
Content-Type:application/json
```

**Response**

```json
{
			    "id": "601a876c0ba28af87dc6d9cd",
			    "createdAt": "2021-02-03T11:22:20Z",
			    "name": "Piazza dei Miracoli - Pisa",
			    "description": "Piazza dei Miracoli Description",
			    "category": "PIAZZE",
			    "brand": "NO BRAND",
			    "country": "IT",
			    "geo": {
			        "lat": 43.723047,
			        "lng": 10.394788
			    },
			    "administrativeAreas": [
			        {
			            "level": "Area Nielsen",
			            "name": "CENTRO"
			        },
			        {
			            "level": "Regione",
			            "name": "TOSCANA"
			        },
							{
			            "level": "Provincia",
			            "name": "PISA"
			        },
							{
			            "level": "Comune",
			            "name": "PISA"
			        }
			    ]
			}
```

### Delete a Custom POI

Deletes a single custom poi, requires authentication.

DELETE `https://api.geouniq.com/v1/custom-pois/601a876c0ba28af87dc6d9cd`

**Header**

```
Authorization:Bearer ieQBddNIRP9Hhw2elpylkHC579hrKSrX
Content-Type:application/json
```
