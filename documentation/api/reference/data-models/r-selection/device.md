# Device

Name        |Type      
------------|----------
deviceBase | [`Point-DeviceBase-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/point-device-base.md) 
time | [`Point-Time-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/point-time.md) 

```json
{
    "deviceBase": {
        "inside" : {
            "deviceId" : ["D1", "D2", "D3"],
            "applicationId" : ["A1", "A2", "A3"],
            "osName" : ["android", "iOs"]
        }
    },
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
            ]
        }
    }
}
```

