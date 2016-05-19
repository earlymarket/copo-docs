# Sign up
## Signing up for coposition
```shell
curl -X POST "https://api.coposition.com/v1/users"
  -H "Content-Type: application/json"
  -H "X-Secret-App-Key: SECRET_APP_KEY_HERE"
  -H "Cache-Control: no-cache"
  -d '{
    "user" : {
      "email" : USER_EMAIL,
      "password" : USER_PASSWORD,
      "username" : USERNAME
      }
    }'
```
```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.coposition.com/v1/users',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Secret-App-Key': 'SECRET_APP_KEY_HERE' },
  body: { user: { email: USER_EMAIL, password: USER_PASSWORD, username: USERNAME } },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```
> The above command returns JSON structured like this:

```json
{
  "id": 15,
  "email": "new@email.com",
  "created_at": "2016-05-17T10:21:11.635Z",
  "updated_at": "2016-05-17T10:21:11.635Z",
  "connection_code": null,
  "username": "",
  "slug": "e6e64fd7-ec73-4fd9-9a73-a41071158085",
  "authentication_token": "3NTUtBNX_3WGRogc6HzB"
}
```
### HTTP Request
`POST https://api.coposition.com/v1/users`

### Headers

`X-Secret-App-Key`
`Content-Type`
`Cache-Control`

### Body
Attribute | Value
-------------- | --------------
user | email, password, username
email | "example@email.com"
password | "password" (>8 characters)
username | "example"
