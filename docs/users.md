# **API Documentation - Get Users**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/users`
- **Method:** `GET`

## Description

> This endpoint only for test Authentication accessToken for user Authorization.

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
    "users": [
        {
            "userId": 1,
            "name": "John Doe",
            "email": "john@example.com",
            "password": "$2b$10$CtyK0nFIgBUGN3g.bVovPOh6PkkBkLa6v1.9hLGfC5PNUZEJNL4nq",
            "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjEsIm5hbWUiOiJ1ZGliIiwiZW1haWwiOiJ1ZGluc2VkdW5pYUBkaWNvZGluZy5jb20iLCJpYXQiOjE3MDE0MjE0NDMsImV4cCI6MTcwMTUwNzg0M30.XhqMxBtmwtkmyqD9idzjmWy3QjeHf0autXprKr1MBqM",
            "role": "user",
            "createdAt": "2023-12-01T06:25:18.000Z",
            "updatedAt": "2023-12-01T09:04:03.000Z"
        },
        And other users...
    ]
}
```

### Error Responses

- **Status Code:** `403 Forbidden`
    - Missing or invalid access token
        ```json
        {
            "error": true,
            "message": "Unauthorized: Missing or invalid access token"
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
