#Overview

####This document contains description of all the REST API calls for the GoGoFish application

###Content:

* [**Authentication, Registration and Login**](docs/authentication.md) - calls and model structure related to user authentication
	* [Create user account with email and password](docs/authentication.md#create-user-with-email-and-password)
	* [Login a user with email and password](docs/authentication.md#login-user-with-email-and-password)
	* [Login a user with Facebook](docs/authentication.md#login-user-with-facebook)
	* [Request a password reset](docs/authentication.md#request-password-reset)
	* [Forgotten password request for reset with token and new password](docs/authentication.md#forgotten-password-request-for-reset-with-token-and-new-password)
	* [Request an email verify](docs/authentication.md#request-email-verify)
	* [Verify email request with a token](docs/authentication.md#verify-email-request-with-token)
	* [Request a phone verify](docs/authentication.md#request-phone-verify)
	* [Verify phone request with verification code](docs/authentication.md#verify-phone-request-with-verification-code)
* [**User**](user) - calls and model structure related to updating a user
	* [Update existing user information](docs/user.md#update-existing-user)
	* [Update user's password](docs/user.md#update-user-password)
	* [Delete a photo by id/hash](docs/photo.md#delete-a-photo)
	* [Retrieve notifications for a user](docs/notifications.md#user-notifications)
	* [Update the status of a notification to `viewed`](docs/notifications.md#user-update-notification)
	* [Get Ratings for User](docs/rating.md#get-user-rating)
	* [Report a User](docs/report.md#report-user)
	* [Get user saved searches](docs/saved_search.md#get-all-user-saved-searches)
	* [Save a user search](docs/saved_search.md#save-a-user-search)
	* [Update a notification flag on a search](docs/saved_search.md#change-notification-flag-of-search)
	* [User delete a saved search](docs/saved_search.md#delete-saved-search)
	* [Get user trips](docs/trip.md#get-all-user-trips)
* [**Search**](search) - calls and model structure related to returning a list of trips, based on criteria
	* [Trip search with parameters](docs/search.md#trip-search-with-parameters)
* [**Trip**](trip) - calls and model structure related to creating, updating and managing a trip
	* [Get all trip's categories and subcategories](docs/category.md#get-all-trips-categories)
	* [Save photos to a trip](docs/photo.md#save-photos-to-a-user)
	* [Retrieve photos by user or by trip](docs/photo.md#retrive-photos)
	* [Rate a trip](docs/rating.md#rate-a-trip)
	* [Get data for a single trip](docs/trip.md#get-trip-information)
	* [Create a trip](docs/trip.md#user-create-trip)
	* [Edit a trip](docs/trip.md#edit-a-trip)
* [**Places**](place) - calls and model structure related to creating and retrieving places
	* [Get all places](docs/place.md#get-all-places)
	* [Get a place by id](docs/place.md#get-a-place-by-ids)
* [**Booking**](bookings) - calls and model structure related to requesting/accepting/declining managing bookings for a trip
	* [Book a Trip](docs/booking.md#book-a-trip)
	* [Delete (Remove) a booking](docs/booking.md#delete-booking)
	* [Accept/Decline Booking of a Trip](docs/booking.md#accept-or-decline-a-booking)
	* [Get a single booking](docs/booking.md#get-a-single-booking)
	* [Get all bookings for a user](docs/booking.md#get-all-bookings-for-a-user)
* [**Subscriptions**](docs/subscriptions.md)
	* [Subscribe a user for a prelaunch or other events](docs/subscriptions.md#subscribe-usere-for-prelaunch)