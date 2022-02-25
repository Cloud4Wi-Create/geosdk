* [Documentation Home](../../../README.md)  
  * [Web API](../../index.md)  
    * [Reference](../index.md)
        * [Dimensions](index.md)

# Space

The *Space* Dimension refers to the Earth Surface.  
A *Space* segment can represent ANY area on the Earth surface, including ANY set of disjoint areas.

 - **Segment Data Model**: [`Space-Segment`](../data-models/d-segment/space.md)
 - **Segmentation Data Model**: [`Space-Segmentation`](../data-models/d-segmentation/space.md)

## Segmentation Criteria

The following segmentation criteria are defined for *Space*.

### By Geohash

Allows to segment a *Space* Segment according to the [geohash](https://en.wikipedia.org/wiki/Geohash) prefix of each point. This leads to dividing the whole area according to a fixed grid at different possible granularity levels. 

#### Segmentation object to use

This Criterion can be indicated using a [`Space-Segmentation`](../data-models/d-segmentation/space.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
geohash  | `Integer` | ANY Integer in [`1`, `8`]

```json
{
    "geohash": 1
}
```

#### Granularity

Indicates the [geohash length](https://en.wikipedia.org/wiki/Geohash#Design).
Expressed as an integer number in the `"geoHash"` field. 
Allowed values are in the interval [`1`, `8`].

#### Resulting Segments

Resulting Segments are indicated on the output side through a 
[`Space-Segment`](../data-models/d-segment/space.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
explicitArea  | [`GuGeoJSON`](../data-models/common/gu-geo-json.md) | Indicates both the geohash which the Segment refers to and the polygon corresponding to that geohash.


```json
{
    "explicitArea": {
        "type": "FeatureCollection",
        "features":[
            "type" : "Feature",
            "geometry" : { 
                "type": "Polygon", 
                "bbox": [-10.0, -10.0, 10.0, 10.0],
                "coordinates": [
        			[
        				[-10.0, -10.0],
        				[10.0, -10.0],
        				[10.0, 10.0],
        				[-10.0, 10.0],
        				[-10.0, -10.0]
        			]
        		]
            },
            "properties" : {
                "geohashes": ["sxdbc"]
            }
        ]
    }
}
```

##### Resulting sub-areas 

A geohash actually identifies a rectangular cell.
The cell sizes of geohashes of different lengths are as follows; note that the cell width reduces moving away from the equator (to 0 at the poles):


Geohash length| Cell width	| Cell height
--------------|-------------|------------
1	          | ≤ 5,000km	|	5,000km
2	          | ≤ 1,250km	|	625km
3	          | ≤ 156km	    |   156km
4	          | ≤ 39.1km	|	19.5km
5	          | ≤ 4.89km	|	4.89km
6	          | ≤ 1.22km	|	0.61km
7	          | ≤ 153m	    |	153m
8	          | ≤ 38.2m	    |	19.1m
9	          | ≤ 4.77m	    |	4.77m
10	          | ≤ 1.19m	    |	0.596m
11	          | ≤ 149mm	    |	149mm
12	          | ≤ 37.2mm	|	18.6mm


### By Place ID

Allows to segment a *Space* Segment with multiple 
[GeoJSON Features](../data-models/common/gu-geo-json.md) according to the value of the field `properties.id`.

#### Segmentation object to use

This Criterion can be indicated using a 
[`Space-Segmentation`](../data-models/d-segmentation/space.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
placeID | `Integer` | `1`

```json
{
    "placeID": 1
}
```

#### Granularity

No granularity can be indicated for tyhis criterion. The value `1` MUST be provided for the `"placeID"` field

#### Resulting Segments

Resulting Segments are indicated on the output side through a 
[`Space-Segment`](../data-models/d-segment/space.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
explicitArea  | [`GuGeoJSON`](../data-models/common/gu-geo-json.md) | A GuGeoJSON Object whose `properties.id` field indicates the specific category which the Segment refers to.


```json
{
    "explicitArea": {
        "features": [
            {
                "geometry": null,
                "properties": {
                    "id": "Place 1"
                },
                "type": "Feature"
            }
        ],
        "type": "FeatureCollection"
    }
}
```


### By Place Category

Allows to segment a *Space* Segment with multiple 
[GeoJSON Features](../data-models/common/gu-geo-json.md) according to the value of the field `properties.category`.

#### Segmentation object to use

This Criterion can be indicated using a 
[`Space-Segmentation`](../data-models/d-segmentation/space.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
placeCategory  | `Integer` | `1`

```json
{
    "placeCategory": 1
}
```

#### Granularity

No granularity can be indicated for tyhis criterion. The value `1` MUST be provided for the `"placeCategory"` field

#### Resulting Segments

Resulting Segments are indicated on the output side through a 
[`Space-Segment`](../data-models/d-segment/space.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
explicitArea  | [`GuGeoJSON`](../data-models/common/gu-geo-json.md) | A GuGeoJSON Object whose `properties.category` field indicates the specific category which the Segment refers to.


```json
{
    "explicitArea": {
        "features": [
            {
                "geometry": null,
                "properties": {
                    "category": "Category 1"
                },
                "type": "Feature"
            }
        ],
        "type": "FeatureCollection"
    }
}
```