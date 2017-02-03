---
title: API Reference

language_tabs:
  - shell

includes:

search: true
---

# Introduction
## Partner APIs for Ride Management on Flywheel Server 

```global
API Production Endpoint
https://mobile.flywheel.com

API Staging Endpoint
https://mobile-staging.flywheel.com
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

# APIs

## Create Ride

API to create a ride on Flywheel server for a partner passenger.

```shell
# Definition
POST {ENVIRONMENT_ENDPOINT}/partner/{PARTNER_ID}/rides

# Example request
curl  \
 -XPOST "https://mobile.flywheel.com/partner/2001/rides" \
 -H "Content-type: application/json" \
 -d \
 '
 {
  "auth_token": "<PARTNER_TOKEN>",
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
  "telephone": "919433853357"
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

### API
POST /partner/:partner_id/rides

### Attributes

Attribute | Type | Description 
--------- | ----------- | -----------
**auth_token** | **string required** | Authorization token provided to the partner by flywheel
**telephone** | **string required** | Passenger telephone number in full, that is along with the country code.
**pick_up_location.latitude** | **float required**| Latitude of the pick up location.
**pick_up_location.longitude** | **float required** | Latitude of the pick up location.
**pick_up_location.address_1** | **string optional** | Line 1 of the pick up address.
**pick_up_location.address_2** | **string optional** | Line 2 of the pick up address.
**pick_up_location.city** | **string optional** | Pick up city.
**pick_up_location.state** | **string optional** | Pick up state.
**pick_up_location.postal_code** | **string optional** | Pick up postal code.
**pick_up_location.country** | **string optional** | Pick up country.

### Success Response
* Response Type: application/json
* Content: [Ride Object](#ride-object)

### Error Responses
* Unauthorized access in case of missing/invalid token:
    * Status Code: 401
    * Content: {error: error_message} (Error = “Malformed Token”/“Missing Token”)
* Unauthorized access in case of token-id mismatch:
    * Status Code: 403
    * Content: “Unauthorized access”
* Bad Request, Missing required parameters:
    * Status Code: 400
    * Content: “Missing telephone/Pick_up_location/Latitude/Longitude”
* Error in ride creation:
    * Status Code: 400
    * Content:
        * **error_message** (string): Short message describing the error.
        * **error** (string): Short id describing the error. This could have the following values-
            * missing_service_availabilities: Flywheel does not provide hailing services in the specified pick up location 
            * existing_open_ride: There already is an open ride for the provided passenger
            * book_time_invalid: In case of advance booked rides, the provided pick up time is either too early or too late
        * **user_presentable_message** (string): Displayable error message.
        * **user_presentable_title** (string): Displayable error title.

> Sample error response in case of error in ride creation:

```json
{
  "error": "missing_service_availabilities",
  "error_message": "Service availability ids missing in request for known pick up location",
  "user_presentable_message": "Issues with pick up Location",
  "user_presentable_title": "Error"
}
```


## Get Ride
Get ride details for a previously created ride given Flywheel Ride Id.

```shell
# Definition
GET {ENVIRONMENT_ENDPOINT}/partner/{PARTNER_ID}/rides/{RIDE_ID}?auth_token={PARTNER_TOKEN}

# Example request
curl -XGET \
  "https://mobile.flywheel.com/partner/2001/rides/4023232069859070442" \
   -H "Content-type: application/json" \
   -d auth_token=<PARTNER_TOKEN> \
   -G 
```

> The above command returns JSON structured like this:

```json
{
  "id": "4023232069859070442",
  "status": "hail_accepted",
  "created_at": 1486019275,
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

### API
GET /partner/:partner_id/rides/:ride_id

### Parameters

Attribute  | Type | Description  
--------- | ----------- | ---------------
**auth_token** | Query | Authorization token provided to the partner by flywheel
**ride_id**  | URL | Id of the ride provided on successful ride creation
**partner_id**  | URL | Partner id provided by Flywheel

### Success Response
* Response Type: application/json
* Content: [Ride Object](#ride-object)

### Error Responses
* Unauthorized access in case of missing/invalid token:
    * Status Code: 401
    * Content: {error: error_message} (Error = “Malformed Token”/“Missing Token”)
* Unauthorized access in case of token-id mismatch:
    * Status Code: 403
    * Content: “Unauthorized access”
* Ride not found for the partner:
    * Status Code: 404

## Get Ride By Passenger
Get details of the latest *open* ride for a partner passenger.

```shell
# Definition
GET {ENVIRONMENT_ENDPOINT}/partner/{PARTNER_ID}/rides/{RIDE_ID}?auth_token={PARTNER_TOKEN}&telephone={PASSENGER_TELEPHONE}

# Example request
curl -XGET \
  "https://mobile.flywheel.com/partner/2001/rides" \
   -H "Content-type: application/json" \
   -d auth_token=<PARTNER_TOKEN> \
   -d telephone=919433853357 \
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

### API
GET /partner/:partner_id/rides

### Parameters

Attribute  | Type | Description 
--------- |-------|-----------
**auth_token**  | Query | Authorization token provided to the partner by flywheel
**telephone**  | Query | Passenger telephone number in full, along with the country code.
**partner_id**  | URL | Partner id provided by Flywheel

### Success Response
* Response Type: application/json
* Content: Empty, in case of no open rides for the passenger. [Ride Object](#ride-object) when an open ride is found.

### Error Responses
* Unauthorized access in case of missing/invalid token:
    * Status Code: 401
    * Content: {error: error_message} (Error = “Malformed Token”/“Missing Token”)
* Unauthorized access in case of token-id mismatch:
    * Status Code: 403
    * Content: “Unauthorized access”

## Cancel Ride
Cancel an existing partner Flywheel ride.

```shell
# Definition
PUT {ENVIRONMENT_ENDPOINT}/partner/{PARTNER_ID}/rides/{RIDE_ID}/cancel

# Example request
curl -XPUT \
 "https://mobile.flywheel.com/partner/2001/rides/1441409342165030696/cancel" \
 -H "Content-type: application/json" \
 -d \
 '
 {
  "auth_token": "<PARTNER_TOKEN>",
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

### API
PUT /partner/:partner/rides/:ride_id/cancel

### URL Parameters

Attribute | Description 
--------- | -----------
**partner_id** | Partner id provided by Flywheel
**ride_id** | Id of the ride provided on successful ride creation

### Attributes

Attribute | Type | Description 
--------- | ----------- | -----------
**auth_token** | **string required** | Authorization token provided to the partner by flywheel
**reason** | **string optional** | Text representing the reason for cancellation

### Success Response
* Response Type: application/json
* Content: [Ride Object](#ride-object)

### Error Responses
* Unauthorized access in case of missing/invalid token:
    * Status Code: 401
    * Content: {error: error_message} (Error = “Malformed Token”/“Missing Token”)
* Unauthorized access in case of token-id mismatch:
    * Status Code: 403
    * Content: “Unauthorized access”
* Ride not found for the partner:
    * Status Code: 404
* Ride already in terminal state:
      * Status Code: 400
      * Content:
        * **error_message** (string): Short message describing the error.
        * **error** (string): Short id describing the error.

> Sample error response in case of error in ride cancellation:

```json
{
  "error": "ride_status_terminal",
  "error_message": "Cancel failed: ride already in status: completed",
}
```

## Get Nearby drivers
Get a list of nearby drivers for a given location, sorted in the order of etas.

```shell
# Definition
GET {ENVIRONMENT_ENDPOINT}/partner/{PARTNER_ID}/driverlocations>auth_token={PARTNER_TOKEN}&latitude={LATITUDE}&longitude={LONGITUDE}

# Example request
curl -XGET \
  "https://mobile.flywheel.com/partner/2001/driverlocations" \
   -H "Content-type: application/json" \
   -d auth_token=<PARTNER_TOKEN> \
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

### API
GET /partner/:partner_id/driverlocations

### Parameters

Parameter | Type | Description 
--------- |------|-----------
**auth_token**  | Query  | Authorization token provided to the partner by flywheel
**partner_id**  | URL | Partner id provided by Flywheel
**latitude** | Query | Latitude of the pick up location
**longitude** | Query | Longitude of the pick up location

### Success Response
  * Response Type: application/json
  * Content: 
      * drivers(List of Objects): Each driver object has the following attributes-
          * latitude(float): Driver latitude
          * longitude(float): Driver longitude  
          * token(long): Epoch
      * eta(integer): Eta(in secs) of the nearest driver

### Error Responses
* Unauthorized access in case of missing/invalid token:
    * Status Code: 401
    * Content: {error: error_message} (Error = “Malformed Token”/“Missing Token”)
* Unauthorized access in case of token-id mismatch:
    * Status Code: 403
    * Content: “Unauthorized access”
* Missing Latitude/Longitude Errors:
    * Status Code: 400
    * Content: {error_message: error_message}
        error_message=“latitude invalid”/“latitude is empty”/“longitude invalid”/“longitude is empty”



# Notes
## Ride Object
> Sample Ride Object:

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

* **id**(string): Id of the ride. The id used to reference rides on Flywheel server.
* **status**(string): The ride status. It can be one of the following-
 * **booked**: Ride status of an advance booked ride created successfully.
 * **setting_up**: Initial status upon successful creation of ride
 * **hailing**: The server is looking for a driver
 * **hail_accepted**: A driver has accepted the ride. A hail will be associated with the ride. For further details on ride progress check hail status.
 * **completed**: The ride has successfully completed.
 * **canceled**: The ride was cancelled by the partner. 
 * **failed**: The ride failed. For further details check failure_reason.
* **created_at**(long): Epoch timestamp of, when the ride was created
* **failure_reason**(string): Reason for ride failure, if ride status is ‘failed’. failure_reason can be one of the following-
 * **could_not_find_driver**: No drivers were available to accept the ride.
 * **system_error**: An internal server error occurred.
 * **passenger_did_not_show**: The driver marked the ride as ‘no show’, that is, the passenger did not show up at the pick up location. 
 * **driver_canceled**: The driver assigned to the cancelled.
 * **administrative**: The ride was manually forcefully failed due to administrative reasons.
* **passenger_id**(string): uuid of the passenger for which the ride was created.
* **pick_up_location**(Object): Object containing pick-up location details as specified when creating the ride
* **drop_off_location**(Object): Object containing drop-off location details as specified when creating the ride. This will always be empty for partner rides.
* **hail**(Object): Object containing details of the current hail status. There will be a hail object once ride hailing has started.
  * **status**(string): Status of the hail. Can be one of the following-
      * **driver_en_route**:  Driver on the way. For estimated time of driver’s arrival at the pick-up location refer to ‘driver_eta’.
      * **driver_on_location**: Driver at the pick-up location.
      * **passenger_on_board**: Passenger showed up and boarded the cab.
      * **completed**: The passenger has been dropped.
      * **passenger_canceled**: The ride was cancelled by partner
      * **driver_canceled**: The assigned driver cancelled. 
      * **hailing**: Looking for a driver, or waiting for a driver to accept/decline the hail.
      * **declined**: Driver declined the hail.
      * **timed_out**: Hail timed out, the driver did not respond.
      * **passenger_did_not_show**: Driver marked passenger as ‘no show’
 When the ride status is ‘hail_accepted’, hail status could be driver_en_route, driver_on_location or passenger_on_board.
  * **created_at**(long): Epoch timestamp of, when this hail was created.
  * **driver_eta**(integer): Will be present when the driver is on the way. Estimated number of seconds for driver to arrive at the pick-up location. 
  * **driver**(Object): 
      * **name**(string): Driver name.
      * **phone**(string): Driver telephone.
      * **latitude**(float): Current driver latitude.
      * **longitude**(float): Current driver longitude.
      * **location_timestamp**(long): Epoch timestamp of the current driver location.
      * **vehicle**(Object):
          * **fleet_name**(string): Name of the vehicle’s fleet
          * **seat_count**(integer): Number of seats, that is, the number of passengers that can be accommodated
          * **cab_number**(string): Cab number
          * **vehicle_type**(string): Can be sedan, van, suv, limo, bus or rampvan.
          * **medallion_number**(string): Medallion number. This is to be displayed as the vehicle number to the passenger.
          * **cab_number_label**(string): Cab number label