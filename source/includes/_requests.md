# Requests

## Getting API request information

Allows you to view previous API requests that you have made regarding a specific user.

```shell
curl -X GET "https://api.coposition.com/users/USER_ID/requests?access_token=ACCESS_TOKEN"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/users/USER_ID/requests?access_token=ACCESS_TOKEN',
  headers:
   { 'X-Api-Key': 'YOUR_API_KEY_HERE' },
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
    "developer_id": 1,
    "created_at": "2017-11-24T22:53:31.403Z",
    "paid": false,
    "user_id": 1,
    "action": "index",
    "controller": "api/v1/checkins"
  },
  {
    "id": 1,
    "developer_id": 1,
    "created_at": "2017-11-23T16:26:34.542Z",
    "paid": false,
    "user_id": 1,
    "action": "last",
    "controller": "api/v1/checkins"
  },
]
```
### HTTP Request
`GET https://api.coposition.com/users/USER_ID/requests?access_token=ACCESS_TOKEN`

### Headers

`X-Api-Key`

## Getting last API request made

Allows you to view the last API request you made for a specific user.

```shell
curl -X GET "https://api.coposition.com/users/USER_ID/requests/last?access_token=ACCESS_TOKEN"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/users/USER_ID/requests/last?access_token=ACCESS_TOKEN',
  headers:
   { 'X-Api-Key': 'YOUR_API_KEY_HERE' },
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
    "developer_id": 1,
    "created_at": "2017-11-24T22:53:31.403Z",
    "paid": false,
    "user_id": 1,
    "action": "index",
    "controller": "api/v1/checkins"
  }
]
```
### HTTP Request
`GET https://api.coposition.com/users/USER_ID/requests/last?access_token=ACCESS_TOKEN`

### Headers

`X-Api-Key`
