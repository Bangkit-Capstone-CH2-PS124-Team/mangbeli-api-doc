# **API Documentation - User Location**

---
## **Update User Location**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/location`
- **Method:** `PATCH`

## Description

> This endpoint is used to update the location coordinates of a user.

## Request

### Headers

| Key           | Value                                | Required | Description                                |
| ------------- | ------------------------------------ | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>`              | Yes      | Authentication token for user authorization|

### Body

| Key         | Type    | Required | Description                      |
| ----------- | ------- | -------- | -------------------------------- |
| `latitude`  | double  | Yes      | New latitude coordinate          |
| `longitude` | double  | Yes      | New longitude coordinate         |

#### Example
```bash
curl -X PATCH https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/location \
-H "Authorization: Bearer <accessToken>" \
-H "Content-Type: application/json" \
-d '{
    "latitude": -6.17521,
    "longitude": 106.82718
}'
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "Location updated successfully"
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

- **Status Code:** `500 Internal Server Error`
    - Internal server error
        ```json
        {
            "error": true,
            "message": "Internal Server Error",
            "errorMessage": "Details about the internal server error"
        }
        ```

---
## **Get User Location**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/location`
- **Method:** `GET`

## Description

> This endpoint is used to retrieve the current location coordinates of a specified user.

## Request

### Headers

| Key           | Value                                | Required | Description                                |
| ------------- | ------------------------------------ | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>`              | Yes      | Authentication token for user authorization|

### Query Parameters

| Key           | Type                                 | Required | Description                               |
| ------------- | ------------------------------------ | -------- | ----------------------------------------- |
| `userId`      | string                               | Yes      | User ID to fetch location for             |

#### Example
```bash
curl -X GET "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/location?userId=527s8rXvQy" \
-H "Authorization: Bearer <accessToken>"
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "Location fetched successfully",
    "latitude": -6.17521,
    "longitude": 106.82718
}
```

### Error Responses

- **Status Code:** `400 Bad Request`
    - Invalid input or missing fields
        ```json
        {
            "error": true,
            "message": "Parameter userId required"
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

- **Status Code:** `404 Not Found`
    - Specified userId is not found
        ```json
            {
                "error": true,
                "message": "User not found"
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
