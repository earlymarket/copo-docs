# Devices
## Get a list of user's devices

Returns a list of devices belonging to the specified user. The user must have approved your App.

```shell
curl -X GET "https://api.coposition.com/users/USER_ID/devices?access_token=ACCESS_TOKEN"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "Content-Type: application/json"
  -H "Cache-Control: no-cache"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/users/USER_ID/devices?access_token=ACCESS_TOKEN',
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
`GET https://api.coposition.com/users/USER_ID/devices?access_token=ACCESS_TOKEN`

For a specific device (will return full device info if developer configures device)

`GET https://api.coposition.com/users/USER_ID/devices/DEVICE_ID?access_token=ACCESS_TOKEN`

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
    "published": false,
    "cloaked": false
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
