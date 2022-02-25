# Activity

Data Model used to represent an [*Activity*](/api/reference/resources/resources/platform-created/device-related/activity.md) Resource.

## Fields Specificcation

Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
device | [`DeviceReference`](/api/reference/data-modelsata-models/common/device-reference.md) | ANY valid `DeviceReference` | Indicates which *Device* the Resource refers to. 
motionType | `String` | One of the values defined for [Motion Type](/api/reference/dimensionsdimensions/motion-type.md) | The type of motion that characterizes the *Activity*.
startedAt | [`Date`](/api/reference/data-modelsata-models/common/date.md) | ANY valid `Date` | The date and time when the *Activity* started.
endedAt | [`Date`](/api/reference/data-modelsata-models/common/date.md) | ANY valid `Date` | The date and time when the *Activity* finished. If `null`, then the *Activity* is still in progress.
referencePositions | [`[GeoPoint]`](/api/reference/data-modelsata-models/common/geo-point.md) | At least one `GeoPoint` |If `"motionType": "stationary"`, it contains a single `GeoPoint` representing the geographical position where the *Device* was still. Otherwise, it will contain at least two elemets representing the Start and the End positions. It may contain other elements corresponding to significant intermediate positions.
duration | `Integer` | ANY `Ìnteger` `n > 0` | The duration of the activity, in seconds.
travelledDistance | `Number` | ANY `Ìnteger` `n > 0` | An estimation of the total distance travelled during the *Activity*, in meters.
averageSpeed | `Number` | ANY `Number` `x > 0` | An estimation of the average speed during the *Activity*, computed as ratio between `"travelledDistance"` and `"duration"`, in meters per seconds.
endToEndDistance | `Number` | ANY `Number` `x > 0` | The distance, in meters, between the first and the last positions.
straightIndex | `Number` | ANY `Number` in [`0`, `1`] | The ratio between `"endToEndDistance"` and `"travelledDistance"`.



## Example Object



```json
{
    "device" : {
        "id": "56fa6815af4ecd00010b000a",
        "customId": "My first device",
        "token": "TOKEN"
    },
    "motionType": "walking",
    "startedAt": "2016-03-11T08:31:00Z",
    "endedAt": "2016-03-11T08:33:00Z",
    "referencePositions": [{
        "lat": 43.722,
        "lng": 10.399
        },{
        "lat": 43.724,
        "lng": 10.398
    }],
    "duration": 120,
    "travelledDistance": 180,
    "averageSpeed": 1.5,
    "endToEndDistance": 150,
    "straightIndex": 0.8333
}
```