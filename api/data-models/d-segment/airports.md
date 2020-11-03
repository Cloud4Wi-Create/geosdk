# Airports-Segment

Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
iataCode | `[String]` | ANY valid [IATA code](http://www.iata.org/services/Pages/codes.aspx)   | All the airsports whose IATA code is among those indicated in the provided set.
continent | `[String]` | ANY   | All the airsports located in one of the continents indicated in the provided set.
country | `[String]` | ANY   | All the airsports located in one of the countries indicated in the provided set.
city | `[String]` | ANY   | All the airsports located in one of the cities indicated in the provided set.

```json
{
    "iataCode" : ["FCO", "JFK"],
    "continent" : ["Europe", "Asia"],
    "country": ["Italy", "Japan"],
    "city": ["Rome", "Milan"],
}
```
