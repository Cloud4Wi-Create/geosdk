# Endpoints

This Section documents the various Endpoints provided by this API.

For all of them, it holds the following.

**PROTOCOL**: `https`

**HOST NAME**: `api.geouniq.com`

**PATH ENTRY POINT**: `/v1`

**EXAMPLE URL**: `https://api.geouniq.com/v1/<ENDPOINT_SPECIFIC_PATH>`


The following categories of Endpoints are provided.

* **[Resources Endpoints](/api/endpoints/resources/index.md)** Allow to perform CRUD operations on [Resources](/api/resources/index.md).
* **[Statistic Endpoints](/api/endpoints/statistics/index.md)** Allow to obtain [Statistics](/api/concepts/statistics.md) for [Platform-created Resources](/api/resources/platform-created/index.md).


Regardless of the specific Endpoint, each Request must be authorized according to the [Authentication and Authorization mecanism defined by this API](/api/auth.md).

In addition, if the Endpoint provides for a Paginated Response, [Pagination](/api/general-aspects/pagination.md) must be handled by the client.