# Multipoint-Space-Segmentation

Name        |Type      
------------|----------
inside | [`Space-Segmentation`](/api/data-models/d-segmentation/space.md) | Indicates that a Segmentation has to be performed with respect to the [*inside* Selection Condition] on the *Space* Dimension.
intersect | [`Space-Segmentation`](/api/data-models/d-segmentation/space.md) | Indicates that a Segmentation has to be performed with respect to the [*intersect* Selection Condition] on the *Space* Dimension.

```json
{
    "inside" : {
        "geohash": 5
    },
    "intersect" : {
        "geohash": 4
    }
}
```

