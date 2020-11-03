# Hook

Data Model used to represent a [*Hook*](/api/resources/user-created/hook.md) Resource.

## Fileds Specification


Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
id    | `String` | Forbidden - Output Only |N.A. | The Resource ID.
createdAt | [`Date`](/api/data-models/common/date.md) | Forbidden - Output Only | N.A. | The date and time when the Resource was created.
name    | `String` | Optional | ANY `String` with length lower than 32 characters| A name for the *Hook*. Can be used to select *Hooks*.
description    | `String` | Optional | ANY `String` with length lower than 128 characters| A description of the *Hook*. Useful for visualization only.
labels  | `[String]` | Optional | At most 10 elements. Each element lower than 16 characters | A set of labels that can be associated to the *Hook*. Can be used to select *Hooks*.
type |`String` | Mandatory | ANY `String` in {`"web"`}| The type of Hook.
web |[`WebHook`](#webhook) | Mandatory if `"type": "web"`. Forbidden otherwise. | ANY valid `WebHook` Object| Information specific for a *Hook* of type *Web*.


## Example Object

```json
{
	"id": "hook1",
	"name": "My First Hook",
	"description": "A simple web hook",
	"labels": ["test"],
    "type": "web",
    "web": {
        "url": "https://api.mydomain.com/geouniq/test"
    }
}
```

---

# WebHook

Data Model used to provide information specific for a *Hook* of type *Web*

## Fileds Specification


Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
url    | `String` | Mandatory | ANY valid HTTP URL | The URL where the HTTP Request carrying the Web Notification has to be sent.

