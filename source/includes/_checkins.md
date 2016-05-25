# Check-ins
A check-in is our basic unit of geolocation information. It has a latitude, longitude and the UUID of the device it belongs to. It can also contain an address and privacy information.

## Check-in privacy
Coposition allows you to pass a less specific location on to your friends and apps. We call this "fogging". A check-in's fogged location is either the centre of the nearest named urban area with a population of more than 1000 people (usually a city district, borough, town, village or suburb). If there isn't one within 200 miles, it is assigned a random location &plusmn;0.5 decimal degrees of latitude/longitude. This information is saved to the check-in so you can consistently report the same location.

You may also delay sharing a check-in to a less sensitive time by changing the delay property on the parent device.

## Create a new check-in
A latitude and longitude are required. You can also provide a created at date and time in the format "yyyy-mm-dd [hh:mm:ss]".

```shell
curl -X PUT "https://api.coposition.com/v1/checkins"
     -H "X-Api-Key: YOUR_API_KEY_HERE"
     -H "Content-Type: application/json"
     -H "X-UUID": "DEVICE-UUID-HERE"
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
  url: 'https://api.coposition.com/v1/checkins',
  headers:
   { 'cache-control': 'no-cache',
     'content-type': 'application/json',
     'X-UUID': 'DEVICE-UUID-HERE'
     'x-api-key': 'YOUR_API_KEY_HERE' },
  body: { lat: '51.588330', lng: '-0.513069', created_at : '2016-10-31 [10:30:12]' },
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
    "id": 41649,
    "lat": 51.58833,
    "lng": -0.513069,
    "created_at": "2016-10-31T10:30:12.549Z",
    "updated_at": "2016-10-31T10:30:12.214Z",
    "uuid": "b64f4dbb-7981-44bd-88a8-d9626259f720",
    "device_id": 65,
    "address": "No address available",
    "city": null,
    "postal_code": null,
    "country_code": null,
    "fogged": true,
    "fogged_lat": 51.60333,
    "fogged_lng": -0.48546,
    "fogged_area": "Harefield"
  }
]
```
### HTTP Request
`POST https://api.coposition.com/v1/checkins`

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
curl -X GET "https://api.coposition.com}v1/users/USER_ID/devices/DEVICE_ID/checkins/"
  -H "X-Api-Key: YOUR_API_KEY_HERE"
```
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.coposition.com}v1/users/USER_ID/devices/DEVICE_ID/checkins/',
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

`GET https://api.coposition.com/v1/users/USER_ID/checkins`

Just the last checkin

`GET https://api.coposition.com/v1/users/USER_ID/checkins/last`

#### Optional filters

You can specify additional filtering in the query string

Option                                          | Query string
----------------------------------------------- | --------------------------------------------------------
Filter by device                                | `?device_id=DEVICE_ID`
Geocode/show street address                     | `?type=address`
Page and results per page (default 30 max 1000) | `?per_page=100&page=2`

### Headers

`X-Api-Key`
`Content-Type`
`Cache-Control`
