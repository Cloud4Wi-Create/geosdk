* [Documentation Home](../../../../README.md)
    * [Web API](../../../index.md)  
      * [Reference](../../index.md)  
        * [Endpoints](../index.md)
            

# User-created Resource Endpoints


This section documents the various Endpoints that allow to perform CRUD operations on 
[User-created Resources](../../../resources/user-created/index.md).

For each User-created Resource type defined by this API, the following Endpoints are provided.

* **CREATE Resource**. Allows to create a Resource for the specific type.
    * **Request**
        * **HTTP Method:** POST
        * **Path parameters:** None
        * **Query String parameters:** None
        * **Body:** Data Model used to represent the specific Resource type
    * **Successfull Response:**
        * **Status Code:** 201
        * **Paginated:** NO
        * **Boby:** The representation of the created Resource

* **READ Collection**. Allows to read the whole collection of Resources for the specific type.
    * **Request**
        * **HTTP Method:** GET
        * **Path parameters:** None
        * **Query String parameters:** Possible. Defined by each Endpoint.
        * **Body:** None
    * **Successfull Response:**
        * **Status Code:** 200
        * **Paginated:** YES
        * **Boby:** A [`Page`](../../../general-aspects/pagination.md) of Items, each represented through the Data Model used to represent the specific Resource type

* **READ single Resource**. Allows to read a single Resource of the specific type.
    * **Request**
        * **HTTP Method:** GET
        * **Path parameters:** ID of the desired Resource.
        * **Query String parameters:** None
        * **Body:** None
    * **Successfull Response:**
        * **Status Code:** 200
        * **Paginated:** NO
        * **Boby:** Data Model used to represent the specific Resource type

* **UPDATE Resource**. Allows to update a Resource of the specific type.
    * **Request**
        * **HTTP Method:** PATCH
        * **Path parameters:** ID of the Resource that has to be updated.
        * **Query String parameters:** None
        * **Body:** Data Model used to represent the specific Resource type. Can contain a field if this is allowed input side. Each field provided in the input Body will update the related Resource Attribute. 
    * **Successfull Response:**
        * **Status Code:** 200
        * **Paginated:** NO
        * **Boby:** The The representation of the updated Resource

* **DELETE Resource**. Allows to delete a Resource of the specific type.
    * **Request**
        * **HTTP Method:** DELETE
        * **Path parameters:** ID of the Resource that has to be deleted.
        * **Query String parameters:** None
        * **Body:** None
    * **Successfull Response:**
        * **Status Code:** 204
        * **Paginated:** NO
        * **Boby:** None


According to the various [User-created Resource types defined by this API](../../../resources/user-created/index.md), 
the following set of Endpoints are provided.

* [*Trigger* Endpoints](trigger/index.md)
* [*Campaign* Endpoints](campaign/index.md)
* [*Audience Analysis* Endpoints](audience-analysis/index.md)
* [*Footfall Analysis* Endpoints](campaign/footfall/index.md)
