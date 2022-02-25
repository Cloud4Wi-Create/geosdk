# Space-Segmentation

Name        |Type      | Allowed Values | Description
------------|----------|-------------- | -------------
geohash | `Integer` | [`1`, `8`] | Indicates to segment the selected area according to the Geohash grid with Geohash precision as indicated in this field
placeID | `Integer` | `1` | Indicates to segment the selected area according to the value of the field `"properites.id"` of each GuGeoJSON Feature (see [`GuGeoJSON`](/api/reference/data-modelsata-models/common/gu-geo-json.md))
placeCategory | `Integer` | `1`| Indicates to segment the selected area according to the value of the field `"properites.category"` of each GuGeoJSON Feature (see [`GuGeoJSON`](/api/reference/data-modelsata-models/common/gu-geo-json.md))

> Note that only one field must be present in the provided `Space-Segmentation` object

> `Space-Segmentation` Object indicating a segmentation *By Geohash* with geohash prefix of length equal to `5`

```json
{
    "geohash": 5
}
```

> `Space-Segmentation` Object indicating a segmentation *By Place ID*. No granularity is needed, so the value of the `"placeID"` must be equal to `1`

```json
{
    "placeID": 1
}
```

> `Space-Segmentation` Object indicating a segmentation *By Place Category*. No granularity is needed, so the value of the `"placeCategory"` must be equal to `1`

```json
{
    "placeCategory": 1
}
```
