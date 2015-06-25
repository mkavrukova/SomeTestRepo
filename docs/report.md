##<a name="report-user"></a>Report a User
* **URL**

	`POST`
	/reports/

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Data Json Payload**

	```json
	{
		"user": {
			"id": 123
		},
		"reason":""
	}
	```

	| Name   | Type     | Required | Description                                                  |
  |--------|----------|----------|--------------------------------------------------------------|
  | user   | *object* | true     | Object for the user to be reported in the format `{id: 456}` |
  | reason | *string* | true     | Reason for reporting a user                                  |

* **Success Response:**

	* **Code:** 201 <br />

* **Error Response:**

	* **Code:** 400 BAD REQUEST
	*	**Content:**
		```json
		{
			"error": "Invalid parameters",
			"details": {
				"reason": "reason is required",
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

	* **Code:** 404 NOT FOUND
	* **Content:**

		```json
		{
			"error": "Not Found",
			"details": {
				"user": "User not found"
			}
		}
		```