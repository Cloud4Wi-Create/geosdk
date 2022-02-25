# R-Segment

Data models used to indicate a [Segment of Resources of type *R*](/api/concepts/resource-definition.md).
They are generically indicated as `R-Segment`.

These Data Models are used:

- **on the input side**: to indicate the desired *R* Segment. 
    - [**when accessing Resources**](/api/reference/endpoints/endpoints/resources/index.md)
    - [**when accessing Statistics**](/api/reference/endpoints/endpoints/statistics/index.md)
- **on the output side**:
    - [**when accessing Statistics**](/api/reference/endpoints/endpoints/statistics/index.md): to indicate the *R* Segment which an Item refers to if a [Segmentation operation](/api/concepts/statistics.md#segmentation) has been performed.

According to the specific Resource type *R*, the following `R-Segment` Data Models are defined:

* [`DetectedPosition-Segment`](api/data-models/r-segment/detected-position.md)
* [`Visit-Segment`](api/data-models/r-segment/visit.md)
* [`HomeLocation-Segment`](api/data-models/r-segment/home-location.md)
* [`WorkLocation-Segment`](api/data-models/r-segment/work-location.md)
* [`UserProfile-Segment`](api/data-models/r-segment/profile.md)
