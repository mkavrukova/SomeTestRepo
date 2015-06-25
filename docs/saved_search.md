##<a name="get-all-user-saved-searches"></a>Get user saved searches
* **URL**

	`GET`
	/searches/my

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Query Params**

	| Name     | Type  | Required | Description                        |
	|----------|-------|----------|------------------------------------|
	| `limit`  | *int* |          | Number of results (**Default 10**) |
	| `offset` | *int* |          | Result offset (**Default 0**)      |

* **Success Response:**

	* **Code:** 200
	* **Content:**

		```json
		{
			"data": [
				{
					"category": "Structure of categories and subcategories",
					"startDate": "2015-06-23T00:00:00.000Z",
					"endDate": "2015-06-25T00:00:00.000Z",
					"notificationFlag": true
				},
				{
					"category": "Structure of categories and subcategories",
					"startDate": "2015-06-23T00:00:00.000Z",
					"endDate": "2015-06-25T00:00:00.000Z",
					"notificationFlag": true
				}
			],
			"totalCount": 2
		}

		```

* **Error Response:**

	* **Code:** 401 UNAUTHORIZED
	* **Content:**

		```json
		{
			"error": "Unauthorized"
		}
		```

##<a name="save-a-user-search"></a>Save a user search

* **URL**

	`POST`
	/searches

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Data Json Payload**

	```json
	{
		"category": "Structure of categories and subcategories",
		"startDate": "2015-06-23T00:00:00.000Z",
		"endDate": "2015-06-25T00:00:00.000Z",
		"notificationFlag" : true
	}
	```

	| Name               | Type      | Required | Description                                                                                     |
	|--------------------|-----------|----------|-------------------------------------------------------------------------------------------------|
	| `category`         | *struct*  | true     | Structure of categories and subcategories<br />*Example: shore(catfish,spinning),boat(catfish)* |
	| `startDate`        | *date*    | true     | trip start date dd/MM/yyyy                                                                      |
	| `endDate`          | *date*    | true     | trip start date dd/MM/yyyy                                                                      |
	| `notificationFlag` | *boolean* | true     | notify user or not                                                                              |


* **Success Response:**

	* **Code:** 201 <br />

* **Error Response:**

	* **Code:** 400 BAD REQUEST
	* **Content:**
		```json
		{
			"error": "Invalid parameters",
			"details": {
				"category": "Invalid category",
			}
		}
		```

	* **Code:** 401 UNAUTHORIZED
	* **Content:**

		```json
		{
			"error": "Unauthorized"
		}
		```

##<a name="change-notification-flag-of-search"></a>Update a notification flag on a search
#####User can update saved search notifications

* **URL**

	`PUT`
	/searches/{savedsearch_id}

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |


* **Data Json Payload**

	```json
	{
		"notificationFlag" : true
	}
	```

	| Name               | Type      | Required | Description        |
	|--------------------|-----------|----------|--------------------|
	| `notificationFlag` | *boolean* | true     | notify user or not |

* **Success Response:**

	*  **Code:** 204 <br />

* **Error Response:**

	* **Code:** 401 UNAUTHORIZED
	* **Content:**

		```json
		{
			"error": "Unauthorized"
		}
		```

##<a name="delete-saved-search"></a>User delete a saved search
#####User can delete saved search

* **URL**

	`DELETE`
	/searches/{savedsearch_id}

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Success Response:**

	* **Code:** 204 <br />

* **Error Response:**

	* **Code:** 401 UNAUTHORIZED
	* **Content:**

		```json
		{
			"error": "Unauthorized"
		}
		```
