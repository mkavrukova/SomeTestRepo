##<a name="get-all-places"></a>Get all places

* **URL**

	`GET`
	/places/

* **Query Params**

	| Name     | Type     | Required | Description                           |
	|----------|----------|----------|---------------------------------------|
	| `q`      | *string* |          | Filter the places results by a string |
	| `limit`  | *int*    |          | Number of results (**Default 10**)    |
	| `offset` | *int*    |          | Result offset (**Default 0**)         |

* **Success Response:**

	* **Code:** 200 <br />
	* **Content:**

		```json
		{
			"data": [
				{
					"id": 1,
					"name": "",
					"lat": 0,
					"lon": 0
				}
			],
			"totalCount":1
		}
		```
* **Error Response:**

	* **Code:** 404 NOT FOUND
	* **Content:**

		```json
		{
			"error": "Not found",
		}
		```

##<a name="get-a-place-by-id"></a>Get a place by id

* **URL**

	`GET`
	/places/{placeId}

* **Success Response:**

	* **Code:** 200 <br />
	* **Content:**

		```json
		{
			"id": 1,
			"name": "",
			"lat": 0,
			"lon": 0
		}
		```

* **Error Response:**

	* **Code:** 404 NOT FOUND
	* **Content:**

		```json
		{
			"error": "Not found",
		}
		```