# Calendars

## Get All Calendars

```shell
curl "https://app.karmacrm.com/api/v3/activities.json?api_token=oGscoGFsdS54mProUdDz" \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "results": [
    {
      "id": 9,
      "title": "My private calendar",
      "color": "#336699",
      "user_id": 4,
      "personal": true,
      "public": false,
      "calendar_users": []
    },
    {
      "id": 10,
      "title": "My Public Calendar",
      "color": "#b08b59",
      "user_id": 4,
      "personal": false,
      "public": true,
      "calendar_users": []
    },
    {
      "id": 12,
      "title": "My Shared Calendar",
      "color": "#b08b59",
      "user_id": 4,
      "personal": false,
      "public": false,
      "calendar_users": [
        {
          "user_id": 5,
          "hidden": null,
          "position": null
        }
      ]
    }
  ],
  "total_count": 6
}
```

This endpoint retrieves all calendars.

### HTTP Request
`GET https://app.karmacrm.com/api/v3/calendars.json`

### Query Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

## Get All Calendar Items

```shell
curl "https://app.karmacrm.com/api/v3/calendars/items?api_token=oGscoGFsdS54mProUdDz&include%5B%5D=activities&start_date=2019-05-26&end_date=2019-07-07&calendar_ids%5B%5D=4" \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "events": [
    {
      "id": 41,
      "name": "Deal ask",
      "calendar_id": 4,
      "all_day": false,
      "logged_at": null,
      "parent_id": null,
      "activity_type": "Todo",
      "event_category_id": 17,
      "complete": false,
      "start_at": "2019-06-10T20:30:00Z",
      "end_at": "2019-06-10T20:30:00Z"
    },
    {
      "id": 51,
      "name": "My Body",
      "calendar_id": 4,
      "all_day": true,
      "logged_at": null,
      "parent_id": null,
      "activity_type": null,
      "event_category_id": 20,
      "complete": false,
      "start_at": "2019-06-21T06:00:00Z",
      "end_at": "2019-06-21T06:00:00Z"
    }
  ],
  "todos": []
}
```

This endpoint retrieves all calendar items.

### HTTP Request
`GET https://app.karmacrm.com/api/v3/calendars/items.json`

### Query Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request
include | An array of calendar item types, i.e. `activities`
start_date | Retrieves calendar items after this date
end_date | Retrieves calendar items before this date
calendar_ids | An array of calendar ids that the calendar items belong to.



## Get a Specific Calendar
```shell
curl "https://app.karmacrm.com/api/v3/calendars/12.json?api_token=oGscoGFsdS54mProUdDz" \
  -H "Content-Type: application/json"
```

> Example Response:

```json
{
  "id": 12,
  "title": "My Shared Calendar",
  "color": "#b08b59",
  "token": "X2ed2K8AJzDjc6zxp7Yi",
  "personal": false,
  "public": false,
  "user_id": 4,
  "calendar_users": [
    {
      "user_id": 5
    }
  ]
}
```

This endpoint retrieves a specific calendar.

### HTTP Request

`GET https://app.karmacrm.com/api/v3/calendars/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the calendar to retrieve
api_token | The token to authenticate request

## Create a Calendar

```shell
curl "https://app.karmacrm.com/api/v3/calendars.json?api_token=oGscoGFsdS54mProUdDz" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"calendar":{"title":"My Shared Calendar","color":"#b08b59","calendar_users":[{"user_id":"36348"}],"personal":false,"public":false}}'
```
> Successful calendar creation response:

```json
{
  "id": 12,
  "title": "My Shared Calendar",
  "color": "#b08b59",
  "token": "X2ed2K8AJzDjc6zxp7Yi",
  "personal": false,
  "public": false,
  "user_id": 4,
  "calendar_users": [
    {
      "user_id": 5
    }
  ]
}
```

### HTTP Request

`POST https://app.karmacrm.com/api/v3/calendars.json`

### URL Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
calendar[title] | Calendar's title
calendar[color] | Calendar's color i.e. `#b08b59`
calendar[personal] | Boolean value for calendar is private
calendar[public] | Boolean value for if calendar is public
calendar[calendar_users] | Array of user objects to share calendar with i.e. `{ "user_id": "5"}`

## Update a Calendar

```shell
curl "https://app.karmacrm.com/api/v3/calendars/20.json?api_token=oGscoGFsdS54mProUdDz" \
  -X PUT \
  -H "Content-Type: application/json" \
  -d '{"calendar":{"title":"My Shared Calendar","color":"#b08b59","personal":false,"public":false,"calendar_users":[{"user_id":"7"},{"user_id":"5","_destroy":true}]}}'
```

This endpoint updates a specific calendar.

### HTTP Request

`PUT https://app.karmacrm.com/api/v3/calendars/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the calendar to update
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
calendar[title] | Calendar's title
calendar[color] | Calendar's color i.e. `#b08b59`
calendar[personal] | Boolean value for calendar is private
calendar[public] | Boolean value for if calendar is public
calendar[calendar_users] | Array of user objects to share calendar with i.e. <br><strong>add new:</strong><br> `{"user_id":"5"}`<br><strong>delete:</strong><br> `{"user_id":6,"_destroy":true}`

### Return Codes

Code | Description
---- | -----------
204 |  No content

## Delete a Calendar

```shell
curl "https://app.karmacrm.com/api/v2/calendars/27.json?api_token=oGscoGFsdS54mProUdDz"
  -X DELETE \
  -H "Content-Type: application/json"
```

This endpoint deletes a specific calendar.

### HTTP Request

`DELETE https://app.karmacrm.com/api/v2/calendars/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the calendars to delete
api_token | The token to authenticate request

### Return Codes

Code | Description
---- | -----------
204 |  No content
