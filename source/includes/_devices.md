# Devices
## Creating a new device

Creates a new device for the current user.

```shell
curl -X POST "https://api.coposition.com/v1/users/USER_ID/devices"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "Content-Type: application/json"
  -H "X-User-Token: USER_AUTH_TOKEN"
  -H "X-User-Email: USER_EMAIL"
  -H "Cache-Control: no-cache"
  -d '{
    "device" : {
      "name" : DEVICE_NAME,
      }
    }'
```
```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.coposition.com/v1/users/USER_ID/devices',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Api-Key': 'YOUR_API_KEY_HERE',
     'X-User-Token': 'USER_AUTH_TOKEN',
     'X-User-Email': 'USER_EMAIL' },
  body: { device: { name: DEVICE_NAME } },
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
    "id": 62,
    "uuid": "fbd002bd-20d6-412e-b756-e5ab058713ca",
    "user_id": 2,
    "name": "laptop",
    "fogged": false,
    "delayed": null,
    "alias": null,
    "published": false
  }
]
```
### HTTP Request
`POST https://api.coposition.com/v1/users/USER_ID/devices`

### Headers

`X-Api-Key`
`X-User-Token`
`X-User-Email`
`Content-Type`
`Cache-Control`

### Body
Attribute | Value
-------------- | --------------
device | name
name | "device name"

## Get a list of user's devices

Returns a list of devices belonging to the specified user. The user must have approved your App.

```shell
curl -X GET "https://api.coposition.com/v1/users/USER_ID/devices"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "Content-Type: application/json"
  -H "Cache-Control: no-cache"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/v1/users/USER_ID/devices',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Api-Key': 'YOUR_API_KEY_HERE' },
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
    "id": 62,
    "uuid": "fbd002bd-20d6-412e-b756-e5ab058713ca",
    "user_id": 2,
    "name": "laptop",
    "fogged": false,
    "delayed": null,
    "alias": null,
    "published": false
  },
  {
    "id": 62,
    "uuid": "fbd002bd-20d6-412e-b756-e5ab058713ca",
    "user_id": 2,
    "name": "laptop",
    "fogged": false,
    "delayed": null,
    "alias": null,
    "published": false
  }
]
```
### HTTP Request
`GET https://api.coposition.com/v1/users/USER_ID/devices`

For a specific device

`GET https://api.coposition.com/v1/users/USER_ID/devices/DEVICE_ID`

### Headers

`X-Api-Key`
`Content-Type`
`Cache-Control`

## Update device settings
You can fog, delay or share a device. Checkins created while a device is fogged will have their address shown as the nearest city rather than the exact location. Delay works by not making checkins available to your data consumers until x minutes after they have been created. Publishing a device allows anyone with a coposition account access to your latest fogged or unfogged location for this device.

```shell
curl -X PUT "https://api.coposition.com/v1/users/USER_ID/devices/DEVICE_ID"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "X-User-Token: USER_AUTH_TOKEN"
  -H "X-User-Email: USER_EMAIL"
  -H "Content-Type: application/json"
  -H "Cache-Control: no-cache"
  -d '{
    "fogged" : false,
    "delayed" : 10,
    "published" : true
    }'
```
```javascript
var request = require("request");

var options = { method: 'PUT',
  url: 'https://api.coposition.com/v1/users/USER_ID/devices/DEVICE_ID',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Api-Key': 'YOUR_API_KEY_HERE'
     'X-User-Token': 'USER_AUTH_TOKEN',
     'X-User-Email': 'USER_EMAIL' },
  body: { fogged: false,  delayed: 10, published: true},
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
    "id": 62,
    "uuid": "fbd002bd-20d6-412e-b756-e5ab058713ca",
    "user_id": 2,
    "name": "laptop",
    "fogged": false,
    "delayed": 10,
    "alias": null,
    "published": true
  }
]
```
### HTTP Request
`PUT https://api.coposition.com/v1/users/USER_ID/devices/DEVICE_ID`

### Headers

`X-Api-Key`
`X-User-Token`
`X-User-Email`
`Content-Type`
`Cache-Control`

### Body
Attribute | Value
-------------- | --------------
fogged | boolean
delayed | integer (number of minutes)
published | boolean
