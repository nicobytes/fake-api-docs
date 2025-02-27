---
title: Categories
description: API endpoints for managing product categories
---

Retrieve a list of all available categories.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/categories
```

##### Response

```json
[
  {
    "id": 1,
    "name": "Clothes",
    "slug": "clothes",
    "image": "https://placehold.co/600x400"
  }
  // Additional categories...
]
```

## Get a single category by ID

Retrieve detailed information about a specific category by its ID.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/categories/{id}
```

##### Response

```json
{
  "id": 1,
  "name": "Clothes",
  "slug": "clothes",
  "image": "https://placehold.co/600x400"
}
```

## Get a single category by slug

Retrieve detailed information about a specific category by its slug.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/categories/slug/{slug}
```

##### Response

```json
{
  "id": 1,
  "name": "Clothes",
  "slug": "clothes",
  "image": "https://placehold.co/600x400"
}
```

##### Response

```json

```

## Create a category

Create a new category by providing the required information.

##### Request

```sh
[POST] https://api.escuelajs.co/api/v1/categories/

#Body
{
  "name": "New Category",
  "image": "https://placeimg.com/640/480/any"
}
```

##### Response

```json
{
  "name": "New Category",
  "slug": "new-category",
  "image": "https://placeimg.com/640/480/any",
  "id": 6
}
```

> **Note:** The image field must be a valid URL to an image resource.

## Update a category

Update an existing category's information by its ID.

##### Request

```sh
[PUT] https://api.escuelajs.co/api/v1/categories/{id}

#Body
{
  "name": "Updated Category Name",
  "image": "https://placeimg.com/640/480/any"
}
```

##### Response

```json
{
  "id": 3,
  "name": "Updated Category Name",
  "slug": "updated-category-name",
  "image": "https://placehold.co/600x400"
}
```

## Delete a category

Remove a category from the system by its ID.

##### Request

```sh
[DELETE] https://api.escuelajs.co/api/v1/categories/{id}
```

##### Response

```json
true
```

## Get all products by category

Retrieve all products that belong to a specific category with pagination support.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/categories/{id}/products
```

##### Response

```json
[
  {
    "id": 4,
    "title": "Handmade Fresh Table",
    "slug": "handmade-fresh-table",
    "price": 687,
    "description": "Andy shoes are designed to keeping in...",
    "category": {
      "id": 1,
      "name": "Others",
      "slug": "others",
      "image": "https://placehold.co/600x400"
    },
    "images": [
      "https://placehold.co/600x400",
      "https://placehold.co/600x400",
      "https://placehold.co/600x400"
    ]
  }
  // Additional products...
]
```

## Category Schema

| Attribute | Type   | Description                           |
| --------- | ------ | ------------------------------------- |
| id        | number | The unique identifier of the category |
| name      | string | Name of the category                  |
| image     | string | URL to the category's image           |
| slug      | string | URL-friendly version of the name      |
