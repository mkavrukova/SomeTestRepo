##<a name="save-photos-to-a-user"></a>Save photos to a trip
#####User can save photos to a trip, on save user is set as owner

* **URL**

	`POST`
	/photos/

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Data Json Payload**

	```json
	{
		"trip": {
			"id": 123
		},
		"images": [
			{
				"imageUrl": "",
				"description": ""
			}
		]
	}
	```

	| Name     | Type     | Required | Description                                                                         |
	|----------|----------|----------|-------------------------------------------------------------------------------------|
	| `trip`   | *object* | true     | Object containing the id of the trip the user wants to save an object to `{id: 23}` |
	| `images` | *array*  | true     | Array of images to upload to a trip `[{imageUrl: '', description: ''}]`             |

* **Success Response:**

	* **Code:** 201 <br />

* **Error Response:**

	* **Code:** 400 BAD REQUEST
	* **Content:**
		```json
		{
			"error": "Invalid parameters",
			"details": {
				"images": "No images",
			}
		}
		```

	* **Code:** 401 UNAUTHERIZED
	* **Content:**
		```json
		{
			"error": "Unauthorized"
		}
		```

##<a name="retrive-photos"></a>Retrieve photos by user or by trip

* **URL**

	`GET`
	/photos

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |


* **Query Params**

	| Name     | Type     | Required | Description                        |
	|----------|----------|----------|------------------------------------|
	| `tripId` | *tripId* |          | The id of the trip                 |
	| `userId` | *userId* |          | The id of the photo owner          |
	| `limit`  | *int*    |          | Number of results (**Default 10**) |
	| `offset` | *int*    |          | Result offset (**Default 0**)      |


* **Success Response:**

	* **Code:** 200
	* **Content:**
	```json
	{
		"data":[
			{
				"id": "hash",
				"description": "",
				"imageUrl": "",
				"createdDate":"2015-06-24T10:10:12.568Z",
				"trip": {
					"id": 0,
					"title": "",
					"category": [
						{
							"name": "Boat",
							"parentId": 0
						},
						{
							"name": "Catfish",
							"parentId": 1
						}
					],
					"startDate": "2015-06-24T10:10:12.568Z",
					"endDate": "2015-06-24T10:10:12.568Z",
					"route": [
						{
							"type": "from",
							"place": {
								"name": "",
								"lat": 0,
								"lon": 0
							}
						},
						{
							"type": "to_closest",
							"place": {
								"name": "",
								"lat": 0,
								"lon": 0
							}
						},
						{
							"type": "to_exact",
							"place": {
								"name": "",
								"lat": 0,
								"lon": 0
							}
						}
					]
				},
				"onwer": {
					"id": 0
				}
			}
		],
		"totalCount":1
	}
	```

* **Error Response:**

	* **Code:** 400 BAD REQUEST
	*	**Content:**
		```json
		{
			"error": "Invalid parameters",
			"details": {
				"userId": "Required user id",
			}
		}
		```

	* **Code:** 401 UNAUTHERIZED
	* **Content:**

		```json
		{
			"error": "Unauthorized"
		}
		```

##<a name="delete-a-photo"></a>Delete a photo by id/hash
#####Owner can delete owned photos

* **URL**

	`DELETE`
	/photos/{photoId/hash}

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Success Response:**

	* **Code:** 204

* **Error Response:**

	* **Code:** 401 UNAUTHORIZED
	* **Content:**
		```json
		{
			"error": "Unauthorized"
		}
		```

	* **Code:** 404 NOT FOUND