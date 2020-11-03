# User-created Resource Endpoints


This section documents the various Endpoints that allow to perform CRUD operations on [User-created Resources](/api/resources/user-created/index.md).

For all of them, it holds the following.

**EXAMPLE URL:** `https://api.geouniq.com/v1/<ENDPOINT_SPECIFIC_PATH>`

For each User-created Resource Class defined by this API, the following Endpoints are provided.

* **CREATE Resource**. Allows to create a Resource for the specific Class.
    * **Request**
        * **HTTP Method:** POST
        * **Path parameters:** None
        * **Query String parameters:** None
        * **Body:** Data Model used to represent the specific Resource Class
    * **Successfull Response:**
        * **Status Code:** 201
        * **Paginated:** NO
        * **Boby:** The representation of the created Resource
* **READ Collection**. Allows to read the whole collection of Resources for the specific Class.
    * **Request**
        * **HTTP Method:** GET
        * **Path parameters:** None
        * **Query String parameters:** Possible. Defined by each Endpoint.
        * **Body:** None
    * **Successfull Response:**
        * **Status Code:** 200
        * **Paginated:** YES
        * **Boby:** A [`Page`](/api/general-aspects/pagination.md) of Items, each represented through the Data Model used to represent the specific Resource Class
* **READ single Resource**. Allows to read a single Resource of the specific Class.
    * **Request**
        * **HTTP Method:** GET
        * **Path parameters:** ID of the desired Resource.
        * **Query String parameters:** None
        * **Body:** None
    * **Successfull Response:**
        * **Status Code:** 200
        * **Paginated:** NO
        * **Boby:** Data Model used to represent the specific Resource Class
* **UPDATE Resource**. Allows to update a Resource of the specific Class.
    * **Request**
        * **HTTP Method:** PATCH
        * **Path parameters:** ID of the Resource that has to be updated.
        * **Query String parameters:** None
        * **Body:** Data Model used to represent the specific Resource Class. Can contain a field if this is allowed input side. Each field provided in the input Body will update the related Resource Attribute. 
    * **Successfull Response:**
        * **Status Code:** 200
        * **Paginated:** NO
        * **Boby:** The The representation of the updated Resource
* **DELETE Resource**. Allows to delete a Resource of the specific Class.
    * **Request**
        * **HTTP Method:** DELETE
        * **Path parameters:** ID of the Resource that has to be deleted.
        * **Query String parameters:** None
        * **Body:** None
    * **Successfull Response:**
        * **Status Code:** 204
        * **Paginated:** NO
        * **Boby:** None


According to the various [User-created Resource Classes defined by this API](/api/resources/user-created/index.md), the following set of Endpoints are provided.

* [*Campaign* Endpoints](/api/endpoints/resources/user-created/campaign/index.md)
* [*Audience Analysis* Endpoints](/api/endpoints/resources/user-created/audience-analysis/index.md)
* [*Footfall Analysis* Endpoints](/api/endpoints/resources/user-created/campaign/footfall/index.md)
* [*Trigger* Endpoints](/api/endpoints/resources/user-created/trigger/index.md)
* [*Hook* Endpoints](/api/endpoints/resources/user-created/hook/index.md)
* [*Campaign* Endpoints](/api/endpoints/resources/user-created/campaign/index.md)
