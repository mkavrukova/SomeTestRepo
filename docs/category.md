##<a name="get-all-trips-categories"></a>Get all trip's categories and subcategories
#####Return all trip's categories and subcategories

* **URL**

	`GET`
	/trips/categories/

* **Success Response:**

	* **Code:** 200 <br />
	* **Content:**

		```json
		{
			"data": [
				{
					"id": 1,
					"name": "Boat",
					"parentId": 0,
					"imageUrl": "http://endpoint/",
					"description": "description text of the category"
				},
				{
					"id": 2,
					"name": "Shore",
					"parentId": 0,
					"imageUrl": "http://endpoint/",
					"description": "description text of the category"
				},
				{
					"id": 101,
					"name": "Catfish",
					"parentId": 1,
					"imageUrl": "http://endpoint/",
					"description": "description text of the category"
				},
				{
					"id": 201,
					"name": "Catfish",
					"parentId": 2,
					"imageUrl": "http://endpoint/",
					"description": "description text of the category"
				}
			]
		}
		```