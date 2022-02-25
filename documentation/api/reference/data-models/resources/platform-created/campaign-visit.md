# Campaign Visit

Data Model used to represent a visit to one of the target POIs configured for [*Campaign*](/api/reference/resources/resources/user-created/campaign.md) Resource related to one of the exposed devices.

## Fields Specificcation

Name        | Type      | Possible Values | Description
------------|----------|----------------|-----------
campaignID | `String` | Any valid Resource ID  | The ID of the [*Campaign*](/api/reference/resources/resources/user-created/campaign.md) Resource for which the has been identified.
device | [`DeviceReference`](/api/reference/data-modelsata-models/common/device-reference.md) | N.A. | The date and time when the Resource was created.
startedAt | [`Date`](/api/reference/data-modelsata-models/common/date.md) | Any valid [`Date`](/api/reference/data-modelsata-models/common/date.md) | The time and date when the visit started
endedAt | [`Date`](/api/reference/data-modelsata-models/common/date.md) | Any valid [`Date`](/api/reference/data-modelsata-models/common/date.md) | The time and date when the visit ended
poiID | `String` | Any value | The ID of the specific POI that has been visited if provided

## Example Object

```json
{
  "campaignID": "campaign1",
  "device": {
    "id": "device1",
    "clientAppId": "clientApp1",
    "customId": "User1",
    "idfa": "cdda802e-fb9c-47ad-9866-0794d394c912"
  },
  "startedAt": "2020-05-01T10:00:00Z",
  "endedAt": "2020-05-01T10:20:00Z",
  "poiID": "POI_1"
}
```
