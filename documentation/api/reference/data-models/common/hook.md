* [Documentation Home](../../../../README.md)  
  * [Web API](../../../index.md)  
    * [Reference](../../index.md)
        * [Data models](../index.md)
          * [Common Data Models](index.md)
          
# Hook

Data model used to indicate a hook to which send information

Name | Type | Possible Values | Description 
--------|--------|--------|--------
type | `String` | {`"web"`;`"email"`} | indicates the type of hook
web |[`WebHook`](#webhook) | Mandatory if `"type": "web"`. Forbidden otherwise. | ANY valid `WebHook` Object| Information specific for a *Hook* of type *Web*.
email |[`EmailHook`](#emailhook) | Mandatory if `"type": "email"`. Forbidden otherwise. | ANY valid `EmailHook` Object| Information specific for a *Hook* of type *Email*.

# WebHook

Data Model used to provide information specific for a *Hook* of type *Web*

## Fields Specification


Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
url    | `String` | Mandatory | ANY URL with https protocol
authKey| `String` | Optional | ANY value

# EmailHook

Data Model used to provide information specific for a *Hook* of type *Email*

## Fields Specification


Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
address    | `String` | Mandatory | ANY valid email address

## Example WebHook Object

```json
{
    "type": "web",
    "web": {
        "url": "https://api.mydomain.com/geouniq/test"
        "authKey": "òà2lasxa8013e1"
    }
}
```

## Example EmailHook Object

```json
{
    "type": "email",
    "email": {
        "address": "test@mydomain.com"
    }
}
```
