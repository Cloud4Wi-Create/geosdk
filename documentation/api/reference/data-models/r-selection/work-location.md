# WorkLocation-Segment

Name        |Type      
------------|----------
deviceBase | [`Point-DeviceBase-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/point-device-base.md) 
space | [`Point-Space-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/point-space.md) 

```json
{
    "deviceBase": {
        "inside" : {
            "deviceId" : ["D1", "D2", "D3"],
            "applicationId" : ["A1", "A2", "A3"],
            "osName" : ["android", "iOs"]
        }
    },
    "space": {
        "inside" : {
            "explicitArea" : {},
            "implicitAreas" : ["living", "home", "work"],
            "savedAreas" : {}
        }
    }
}
```

