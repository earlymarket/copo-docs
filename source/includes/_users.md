# Users

## Getting app users

Allows you to view a list of users who have approved your app/developer and obtain user ID's which can be used in creating/updating an approval or updating permissions for a device.

```shell
curl -X GET "https://api.coposition.com/v1/users"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "Content-Type: application/json"
  -H "Cache-Control: no-cache"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/v1/users',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Api-Key': 'YOUR_API_KEY_HERE'},
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
    "id": 2,
    "email": "tom@email.com",
    "username": "tom",
    "slug": "tom"
  },
  {
    "id": 3,
    "email": "sam@email.com",
    "username": "sam",
    "slug": "sam"
  }
]
```
### HTTP Request
`GET https://api.coposition.com/v1/users`

### Headers

`X-Api-Key`
`Content-Type`
`Cache-Control`

## Showing user info

Allows you to view user info such as username and email.

```shell
curl -X GET "https://api.coposition.com/v1/users/USER_ID"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "Content-Type: application/json"
  -H "Cache-Control: no-cache"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/v1/users/USER_ID',
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
{
  "id": 1,
  "email": "delia.kirlin@ortiz.biz",
  "username": "coporulez",
  "slug": "coporulez"
}
```
### HTTP Request
`GET https://api.coposition.com/v1/users/USER_ID`

### Headers

`X-Api-Key`
`Content-Type`
`Cache-Control`
