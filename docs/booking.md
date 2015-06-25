##<a name="book-a-trip"></a>Book a Trip
#####Book a trip (add participant). TripId/UserId is unique pair so we can't have multiple bookings from one user.

[TBD] User asked for 2 seats and was declined, then user should be able to ask for 1 seat

* **URL**

	`POST`
	/bookings/

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Data Json Payload**

	```json
	{
		"trip": {
			"id": 0
		},
		"seats": 2,
	}
	```
	| Name    | Type     | Required | Description                                                      |
	|---------|----------|----------|------------------------------------------------------------------|
	| `trip`  | *object* | true     | Object containing the `id` of the trip for the booking `{id: 4}` |
	| `seats` | *number* | true     | The number of seats that the booking user requests               |

* **Success Response:**

	* **Code:** 201
	* **Content:**

		```json
		{
			"id": 0
			"trip": {
				"id": 123
			},
			"seats": 2,
			"status": "pending",
			"reason": null,
			"createdDate": "2015-06-24T12:08:39.249Z",
			"updatedDate": "2015-06-24T12:08:39.249Z"
		}
		```


* **Error Response:**

	* **Code:** 400 BAD REQUEST
	* **Content:**
		```json
		{
			"error": "Invalid input"
			"details": {
				"seats":"Invalid number of seats"
			}
		}
		```

	* **Code:** 400 BAD REQUEST
	* **Content:**
		```json
		{
			"error": "Invalid input"
			"details": {
				"seats":"Not enough seats"
			}
		}
		```

	* **Code:** 401 NOT FOUND
	* **Content:**
		```json
		{
			"error": "Not found"
			"details": {
				"trip":"Trip with this id does not exist"
			}
		}
		```

	* **Code:** 404 UNAUTHORIZED
	* **Content:**

		```json
		{
			"error": "Unauthorized"
		}
		```

##<a name="delete-booking"></a>Delete (Remove) a booking
#####Remove a booking (so one can send request again)

* **URL**

	`DELETE`
	/bookings/{bookingId}

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Success Response:**

	* **Code:** 204

* **Error Response:**

	* **Code:** 404 NOT FOUND
	* **Code:** 401 UNAUTHORIZED


##<a name="accept-or-decline-a-booking"></a> Accept/Decline Booking of a Trip
#####Organizer can accept/decline (update) the booking request

* **URL**

	`PUT`
	/bookings/{bookingId}

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Data Json Payload**

	```json
	{
		"status": "accepted",
		"reason": null
	}
	```
	| Name     | Type     | Required | Description                                                   |
	|----------|----------|----------|---------------------------------------------------------------|
	| `status` | *string* | true     | The changed status of a booking. Could be `accepted/declined` |
	| `reason` | *string* |          | The reason in case booking is declined                        |

* **Success Response:**

	* **Code:** 204

* **Error Response:**

	* **Code:** 400 BAD REQUEST
	* **Content:**

	```json
	{
		"error": "Invalid input"
		"details": {
			"status":"Invalid status"
		}
	}
	```

##<a name="get-a-single-booking"></a>Get a single booking
#####Get a single booking

* **URL**

	`GET`
	/bookings/{bookingId}

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
			"id" :0,
			"trip": {
				"id": 123,
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
					"birthYear": 1984
				}
			},
			"user": {
				"id": 312,
				"alias": "",
				"phone": null,
				"imageUrl": "",
				"rate": 0,
				"rateCount": 0,
				"experience": "",
				"location": {
					"name": "",
					"lat": 0,
					"lon": 0
				},
				"birthYear": 1984
			},
			"seats": 2,
			"status": "pending",
			"reason": null,
			"contact": "organizer contact info only if accepted",
			"createdDate": "2015-06-24T12:08:39.249Z",
			"updatedDate": "2015-06-24T12:08:39.249Z"
		}
		```

* **Error Response:**

	* **Code:** 404 NOT FOUND
	* **Code:** 401 NOT AUTHORIZED


##<a name="get-all-bookings-for-a-user"></a>Get all bookings for a user
#####Get all bookings for a user based on the auth token

* **URL**

	`GET`
	/bookings

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Query Params**

	| Name     | Type  | Required | Description                        |
	|----------|-------|----------|------------------------------------|
	| `limit`  | *int* |          | Number of results (**Default 10**) |
	| `offset` | *int* |          | Result offset (**Default 0**)      |
	| `tripId` | *id*  |          | The id of a trip      |


* **Success Response:**

	* **Code:** 200
	* **Content:**

		```json
		{
			data: [
				{
	        "id" :0,
	        "trip": {
	          "id": 123,
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
	            "birthYear": 1984
	          }
	        },
	        "user": {
	          "id": 312,
	          "alias": "",
	          "phone": null,
	          "imageUrl": "",
	          "rate": 0,
	          "rateCount": 0,
	          "experience": "",
	          "location": {
	            "name": "",
	            "lat": 0,
	            "lon": 0
	          },
	          "birthYear": 1984
	        },
	        "seats": 2,
	        "status": "pending",
	        "reason": null,
	        "contact": "organizer contact info only if accepted",
	        "createdDate": "2015-06-24T12:08:39.249Z",
	        "updatedDate": "2015-06-24T12:08:39.249Z"
	      }
			]
		}

		```

* **Error Response:**

	* **Code:** 404 NOT FOUND
	* **Code:** 401 NOT AUTHORIZED
