# Devices
## Creating a new device

Creates a new device for the current user.

```shell
curl -X POST "https://api.coposition.com/users/USER_ID/devices"
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
  url: 'https://api.coposition.com/users/USER_ID/devices',
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
{
  "data": {
    "id": 1,
    "uuid": "95515f5a-c89c-476d-9360-f58a12fb3878",
    "user_id": 1,
    "name": "mobile",
    "fogged": false,
    "delayed": null,
    "alias": null,
    "published": false
  },
  "config": {
    "id": 1,
    "developer_id": 1,
    "device_id": 1,
    "custom": null,
    "created_at": "2016-08-30T10:48:15.911Z",
    "updated_at": "2016-08-30T10:48:15.911Z"
  }
}
```
### HTTP Request
`POST https://api.coposition.com/users/USER_ID/devices`

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
curl -X GET "https://api.coposition.com/users/USER_ID/devices"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "Content-Type: application/json"
  -H "Cache-Control: no-cache"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/users/USER_ID/devices',
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
    "id": 54,
    "user_id": 2,
    "name": "empty",
    "alias": null,
    "published": false
  },
  {
    "id": 7,
    "user_id": 2,
    "name": "Computer",
    "alias": null,
    "published": true
  }
]
```
### HTTP Request
`GET https://api.coposition.com/users/USER_ID/devices`

For a specific device (will return full device info if developer configures device)

`GET https://api.coposition.com/users/USER_ID/devices/DEVICE_ID`

> For a specific device:

```json
{
  "data": {
    "id": 1,
    "uuid": "95515f5a-c89c-476d-9360-f58a12fb3878",
    "user_id": 1,
    "name": "mobile",
    "fogged": false,
    "delayed": null,
    "alias": null,
    "published": false
  },
  "config": {
    "id": 1,
    "developer_id": 1,
    "device_id": 1,
    "custom": null,
    "created_at": "2016-08-30T10:48:15.911Z",
    "updated_at": "2016-08-30T10:48:15.911Z"
  }
}
```

### Headers

`X-Api-Key`
`Content-Type`
`Cache-Control`

## Update device settings
You can fog, delay or share a device. Checkins created while a device is fogged will have their address shown as the nearest city rather than the exact location. Delay works by not making checkins available to your data consumers until x minutes after they have been created. Publishing a device allows anyone with a coposition account access to your latest fogged or unfogged location for this device.

```shell
curl -X PUT "https://api.coposition.com/users/USER_ID/devices/DEVICE_ID"
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
  url: 'https://api.coposition.com/users/USER_ID/devices/DEVICE_ID',
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
{
  "data": {
    "id": 1,
    "uuid": "95515f5a-c89c-476d-9360-f58a12fb3878",
    "user_id": 1,
    "name": "mobile",
    "fogged": false,
    "delayed": 10,
    "alias": null,
    "published": true
  },
  "config": {
    "id": 1,
    "developer_id": 1,
    "device_id": 1,
    "custom": null,
    "created_at": "2016-08-30T10:48:15.911Z",
    "updated_at": "2016-08-30T10:48:15.911Z"
  }
}
```
### HTTP Request
`PUT https://api.coposition.com/users/USER_ID/devices/DEVICE_ID`

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
