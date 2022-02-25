# ConditionsTreeNode

Data Model used to indicate a Boolean expression for [Triggers](/api/concepts/triggers.md) and to obtain a [selection of devices](/api/concepts/device-selection.md).

## Fields Specification

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
nodeType    | `String` | Mandatory |{`"and"`, `"or"`, `"detectedPosition"`, `"activity"`, `"visit"`, `"travel"`, `"livingArea"`, `"homeLocation"`, `"workLocation"`, `"flight"`}| Indicates the type of node. The values `"and"` and `"or"` respectively indicate the logical AND and OR operations among the nodes provided in `"children"`. The other values refer to a leaf node that expresses a [*Statistic Condition*](/api/concepts/statistic-conditions.md) on a specific [type of Resources](/api/reference/resources/device-related/index.md). In these cases, the node will have no children whilst an [`R-StatisticCondition`](/api/reference/data-modelsata-models/r-statistic-condition/index.md) object must be provided.
children    | `[ConditionsTreeNode]` | Mandatory if `"nodeType" : "and"` or `"nodeType" : "or"`. Forbidden otherwise. | Any number `N>2` of `ConditionsTreeNode`  objects. | A set of two or more `ConditionsTreeNode` that must be evaluated considering the logical operator indicated in `"nodeType"`.
detectedPosition | [`DetectedPosition-StatisticCondition`](/api/reference/data-modelsata-models/r-statistic-condition/detected-position.md) | Mandatory if `"nodeType": "detectedPosition"`. Forbidden otherwise. | Any valid `DetectedPosition-Condition` object | A Statistic Condition on *Detected Position* Resources.
activity | [`Activity-StatisticCondition`](/api/reference/data-modelsata-models/r-statistic-condition/activity.md) | Mandatory if `"nodeType": "activity"`. Forbidden otherwise. | Any valid `Activity-Condition` object | A Statistic Condition on *Activity* Resources.
visit | [`Visit-StatisticCondition`](/api/reference/data-modelsata-models/r-statistic-condition/visit.md) | Mandatory if `"nodeType": "visit"`. Forbidden otherwise. | Any valid `Visit-Condition` object | A Statistic Condition on *Visit* Resources.
travel | [`Travel-StatisticCondition`](/api/reference/data-modelsata-models/r-statistic-condition/travel.md) | Mandatory if `"nodeType": "travel"`. Forbidden otherwise. | Any valid `Travel-Condition` object | A Statistic Condition on *Travel* Resources.
livingArea | [`LivingArea-StatisticCondition`](/api/reference/data-models/r-statistic-condition/livin-area.md) | Mandatory if `"nodeType": "livingArea"`. Forbidden otherwise. | Any valid `LivingArea-Condition` object | A Statistic Condition on *Living Area* Resources.
homeLocation | [`HomeLocation-StatisticCondition`](/api/reference/data-modelsata-models/r-statistic-condition/home-location.md) | Mandatory if `"nodeType": "homeLocation"`. Forbidden otherwise. | Any valid `HomeLocation-Condition` object | A Statistic Condition on *Home Location* Resources.
workLocation | [`WorkLocation-StatisticCondition`](/api/reference/data-modelsata-models/r-statistic-condition/work-location.md) | Mandatory if `"nodeType": "workLocation"`. Forbidden otherwise. | Any valid `WorkLocation-Condition` object | A Statistic Condition on *Work Location* Resources.
flight | [`Flight-StatisticCondition`](/api/reference/data-modelsata-models/r-statistic-condition/flight.md) | Mandatory if `"nodeType": "flight"`. Forbidden otherwise. | Any valid `Flight-Condition` object | A Statistic Condition on *Flight* Resources.


## Example Object

```json
{
    "nodeType" : "and",
    "children": [{
        "nodeType": "homeLocation",
        "homeLocation": {
            "select" : {
                "space": {
                    "inside": {
                        "savedAreas": {"name": ["Rome"]}
                    }
                }
            },
            "condition": {
                "count": {"$gt" : 0}
            }
        }
    },{
        "nodeType": "visit",
        "visit": {
            "selection" : {
                "space": {
                    "inside": {
                        "savedAreas": {"name": ["Rome"]}
                    }
                },
                "spatialGranularity" : {
                    "inside": ["City"]
                },
                "time" : {
                    "intersect": {
                        "intervals": [{"from": {"relative":0}, "to": {"relative":0}}]
                    }
                },
                "duration": {"$gt" : 300}
            },
            "condition": {
                "count": {"$gt": 0}
            }
        }
    }]
}
```
