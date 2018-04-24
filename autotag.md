# Auto Tag Service

This service exposes an HTTP-based API for applying tags to images.

## API

```
POST https://sensei.adobe.io/functions/image/autotag

```

Tags for a given image can be predicted by sending JSON POST requests to `/functions/image/autotag` where:

* an `image` object provides either a URL string to the processed image, or a JSON object that presents the image
* a `results` object specifies the maximum number of tags to be returned
* a `confidence` object specifies the minimal tag confidence value to consider (range [0 1], 1 for highest possible confidence)

Example:

```json
{
  "image": {
    "uri": "https://cc-api-storage.adobe.io/id/urn:aaid:sc:abc",
    "headers": {
      "Authorization": "Bearer <token>",
      "X-Api-Key": ""
    }
  },
  "results": 10,
  "confidence": 0.5
}
```

On successful completion, the server returns a JSON array of object entries for every tag where the `tag` property specifies the tag name and `confidence` specifies the confidence of the tag assignment with a value ranging from 0.0 to 1.0 (1.0 represents highest possible confidence).

Example:

```json
{
  "tags":
  [
    { "tag": "landscape", "confidence": "0.851" },
    { "tag": "nature", "confidence": "0.762" }
  ]
}
```
