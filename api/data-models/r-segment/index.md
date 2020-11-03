# R-Segment

Data models used to indicate a [Segment of Resources of Class *R*](/api/concepts/resource-definition.md).
They are generically indicated as `R-Segment`.

These Data Models are used:

- **on the input side**: to indicate the desired *R* Segment. 
    - [**when accessing Resources**](/api/endpoints/resources/index.md)
    - [**when accessing Statistics**](/api/endpoints/statistics/index.md)
- **on the output side**:
    - [**when accessing Statistics**](/api/endpoints/statistics/index.md): to indicate the *R* Segment which an Item refers to if a [Segmentation operation](/api/concepts/statistics.md#segmentation) has been performed.

According to the specific Resource Class *R*, the following `R-Segment` Data Models are defined:

* [`DetectedPosition-Segment`](api/data-models/r-segment/detected-position.md)
* [`Activity-Segment`](api/data-models/r-segment/activity.md)
* [`Visit-Segment`](api/data-models/r-segment/visit.md)
* [`Travel-Segment`](api/data-models/r-segment/travel.md)
* [`HomeLocation-Segment`](api/data-models/r-segment/home-location.md)
* [`WorkLocation-Segment`](api/data-models/r-segment/work-location.md)
* [`LivingArea-Segment`](api/data-models/r-segment/living-area.md)
* [`Flight-Segment`](api/data-models/r-segment/flight.md)
