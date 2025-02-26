---
title: Locations
description: Endpoints for locations API
---

The Locations API provides access to geographical location data. Use these endpoints to retrieve location information with various filtering options.

## Get all locations

Retrieve a list of 10 locations randomly.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/locations
```

##### Response

```json
[
    {
        "id": 3456024234637667,
        "name": "2063 Bath Street",
        "description": "Urbanus illum aspernatur.",
        "latitude": 4.647499671477389,
        "longitude": -74.27320830941972
    },
    // Additional locations...
]
```

## Get locations by origin

Retrieve locations sorted by distance from a specified origin point.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/locations?origin=6.2071641,-75.5720321
```

##### Response

```json
[
    {
        "id": 3456024234637667,
        "name": "2063 Bath Street",
        "description": "Urbanus illum aspernatur.",
        "latitude": 4.647499671477389,
        "longitude": -74.27320830941972
    },
    // Additional locations...
]
```

## Get locations with a limit

Retrieve a specific number of locations.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/locations?size=10
```

##### Response

```json
[
    {
        "id": 3456024234637667,
        "name": "2063 Bath Street",
        "description": "Urbanus illum aspernatur.",
        "latitude": 4.647499671477389,
        "longitude": -74.27320830941972
    },
    // Additional locations...
]
```

## Get locations within a radius

Retrieve locations within a specified radius (in kilometers) from an origin point.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/locations?origin=6.2071641,-75.5720321&radius=10
```

##### Response

```json
[
    {
        "id": 3456024234637667,
        "name": "2063 Bath Street",
        "description": "Urbanus illum aspernatur.",
        "latitude": 4.647499671477389,
        "longitude": -74.27320830941972
    },
    // Additional locations...
]
```

## Inspiration

This endpoint allows you to retrieve store locations for an e-commerce platform and display them on a map, enabling you to create interfaces similar to "Starbucks stores near you" that help users find nearby physical locations.

![Locations in a map](https://i.imgur.com/MDLFQpb.png)