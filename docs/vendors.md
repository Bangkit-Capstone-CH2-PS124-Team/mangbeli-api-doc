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

| Key         | Type    | Required | Description                                                                                                              |
| ----------- | ------- | -------- | ------------------------------------------------------------------------------------------------------------------------ |
| `page`      | integer | Optional | Page number for pagination (default: `1`)                                                                                |
| `size`      | integer | Optional | Number of vendors to fetch per page (default: `10`)                                                                      |
| `location`  | integer | Optional | Location filter (`0` or `1`, default: `0`) - `1`: get vendors with location, `0`: without considering location           |
| `null`      | integer | Optional | Show vendors with null coordinates (`0` or `1`, default: `0`) - `1`: show null coordinates, `0`: not show vendors with null coordinates |
| `filter`    | string  | Optional | Sorting/filtering options - `name`, `minPrice`, `maxPrice`, `nearby`                                                     |
| `search`    | string  | Optional | Search query for name vendors or products - must be at least 2 characters long                                           |

#### Example
- Example request **#1**

```bash
curl -X GET "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/vendors?page=1&size=10" \
-H "Authorization: Bearer <accessToken>"
```

- Example request **#2**

```bash
curl -X GET "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/vendors?page=1&size=5&location=1&filter=nearby&null=1&search=bakso" \
-H "Authorization: Bearer <accessToken>"
```

## Response

### Success Response

- **Status Code:** `200 OK`
    - Example response **#1**
```json
{
    "error": false,
    "message": "Vendors fetched successfully",
    "listVendors": [
        {
            "vendorId": "BQX7Slyu8W",
            "userId": "sxSdOtPSeU",
            "image_url": "https://media.discordapp.net/attachments/880802395414736916/1180103125491789875/7c3613dba5171cb6027c67835dd3b9d4-r.png",
            "name": "Mang Dadang",
            "nameVendor": "Mie Ayam Dadang",
            "no_hp": "089817264568",
            "products": ["Mie Ayam Pangsit", "Mie Ayam Bakso"],
            "minPrice": 10000,
            "maxPrice": 25000,
        },
        // ... (9 more vendors)
    ],
    "currentPage": 1,
    "totalPages": 3
}
```

    - Example response **#2**
```json
{
    "error": false,
    "message": "Vendors fetched successfully",
    "listVendors": [
        {
            "vendorId": "BQX7Slyu8W",
            "userId": "sxSdOtPSeU",
            "image_url": "https://media.discordapp.net/attachments/880802395414736916/1180103125491789875/7c3613dba5171cb6027c67835dd3b9d4-r.png",
            "name": "Mang Dadang",
            "nameVendor": "Mie Ayam Dadang",
            "no_hp": "089817264568",
            "products": ["Mie Ayam Pangsit", "Mie Ayam Bakso"],
            "minPrice": 10000,
            "maxPrice": 25000,
            "latitude": -3.0048287,
            "longitude": 103.5775259,
            "distance": "2.5 KM"
        },
        // ... (4 more vendors)
    ],
    "currentPage": 1,
    "totalPages": 5
}
```

### Error Responses

- **Status Code:** `400 Bad Request`
    - Invalid input or missing fields
        ```json
        {
            "error": true,
            "message": "Invalid value parameter <parameter>"
        }
        ```

    ?> `filter`=`nearby` required parameters `location`

    - Invalid value parameter location for nearby filter
        ```json
        {
            "error": true,
            "message": "Value parameter location required and must be 1 when filter is 'nearby'"
        }
        ```

    - Invalid or missing value latitude and longitude for nearby filter
        ```json
        {
            "error": true,
            "message": "User coordinates not found. Please turn on your location"
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


# **API Documentation - Get Vendors Maps**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/vendors/maps`
- **Method:** `GET`

## Description

> This endpoint is used to retrieve a list of vendors for maps.

## Request

### Headers

| Key            | Value                  | Required | Description                                |
| -------------- | ---------------------- | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>` | Yes      | Authentication token for user authorization|

#### Example
```bash
curl -X GET "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/vendors/maps" \
-H "Authorization: Bearer <accessToken>"
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
            "image_url": "https://media.discordapp.net/attachments/880802395414736916/1180103125491789875/7c3613dba5171cb6027c67835dd3b9d4-r.png",
            "name": "Mang Dadang",
            "nameVendor": "Mie Ayam Dadang",
            "no_hp": "089817264568",
            "products": ["Mie Ayam Pangsit", "Mie Ayam Bakso"],
            "minPrice": 10000,
            "maxPrice": 25000,
            "latitude": -3.0048287,
            "longitude": 103.5775259,
            "distance": "2.5 KM"
        },
        // ... (more vendors)
    ],
    "currentPage": 1,
    "totalPages": 5
}
```

!> Any other HTTP method will result in a **405 Method Not Allowed** response.
