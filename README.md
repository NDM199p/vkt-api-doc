# API Documentation

# API Documentation: Add Taxonomy Item to User's Repeater Field
POST /wp-json/custom-user/v1/fl-dmsp
## Description
Add a taxonomy item to the user's repeater field (danh_muc_theo_doi) based on the provided parameters.

## Request Body
```
{
  "taxonomy_item": 123
}
```
- taxonomy_item (integer, required):
The ID of the taxonomy item to add to the user's repeater field (danh_muc_theo_doi).
## Response
### Success Response:

Status: 200 OK
```
{
  "status": "success",
  "message": "Taxonomy item added successfully",
  "data": [
    {
      "danh_muc_san_pham": 123
    },
    // Additional taxonomy items in the repeater field
  ]
}
```
- status (string): Indicates the outcome of the operation (success).
- message (string): Description of the operation result.
- data (array): Array containing the updated user's repeater field (danh_muc_theo_doi) including the newly added taxonomy item.
### Error Responses:

Status: 400 Bad Request
```
{
  "status": "error",
  "message": "Missing parameters"
}
```
Status: 404 Not Found
```
{
  "status": "error",
  "message": "Taxonomy item not found"
}
```
Status: 400 Bad Request
```
{
  "status": "error",
  "message": "Taxonomy ID already exists in the repeater field."
}
```
Status: 500 Internal Server Error
```
{
  "status": "error",
  "message": "Failed to update the repeater field"
}
```

## API Documentation: Retrieve Taxonomy Information for User's Repeater Data
GET /wp-json/custom-user/v1/fl-dmsp
## Description
Retrieve taxonomy information associated with a user's repeater data based on provided parameters like user ID, pagination (page and limit).

## Parameters
- user_id (integer, required):

The ID of the user for whom to retrieve taxonomy information.
- page (integer, optional, default: 1):

The page number of results to retrieve (for pagination).
- limit (integer, optional, default: 10):

The maximum number of taxonomy items to retrieve per page (for pagination).
## Response
### Success Response:

Status: 200 OK
```
{
  "status": "success",
  "message": "Taxonomy information retrieved successfully.",
  "data": [
    {
      "term_id": 1,
      "name": "Category 1"
    },
    {
      "term_id": 2,
      "name": "Category 2"
    },
    // Additional taxonomy items as per pagination
  ],
  "page": 1,
  "limit": 10
}
```
### Error Responses:

Status: 400 Bad Request
```
{
  "status": "error",
  "message": "Invalid user ID provided."
}
```
Status: 404 Not Found
```
{
  "status": "error",
  "message": "User does not exist."
}
```
Status: 500 Internal Server Error
```
{
  "status": "error",
  "message": "Failed to retrieve repeater data."
}
```

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
