# Permissions
## Listing Permissions

Lists all of a device permission settings, returns id of permission which can be used for updating a permission.

```shell
curl -X GET "https://api.coposition.com/users/USER_ID/devices/DEVICE_ID/permissions"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "X-User-Token: USER_AUTH_TOKEN"
  -H "X-User-Email: USER_EMAIL"
  -H "Content-Type: application/json"
  -H "Cache-Control: no-cache"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/users/USER_ID/devices/DEVICE_ID/permissions',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Api-Key': 'YOUR_API_KEY_HERE'
     'X-User-Token': 'USER_AUTH_TOKEN',
     'X-User-Email': 'USER_EMAIL' },
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
    "id": 294,
    "permissible_id": 3,
    "device_id": 7,
    "privilege": "complete",
    "permissible_type": "User",
    "bypass_fogging": false,
    "bypass_delay": false
  },
  {
    "id": 395,
    "permissible_id": 1,
    "device_id": 7,
    "privilege": "complete",
    "permissible_type": "User",
    "bypass_fogging": false,
    "bypass_delay": false
  }
]
```
### HTTP Request
`GET https://api.coposition.com/users/USER_ID/devices/DEVICE_ID/permissions`

### Headers

`X-Api-Key`
`X-User-Token`
`X-User-Email`
`Content-Type`
`Cache-Control`

## Edit Permissions

Update device permissions for a Developer/App or User. Permission settings include privilege level, bypass fogging and bypass delay. Privilege level controls the access a consumer has, disallowed, last_only (can only view last checkin) or complete.

```shell
curl -X PUT "https://api.coposition.com/users/USER_ID/devices/DEVICE_ID/permissions/PERMISSION_ID"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "X-User-Token: USER_AUTH_TOKEN"
  -H "X-User-Email: USER_EMAIL"
  -H "Content-Type: application/json"
  -H "Cache-Control: no-cache"
  -d '{
    "privilege" : "complete",
    "bypass_fogging" : "true",
    "bypass_delay" : "true"
    }'
```
```javascript
var request = require("request");

var options = { method: 'PUT',
  url: 'https://api.coposition.com/users/USER_ID/devices/DEVICE_ID/permissions/PERMISSION_ID',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Api-Key': 'YOUR_API_KEY_HERE'
     'X-User-Token': 'USER_AUTH_TOKEN',
     'X-User-Email': 'USER_EMAIL' },
  body: { privilege: "complete", bypass_fogging: true, bypass_delay: true },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```
> The above command returns JSON structured like this:

```json
{
  "id": 293,
  "permissible_id": 3,
  "device_id": 10,
  "privilege": "complete",
  "permissible_type": "User",
  "bypass_fogging": true,
  "bypass_delay": true
}
```
### HTTP Request
`PUT https://api.coposition.com/users/USER_ID/devices/DEVICE_ID/permissions/PERMISSION_ID`

To update all permissions for a specific device, use the endpoint:

`PUT https://api.coposition.com/users/USER_ID/devices/DEVICE_ID/permissions`

### Headers

`X-Api-Key`
`X-User-Token`
`X-User-Email`
`Content-Type`
`Cache-Control`

### Body
Attribute | Value
-------------- | --------------
privilege | 'complete', 'last_only', 'disallowed'
bypass_fogging | boolean
bypass_delay | boolean
