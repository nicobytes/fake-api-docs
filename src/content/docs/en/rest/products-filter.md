---
title: Filter Products
description: Endpoints to filter products by various criteria
---

The API provides several ways to filter products using query parameters. All filter requests should be made to the base endpoint:

```sh
[GET] https://api.escuelajs.co/api/v1/products
```

## Filter by Title

Filter products by their title using the `title` query parameter.

```sh
[GET] https://api.escuelajs.co/api/v1/products/?title=Generic
```

## Filter by Price

Filter products by their exact price using the `price` query parameter.

```sh
[GET] https://api.escuelajs.co/api/v1/products/?price=100
```

## Filter by Price Range

Filter products within a price range using the `price_min` and `price_max` query parameters.

```sh
[GET] https://api.escuelajs.co/api/v1/products/?price_min=900&price_max=1000
```

## Filter by Category

Filter products by their category using the `categoryId` or `categorySlug` query parameter.

```sh
[GET] https://api.escuelajs.co/api/v1/products/?categoryId=1
```

```sh
[GET] https://api.escuelajs.co/api/v1/products/?categorySlug=clothes
```

## Combining Filters

You can combine multiple filters by adding multiple query parameters to create more specific queries.

#### Example 1: Title, Price Range, and Category

Get all products with the title "Generic", price between 900 and 1000, and category ID 1:

```sh
[GET] https://api.escuelajs.co/api/v1/products/?title=Generic&price_min=900&price_max=1000&categoryId=1
```

#### Example 2: Price Range and Category with Pagination

Get products with price between 900 and 1000, category ID 1, with pagination (10 products per page, starting from the 10th product):

```sh
[GET] https://api.escuelajs.co/api/v1/products/?price_min=900&price_max=1000&categoryId=1&limit=10&offset=10
```

#### Example 3: Price Range with Pagination

Get products with price between 100 and 1000, with pagination (10 products per page, starting from the 10th product):

```sh
[GET] https://api.escuelajs.co/api/v1/products/?price_min=100&price_max=1000&limit=10&offset=10
```

## Response Format

The API returns an array of product objects that match the specified filters. Each product includes details such as ID, title, price, description, category, and images.
