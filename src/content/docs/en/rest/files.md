---
title: Upload File
description: Endpoints for file uploads and retrieval
---

This endpoint allows you to upload files to the server. The uploaded files can later be referenced in other resources such as product images.

##### Request

To upload a file, send a POST request to the `/files/upload` endpoint. The request must use the `multipart/form-data` content type in the header.

```sh
[POST] https://api.escuelajs.co/api/v1/files/upload
Content-Type: multipart/form-data
#Body
{
  "file": "<Binary File>"
}
```

##### Response

A successful upload will return a JSON object containing information about the uploaded file:

```json
{
  "originalname": "Djhv7NO - Imgur.png",
  "filename": "f3a5.png",
  "location": "https://api.escuelajs.co/api/v1/files/f3a5.png"
}
```

## Get a File

You can retrieve a file by using its filename as a parameter in the URL path.

##### Request

```sh
[GET] https://api.escuelajs.co/api/v1/files/{fileName}
```

Where `{fileName}` is the name of the file you want to retrieve (the `filename` value returned from the upload endpoint).

Example:

```sh
[GET] https://api.escuelajs.co/api/v1/files/f3a5.png
```

##### Response

The response will be the requested file with the appropriate content type.
