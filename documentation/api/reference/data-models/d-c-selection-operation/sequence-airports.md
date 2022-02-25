# Sequence-Airports-SelectionOperation

Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
inside | [`Airports-Segment`]() | ANY | 
intersect | [`Airports-Segment`]() | ANY | 
start | [`Airports-Segment`]() | ANY | 
end | [`Airports-Segment`]() | ANY | 

```json
{
    "inside" : {
        "iataCode" : ["FCO", "JFK"],
        "continent" : ["Europe", "Asia"],
        "country": ["Italy", "Japan"],
        "city": ["Rome", "Milan"],
    },
    "intersect" : {},
    "start" : {},
    "end" : {}
}
``` 
