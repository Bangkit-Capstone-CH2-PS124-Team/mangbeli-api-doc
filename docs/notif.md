# **API Documentation - Notification Service**

---
## **Update FCM Token**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/fcm`
- **Method:** `POST`

## Description

> This endpoint is used to update the FCM (Firebase Cloud Messaging) token for a user device.

### Headers

| Key            | Value                                | Required | Description                                |
| -------------- | ------------------------------------ | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>`               | Yes      | Authentication token for user authorization|

### Body

| Key   | Type    | Required | Description                |
| ----- | ------- | -------- | -------------------------- |
| `fcm` | string  | Yes      | FCM token from user device |

#### Example
```bash
curl -X POST "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/fcm" \
-H "Authorization: Bearer <accessToken>" \
-H "Content-Type: application/json" \
-d '{
    "fcm": "J7DS4CJcMJSa2hUJZAU9MHhF5GIclgvIniAUgXS3r:06JawB2Ydk2l.4Q9rq7t2Bi8PTR2H4inKyvS5Lcog9ltRJYoMDVhaCji-u41eTL3YUp_Zs1ZfvmKi8-IerlYu6hXiojAmT1JizUoB15a0EQEvy0G-8YiLT_VISdCZwL"
}'
```
## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "FCM token updated successfully"
}
```

### Error Responses

- **Status Code:** `400 Bad Request`
    - FCM token is required
        ```json
        {
            "error": true,
            "message": "FCM token are required"
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
## **Send Notification**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/notif`
- **Method:** `POST`

## Description

> This endpoint is used to send a notification to a specific user using Firebase Cloud Messaging (FCM).

## Request

### Body

| Key      | Type    | Required | Description                            |
| -------- | ------- | -------- | -------------------------------------- |
| `to`     | string  | Yes      | User ID to send the notification to    |
| `title`  | string  | Yes      | Title of the notification              |
| `body`   | string  | Yes      | Body content of the notification       |

#### Example
```bash
curl -X POST "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/notif" \
-H "Content-Type: application/json" \
-d '{
    "to": "sxSdOtPSeU",
    "title": "MangBeli",
    "body": "Kamu dapet orderan nih!"
}'
```

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "Notification sent successfully"
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

- **Status Code:** `404 Not Found`
    - User not found or FCM token not found for the user
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
