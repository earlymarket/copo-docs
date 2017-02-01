# Check-ins
A check-in is our basic unit of geolocation information. It has a latitude, longitude and the UUID of the device it belongs to. It can also contain an address and privacy information.

## Check-in privacy
Coposition allows you to pass a less specific location on to your friends and apps. We call this "fogging". A check-in's fogged location is either the centre of the nearest named urban area with a population of more than 1000 people (usually a city district, borough, town, village or suburb). If there isn't one within 200 miles, it is assigned a random location &plusmn;0.5 decimal degrees of latitude/longitude. This information is saved to the check-in so you can consistently report the same location.

You may also delay sharing a check-in to a less sensitive time by changing the delay property on the parent device.

## Create a new check-in
A latitude and longitude are required. You can also provide a created at date and time in the format "yyyy-mm-dd [hh:mm:ss]". If the API key belongs to the developer who originally created the device, the device config will also be returned.

```shell
curl -X POST "https://api.coposition.com/checkins"
     -H "X-Api-Key: YOUR_API_KEY_HERE"
     -H "Content-Type: application/json"
     -H "X-UUID: DEVICE-UUID-HERE"
     -H "Cache-Control: no-cache"
     -d '{
      "lat" : "51.588330",
      "lng" : "-0.513069",
      "created_at" : "2016-10-31 [10:30:12]"
     }'
```
```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.coposition.com/checkins',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-UUID': 'DEVICE-UUID-HERE'
     'x-api-key': 'YOUR_API_KEY_HERE' },
  body: { lat: '51.588330', lng: '-0.513069', created_at : '2017-02-01 [11:01:38]' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```
> The above command returns JSON structured like this.
> Config will only be returned if checkin is created with the api key of the developer who created the device.

```json
{
  "data": [
    {
      "lat": 51.58833,
      "lng": -0.513069,
      "device_id": 309,
      "fogged": false,
      "id": 287282,
      "uuid": "cb732efc-b34f-427a-b80c-c39d4ff4a8f7",
      "fogged_lat": 51.60333,
      "fogged_lng": -0.48546,
      "fogged_city": "Harefield",
      "country_code": "GB",
      "fogged_country_code": "GB",
      "created_at": "2017-02-01T11:01:38.000Z",
      "updated_at": "2017-02-01T11:04:02.661Z",
      "address": "Not yet geocoded",
      "city": null,
      "postal_code": null,
      "output_lat": 51.58833,
      "output_lng": -0.513069,
      "output_address": "Not yet geocoded",
      "output_city": null,
      "output_postal_code": null,
      "output_country_code": "GB",
      "edited": false
    }
  ],
  "config": {
    "id": 23,
    "developer_id": 2,
    "device_id": 309,
    "custom": null,
    "created_at": "2016-06-08T07:59:17.005Z",
    "updated_at": "2016-06-13T09:27:52.338Z"
  }
}
```
### HTTP Request
`POST https://api.coposition.com/checkins`

### Headers
`X-Api-key`
`X-UUID`
`Content-Type`

### Body
Attribute               | Value
----------------------- | --------------------------------------------------------
lat                     | -180/+180
lng                     | -180/+180
created_at *(optional)* | A valid [Ruby datetime](http://ruby-doc.org/stdlib-2.3.0/libdoc/date/rdoc/DateTime.html#method-c-parse) value e.g. "yyyy-mm-dd [hh:mm:ss]"

## Create a batch of new check-ins
Again, the latitude and longitude of each check-in is required and you can also supply a created at date and time.

```shell
curl -X POST "https://api.coposition.com/checkins/batch_create"
     -H "X-Api-Key: YOUR_API_KEY_HERE"
     -H "Content-Type: application/json"
     -H "X-UUID: DEVICE-UUID-HERE"
     -H "Cache-Control: no-cache"
     -d '[
       {
         "lat" : "51.588330",
         "lng" : "-0.513069",
         "created_at" : "2016-10-31 [10:30:12]"
       },
       {
         "lat" : "52.345334",
         "lng" : "-0.563423",
         "created_at" : "2016-10-31 [11:05:54]"
       }]'
```
```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.coposition.com/checkins/batch_create',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-UUID': 'DEVICE-UUID-HERE'
     'x-api-key': 'YOUR_API_KEY_HERE' },
  body: [
    { lat: '51.588330', lng: '-0.513069', created_at : '2017-02-01 [11:01:38]' },
    { lat: '52.345334', lng: '-0.563423', created_at: '2016-10-31 [11:05:54]' }
  ],
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```
> The above command returns JSON structured like this.

```json
{
  "message": "Checkins created"
}
```
### HTTP Request
`POST https://api.coposition.com/checkins/batch_create`

### Headers
`X-Api-key`
`X-UUID`
`Content-Type`

### Body
Attribute               | Value
----------------------- | --------------------------------------------------------
lat                     | -180/+180
lng                     | -180/+180
created_at *(optional)* | A valid [Ruby datetime](http://ruby-doc.org/stdlib-2.3.0/libdoc/date/rdoc/DateTime.html#method-c-parse) value e.g. "yyyy-mm-dd [hh:mm:ss]"


##  Get a list of user checkins
Get a list of a user's checkins, you can choose to geocode the checkins to get a full address if available, you can specific a device from which you want checkins from and how many checkins you want to receive.

```shell
curl -X GET "https://api.coposition.com/users/USER_ID/checkins/"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
```
```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'https://api.coposition.com/users/USER_ID/checkins/',
  headers:
   { 'x-api-key': 'YOUR_API_KEY_HERE' },
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
    "id": 18546,
    "lat": 51.513977,
    "lng": -0.234924,
    "created_at": "2016-05-12T17:10:55.776Z",
    "updated_at": "2016-05-13T09:23:33.125Z",
    "device_id": 7,
    "address": "Community Centre, India Way, White City, London W12 7AQ, UK",
    "city": "London",
    "postal_code": "W12 7AQ",
    "country_code": "GB"
  },
  {
    "id": 18544,
    "lat": 51.587736,
    "lng": -0.302124,
    "created_at": "2016-05-11T14:36:15.604Z",
    "updated_at": "2016-05-12T14:23:46.519Z",
    "device_id": 7,
    "address": "3 Westfield Ln, Harrow, Greater London HA3 9EA, UK",
    "city": "Harrow",
    "postal_code": "HA3 9EA",
    "country_code": "GB"
  },
]
```

### HTTP Request

For checkins for a user.

`GET https://api.coposition.com/users/USER_ID/checkins`

Just the last checkin

`GET https://api.coposition.com/users/USER_ID/checkins/last`

#### Optional filters

You can specify additional filtering in the query string

Option                                                  | Query string
------------------------------------------------------- | --------------------------------------------------------
Filter by device                                        | `?device_id=DEVICE_ID`
Show street address (only when filtering by device)     | `?type=address`
Page and results per page (default 30 max 1000)         | `?per_page=100&page=2`
Filter by date                                          | `?date=DD MM YYYY`
Find checkins near to coordinates                       | `?near=[LATITUDE LONGITUDE]`
Returns only one checkin for each area you have visited | `?unique_places=true`
Find check-ins created in the last n hours/days/weeks   | `?time_unit=UNIT&time_amount=AMOUNT e.g. ?time_unit=day&time_amount=10`

### Headers

`X-Api-Key`
`Content-Type`
`Cache-Control`
