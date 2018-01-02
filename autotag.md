# Auto Tag Service

This service exposes an HTTP-based API for applying tags to images.

## API

```
POST /api/tag

```

Tags for a given image can be predicted by sending `multipart/form-data` POST requests to `/api/tag` where:

* a binary body part named `queryImage` provides the raw query image data
* a text body part named `maxResults` specifies the maximum number of tags to be returned
* a text body part named `minConfidence` specifies the minimal tag confidence value to consider (range [0 1], 1 for highest possible confidence)

On successful completion, the server returns a JSON array with object entries for every tag where the `tag` property specifies the tag name and `confidence` specifies the confidence of the tag assignment with a value ranging from 0.0 to 1.0 (1.0 represents highest possible confidence).

Example:

```
POST http://localhost:8888/api/tag HTTP/1.1
Content-Type: multipart/form-data; boundary=---------------------------41184676334

-----------------------------41184676334
Content-Disposition: form-data; name="queryImage"; filename="test.jpg"
Content-Type: image/jpeg

(Binary data not shown)
-----------------------------41184676334
Content-Disposition: form-data; name="maxResults"

25
-----------------------------41184676334
Content-Disposition: form-data; name="minConfidence"

0.75
-----------------------------41184676334--



HTTP/1.1 200 OK
Content-Type: application/json

[
  { "tag": "landscape", "confidence": "0.851" },
  { "tag": "nature", "confidence": "0.762" }
]
```

## Run the service locally

1. Download Model Files

   Copy `data.zip` from `smb://sjshare.corp.adobe.com/share/mil_research_engineering/installation_large_files/hashtag2/` and extract it in `/sensei-data/autotagging` folder.

2. Install dependencies

     ```
     cd /path/to/GitLocal
     cd autotagging-service
     npm install
     cd ..
     ```

3. Run server

     ```
    ./mac_run.sh
     ```

4. Test service

   Open [http://localhost:8888](http://localhost:8888) in your browser.
