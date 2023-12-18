# **API Documentation - Get Users Maps**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/users/maps`
- **Method:** `GET`

## Description

> This endpoint is used to retrieve a list of users for maps.

## Request

### Headers

| Key            | Value                  | Required | Description                                |
| -------------- | ---------------------- | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>` | Yes      | Authentication token for user authorization|

#### Example
```bash
curl -X GET "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/users/maps" \
-H "Authorization: Bearer <accessToken>"
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "Maps users fetched successfully",
    "listUsers": [
        {
            "userId": "527s8rXvQy",
            "name": "John Doe",
            "imageUrl": "https://media.discordapp.net/attachments/880802395414736916/1180103125491789875/7c3613dba5171cb6027c67835dd3b9d4-r.png",
            "noHp": "081234567890",
            "favorite": ["Bakpao", "Mie Ayam Bakso"],
            "latitude": -3.0048287,
            "longitude": 103.5775259,
            "distance": "1.2 KM"
        },
        // ... (more users)
    ],
}
```

### Error Responses

- **Status Code:** `400 Bad Request`
    - Invalid or missing value user latitude and longitude
        ```json
        {
            "error": true,
            "message": "Vendor coordinates not found. Please turn on your location"
        }
        ```

- **Status Code:** `401 Unauthorized`
    - Missing access token
        ```json
        {
            "error": true,
            "message": "Missing access token"
        }
        ```

- **Status Code:** `403 Forbidden`
    - Invalid access token
        ```json
        {
            "error": true,
            "message": "Invalid access token"
        }
        ```

    - Invalid role
        ```json
        {
            "error": true,
            "message": "Invalid role"
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
