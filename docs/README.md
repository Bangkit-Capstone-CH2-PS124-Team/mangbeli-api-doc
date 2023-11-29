# API Documentation Mang Beli

> API untuk Authentifikasi aplikasi Mang Beli

## URL
https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/

### Register
- Endpoint
    - `/register`
- Method
    - POST
- Request Body
    - `name` as `string`
    - `email` as `string`, must be unique
    - `password` as `string`, must be at least 8 characters
    - `confPassword` as `string`, must exactly match the password
- Response
    -  **201 Created**
        ```json
        {
            "message": "Register Success."
        }
        ```
    - **400 Bad Request**
        ```json
        {
            "message": "Email is already registered."
        }
        ```
        ```json
        {
            "message": "Password and Confirm Password do not match!"
        }
        ```


### Login
- Endpoint
    - `/login`
- Method
    - POST
- Request Body
    - `email` as `string`
    - `password` as `string`, must be at least 8 characters
- Response
    -  **201 Created**
        ```json
        {
            "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjEsIm5hbWUiOiJkdW1teSBhY2NvdW50IiwiZW1haWwiOiJkdW1teUB0ZXN0LmNvbSIsImlhdCI6MTcwMTI0OTIzNywiZXhwIjoxNzAxMjQ5Mjk3fQRWSktb0vigH8kulmLmCCIVmWn0Xy_mJN8pzfhcx5-JY"
        }
        ```
    - **400 Bad Request**
        ```json
        {
            "message": "Wrong Password!"
        }
        ```
        ```json
        {
            "message": "Email is not registered yet!"
        }
        ```

### Get All User
- Endpoint
    - `/users`
- Method
    - GET
- Headers
    - `Authorization`: `Bearer <token>`
- Response
    -  **200 OK**
        ```json
        {
            {
                "users": [
                    {
                        "id": 1,
                        "name": "dummy account",
                        "email": "dummy@test.com",
                        "password": "$2b$10$4MjrZvkGwcqHKXxYobSg5OZpqk5eqBIJ8ijoCXPdmCw/RZpZH5y6.",
                        "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjEsIm5hbWUiOiJkdW1teSBhY2NvdW50IiwiZW1haWwiOiJkdW1teUB0ZXN0LmNvbSIsImlhdCI6MTcwMTI0OTIzNywiZXhwIjoxNzAxMzM1NjM3ft-49zgNWNxjZ-UXVmhrgM74rz7RBlCJKWPOYNA5kHuY",
                        "createdAt": "2023-11-29T07:17:26.000Z",
                        "updatedAt": "2023-11-29T09:13:57.000Z"
                    }
                ]
            }
        }
        ```

### Refresh Token (without Login anymore)
- Endpoint
    - `/token`
- Method
    - GET
- Response
    -  **200 OK**
        ```json
        {
            "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjEsIm5hbWUiOiJkdW1teSBhY2NvdW50IiwiZW1haWwiOiJkdW1teUB0ZXN0LmNvbSIsImlhdCI6MTcwMTI0OTIzNywiZXhwIjoxNzAxMjQ5Mjk3fQRWSktb0vigH8kulmLmCCIVmWn0Xy_mJN8pzfhcx5-JY"
        }

### Logout
- Endpoint
    - `/logout`
- Method
    - DELETE
- Response
    -  **200 OK**
        ```
            OK
        ```
