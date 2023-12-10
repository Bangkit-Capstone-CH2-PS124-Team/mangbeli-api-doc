# **API Documentation - User Information**

---
## **Get My Profile Information**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/user/profile`
- **Method:** `GET`

## Description

> This endpoint is used to retrieve user profile information for the authenticated user.

## Request

### Headers

| Key            | Value                                | Required | Description                                |
| -------------- | ------------------------------------ | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>`               | Yes      | Authentication token for user authorization|

#### Example
```bash
curl -X GET "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/user/profile" \
-H "Authorization: Bearer <accessToken>"
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "User fetched successfully",
    "dataUser": {
        "userId": "527s8rXvQy",
        "name": "John Doe",
        "email": "john@example.com",
        "imageUrl": "\nhttps://media.discordapp.net/attachments/880802395414736916/1180103125491789875/7c3613dba5171cb6027c67835dd3b9d4-r.png",
        "noHp": "081234567890",
        "role": "user",
        "latitude": -6.17521,
        "longitude": 106.82718,
        "favorite": ["Bakso Telur"],
        "createdAt": "2023-12-01T06:28:46.000Z",
        "updatedAt": "2023-12-07T06:47:21.000Z"
    }
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


---
## **Update My Profile Information**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/user/profile`
- **Method:** `PATCH`

## Description

> This endpoint is used to update information about a user profile, such as name, password, phone number, and favorites.

## Request

### Headers

| Key            | Value                                | Required | Description                                |
| -------------- | ------------------------------------ | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>`               | Yes      | Authentication token for user authorization|

### Body

| Key            | Type     | Required | Description                                          |
| -------------- | -------- | -------- | ---------------------------------------------------- |
| `name`         | string   | Optional | New name of the user                                 |
| `oldPassword`  | string   | Optional | Old password for verification (if updating password) |
| `newPassword`  | string   | Optional | New password for the user (if updating password)     |
| `noHp`         | string   | Optional | New phone number of the user                         |
| `favorite`     | string   | Optional | New user favorites                                   |
| `role`         | string   | Optional | The user's role (e.g., user or vendor)               |

#### Example
```bash
curl -X PATCH https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/user/profile \
    -H "Authorization: Bearer <accessToken>" \
    -H "Content-Type: application/json" \
    -d '{
        "name": "John Doe Heisenberg",
        "oldPassword": "securepassword",
        "newPassword": "newsecurepassword",
        "noHp": "08987654210",
        "favorite": "[\"Mie Ayam Pangsit\"]",
        "role": "user",
    }'
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "User updated successfully"
}
```

### Error Responses

- **Status Code:** `400 Bad Request`
    - If oldPassword filled, newPassword must also be filled
    ```json
    {
        "error": true,
        "message": "newPassword must also be provided"
    }
    ```

    - newPassword less than 8 characters
    ```json
    {
        "error": true,
        "message": "New Password must be at least 8 characters"
    }
    ```

    - Password in database and oldPassword do not match
    ```json
    {
        "error": true,
        "message": "Password and oldPassword do not match"
    }
    ```

    - Invalid role
        ```json
        {
            "error": true,
            "message": "Invalid role"
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
## **Update My Profile Image**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/user/profile/upload`
- **Method:** `POST`

## Description

>  This endpoint is used to upload an image for a user profile.

## Request

### Headers

| Key            | Value                                | Required | Description                                |
| -------------- | ------------------------------------ | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>`               | Yes      | Authentication token for user authorization|

### Body

| Key          | Type     | Required | Description                           |
| ------------ | -------- | -------- | ------------------------------------- |
| `image`      | File     | Yes      | Image file to be uploaded             |

?> `Content-Type` must be `form-data`.

#### Example
```bash
curl -X POST https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/user/profile/upload \
    -H "Authorization: Bearer <accessToken>" \
    -H "Content-Type: multipart/form-data" \
    -F "image=@/path/to/your/image.jpg"
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "Image uploaded successfully",
    "imageUrl": "https://storage.googleapis.com/mangbeli-profile-images/527s8rXvQy-1701932752478.jpg"
}
```

### Error Responses

- **Status Code:** `400 Bad Request`
    - Invalid input or missing fields
        ```json
        {
            "error": true,
            "message": "File image are required"
        }
        ```

    - File extension not allowed
        ```json
        {
            "error": true,
            "message": "File extension not allowed"
        }
        ```
    ?> `File extension` is allowed only `.jpg`, `.jpeg`, `.png`.

    - File type not allowed
        ```json
        {
            "error": true,
            "message": "File type not allowed"
        }
        ```
    ?> `File type` is allowed only `image/jpeg`, `image/png`.

    - File size exceeds the maximum allowed size (5 MB)
        ```json
        {
            "error": true,
            "message": "File size exceeds the maximum allowed size (5 MB)"
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
## **Get User Information by userId**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/user`
- **Method:** `GET`

## Description

> This endpoint is used to retrieve information about a specific user based on their userId.

## Request

### Headers

| Key            | Value                                | Required | Description                                |
| -------------- | ------------------------------------ | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>`               | Yes      | Authentication token for user authorization|

### Query Parameters

| Key           | Type                                 | Required | Description                               |
| ------------- | ------------------------------------ | -------- | ----------------------------------------- |
| `userId`      | string                               | Yes      | User ID to fetch information for          |

#### Example
```bash
curl -X GET "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/user?userId=527s8rXvQy" \
-H "Authorization: Bearer <accessToken>"
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "User fetched successfully",
    "dataUser": {
        "userId": "sxSdOtPSeU",
        "name": "Mang Dadang",
        "email": "dadang@mangbeli.com",
        "imageUrl": "\nhttps://media.discordapp.net/attachments/880802395414736916/1180103125491789875/7c3613dba5171cb6027c67835dd3b9d4-r.png",
        "noHp": "089817264568",
        "role": "vendor",
        "latitude": -2.0048299,
        "longitude": 102.5775299,
        "favorite": ["Es Jeruk"],
        "createdAt": "2023-12-05T06:29:55.000Z",
        "updatedAt": "2023-12-05T13:03:26.000Z"
    }
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
