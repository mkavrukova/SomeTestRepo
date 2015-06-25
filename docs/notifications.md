##<a name="user-notifications"></a>Retrieve notifications for a user

* **URL**

	`GET`
	/notifications/

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Query Params**

	| Name     | Type      | Required | Description                                  |
	|----------|-----------|----------|----------------------------------------------|
	| `limit`  | *int*     |          | Number of results (**Default 10**)           |
	| `offset` | *int*     |          | Result offset (**Default 0**)                |
	| `viewed` | *boolean* |          | true, false, 'missing' (**Default missing**) |

* **Success Response:**

	* **Code:** 200
	* **Content:**

		```json
		{
			"data": [
				{
					"id": 0,
					"summary": "Notification text",
					"entity": {
						"id":0,
						"type":"savedsearch|trip|booking",
						"action":"open|addphoto"
					}
					"createdDate": "2015-06-25T00:00:00.000Z",
					"viewed": true
				}
			],
			"totalCount": 1
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

##<a name="user-update-notification"></a>Update the status of a notification to `viewed`
* **URL**

	`PUT`
	/notifications/{notification_id}

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Data Json Payload**

	```json
	{
		"viewed" : true
	}
	```

	| Name     | Type      | Required      | Description                  |
  |----------|-----------|---------------|------------------------------|
  | `viewed` | *boolean* | true          | user viewed the notification |

* **Success Response:**

	*  **Code:** 204

* **Error Response:**

	* **Code:** 401 UNAUTHORIZED
	* **Content:**

		```json
		{
			"error": "Unauthorized"
		}
		```