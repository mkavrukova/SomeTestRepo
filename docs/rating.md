##<a name="rate-a-tripr">Rate a trip
#####User can rate the trips of the organizer (making an organizer rate) after it has ended

* **URL**

	`POST`
	/ratings

* **Headers**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Data Json Payload**

	```json
	{
		"trip":{
			"id":123
		},
		"rate": 4,
		"review": "review text"
	}
	```

	| Name     | Type     | Required | Description                                     |
  |----------|----------|----------|-------------------------------------------------|
  | `trip`   | *object* | true     | Trip object for the rating `{id: 34}`           |
  | `rate`   | *num*    | true     | Number in the range 1 - 5 for the actual rating |
  | `review` | *string* |          | Optional review for the trip                    |

* **Success Response:**

	* **Code:** 201 <br />

* **Error Response:**

	* **Code:** 400 BAD REQUEST
	* **Content:**
		```json
		{
			"error": "Invalid parameters",
			"details": {
				"rate": "Invalid rate",
			}
		}
		```

	* **Code:** 401 UNAUTHORIZED
	*	**Content:**
		```json
		{
			"error": "Unauthorized"
		}
		```

	* **Code:** 404 NOT FOUND
	*	**Content:**

		```json
		{
			"error": "Not Found",
			"details": {
				"trip": "Trip not found"
			}
		}
		```

##<a name="get-user-rating"></a>Get Ratings for User
#####This is a value calculated by all the ratings of the trips that this user has been an organizer

* **URL**

  `GET`
  /ratings

* **Query Params: **

	| Name     | Type  | Required | Description                        |
	|----------|-------|----------|------------------------------------|
	| `userId` | *int* | true     | User to get ratings for            |
	| `limit`  | *int* |          | Number of results (**Default 10**) |
	| `offset` | *int* |          | Result offset (**Default 0**)      |


* **Success Response:**

  * **Code:** 200 <br />
  * **Content:**

  	```json
		{
			"data": [
				{
				  "trip":{
					  "id":123,
					  "title":"",
				  },
				  "user": {
					  "id":123,
					  "imageUrl":"",
					  "alias":""
				  }
				  "rate": 4,
				  "review": "review text",
				  "createdDate": "2015-06-24T10:10:12.572Z"
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
			"error": "Not Found",
				"details": {
				"user": "User not found",
			}
		}
		```

