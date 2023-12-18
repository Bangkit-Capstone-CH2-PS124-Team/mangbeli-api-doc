# **API Documentation - Get Track Records**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/tracks`
- **Method:** `GET`

## Description

> This endpoint is used to retrieve a location track records of vendors.

## Request

### Headers

| Key            | Value                  | Required | Description                                |
| -------------- | ---------------------- | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>` | Yes      | Authentication token for user authorization|

?> `accessToken` = `MangBeli-CH2-PS124`

#### Example
```bash
curl -X GET "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/tracks" \
-H "Authorization: Bearer <accessToken>"
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "listTracks": [
        {
            "trackId": "54hueCxWC3",
            "vendorId": "BQX7Slyu8W",
            "userId": "sxSdOtPSeU",
            "latitude": -3.0048222,
            "longitude": 103.5775222,
            "createdAt": "2023-12-07T15:43:39.000Z",
            "updatedAt": "2023-12-07T15:43:39.000Z"
        },
        {
            "trackId": "93JalK4Adv",
            "vendorId": "0Q4gNLpXIF",
            "userId": "GX6JBOpuiJ",
            "latitude": -5.232167,
            "longitude": 102.34877,
            "createdAt": "2023-12-07T15:44:05.000Z",
            "updatedAt": "2023-12-07T15:44:05.000Z"
        },
        // ... (more track records)
    ]
}
```

### Error Responses

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

!> Any other HTTP method will result in a **405 Method Not Allowed** response.
