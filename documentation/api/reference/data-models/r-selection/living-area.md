# LivingArea-Segment

Name        |Type      
------------|----------
deviceBase | [`Point-DeviceBase-Selection`]() 
space | [`Point-Space-Selection`]() 

```json
{
    "deviceBase": {
        "inside" : {
            "deviceId" : ["D1", "D2", "D3"],
            "applicationId" : ["A1", "A2", "A3"],
            "osName" : ["android", "iOs"]
        },
        "intersect": {}
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

