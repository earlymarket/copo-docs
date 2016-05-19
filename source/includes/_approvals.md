# Approvals

## Asking for approval

Use this endpoint to create a pending approval between an App/User and the current User.

```shell
curl -X POST "https://api.coposition.com/v1/users/USER_ID/approvals/"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "X-Secret-App-Key: SECRET_APP_KEY"
  -H "Content-Type: application/json"
  -H "Cache-Control: no-cache"
  -d '{
    "approval" : {
      "approvable": DEVELOPER_ID,
      "approvable_type": "Developer"
      }
    }'
```
```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.coposition.com/v1/users/USER_ID/approvals/',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Api-Key': 'YOUR_API_KEY_HERE'
     'X-Secret-App-Key': 'SECRET_APP_KEY_HERE' },
  body: { approval: { approvable: DEVELOPER_ID, approvable_type: 'Developer' } },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```
> The above command returns JSON structured like this:

```json
{
  "id": 103,
  "approvable_id": 2,
  "user_id": 2,
  "approval_date": "2016-05-17T09:34:24.118Z",
  "created_at": "2016-04-19T09:44:55.319Z",
  "updated_at": "2016-05-17T09:34:24.120Z",
  "status": "accepted",
  "approvable_type": "Developer"
}
```
### HTTP Request
`POST https://api.coposition.com/v1/users/USER_ID/approvals/`

### Headers

`X-Api-Key`
`X-Secret-App-Key`
`Content-Type`
`Cache-Control`

### Body
Attribute | Value
-------------- | --------------
approval | approvable, approvable_type
approvable | integer (id of user/developer)
approvable_type | 'User' or 'Developer'

## Getting a list of approvals including pending approvals

Gets a list of accepted/pending approvals belonging to a user. Returns the approval_id which is used in approved/rejecting an approval.

```shell
curl -X GET "https://api.coposition.com/v1/users/USER_ID/approvals/"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "X-User-Token: USER_AUTH_TOKEN"
  -H "X-User-Email: USER_EMAIL"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/v1/users/USER_ID/approvals/',
  headers:
   { 'X-Api-Key': 'YOUR_API_KEY_HERE'
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
    "id": 120,
    "approvable_id": 3,
    "user_id": 2,
    "approval_date": "2016-04-19T14:37:15.214Z",
    "created_at": "2016-04-19T14:36:37.646Z",
    "updated_at": "2016-04-19T14:37:15.215Z",
    "status": "accepted",
    "approvable_type": "User"
  },
  {
    "id": 38,
    "approvable_id": 1,
    "user_id": 2,
    "approval_date": null,
    "created_at": "2016-03-17T10:42:01.470Z",
    "updated_at": "2016-03-17T10:42:01.470Z",
    "status": "pending",
    "approvable_type": "User"
  },
]
```
### HTTP Request
`GET https://api.coposition.com/v1/users/USER_ID/approvals/`

### Headers

`X-Api-Key`
`X-User-Token`
`X-User-Email`
`Content-Type`
`Cache-Control`

## Approving/Rejecting/Revoking an approval

User needs to approve an approval in order to let a friend/app see their location data. A user can also choose to reject an approval or revoke an existing approval.

```shell
curl -X PUT "https://api.coposition.com/v1/users/USER_ID/approvals/APPROVAL_ID"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
  -H "Content-Type: application/json"
  -H "X-User-Token: USER_AUTH_TOKEN"
  -H "X-User-Email: USER_EMAIL"
  -H "Cache-Control: no-cache"
  -d '{
    "approval" : {
      "status": "accepted" OR "revoked"
      }
    }'
```
```javascript
var request = require("request");

var options = { method: 'PUT',
  url: 'https://api.coposition.com/v1/users/USER_ID/approvals/APPROVAL_ID',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Api-Key': 'YOUR_API_KEY_HERE',
     'X-User-Token': 'USER_AUTH_TOKEN',
     'X-User-Email': 'USER_EMAIL' },
  body: { approval: { status: 'accepted' OR 'revoked' } },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```
> The above command returns JSON structured like this:

```json
{
  "id": 38,
  "approvable_id": 1,
  "user_id": 2,
  "approval_date": "2016-05-17T10:14:58.023Z",
  "created_at": "2016-03-17T10:42:01.470Z",
  "updated_at": "2016-05-17T10:14:58.028Z",
  "status": "accepted",
  "approvable_type": "User"
}
```
### HTTP Request
`PUT https://api.coposition.com/v1/users/USER_ID/approvals/APPROVAL_ID`

### Headers

`X-Api-Key`
`X-User-Token`
`X-User-Email`
`Content-Type`
`Cache-Control`

### Body
Attribute | Value
-------------- | --------------
approval | status
status | 'accepted' or 'revoked'

