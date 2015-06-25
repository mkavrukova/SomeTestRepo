##<a name="update-existing-user"></a>Update existing user

* **URL**

	`PUT`
	/users/{userId}

* **Headers:**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Data Json Payload**

	```json
	{
		"firstname": "",
		"lastname": "",
		"email": "",
		"alias": "",
		"imageUrl": "",
		"phone": null,
		"experience": "",
		"location": {
			"name": "",
			"lat": 0,
			"lon": 0
		},
		"birthYear": 1984,
		"bio": ""
	}
	```

* **Success Response:**

	* **Code:** 204

* **Error Response:**

	* **Code:** 400 BAD REQUEST
	* **Content:**

		```json
		{
			"error": "Invalid parameters",
			"details": {
				"email": "Invalid email"
			}
		}
		```

##<a name="update-user-password"></a>Update user password

* **URL**

	`POST`
	/updatepassword/

* **Headers:**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |


* **Data Json Payload**

	```json
	{
		"oldPassword": "",
		"newPassword":""
	}
	```

	| Name          | Type     | Required | Description  |
	|---------------|----------|----------|--------------|
	| `oldPassword` | *string* | true     | old password |
	| `newPassword` | *string* | true     | new password |

* **Success Response:**

	* **Code:** 200

* **Error Response:**

	* **Code:** 400 BAD REQUEST
	* **Content:**

		```json
		{
			"error": "Invalid parameters",
			"details": {
				"oldPassword": "Mismatch in old password"
			}
		}
		```