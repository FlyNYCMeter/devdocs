---
title: API Reference

language_tabs:
  - shell

includes:

search: true
---

# Introduction

```global
API Endpoint
https://mobile.flywheel.com
```

The Flywheel API is organized around REST. Our API is designed to have predictable, resource-oriented URLs and to use HTTP response codes to indicate API errors.

# Errors
```global
HTTP status codes summary

200 OK - Everything worked as expected.

401 Unauthorized - No valid API credentials provided.

403 Forbidden - You are not authorized to access the requested item.

404 Not Found - The requested item doesn't exist.

500, 502, 503, 504 Server errors - something went wrong on 
Flywheel's end.

```
Flywheel uses conventional HTTP response codes to indicate success or failure of an API request. In general, codes in the 2xx range indicate success, codes in the 4xx range indicate an error that resulted from the provided information (e.g. a required parameter was missing etc.), and codes in the 5xx range indicate an error with Flywheel's servers.

# Rides

## Create Ride

```shell
# Definition
POST https://mobile.flywheel.com/partner/{PARTNER_ID}/rides

# Example request
curl  \
 -XPOST "https://mobile.flywheel.com/partner/2001/rides" \
 -H "Content-type: application/json" \
 -d \
 '
 {
  "auth_token": "8UJbR4KbX1irrHrkeQgRKoT15PhFDLadqNY2FbYQZBTQTb8qtRUwlk0IVkDx",
  "pick_up_location": {
  "address_1": "IIT Bombay, Powai, Mumbai, Maharashtra",
  "address_2": "IIT Campus, Powai Road Mumbai, Powai, Mumbai, Maharashtra",
  "state": "Maharashtra",
  "country": "India",
  "postal_code": "400076",
  "city": "Mumbai",
  "latitude": 28.45011176221372,
  "longitude": 77.00715727447182
  },
  "telephone": "9433853357"
}
'
```

> The above command returns JSON structured like this:

```json
{
  "id": "3383634316955021500",
  "status": "hailing",
  "created_at": 1486021921,
  "failure_reason": null,
  "pick_up_location": {
    "address_1": "IIT Bombay, Powai, Mumbai, Maharashtra",
    "address_2": "IIT Campus, Powai Road Mumbai, Powai, Mumbai, Maharashtra",
    "city": "Mumbai",
    "state": "Maharashtra",
    "postal_code": "400076",
    "country": "India",
    "latitude": 28.45011176221372,
    "longitude": 77.00715727447182,
    "name": "",
    "long_name": null,
    "approach_street": null,
    "turn_street": null
  },
  "drop_off_location": {
    "address_1": "",
    "address_2": "",
    "city": "",
    "state": "",
    "postal_code": "",
    "country": "",
    "latitude": "",
    "longitude": "",
    "name": "",
    "long_name": null,
    "approach_street": null,
    "turn_street": null
  },
  "passenger_id": "e1fa6652-8d8f-4be8-82af-7dc49103e450",
  "hail": {
    "status": null,
    "created_at": null,
    "driver": {
      "name": null,
      "phone": null,
      "latitude": null,
      "longitude": null,
      "location_timestamp": null,
      "vehicle": {
        "fleet_name": null,
        "seat_count": null,
        "cab_number": null,
        "vehicle_type": null,
        "medallion_number": null,
        "cab_number_label": null
      }
    }
  }
}
```

### Attributes

Attribute | Type | Description 
--------- | ----------- | -----------
**auth_token** | **string required** | Authorization token provided to the partner by flywheel
**telephone** | **string required** | Passenger telephone number in full, that is along with the country code.
**pick_up_location.latitude** | **float required**| Latitude of the pick up location.
**pick_up_location.longitude** | **float required** | Latitude of the pick up location.
**pick_up_location.address_1** | **string optional** | Line 1 of the pick up address.
**pick_up_location.address_1** | **string optional** | Line 1 of the pick up address.
**pick_up_location.city** | **string optional** | Pick up city.
**pick_up_location.state** | **string optional** | Pick up state.
**pick_up_location.postal_code** | **string optional** | Pick up postal code.
**pick_up_location.country** | **string optional** | Pick up country.


## Get Ride

