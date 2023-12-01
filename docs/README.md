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

> This API serves the Authentication functionality for the Mang Beli application.

### Technology

> - **Runtime**: Node.js
> - **Framework**: Express.js
> - **Dependencies**:
>     | Package        | Version   |
>     | -------------- | --------- |
>     | bcrypt         | 5.1.1     |
>     | cookie-parser  | 1.4.6     |
>     | cors           | 2.8.5     |
>     | dotenv         | 16.3.1    |
>     | express        | 4.18.2    |
>     | jsonwebtoken   | 9.0.2     |
>     | mysql2         | 3.6.5     |
>     | sequelize      | 6.35.1    |

### Deployment

> The API is deployed using Docker on Google Cloud Run.

### Database
> The database is hosted on Google Cloud SQL, utilizing MySQL. 

The table structure is as follows:

| Field         | Type                  | Null | Key | Default | Extra          |
| ------------- | --------------------- | ---- | --- | ------- | -------------- |
| id            | int                   | NO   | PRI | NULL    | auto_increment |
| name          | varchar(225)          | NO   |     | NULL    |                |
| email         | varchar(225)          | NO   | UNI | NULL    |                |
| password      | varchar(225)          | YES  |     | NULL    |                |
| refresh_token | text                  | YES  |     | NULL    |                |
| no_hp         | varchar(255)          | YES  |     | NULL    |                |
| img_profile   | varchar(255)          | YES  |     | NULL    |                |
| role          | enum('user','vendor') | NO   |     | NULL    |                |
| favorite      | json                  | YES  |     | NULL    |                |
| latitude      | varchar(255)          | YES  |     | NULL    |                |
| longitude     | varchar(255)          | YES  |     | NULL    |                |
| createdAt     | datetime              | NO   |     | NULL    |                |
| updatedAt     | datetime              | NO   |     | NULL    |                |

### API Endpoints

- **[Register](/register)**

- **[Login](/login)**

- **[Users](/users)**

- **[Token](/token)**

- **[Logout](/logout)**

Click on each endpoint to view detailed documentation.
