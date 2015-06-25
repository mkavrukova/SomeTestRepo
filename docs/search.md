##<a name="trip-search-with-parameters"></a>Trip search with parameters

* **URL**

	`GET`

	/trips/search

	/trips/{scope}/search

* **Context**

	| Name    | Type   | Required | Values                 |
	|---------|--------|----------|------------------------|
	| `scope` | *enum* |          | Empty or "recommended" |

* **URL Params**

	| Name                | Type           | Required | Description                                                                                     |
	|---------------------|----------------|----------|-------------------------------------------------------------------------------------------------|
	| `q`                 | *string*       |          | Input search string                                                                             |
	| `limit`             | *int*          |          | Number of results (**Default 10**)                                                              |
	| `offset`            | *int*          |          | Result offset (**Default 0**)                                                                   |
	| `sortBy`            | *enum*         |          | "price", "date" (**Default date**)                                                              |
	| `sortOrder`         | *enum*         |          | "asc", "desc" (**Default desc**)                                                                |
	| `category`          | *struct*       |          | Structure of categories and subcategories<br />*Example: shore(catfish,spinning),boat(catfish)* |
	| `startDate`         | *date*         |          | trip start date dd/MM/yyyy                                                                      |
	| `endDate`           | *date*         |          | trip end date dd/MM/yyyy                                                                        |
	| `destinationFrom`   | *int*          |          | Place object id                                                                                 |
	| `destinationTo`     | *int*          |          | Place object id                                                                                 |
	| `distanceRange`     | *int*          |          | Range in meters                                                                                 |
	| `departureTimeFrom` | *time*         |          | Departure time from HH                                                                          |
	| `departureTimeTo`   | *time*         |          | Departure time to HH                                                                            |
	| `seatsAvailable`    | *int*          |          | Available seats                                                                                 |
	| `priceRangeFrom`    | *unsigned int* |          | Price                                                                                           |
	| `priceRangeTo`      | *time*         |          | Departure time to HH                                                                            |
	| `similarTo`         | *tripId*       |          | Reference this trip for similar searches                                                        |
	| `organizerId`       | *userId*       |          | Filter trips by user                                                                            |


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
					"startDate": "2015-06-23T16:52:51.601Z",
					"endDate": "2015-06-23T16:52:51.601Z",
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
						"type":"car",
							"imageUrl": "",
							"make": "",
							"model": "",
							"year": 0
						},
						{
							"type":"boat",
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
						"alias":"",
						"imageUrl": "",
						"rate": 0,
						"rateCount": 0
					}
				}
			],
			"totalCount": 1
		}
		```

* **Error Response:**

	* **Code:** 400 BAD REQUEST <br />
	* **Content:**

		```json
		{
			"error": "Missing required parameters"
		}
		```
