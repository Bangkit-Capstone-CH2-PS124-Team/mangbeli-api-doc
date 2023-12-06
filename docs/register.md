# **API Documentation - User Registration**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/register`
- **Method:** `POST`

## Description

> This endpoint allows users to register by providing the necessary information.

## Request

### Request Body

| Parameter     | Type   | Required | Description                                       |
| ------------- | ------ | -------- | ------------------------------------------------- |
| `name`        | string | Yes      | The user's name                                   |
| `email`       | string | Yes      | The user's email address                          |
| `password`    | string | Yes      | The user's password (at least 8 characters)       |
| `confPassword`| string | Yes      | Confirm password (must match the `password` field)|
| `role`        | string | Yes      | The user's role (e.g., user or vendor)            |

#### Example
```bash
curl -X POST https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/register \
-H "Content-Type: application/json" \
-d '{
    "name": "John Doe",
    "email": "john@example.com",
    "password": "securepassword",
    "confPassword": "securepassword",
    "role": "user"
}'
```

## Response

### Success Response

- **Status Code:** `201 Created`
```json
{
    "error": false,
    "message": "User Created"
}
```

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

    - Email already registered
        ```json
        {
            "error": true,
            "message": "Email is already registered"
        }
        ```

    - Invalid input password format
        ```json
        {
            "error": true,
            "message": "Password must be at least 8 characters"
        }
        ```

    - Password and Confirm Password do not match
        ```json
        {
            "error": true,
            "message": "Password and Confirm Password do not match"
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
