# Activation Service

## API

```
GET /api/activations/:activationID

```

Activation result of a Sensei processing task can be retrieved by sending a GET request to `/api/activations/:activationID`, where:

* `activationID` query param which is returned by a Sensei function API

On successful completion, the server returns the output of the corresponding Sensei action.
