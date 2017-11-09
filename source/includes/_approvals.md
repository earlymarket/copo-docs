# Approvals

## Asking for approval

Use this endpoint to create a pending approval between an App/User and the current User.

```shell
curl -X POST "https://api.coposition.com/users/USER_ID/approvals/"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
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
  url: 'https://api.coposition.com/users/USER_ID/approvals/',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Api-Key': 'YOUR_API_KEY_HERE'},
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
`POST https://api.coposition.com/users/USER_ID/approvals/`

### Headers

`X-Api-Key`
`Content-Type`
`Cache-Control`

### Body
Attribute | Value
-------------- | --------------
approval | approvable, approvable_type
approvable | integer (id of user/developer)
approvable_type | 'User' or 'Developer'
