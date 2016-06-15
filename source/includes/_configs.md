# Configs
Configs allow developers to set and control any additional device settings they would like. For example, a developer producing a tracking device may want to be able to control the how often the tracking device checks in. Configs are created when a developer requests a UUID. The device with this UUID will have a config that can be updated by the developer.

## Getting a list of configs
Use this endpoint to see a list of device configs under your control.

```shell
curl -X GET "https://api.coposition.com/v1/configs/"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/v1/configs/',
  headers:
   { 'x-api-key': 'YOUR_API_KEY_HERE' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```
> The above command returns JSON structured like this:

```json
[
  {
    "id": 3,
    "developer_id": 2,
    "device_id": 100,
    "custom": null,
    "created_at": "2016-06-09T11:22:22.109Z",
    "updated_at": "2016-06-09T11:22:22.109Z"
  }
]
```

### HTTP Request

`GET https://api.coposition.com/v1/configs`

### Headers

`X-Api-Key`

## Getting a specific config
Use this endpoint to see a specific config

```shell
curl -X GET "https://api.coposition.com/v1/configs/CONFIG_ID"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/v1/configs/CONFIG_ID',
  headers:
   { 'x-api-key': 'YOUR_API_KEY_HERE' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```
> The above command returns JSON structured like this:

```json
{
  "id": 3,
  "developer_id": 2,
  "device_id": 100,
  "custom": null,
  "created_at": "2016-06-09T11:22:22.109Z",
  "updated_at": "2016-06-09T11:22:22.109Z"
}
```

### HTTP Request

`GET https://api.coposition.com/v1/configs/CONFIG_ID`

### Headers

`X-Api-Key`

## Updating a specific config
Use this endpoint to update a specific config. Any and as many key/value combinations you want can go within custom, type/mode/frequency are just examples.

```shell
curl -X PUT "https://api.coposition.com/v1/configs/CONFIG_ID"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "Content-Type: application/json"
  -d '{
    "config": {
      "custom": {
        "type": "herds",
        "mode": "accurate",
        "frequency": "1000"
        }
      }
    }'
```
```javascript
var request = require("request");

var options = { method: 'PUT',
  url: 'https://api.coposition.com/v1/configs/CONFIG_ID',
  headers:
    { 'x-api-key': 'YOUR_API_KEY_HERE'
      'content-type': 'application/json' },
    body: { config: { custom: { "type": "herds", "mode": "accurate", "frequency": "1000" } } },
    json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```
> The above command returns JSON structured like this:

```json
{
  "id": 3,
  "developer_id": 2,
  "device_id": 195,
  "custom": {
    "type": "herds",
    "mode": "accurate",
    "frequency": "1000"
  },
  "created_at": "2016-06-09T11:22:22.451Z",
  "updated_at": "2016-06-15T14:22:13.214Z"
}
```

### HTTP Request

`PUT https://api.coposition.com/v1/configs/CONFIG_ID`

### Headers

`X-Api-Key`
'Content-Type'

### Body
Attribute | Value
-------------- | --------------
config | custom
custom | { 'any key': 'any value' }
