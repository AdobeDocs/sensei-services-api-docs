# Image Quality Service

This service exposes an HTTP-based API for image quality analysis using the aesthetic model.

## API

```
POST https://sensei.adobe.io/functions/image/imagequality
```

An aesthetic score for a given image can be computed by sending JSON POST requests to `/functions/image/imagequality` where:

* an `image` object provides either a URL string to the processed image, or a JSON object that presents the image

Example:

```json
{
  "image": {
    "uri": "https://cc-api-storage.adobe.io/id/urn:aaid:sc:abc",
    "headers": {
      "Authorization": "Bearer <token>",
      "X-Api-Key": ""
    }
  }
}
```

On successful completion, the server returns a JSON object with the computed individual scores.

Example:

```json
{
  "quality": 0.5922086238861084,
  "balancing_element": 0.03501969575881958,
  "color_harmony": 0.2590048909187317,
  "interesting_content": 0.21257229149341583,
  "depth_of_field": 0.03811390697956085,
  "interesting_lighting": 0.044226981699466705,
  "object_emphasis": 0.2578165829181671,
  "repetition": 0.0716829001903534,
  "rule_of_thirds": -0.01592440903186798,
  "symmetry": 0.03112000599503517
}
```
