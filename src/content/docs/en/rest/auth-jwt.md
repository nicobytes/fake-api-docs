---
title: Authentication with JWT
description: API endpoints for JWT-based authentication and authorization
---

This API uses JSON Web Tokens (JWT) for secure authentication. The authentication flow consists of three main operations:
1. Obtaining access and refresh tokens via login
2. Accessing protected resources using the access token
3. Refreshing expired access tokens using the refresh token

## Login

To authenticate a user and obtain JWT tokens, send a POST request with email and password credentials.

### Request

```sh
POST https://api.escuelajs.co/api/v1/auth/login
Content-Type: application/json

{
  "email": "john@mail.com",
  "password": "changeme"
}
```

### Response

Upon successful authentication, the server returns both access and refresh tokens:

```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjEsImlhdCI6MTY3Mjc2NjAyOCwiZXhwIjoxNjc0NDk0MDI4fQ.kCak9sLJr74frSRVQp0_27BY4iBCgQSmoT3vQVWKzJg",
  "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjEsImlhdCI6MTY3Mjc2NjAyOCwiZXhwIjoxNjcyODAyMDI4fQ.P1_rB3hJ5afwiG4TWXLq6jOAcVJkvQZ2Z-ZZOnQ1dZw"
}
```

> **Note:** The access token is valid for 20 days, and the refresh token is valid for 10 hours.

## Retrieving User Profile

To access the authenticated user's profile, include the access token in the Authorization header using the Bearer scheme.

### Request

```sh
GET https://api.escuelajs.co/api/v1/auth/profile
Authorization: Bearer {your_access_token}
```

### Response

```json
{
  "id": 1,
  "email": "john@mail.com",
  "password": "changeme",
  "name": "Jhon",
  "role": "customer",
  "avatar": "https://api.lorem.space/image/face?w=640&h=480&r=867"
}
```

## Refreshing Access Token

When an access token expires, you can obtain a new pair of tokens by using the refresh token.

### Request

```sh
POST https://api.escuelajs.co/api/v1/auth/refresh-token
Content-Type: application/json

{
  "refreshToken": "{your_refresh_token}"
}
```

### Response

```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjEsImlhdCI6MTY3Mjc2NjAyOCwiZXhwIjoxNjc0NDk0MDI4fQ.kCak9sLJr74frSRVQp0_27BY4iBCgQSmoT3vQVWKzJg",
  "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjEsImlhdCI6MTY3Mjc2NjAyOCwiZXhwIjoxNjcyODAyMDI4fQ.P1_rB3hJ5afwiG4TWXLq6jOAcVJkvQZ2Z-ZZOnQ1dZw"
}
```

> **Note:** The access token is valid for 20 days, and the refresh token is valid for 10 hours.

## Error Handling

Common authentication errors include:

- **401 Unauthorized**: Invalid credentials or expired tokens
- **403 Forbidden**: Valid authentication but insufficient permissions
- **400 Bad Request**: Malformed request body or headers

Always ensure your application properly handles token expiration by implementing automatic token refresh when needed.
