# API Documentation

# UPDATE INFO USER

POST /wp-json/custom-user/v1/update-info

## Auth Method Support

- Cookie

## Body

```
{
"user_email": "newemail@example.com",
"first_name": "John",
"user_phone": "+123456789",
"user_birthday": "1990-01-01",
"gioi_tinh": "male",
"avatar_url": "https://example.com/avatar.jpg"
}
```

## Response

### Success Response:

Status: 200 OK

```
{
"status": "success",
"message": "User information updated successfully",
"user_id": 123
}
```

### Error Responses:

- Status: 400 Bad Request

```
{
"status": "failed",
"message": "New email exists"
}
```

- Status: 500 Internal Server Error

```
{
"status": "error",
"message": "Server error occurred"
}
```

# Get User Information

GET /wp-json/custom-user/v1/info

## Description

Retrieve detailed information about the currently authenticated user.

## Auth Method Support

- Cookie

## Parameters

None

## Response

### Success Response:

Status: 200 OK

```
{
  "status": "success",
  "message": "User information retrieved successfully.",
  "data": {
    "ID": 123,
    "user": {
      "user_email": "user@example.com",
      "user_login": "username",
      "first_name": "John"
    },
    "user_meta": {
      "user_phone": "+123456789",
      "user_birthday": "1990-01-01",
      "gioi_tinh": "male",
      "avatar_url": "https://example.com/avatar.jpg"
    },
    "roles": [
      {
        "role_name": "subscriber",
        "role_id": 2
      }
    ]
  }
}
```

### Error Responses:

Status: 401 Unauthorized

```
{
  "status": "error",
  "message": "Authentication credentials were missing or incorrect."
}
```

Status: 500 Internal Server Error

```
{
  "status": "error",
  "message": "Server error occurred."
}
```

# Get User Wishlist Items

## Description

Retrieve wishlist items of the currently authenticated user.

## Endpoint

GET /wp-json/custom-user/v1/sanpham-whislist

## Auth Method Support

- Cookie: Authentication is handled via cookies.

## GET Parameters

- limit (optional): Number of items to retrieve per page (default: 10).
- page (optional): Page number for pagination (default: 1).

example: /wp-json/custom-user/v1/sanpham-whislist?page=1&limit=3


## Response

### Success Response:

Status: 200 OK

```
{
  "status": "success",
  "message": "Wishlist items retrieved successfully.",
  "data": [
    {
      "post_id": 123,
      "post_title": "Product A",
      "post_content": "Description of Product A",
      "post_thumbnail": "https://example.com/product-a-thumbnail.jpg",
      "post_link": "https://example.com/product-a"
    },
    {
      "post_id": 456,
      "post_title": "Product B",
      "post_content": "Description of Product B",
      "post_thumbnail": "https://example.com/product-b-thumbnail.jpg",
      "post_link": "https://example.com/product-b"
    }
  ],
  "page": 1,
  "limit": 10
}
```

### Error Responses:

Status: 401 Unauthorized

```
{
  "status": "error",
  "message": "Authentication credentials were missing or incorrect."
}
```

Status: 500 Internal Server Error

```
{
  "status": "error",
  "message": "Server error occurred."
}
```

# Get User Download Items

## Description

Retrieve wishlist items of the currently authenticated user.

## Endpoint

GET /wp-json/custom-user/v1/sanpham-download

## Auth Method Support

- Cookie: Authentication is handled via cookies.

## Parameters

- limit (optional): Number of items to retrieve per page (default: 10).
- page (optional): Page number for pagination (default: 1).

  example: /wp-json/custom-user/v1/sanpham-download?page=1&limit=3

## Response

### Success Response:

Status: 200 OK

```
{
  "status": "success",
  "message": "Wishlist items retrieved successfully.",
  "data": [
    {
      "post_id": 123,
      "post_title": "Product A",
      "post_content": "Description of Product A",
      "post_thumbnail": "https://example.com/product-a-thumbnail.jpg",
      "post_link": "https://example.com/product-a"
    },
    {
      "post_id": 456,
      "post_title": "Product B",
      "post_content": "Description of Product B",
      "post_thumbnail": "https://example.com/product-b-thumbnail.jpg",
      "post_link": "https://example.com/product-b"
    }
  ],
  "page": 1,
  "limit": 10
}
```

### Error Responses:

Status: 401 Unauthorized

```
{
  "status": "error",
  "message": "Authentication credentials were missing or incorrect."
}
```

Status: 500 Internal Server Error

```
{
  "status": "error",
  "message": "Server error occurred."
}
```

# Update Password

## Description

Update the password for the currently authenticated user.

## Endpoint

POST /wp-json/custom-user/v1/update-password

## Auth Method Support

Cookie: Authentication is handled via cookies.

## Request Body 

```
{
  "old_password": "current_password",
  "new_password": "new_password"
}
```
- old_password (required): The current password of the user.
- new_password (required): The new password to set for the user.

## Response

### Success Response:

Status: 200 OK

```
{
  "status": "success",
  "message": "Password updated successfully.",
  "user_id": 123
}
```

### Error Responses:

Status: 403 Forbidden

```
{
  "status": "error",
  "message": "The old password is incorrect."
}
```

Status: 500 Internal Server Error

```
{
  "status": "error",
  "message": "Server error occurred."
}
```
