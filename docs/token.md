# **API Documentation - Refresh Token**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/token`
- **Method:** `GET`

## Description

> This endpoint refreshes the access token using a valid refresh token.

## Request

### Headers

| Key            | Value                        | Required | Description                                    |
| -------------- | ---------------------------- | -------- | ---------------------------------------------- |
| `Cookie`       | `refreshToken=<refreshToken>`| Yes      | HTTP Cookie containing the refresh token       |

#### Example
```bash
curl -X GET https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/token \
-H "Cookie: refreshToken=<refreshToken>"
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjIsIm5hbWUiOiJsb3JlbSIsImVtYWlsIjoibG9yZW1AdGVzdC5jb20iLCJpYXQiOjE3MDE0MzQ1NTgsImV4cCI6MTcwMTQzNDYxOH0.FPLbgjwx_cy2wWzydB91cYl3Pm2jG-pMgWh317s_Xck"
}
```

### Error Responses

- **Status Code:** `401 Unauthorized`
    - Missing access token
        ```json
        {
            "error": true,
            "message": "Missing refresh token"
        }
        ```

- **Status Code:** `403 Forbidden`
    - Invalid access token
        ```json
        {
            "error": true,
            "message": "Invalid refresh token"
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
