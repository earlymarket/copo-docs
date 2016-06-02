# Log in/out
## Logging into an account
```shell
curl -X POST "https://coposition.com/users/sign_in"
  -H "Content-Type: application/json"
  -H "X-Secret-App-Key: SECRET_APP_KEY_HERE"
  -H "Cache-Control: no-cache"
  -d '{
    "user" : {
      "email" : USER_EMAIL,
      "password" : USER_PASSWORD
      }
    }'
```
```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://coposition.com/users/sign_in',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Secret-App-Key': 'SECRET_APP_KEY_HERE' },
  body: { user: { email: USER_EMAIL, password: USER_PASSWORD } },
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
    "id": "USER_ID",
    "email": "USER_EMAIL",
    "username": "USERNAME",
    "authentication_token": "AUTH_TOKEN"
  }
]
```
### HTTP Request
`POST https://coposition.com/users/sign_in`

### Headers

### Body
Attribute | Value
-------------- | --------------
user | email, password
email | "example@email.com"
password | "password"

`X-Secret-App-Key`
`Content-Type`
`Cache-Control`

## Logging out an account
```shell
curl -X DELETE "https://coposition.com/users/sign_out"
  -H "Content-Type: application/json"
  -H "X-Secret-App-Key: SECRET_APP_KEY_HERE"
  -H "Cache-Control: no-cache"
  -H "X-User-Token": USER_TOKEN
```
```javascript
var request = require("request");

var options = { method: 'DELETE',
  url: 'https://coposition.com/users/sign_out',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-Secret-App-Key': 'SECRET_APP_KEY_HERE',
     'X-User-Token': 'USER_TOKEN' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```
> The above command returns JSON structured like this:

```json
{
  "message": "Signed out"
}
```
### HTTP Request
`DELETE https://coposition.com/users/sign_out`

### Headers

`X-Secret-App-Key`
`X-User-Token`
`Content-Type`
`Cache-Control`

