# **API Documentation - Get Vendors**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/vendors`
- **Method:** `GET`

## Description

> This endpoint is used to retrieve a list of vendors with optional parameters for customization.

## Request

### Headers

| Key            | Value                  | Required | Description                                |
| -------------- | ---------------------- | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>` | Yes      | Authentication token for user authorization|

### Query Parameters

| Key           | Type     | Default | Optional | Description                                                  |
| ------------- | -------- | ------- | -------- | ------------------------------------------------------------ |
| `size`        | integer  | 10      | Yes      | Number of vendors to fetch (optional)                        |
| `location`    | integer  | 0       | Yes      | Location filter (`1` to get vendors with detailed location information, `0` to get vendors without considering location) |

#### Example
```http
GET https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/vendors?size=10&location=1
Authorization: Bearer <accessToken>
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "Vendors fetched successfully",
    "listVendors": [
        {
            "vendorId": "BQX7Slyu8W",
            "userId": "sxSdOtPSeU",
            "image_url": "\nhttps://media.discordapp.net/attachments/880802395414736916/1180103125491789875/7c3613dba5171cb6027c67835dd3b9d4-r.png",
            "name": "Mang Dadang",
            "name_vendor": "Mie Ayam Dadang",
            "no_hp": "089817264568",
            "products": "[\"Mie Ayam Pangsit\", \"Mie Ayam Bakso\"]",
            "minPrice": 10000,
            "maxPrice": 25000,
            "latitude": -3.0048287,
            "longitude": 103.5775259
        },
        // ... (more vendors)
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
