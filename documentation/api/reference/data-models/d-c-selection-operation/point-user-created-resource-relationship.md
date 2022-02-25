# Point-Time-SelectionOperation

Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
inside | [`Time-Segment`]() | ANY | 

```json
{
    "inside" : {
        "intervals" : [
            {
                "from" : {
                    "absolute": "2016-01-01T00:00:00Z",
                    "relative": -100
                },
                "to" : {
                    "absolute": "2016-01-01T00:00:00Z",
                    "relative": -100
                }
            }
        ],
        "periodicity" : {
    		"offset": -2,
    		"hoursOfTheDay": [1, 2, 6, 7, 8, 9, 21, 22],
    		"daysOfTheWeek": ["FRY", "SAT", "SUN"],
    		"monthsOfTheYear": ["JAN", "DEC"]
    	}
    }
}
```

