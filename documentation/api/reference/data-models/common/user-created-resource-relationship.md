# UserCreatedResource-Segment

Data Model used to indicate a [User-Created Resource Segment](/api/reference/resources/user-created/index.md); i.e. a set of Resources, of a specific type, belonging to the [User-Created](/api/reference/resources/user-created/index.md) category.
Depending on where this model is used, it can reefer to a different Resource type among those belonging to the [User-Created](/api/reference/resources/resources/user-created/index.md) category.


Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
id | `[String]` | Any combination of valid [User-Created Resource](/api/reference/resources/user-created/index.md) IDs | All the Resources whose ID is in the provided set.
name | `[String]` | Any combination of valid [User-Created Resource](/api/reference/resources/user-created/index.md) Names | All the Resources whose Name is in the provided set.
labels | `[String]`  | Any combination of valid [User-Created Resource](/api/reference/resources/user-created/index.md) Labels | All the Resources that contain at least one of the Labels in the provided set.


```json
{
    "id": ["ID1", "ID2"],
    "name": ["name1", "name2"],
    "labels": ["label1", "label2"]
}
```
