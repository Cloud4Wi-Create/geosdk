## Sequence-Airports-Segmentation

Name        |Type      
------------|----------
inside | [`Airports-Segmentation`]() | Indicates that a Segmentation has to be performed with respect to the [*inside* Selection Condition] on the *Airports* Dimension.
intersect | [`Airports-Segmentation`]() | Indicates that a Segmentation has to be performed with respect to the [*intersect* Selection Condition] on the *Airports* Dimension.
start | [`Airports-Segmentation`]() | Indicates that a Segmentation has to be performed with respect to the [*start* Selection Condition] on the *Airports* Dimension.
end | [`Airports-Segmentation`]() | Indicates that a Segmentation has to be performed with respect to the [*end* Selection Condition] on the *Airports* Dimension.

```json
{
    "inside" : {
        "byLevel" : 1,
        "byContinent" : 1,
        "byCountry" : 1,
        "byCity" : 1
    },
    "intersect" : {},
    "start" : {},
    "end" : {}
}
``` 

