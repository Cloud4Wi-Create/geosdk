* [Documentation Home](../../README.md)
   * [Web API](../index.md)
      * [Use Cases](index.md)


# Obtain an access token

Before to perform any request to GeoUniq Web API, an access token has to be obtained.
You can do this by performing the request below, where you have to use your API Key for the `<YOUR_API_KEY>` placeholder.

```shell
curl --request POST \
--url https://auth.geouniq.com/oauth2/token \
--header 'authorization: Basic YOUR_API_KEY' \
--header 'content-type: application/x-www-form-urlencoded' \
--data grant_type=client_credentials
```

If a correct API Key has been provided, the response will contain a body like the following

```json
{
    "token_type": "bearer",
    "access_token": "access-token-value",
    "expires_in": 86400
}
```

The `"access_token"` field provides the access token to use in requests.
The access token will be valid for as long as indicated in `"expires_in"`.
One should use the same token for future requests until it expires.