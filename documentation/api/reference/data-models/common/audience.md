# Audience

Indicates a set od Advertising IDs (AIDs)

Name | Type | Possible Values | Description 
--------|--------|--------|--------
type   | `String` | {`"explicit"`; `"audienceBuilder"`} | Indicates whether the set of AIDs is provided as an explicit list or through the ID of an [`AudienceBuilderAnalysis`](/api/reference/resources/resources/user-created/audience-analysis.md)
explicit | [`explicitAudience`](#explicit-audience) | Any valid [`explicitAudience`](#explicit-audience) | The explicit list of AIDs
analysisID | `String` | Any valid analysis ID | The ID of [`AudienceBuilderAnalysis`](/api/reference/resources/resources/user-created/audience-analysis.md) Resource whose result has to be used as Audience

## Explicit Audience

Name | Type | Possible Values | Description 
--------|--------|--------|--------
aids | `[String]` | Any set of valid AIDs | The list of AIDs

## Example Object with an explicit list of AIDs

```json
{
    "type": "explicit",
    "explicit": {
        "aids":[
            "EA7583CD-A667-48BC-B806-42ECB2B48606", 
            "cdda802e-fb9c-47ad-9866-0794d394c912"
        ]
    }
}
```

## Example Object with that indicates an Audience Builder analysis

```json
{
    "type": "audienceBuilder",
    "analysisID": "analysis1"
}
```