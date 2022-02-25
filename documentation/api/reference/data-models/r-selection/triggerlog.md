# Triggerlog-Segment

Name        |Type      
------------|----------
time | [`Point-Time-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/point-time.md) 
triggers | [`Point-UserCreatedResourceRelationship`](/api/reference/data-modelsata-models/g-d-selection-operation/point-user-created-resource-relationship.md) 


## Example Object

```json
{
   "time": {
        "inside" : {
            "intervals" : [
                {
                    "from" : {
                        "absolute": "2016-01-01T00:00:00Z"
                    },
                    "to" : {
                        "absolute": "2016-01-01T00:00:00Z"
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
    },
    "triggers": {
    	"inside": {
    		"id": ["T1", "T2", "T3"],
    		"name": ["Trigger 1", "Trigger 1", "Trigger 3"],
    		"labels": ["L1", "L2"]
    	}
    }
}
```

