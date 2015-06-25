##<a name="subscribe-usere-for-prelaunch"></a>Subscribe a user for a prelaunch or other events
#####Subscribes user for email notifications for specific category

* **URL**

	`POST`
	/subscribe

* **Data Json Payload**

	| Name       | Type     | Required | Description                                |
	|------------|----------|----------|--------------------------------------------|
	| `email`    | *string* | true     | Email to subscribe                         |
	| `category` | *enum*   | true     | Values are s are "prelaunch", "other", ... |


* **Success Response:**

	* **Code:** 201

* **Error Response:**

	* **Code:** 400 BAD REQUEST
	* **Content:**

		```json
		{
			"error": "Invalid parameters",
			"details": {
				"email": "Invalid email",
				"category": "Invalid category"
			}
		}
		```
