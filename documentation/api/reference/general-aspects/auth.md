# Authentication and authorization

Authorization to access resources is grant according to the [OAuth 2.0](https://tools.ietf.org/html/rfc6749) client credentials authorization flow.

## Authentication credentials
Authentication credentials are in the form of an API KEY. The API KEY is specific for each GeoUniq Analytics Project and is generated when the [Project](/service-architecture.md) is created (see [Project Configuration](project-configuration.md)).


## Accessing Resources
All the [endpoints](/api/reference/endpoints/index.md) provided by this API require that a valid access token is provided in the Authorization header of the HTTP request, as detailed below.

> `Authorization : Bearer <access_token>`

## Obtaining an access token
Access tokens are obtained through the HTTPS request detailed below, where `<api_key>` is the API KEY of the specific GeoUniq Analytics Project.

### HTTP Request

* **METHOD**: `POST`

* **HOST**: `auth.geouniq.com`

* **URI**: `/oauth2/token`

* **HEADERS**

    * `Authorization : Basic <api_key>`
    * `Content-Type : application/x-www-form-urlencoded`
    
* **BODY PARAMETERS**

    Name	| Type	    |Description    
    -------|-----------|---------
    grant_type	|String	|Value must be set to `"client_credentials"`


#### Example Request

```
curl --request POST \
  --url https://auth.geouniq.com/oauth2/token \
  --header 'authorization: Basic YOUR_API_KEY' \
  --header 'content-type: application/x-www-form-urlencoded' \
  --data grant_type=client_credentials
```


### Successful Response

* **HTTP STATUS CODE**: 200
* **HEADERS**
    * `Content-Type : application/json`

* **BODY SPECIFICATIONS**

    Name	|Type	| Description
    |-------|-------|------------|
    token_type	|`String`	|Value equal to `"Bearer"`
    expires_in	| `Integer`	| The amount of time (in seconds) after which the token expires
    access_token|	`String`|	The access token

### Example Successful Response

```json
{
    "token_type": "bearer",
    "access_token": "f9ed1c1bfac046699159b4910817b54a",
    "expires_in": 86400
}
````
> Note that, as defined by OAuth2, the content type of the request is application/x-www-form-urlencoded whilst the content type of the response is application/json.