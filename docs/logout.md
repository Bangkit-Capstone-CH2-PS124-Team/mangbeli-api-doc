# **API Documentation - User Logout**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `logout`
- **Method:** `DELETE`

## Description

> This endpoint logs out a user by clearing the refresh token.

## Request

### Headers

| Key           | Value                                | Required | Description                               |
| ------------- | ------------------------------------ | -------- | ----------------------------------------- |
| `Authorization`| Bearer `<accessToken>`               | Yes      | Authentication token for user authorization|

#### Example
```http
GET https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/users
Authorization: Bearer <accessToken>
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "Logout successful"
}
```

### Error Responses
- **Status Code:** `204 No Content`
    - No refresh token is provided or the provided refresh token is invalid
        ```json
        {
            "error": true,
            "message": "No Content"
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
