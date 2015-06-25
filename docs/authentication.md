#<a name="authentication"></a>Authentication

##<a name="create-user-with-email-and-password"></a>Create user account with email and password

* **URL**

	`POST`

	/users/

* **Data Json Payload**

	```json
	{
		"firstname": "",
		"lastname": "",
		"email": "",
		"password" : ""
	}
	```

	| Name        | Type     | Required | Description      |
	|-------------|----------|----------|------------------|
	| `email`     | *string* | true     | User's email     |
	| `password`  | *string* | true     | User's password  |
	| `firstname` | *string* |          | User's firstname |
	| `lastname`  | *string* |          | User's lastname  |


* **Success Response:**
	* **Code:** 201
	* **Headers:**

		| Name            | Description                                                                    |
		|-----------------|--------------------------------------------------------------------------------|
		| `Authorization` | Authorization token for secure communication between a client and the REST API |
	* **Content:**

		```json
		{
			"id":1,
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
			"emailVerified": false,
			"phoneVerified": false,
			"rate": 0,
			"rateCount": 0,
			"birthYear": 1984,
			"createdDate": "2015-06-24T10:10:12.571Z"
		}
		```

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

##<a name="login-user-with-email-and-password">Login a user with email and password

* **URL**

	`POST`

	/login/

* **Data Json Payload**

	```json
	{
		"email": "",
		"password": ""
	}
	```
	| Name       | Type     | Required | Description     |
	|------------|----------|----------|-----------------|
	| `email`    | *string* | true     | User's email    |
	| `password` | *string* | true     | User's password |

* **Success Response:**
	* **Code:** 200
	* **Headers:**

		| Name            | Description                                                                    |
		|-----------------|--------------------------------------------------------------------------------|
		| `Authorization` | Authorization token for secure communication between a client and the REST API |

	* **Content:**
		```json
		{
			"id":1,
			"firstname": "",
			"lastname": "",
			"email": "",
			"imageUrl": ""
		}
		```

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

##<a name="login-user-with-facebook"></a>Login a user with Facebook [TBD]

* **URL**

	`POST`

	/login/facebook/

* **Data Json Payload**

	```json
	{
		"facebookUserId": "",
		"facebookUserToken": "",
		"facebookUserTokenType": ""
	}
	```
	| Name                    | Type     | Required | Description                         |
  |-------------------------|----------|----------|-------------------------------------|
  | `facebookUserId`        | *string* | true     | User's FB id                        |
  | `facebookUserToken`     | *string* | true     | User's FB access token              |
  | `facebookUserTokenType` | *string* | true     | User's FB access token type "short" |

* **Success Response:**

	* **Code:** 201
	* **Headers:**

		|Name|Description|
		|----|-----------|
		|`Authorization`|Authorization token for secure communication between a client and the REST API|

	* **Content:**

		```json
		{
			"id":1,
			"firstname": "",
			"lastname": "",
			"email": "",
			"imageUrl": ""
		}
		```

* **Error Response:**

	* **Code:** 400 BAD REQUEST
	* **Content:**

		```json
		{
			"error": "Invalid parameters",
			"details": {
				"token": "Invalid token"
			}
		}
		```

##<a name="request-password-reset"></a>Request a password reset

* **URL**

  `POST`
  /forgot_password/

* **Data Json Payload**

	```json
	{
	  "email": ""
	}
	```
	| Name    | Type     | Required | Description  |
	|---------|----------|----------|--------------|
	| `email` | *string* | true     | User's email |

* **Success Response:**

  * **Code:** 200

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
	* **Code:** 404 NOT FOUND
	* **Content:**

		```json
		{
			"error": "Invalid parameters",
			"details": {
				"email": "Not Found"
			}
		}
	```

##<a name="forgotten-password-request-for-reset-with-token-and-new-password"></a>Forgotten password request for reset with token and new password

* **URL**

  `POST`

  /resetpassword/

* **Data Json Payload**

	```json
	{
	  "t": "",
	  "password":""
	}
	```

	| Name       | Type     | Required | Description       |
	|------------|----------|----------|-------------------|
	| `t`        | *string* | true     | email reset token |
	| `password` | *string* | true     | new password      |

* **Success Response:**
  * **Code:** 200
  * **Headers:**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Error Response:**

	* **Code:** 400 BAD REQUEST
  * **Content:**

	  ```json
		{
		  "error": "Invalid parameters",
		  "details": {
			  "t": "Invalid token"
		  }
		}
		```

##<a name="request-email-verify"></a>Request an email verify
* **URL**

  `POST`
  /verifyemail

* **Headers:**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Success Response:**

  * **Code:** 200

* **Error Response:**

	* **Code:** 404 UNAUTHORIZED
	* **Content:**

		```json
		{
			"error": "Unauthorized",
		}
		```

##<a name="verify-email-request-with-token"></a>Verify email request with a token
#####Email confirmation via link

* **URL**

  `POST`
  /confirmemail/

* **Data Json Payload**

	```json
	{
	  "t": ""
	}
	```

	| Name | Type     | Required | Description        |
	|------|----------|----------|--------------------|
	| `t`  | *string* | true     | email verify token |

* **Success Response:**

  * **Code:** 200

* **Error Response:**

	* **Code:** 400 BAD REQUEST
	* **Content:**

		```json
		{
			"error": "Invalid parameters",
			"details": {
				"t": "Invalid token"
			}
		}
		```

##<a name="request-phone-verify"></a>Request a phone verify
#####Verify user's phone (get user by SMS code) get phone from authtoken

* **URL**

  `POST`
  /verifyphone/

* **Headers:**

	| Name            | Description                                                                    |
	|-----------------|--------------------------------------------------------------------------------|
	| `Authorization` | Authorization token for secure communication between a client and the REST API |

* **Success Response:**

  * **Code:** 200

* **Error Response:**

	* **Code:** 404 UNAUTHORIZED
	* **Content:**

		```json
		{
			"error": "Unauthorized",
		}
		```

##<a name="verify-phone-request-with-verification-code"></a>Verify phone request with verification code
#####Confirm your phone with code from SMS

* **URL**

  `POST`
  /confirmphone/

* **Data Json Payload**

	```json
	{
	  "code": ""
	}
	```

	| Name   | Type     | Required | Description       |
	|--------|----------|----------|-------------------|
	| `code` | *string* | true     | phone verify code |

* **Success Response:**

  * **Code:** 200

* **Error Response:**

	* **Code:** 400 BAD REQUEST
  * **Content:**

		```json
		{
			"error": "Invalid parameters",
			"details": {
				"code": "Invalid code"
			}
		}
		```