# **API Documentation - User Login**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/login`
- **Method:** `POST`

## Description

> This endpoint allows users to log in by providing their email and password.

## Request

### Request Body

| Parameter | Type   | Required | Description                            |
| --------- | ------ | -------- | -------------------------------------- |
| `email`   | string | Yes      | User's email address                   |
| `password`| string | Yes      | User's password (at least 8 characters)|

#### Example
```http
POST https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/login
Content-Type: application/json

{
    "email": "john@example.com",
    "password": "securepassword",
}
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
  	"error": false,
  	"message": "Login successful",
  	"loginResult": {
    	"userId": "527s8rXvQy",
    	"name": "John Doe",
    	"email": "john@example.com",
    	"role": "user",
    	"accessToken": "eyJhbGciOiJIUsI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOiI1MjdHOHJYdlF5IiwiZW1haWwiOiJmYWl6QG1hbmdiZWxpLmNvbSIsInJsbGUiOiJ1c2VyIiwiaWF0IjoxNzAxNzYzODEzsCJleHAiOjE3MDE4NTAyMTN9.dIcsi2GJaBD_0JDQ17lPplmJbsh16mxtk8OsqfVPVug"
	}
}
```

?> accessToken are only **valid** for **1 minute**.

### Error Responses

- **Status Code:** `400 Bad Request`
    - Invalid input or missing fields
        ```json
        {
            "error": true,
            "message": "All fields are required"
        }
        ```

    - Invalid input email format
         ```json
        {
            "error": true,
            "message": "Invalid email format"
        }
        ```

    - Email not registered
        ```json
        {
            "error": true,
            "message": "Email is not registered"
        }
        ```

    - Invalid input password format
        ```json
        {
            "error": true,
            "message": "Password must be at least 8 characters"
        }
        ```

	- Wrong input password
		```json
		{
			"error": true,
            "message": "Wrong Password"
		}
		```

- **Status Code:** `500 Internal Server Error`
    - Internal server error
        ```json
        {
            "error": true,
            "message": "Internal Server Error",
            "errorMessage": "Details about the internal server error"
        }
        ```

!> Any other HTTP method will result in a **405 Method Not Allowed** response.
