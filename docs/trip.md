##<a name="get-trip-information"></a>Get data for a single trip
#####Return all trip's categories and subcategories

* **URL**

	`GET`

	/trips/{tripId}/

* **Success Response:**

	* **Code:** 200
	* **Content:**

		```json
		{
			"id": 1827635,
			"title": "",
			"description": "",
			"imageUrl": "",
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
					"type": "via",
					"place": {
						"name": "",
						"lat": 0,
						"lon": 0
					}
				},
				{
					"type": "via",
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
			],
			"vehicles": [
				{
					"type": "car",
					"imageUrl": "",
					"make": "",
					"model": "",
					"year": 0
				},
				{
					"type": "boat",
					"imageUrl": "",
					"make": "",
					"model": "",
					"year": 0
				}
			],
			"seatsAvailable": 0,
			"price": 0,
			"priceCurrency": "",
			"organizer": {
				"id": 0,
				"alias": "",
				"imageUrl": "",
				"rate": 0,
				"rateCount": 0,
				"experience": "",
				"location": {
					"name": "",
					"lat": 0,
					"lon": 0
				},
				"birthYear": 1984,
				"createdDate": "2015-06-24T10:10:12.571Z",
				"details": {
					"tripsListed": 0,
					"tripsJoined": 0,
					"tripsCancelled": 0,
					"messageResponseRate": 0
				}
			},
			"equipment": [
				"tent",
				"gps",
				"other input"
			],
			"bait": {
				"shared": false,
				"description": ""
			},
			"arrivalDate": "2015-06-24T10:10:12.572Z",
			"cancelled": false
		}
		```
* **Error Response:**

	* **Code:** 404 NOT FOUND
	* **Content:**

		```json
		{
			"error": "No such trip"
		}
		```

##<a name="get-all-user-trips"></a>Get all user trips
#####Return all trip's for the authenticated user (joined or organized)subcategories

* **URL**

	`GET`

	/trips/my - returns authenticated trips

	/trips/joined - returns trips authenticated user has joined

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

	* **Code:** 200 <br />
	* **Content:**

		```json
		{
			"data": [
				{
				"id": 1827635,
				"title": "",
				"description": "",
				"imageUrl": "",
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
				],
				"vehicles": [
					{
						"type": "car",
						"imageUrl": "",
						"make": "",
						"model": "",
						"year": 0
					},
					{
						"type": "boat",
						"imageUrl": "",
						"make": "",
						"model": "",
						"year": 0
					}
				],
				"seatsAvailable": 0,
				"price": 0,
				"priceCurrency": "",
				"organizer": {
					"id": 0,
					"alias": "",
					"imageUrl": "",
					"rate": 0,
					"rateCount": 0
				},
				"cancelled": false
			}
		}],
		"totalCount":1
	}
		```
* **Error Response:**

	* **Code:** 404 NOT FOUND
	* **Content:**
		```json
		{
			"error": "No such trip"
		}
		```

	* **Code:** 401 UNAUTHORIZED
	* **Content:**

		```json
		{
			"error": "Unauthorized"
		}
		```

##<a name="user-create-trip"></a>Create a trip
#####User create new trip in the system

* **URL**

	`POST`

	/trips/

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Data Json Payload**

	```json
	{
		"title": "",
		"description": "",
		"imageUrl": "",
		"category": [
			{
				"id": 1
			}
		],
		"startDate": "2015-06-24T10:10:12.568Z",
		"endDate": "2015-06-24T10:10:12.568Z",
		"route": [
			{
				"type": "from",
				"place": {
				"id": 1
				}
			},
			{
				"type": "via",
				"place": {
				"id": null
					"name": "",
					"lat": 0,
					"lon": 0
				}
			},
			{
				"type": "to_closest",
				"place": {
					"id": 2
				}
			},
			{
				"type": "to_exact",
				"place": {
					"id": null
					"name": "",
					"lat": 0,
					"lon": 0
				}
			}
		],
		"vehicles": [
			{
				"type": "car",
				"imageUrl": "",
				"make": "",
				"model": "",
				"year": 0
			},
			{
				"type": "boat",
				"imageUrl": "",
				"make": "",
				"model": "",
				"year": 0
			}
		],
		"seatsAvailable": 0,
		"price": 0,
		"priceCurrency": "",
		"equipment": [
			"tent",
			"gps",
			"other input"
		],
		"bait": {
			"shared": false,
			"description": ""
		},
		"arrivalDate": "2015-06-24T10:10:12.572Z",
	}
	```

* **Success Response:**

	* **Code:** 201 <br />
	* **Content:**

		```json
		{
			"id": 1827635,
			"title": "",
			"description": "",
			"imageUrl": "",
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
					"type": "via",
					"place": {
						"name": "",
						"lat": 0,
						"lon": 0
					}
				},
				{
					"type": "via",
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
			],
			"vehicles": [
				{
					"type": "car",
					"imageUrl": "",
					"make": "",
					"model": "",
					"year": 0
				},
				{
					"type": "boat",
					"imageUrl": "",
					"make": "",
					"model": "",
					"year": 0
				}
			],
			"seatsAvailable": 0,
			"price": 0,
			"priceCurrency": "",
			"organizer": {
				"id": 0,
				"alias": "",
				"imageUrl": "",
				"rate": 0,
				"rateCount": 0,
				"experience": "",
				"location": {
					"name": "",
					"lat": 0,
					"lon": 0
				},
				"birthYear": 1984,
				"createdDate": "2015-06-24T10:10:12.571Z",
				"details": {
					"tripsListed": 0,
					"tripsJoined": 0,
					"tripsCancelled": 0,
					"messageResponseRate": 0
				}
			},
			"equipment": [
				"tent",
				"gps",
				"other input"
			],
			"bait": {
				"shared": false,
				"description": ""
			},
			"arrivalDate": "2015-06-24T10:10:12.572Z",
			"cancelled": false
		}
		```
* **Error Response:**

	* **Code:** 400 BAD REQUEST
	* **Content:**

		```json
		{
			"error": "Invalid input"
			"details": {
				"endDate":"End date is before start date"
			}
		}
		```


##<a name="edit-a-trip"></a>Edit a trip

* **URL**

	`PUT`
	/trips/{tripId}/

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Data Json Payload**

	```json
	{
		"cancelled": false
	}
	```

* **Success Response:**

	* **Code:** 204 <br />

* **Error Response:**

	* **Code:** 404 NOT FOUND
	* **Content:**

		```json
		{
			"error": "No such trip"
		}
		```

	* **Code:** 401 UNAUTHORIZED
	* **Content:**

		```json
		{
			"error": "Unauthorized"
		}
		```


