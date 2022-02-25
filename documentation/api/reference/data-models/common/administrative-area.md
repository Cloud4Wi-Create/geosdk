* [Documentation Home](../../../../README.md)  
  * [Web API](../../../index.md)  
    * [Reference](../../index.md)
        * [Data models](../index.md)
          * [Common Data Models](index.md)
          
# Administrative Area

Indicates an administrative area trhorugh a level and a name

Name | Type | Possible Values | Description 
--------|--------|--------|--------
level   |`String` | The set of possible values depends on the specific country |The level of the administrative area
name|`String` | Any string value| The name of the specific area

## Example Object

```json
{
    "level": "Comune",
    "name": "Ascoli Piceno"
}
```

# Administrative levels for Italy

* `"Area Nielsen"` 
* `"Regione"`
* `"Provincia"`
* `"Comune"`

