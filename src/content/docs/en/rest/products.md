---
title: Products
description: Endpoints for products
---

You can access the list of 50 products by using the `/products` endpoint.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/products
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
      "id": 5,
      "name": "Others",
      "image": "https://placehold.co/600x400",
      "slug": "others"
    },
    "images": [
      "https://placehold.co/600x400",
      "https://placehold.co/600x400",
      "https://placehold.co/600x400"
    ]
  }
  // ...
]
```

## Get a single product by id

You can get a single product by adding the `id` as a parameter: `/products/<id>`

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/products/4
```

##### Response

```json
{
  "id": 4,
  "title": "Handmade Fresh Table",
  "slug": "handmade-fresh-table",
  "price": 687,
  "description": "Andy shoes are designed to keeping in...",
  "category": {
    "id": 5,
    "name": "Others",
    "image": "https://placehold.co/600x400",
    "slug": "others"
  },
  "images": [
    "https://placehold.co/600x400",
    "https://placehold.co/600x400",
    "https://placehold.co/600x400"
  ]
}
```

## Get a single product by slug

You can get a single product by its slug using the endpoint: `/products/slug/<slug>`

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/products/slug/handmade-fresh-table
```

##### Response

```json
{
  "id": 4,
  "title": "Handmade Fresh Table",
  "slug": "handmade-fresh-table",
  "price": 687,
  "description": "Andy shoes are designed to keeping in...",
  "category": {
    "id": 5,
    "name": "Others",
    "image": "https://placehold.co/600x400",
    "slug": "others"
  },
  "images": [
    "https://placehold.co/600x400",
    "https://placehold.co/600x400",
    "https://placehold.co/600x400"
  ]
}
```

## Create a product

You can create a new product by sending an object like the following to `/products/`

##### Request

```sh
[POST] https://api.escuelajs.co/api/v1/products/
# Body
{
  "title": "New Product",
  "price": 10,
  "description": "A description",
  "categoryId": 1,
  "images": ["https://placehold.co/600x400"]
}
```

##### Response

```json
{
  "title": "New Product",
  "slug": "new-product",
  "price": 10,
  "description": "A description",
  "images": ["https://placehold.co/600x400"],
  "category": {
    "id": 1,
    "name": "Clothes",
    "image": "https://placehold.co/600x400",
    "slug": "clothes"
  },
  "id": 210,
  "creationAt": "2023-01-03T16:51:33.000Z",
  "updatedAt": "2023-01-03T16:51:33.000Z"
}
```

> Note that the `categoryId` should be an ID that exists in `/categories` and the images are an array with URLs.

## Update a product

You can update a product by sending an object like the following and adding the `id` as a parameter: `/products/<id>`

##### Request

```sh
[PUT] https://api.escuelajs.co/api/v1/products/1
# Body
{
  "title": "Change title",
  "price": 100
}
```

##### Response

```json
{
  "id": 1,
  "title": "Change title",
  "slug": "change-title",
  "price": 100,
  "description": "The automobile layout consists of a front-engine design, with transaxle-type transmissions mounted at the rear of the engine and four wheel drive",
  "images": ["https://placehold.co/600x400"],
  "category": {
    "id": 4,
    "name": "Shoes",
    "image": "https://placehold.co/600x400",
    "slug": "shoes"
  }
}
```

> Note that it is not necessary to send all product attributes, just send the ones you want to update.

## Delete a product

You can delete a product by adding the `id` as a parameter: `/products/<id>`

##### Request

```sh
[DELETE] https://api.escuelajs.co/api/v1/products/1
```

##### Response

```json
true
```

## Pagination

The API supports offset-based pagination for retrieving products in manageable chunks. Use the `offset` and `limit` query parameters to control which products are returned.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/products?offset=0&limit=10
```

##### Response

```json
[
  {
    "id": 1,
    "title": "Handmade Fresh Table",
    "slug": "handmade-fresh-table",
    "price": 687,
    "description": "Andy shoes are designed to keeping in...",
    "category": {
      "id": 5,
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
  // ... and 9 items more
]
```

##### How pagination works

- `offset`: The number of items to skip before starting to collect the result set
- `limit`: The maximum number of items to return

To navigate through pages, increase the offset by the value of the limit:

| Request                          | Description                   |
| -------------------------------- | ----------------------------- |
| /products?**offset=0&limit=10**  | Return the first 10 products  |
| /products?**offset=10&limit=10** | Return products from 11 to 20 |
| /products?**offset=20&limit=10** | Return products from 21 to 30 |

For a pagination with 20 items per page:

| Request                          | Description                   |
| -------------------------------- | ----------------------------- |
| /products?**offset=0&limit=20**  | Return the first 20 products  |
| /products?**offset=20&limit=20** | Return products from 21 to 40 |
| /products?**offset=40&limit=20** | Return products from 41 to 60 |

## Get products related by id

You can access the list of related products by using the `/products/<id>/related` endpoint.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/products/1/related
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
      "id": 5,
      "name": "Others",
      "image": "https://placehold.co/600x400",
      "slug": "others"
    },
    "images": [
      "https://placehold.co/600x400",
      "https://placehold.co/600x400",
      "https://placehold.co/600x400"
    ]
  }
  // ...
]
```

## Get products related by slug

You can get the list of related products by using the `/products/slug/<slug>/related` endpoint.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/products/slug/handmade-fresh-table/related
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
      "id": 5,
      "name": "Others",
      "image": "https://placehold.co/600x400",
      "slug": "others"
    },
    "images": [
      "https://placehold.co/600x400",
      "https://placehold.co/600x400",
      "https://placehold.co/600x400"
    ]
  }
  // ...
]
```

## Product Schema

| Attribute   | Type     | Description                                   | Required for Create |
| ----------- | -------- | --------------------------------------------- | ------------------ |
| id          | number   | The unique identifier of the product          | No (auto-generated)|
| title       | string   | The name of the product                       | Yes                |
| price       | number   | Price of the product                          | Yes                |
| description | string   | Description of the product                    | Yes                |
| categoryId  | number   | ID of the category (for create/update)        | Yes                |
| category    | object   | Object containing category information        | No (auto-populated)|
| images      | string[] | List of image URLs                            | Yes                |
| slug        | string   | URL-friendly version of the title             | No (auto-generated)|
| creationAt  | string   | Creation timestamp                            | No (auto-generated)|
| updatedAt   | string   | Last update timestamp                         | No (auto-generated)|