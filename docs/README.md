# **API Documentation Mang Beli**

<p align="center">
    <img src="https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E">
    <img src="https://img.shields.io/badge/Express%20js-000000?style=for-the-badge&logo=express&logoColor=white">
    <img src="https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white">
    <img src="https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=JSON%20web%20tokens&logoColor=white">
    <img src="https://img.shields.io/badge/Sequelize-52B0E7?style=for-the-badge&logo=Sequelize&logoColor=white">
    <img src="https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white">
    <img src="https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white">
    <img src="https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white">
</p>

## Overview

> This API serves the Authentication and Authorization functionality for the Mang Beli application.

### Technology

> - **Runtime**: Node.js
> - **Framework**: Express.js
> - **Dependencies**:
>     | Package         | Version   |
>     | --------------- | --------- |
>     | bcrypt          | 5.1.1     |
>     | cookie-parser   | 1.4.6     |
>     | cors            | 2.8.5     |
>     | dotenv          | 16.3.1    |
>     | express         | 4.18.2    |
>     | jsonwebtoken    | 9.0.2     |
>     | mysql2          | 3.6.5     |
>     | nanoid          | 5.0.4     |
>     | sequelize       | 6.35.1    |

### Deployment

> The API is deployed using Docker on Google Cloud Run.

### Database
> The database is hosted on Google Cloud SQL, utilizing MySQL. 

The table structure is as follows:

- **Users**

| Field          | Type                  | Null | Key | Default | Extra |
| -------------- | --------------------- | ---- | --- | ------- | ----- |
| userId         | varchar(10)           | NO   | PRI | NULL    |       |
| name           | varchar(225)          | NO   |     | NULL    |       |
| email          | varchar(225)          | NO   | UNI | NULL    |       |
| password       | varchar(225)          | YES  |     | NULL    |       |
| refreshToken   | text                  | YES  |     | NULL    |       |
| imageUrl       | varchar(255)          | YES  |     | NULL    |       |
| noHp           | varchar(20)           | YES  |     | NULL    |       |
| role           | enum('user','vendor') | YES  |     | NULL    |       |
| latitude       | double                | YES  |     | NULL    |       |
| longitude      | double                | YES  |     | NULL    |       |
| favorite       | longtext              | YES  |     | NULL    |       |
| createdAt      | datetime              | NO   |     | NULL    |       |
| updatedAt      | datetime              | NO   |     | NULL    |       |

- **Vendors**

| Field       | Type         | Null | Key | Default | Extra |
| ----------- | ------------ | ---- | --- | ------- | ----- |
| vendorId    | varchar(10)  | NO   | PRI | NULL    |       |
| userId      | varchar(10)  | NO   | MUL | NULL    |       |
| nameVendor  | varchar(225) | YES  |     | NULL    |       |
| products    | longtext     | YES  |     | NULL    |       |
| minPrice    | int(11)      | YES  |     | NULL    |       |
| maxPrice    | int(11)      | YES  |     | NULL    |       |
| createdAt   | datetime     | NO   |     | NULL    |       |
| updatedAt   | datetime     | NO   |     | NULL    |       |

- **Tracks**

| Field     | Type        | Null | Key | Default | Extra |
| --------- | ----------- | ---- | --- | ------- | ----- |
| trackId   | varchar(10) | NO   | PRI | NULL    |       |
| vendorId  | varchar(10) | NO   | MUL | NULL    |       |
| userId    | varchar(10) | NO   | MUL | NULL    |       |
| latitude  | double      | YES  |     | NULL    |       |
| longitude | double      | YES  |     | NULL    |       |
| createdAt | datetime    | NO   |     | NULL    |       |
| updatedAt | datetime    | NO   |     | NULL    |       |

### API Endpoints

- **[Register](/register)**

- **[Login](/login)**

- **[User](/user)**

- **[Vendor](/vendor)**

- **[Vendors](/vendors)**

- **[Tracks](/tracks)**

- **[Location](/location)**

- **[Token](/token)**

- **[Logout](/logout)**

?> Click on each endpoint to view detailed documentation.
