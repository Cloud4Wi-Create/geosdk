### TargetPOIs

Data model used to indicate a combination of custom POIs and "standard" POIs provided by the platform

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
custom | [`GuGeoJSON`](/api/reference/data-modelsata-models/common/gu-geo-json.md) | Semi-Optional | Any valid [`GuGeoJSON`](/api/reference/data-modelsata-models/common/gu-geo-json.md) | Indicates a set of custom POIs
standard | [`POI-Segemnt`](/api/reference/data-modelsata-models/r-segment/poi.md) | Semi-Optional | [`POI-Segemnt`](/api/reference/data-modelsata-models/r-segment/poi.md) | Indicates a set of POIs within the analytics platform
