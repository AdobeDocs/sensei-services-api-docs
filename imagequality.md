# Image Aesthetic Score Service

## API

```
POST /api/score

```

An aesthetic score for a given image can be computed by sending `multipart/form-data` POST requests to `/api/score` where:

* a binary body part named `image` provides the raw query image data

On successful completion the server returns a JSON object with with the computed indiviual scores.

Example:

```
POST http://localhost:8888/api/score HTTP/1.1
Content-Type: multipart/form-data; boundary=---------------------------41184676334

-----------------------------41184676334
Content-Disposition: form-data; name="image"; filename="test.jpg"
Content-Type: image/jpeg

(Binary data not shown)
-----------------------------41184676334--



HTTP/1.1 200 OK
Content-Type: application/json

{
  quality: 0.5922086238861084,
  balancing_element: 0.03501969575881958,
  color_harmony: 0.2590048909187317,
  interesting_content: 0.21257229149341583,
  depth_of_field: 0.03811390697956085,
  interesting_lighting: 0.044226981699466705,
  object_emphasis: 0.2578165829181671,
  repetition: 0.0716829001903534,
  rule_of_thirds: -0.01592440903186798,
  symmetry: 0.03112000599503517
}
```