```shell
# Definition
GET https://mobile.flywheel.com/partner/{PARTNER_ID}/rides/{RIDE_ID}?auth_token={AUTH_TOKEN}

# Example request
curl -XGET \
  "https://mobile.flywheel.com/partner/2001/rides/4023232069859070442" \
   -H "Content-type: application/json" \
   -d auth_token=8UJbR4KbX1irrHrkeQgRKoT15PhFDLadqNY2FbYQZBTQTb8qtRUwlk0IVkDx \
   -G 
```

> The above command returns JSON structured like this:

```json
{
  "id": "4023232069859070442",
  "status": "hail_accepted",
  "created_at": 1486019275,
  "failure_reason": null,
  "hailed_at": null,
  "pick_up_location": {
    "address_1": "IIT Bombay, Powai, Mumbai, Maharashtra",
    "address_2": "IIT Campus, Powai Road Mumbai, Powai, Mumbai, Maharashtra",
    "city": "Mumbai",
    "state": "Maharashtra",
    "postal_code": "400076",
    "country": "India",
    "latitude": 28.45011176221372,
    "longitude": 77.00715727447182,
    "name": "",
    "long_name": "",
    "approach_street": null,
    "turn_street": null
  },
  "drop_off_location": {
    "address_1": "",
    "address_2": "",
    "city": "",
    "state": "",
    "postal_code": "",
    "country": "",
    "latitude": null,
    "longitude": null,
    "name": "",
    "long_name": "",
    "approach_street": null,
    "turn_street": null
  },
  "passenger_id": "e1fa6652-8d8f-4be8-82af-7dc49103e450",
  "hail": {
    "status": "driver_en_route",
    "created_at": 1486019276,
    "driver_eta": 41,
    "driver": {
      "name": "driver_3743",
      "phone": "5005550006",
      "latitude": 28.449935401911336,
      "longitude": 77.00715727447182,
      "location_timestamp": 1485960249,
      "vehicle": {
        "fleet_name": "Demo Fleet 1",
        "seat_count": null,
        "cab_number": "23744",
        "vehicle_type": null,
        "medallion_number": "23744",
        "cab_number_label": null
      }
    }
  }
}
```

### URL Parameters

Attribute  | Description 
--------- | ----------- | -----------
**AUTH_TOKEN** | Authorization token provided to the partner by flywheel
**RIDE_ID**  | Id of the ride provided on successful ride creation
**PARTNER_ID**  | Partner id provided by Flywheel

## Get Ride By Passenger

```shell
# Definition
GET https://mobile.flywheel.com/partner/{PARTNER_ID}/rides/{RIDE_ID}?auth_token={AUTH_TOKEN}&telephone={PASSENGER_TELEPHONE}

# Example request
curl -XGET \
  "https://mobile.flywheel.com/partner/2001/rides" \
   -H "Content-type: application/json" \
   -d auth_token=8UJbR4KbX1irrHrkeQgRKoT15PhFDLadqNY2FbYQZBTQTb8qtRUwlk0IVkDx \
   -d telephone=9433853357 \
   -G 

```

> The above command returns JSON structured like this:

```json
{
  "id": "441849373081953955",
  "status": "hailing",
  "created_at": 1486023985,
  "failure_reason": null,
  "pick_up_location": {
    "address_1": "IIT Bombay, Powai, Mumbai, Maharashtra",
    "address_2": "IIT Campus, Powai Road Mumbai, Powai, Mumbai, Maharashtra",
    "city": "Mumbai",
    "state": "Maharashtra",
    "postal_code": "400076",
    "country": "India",
    "latitude": 28.45011176221372,
    "longitude": 77.00715727447182,
    "name": "",
    "long_name": null,
    "approach_street": null,
    "turn_street": null
  },
  "drop_off_location": {
    "address_1": "",
    "address_2": "",
    "city": "",
    "state": "",
    "postal_code": "",
    "country": "",
    "latitude": null,
    "longitude": null,
    "name": "",
    "long_name": null,
    "approach_street": null,
    "turn_street": null
  },
  "passenger_id": "e1fa6652-8d8f-4be8-82af-7dc49103e450",
  "hail": {
    "status": null,
    "created_at": null,
    "driver": {
      "name": null,
      "phone": null,
      "latitude": null,
      "longitude": null,
      "location_timestamp": null,
      "vehicle": {
        "fleet_name": null,
        "seat_count": null,
        "cab_number": null,
        "vehicle_type": null,
        "medallion_number": null,
        "cab_number_label": null
      }
    }
  }
}
```

