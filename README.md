Certainly! Here's the documentation in Markdown format that you can use for your README file on GitHub:

```
# API Documentation

This API provides functionality for managing posts and user authentication using JSON Web Tokens (JWT).

## Base URL

The base URL for accessing the API endpoints is `http://localhost:3000` for the posts-related endpoints, and `http://localhost:4000` for the authentication-related endpoints.

## Authentication

All requests except for the `POST /login` endpoint require authentication. The authentication is done using JWT. The JWT should be included in the `Authorization` header using the `Bearer` scheme.

Example:
```
Authorization: Bearer <JWT>
```

## Endpoints

### POST /login

This endpoint is used to authenticate a user and obtain an access token and a refresh token.

#### Request
- Method: POST
- URL: `http://localhost:4000/login`
- Headers:
  - `Content-Type: application/json`
- Body:
  ```json
  {
      "username": "User 1"
  }
  ```

#### Response
- Status: 200 OK
- Body:
  ```json
  {
      "accessToken": "<ACCESS_TOKEN>",
      "refreshToken": "<REFRESH_TOKEN>"
  }
  ```

### POST /token

This endpoint is used to request a new access token using a valid refresh token.

#### Request
- Method: POST
- URL: `http://localhost:4000/token`
- Headers:
  - `Content-Type: application/json`
- Body:
  ```json
  {
      "token": "<REFRESH_TOKEN>"
  }
  ```

#### Response
- Status: 200 OK
- Body:
  ```json
  {
      "accessToken": "<NEW_ACCESS_TOKEN>"
  }
  ```

### DELETE /logout

This endpoint is used to invalidate a refresh token, effectively logging out the user.

#### Request
- Method: DELETE
- URL: `http://localhost:4000/logout`
- Headers:
  - `Content-Type: application/json`
- Body:
  ```json
  {
      "token": "<REFRESH_TOKEN>"
  }
  ```

#### Response
- Status: 204 No Content

### GET /posts

This endpoint is used to retrieve posts for the authenticated user.

#### Request
- Method: GET
- URL: `http://localhost:3000/posts`
- Headers:
  - `Authorization: Bearer <ACCESS_TOKEN>`

#### Response
- Status: 200 OK
- Body:
  ```json
  [
      {
          "username": "User 1",
          "post": "Post 1"
      }
  ]
  ```

Please note that the `<ACCESS_TOKEN>` and `<REFRESH_TOKEN>` placeholders in the request and response examples should be replaced with the actual tokens obtained during the authentication process.

Remember to start the servers at the respective ports before making requests to the API.
```
```

Feel free to copy and paste this Markdown-formatted documentation into your README file on GitHub, making any necessary adjustments or additions to fit your specific project and requirements.