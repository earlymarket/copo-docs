---
title: Coposition API Reference

language_tabs:
  - shell: cURL
  - javascript: node.js

toc_footers:
  - <a href='https://www.coposition.com/developers/sign_up'>Sign Up for a Developer Key</a>
  - ~or~
  - <a href="https://coposition.com/developers/console">Log In to your Developer Console</a>

includes:
  - oauth
  - checkins
  - signups
  - logins
  - devices
  - approvals
  - permissions
  - users
  - developers
  - configs
  - errors

search: true

---

# Introduction

Welcome to Coposition! You can use our API to securely store and retrieve geolocation info associated with devices and users. You can also use the api
to view and manage permissions.

You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```javascript
// For brevity, the node code samples use
// the Request module (https://www.npmjs.com/package/request)
// But feel free to use whatever method you prefer
// to make http requests

var request = require("request");

var options = {
  method: 'HTTP_VERB_HERE',
  url: 'API_ENDPOINT_HERE',
  headers:
   { 'cache-control': 'no-cache',
     'x-api-key': 'YOUR_API_KEY_HERE' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```shell
# With cURL, you can just pass the correct header with each request
curl "API_ENDPOINT_HERE"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
```

> Make sure to replace `YOUR_API_KEY_HERE` with your API key.

Coposition uses custom HTTP headers to control access to different parts of the API. All API requests are expected to have an API key header:

`X-Api-Key: YOUR_API_KEY_HERE`

You can get a new Coposition API key from your [developer console](https://coposition.com/developers/console).

<aside class="notice">
You must replace <code>YOUR_API_KEY_HERE</code> with your personal API key.
</aside>

Other custom headers used by the API are shown below. We'll revisit them when they're required.

Header           | Value
---------------- | ------------------------------------------------------------------------
X-Secret-App-Key | Exclusively used by the Coposition app
X-User-Token     | Authentication token returned on sign in/sign up, destroyed on sign out.
X-UUID           | Unique identifier associated with a specific device in our database.
X-User-Email     | User's email address
X-User-Password  | User's password

# UUID
All hardware is identified by a **universally unique identifier** (UUID). This is because not all devices share the same identifying marks e.g. serial numbers, IMEI so we create an
artificial one to standardize on.
## Create a new UUID
UUID's can be pre-generated to allow you to uniquely identify a device after manufacture. When you request a UUID, a device config will also be created allowing you the developer to control any additional device settings you may want to configure.

> At the moment: 1 request = 1 UUID.

```shell
curl -X GET "https://api.coposition.com/uuid"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com/uuid',
  headers:
   { 'cache-control': 'no-cache',
     'x-api-key': 'YOUR_API_KEY_HERE' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

> The above command returns JSON structured like this:

```json
{
  "uuid": "7d274e7c-76ab-45e7-8d96-ef063ad725f8"
}
```

### HTTP Request
`GET https://api.coposition.com/uuid`

<aside class="success">
Remember your API key!
</aside>