### URL Parameters

Attribute  | Description 
--------- | -----------
**AUTH_TOKEN**  | Authorization token provided to the partner by flywheel
**PASSENGER_TELEPHONE**  | Passenger telephone number in full, along with the country code.
**PARTNER_ID**  | Partner id provided by Flywheel

## Cancel Ride

```shell
# Definition
PUT https://mobile.flywheel.com/partner/{PARTNER_ID}/rides/{RIDE_ID}/cancel

# Example request
curl -XPUT \
 "https://mobile.flywheel.com/partner/2001/rides/1441409342165030696/cancel" \
 -H "Content-type: application/json" \
 -d \
 '
 {
  "auth_token": "8UJbR4KbX1irrHrkeQgRKoT15PhFDLadqNY2FbYQZBTQTb8qtRUwlk0IVkDx",
  "reason": "no_longer_need_cab"
}
'
```

> The above command returns JSON structured like this:

```json
{
  "id": "1441409342165030696",
  "status": "canceled",
  "created_at": 1486024623,
  "failure_reason": null,
  "pick_up_location": {
    "address_1": "IIT Bombay, Powai, Mumbai, Maharashtra",
    "address_2": "IIT Campus, Powai Road Mumbai, Powai, Mumbai, Maharashtra",
    "city": "Mumbai",
    "state": "Maharashtra",
    "postal_code": "400076",
    "country": "India",
    "latitude": 28.728369128194476,
    "longitude": 77.50733955957557,
    "name": "",
    "long_name": "",
    "approach_street": null,
    "turn_street": null
  },
  "drop_off_location": {
    "address_1": "",
    "address_2": "",
    "city": "",
    "state": "",
    "postal_code": "",
    "country": "",
    "latitude": null,
    "longitude": null,
    "name": "",
    "long_name": "",
    "approach_street": null,
    "turn_street": null
  },
  "passenger_id": "06b64296-06cc-4766-b4c6-91e74be9c93f",
  "hail": {
    "status": "passenger_canceled",
    "created_at": 1486024624,
    "driver": {
      "name": "driver_3243",
      "phone": "5005550006",
      "latitude": 28.7282104039223,
      "longitude": 77.5073395595756,
      "location_timestamp": 1486024351,
      "vehicle": {
        "fleet_name": "Demo Fleet 1",
        "seat_count": null,
        "cab_number": "23244",
        "vehicle_type": null,
        "medallion_number": "23244",
        "cab_number_label": null
      }
    }
  }
}
```

### URL Parameters

Attribute | Description 
--------- | -----------
**PARTNER_ID** | Partner id provided by Flywheel
**RIDE_ID** | Id of the ride provided on successful ride creation

### Attributes

Attribute | Type | Description 
--------- | ----------- | -----------
**auth_token** | **string required** | Authorization token provided to the partner by flywheel
**reason** | **string required** | Text representing the reason for cancellation


## Get Nearby drivers

```shell
# Definition
GET https://mobile.flywheel.com/partner/{PARTNER_ID}/driverlocations>auth_token={AUTH_TOKEN}&latitude={LATITUDE}&longitude={LONGITUDE}

# Example request
curl -XGET \
  "https://mobile.flywheel.com/partner/2001/driverlocations" \
   -H "Content-type: application/json" \
   -d auth_token=8UJbR4KbX1irrHrkeQgRKoT15PhFDLadqNY2FbYQZBTQTb8qtRUwlk0IVkDx \
   -d latitude=28.728369128194476 \
   -d longitude=77.50733955957557 \
   -G 
```

> The above command returns JSON structured like this:

```json
{
  "drivers": [{
    "latitude": 28.666466662058333,
    "longitude": 77.44101103915963,
    "token": 1118543664
  }, {
    "latitude": 28.67352107415362,
    "longitude": 77.43318209904497,
    "token": 686571212
  }],
  "eta": 2030
}
```

### URL Parameters

Attribute | Description 
--------- | -----------
**AUTH_TOKEN**  | Authorization token provided to the partner by flywheel
**PARTNER_ID**  | Partner id provided by Flywheel
**LATITUDE** | Latitude of the pick up location
**LONGITUDE** | Longitude of the pick up location


