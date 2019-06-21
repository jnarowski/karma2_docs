# Activities

## Get All Activities

```shell
curl "
https://app.karmacrm.com/api/v3/activities.json?api_token=oGscoGFsdS54mProUdDz&per_page=100&page=1&filters%5Bdue_category%5D=overdue&filters%5Btodo_category_id%5D%5Bvalues%5D%5B%5D=21&filters%5Buser_id%5D=mine&columns%5B%5D=all_day&columns%5B%5D=body&columns%5B%5D=complete&columns%5B%5D=end_at&columns%5B%5D=due_at" \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "results": [
    {
      "id": 21,
      "body": "Meeting",
      "todo_category_id": 21,
      "all_day": false,
      "start_at": "2019-04-12T00:00:00Z"
    },
    {
      "id": 34,
      "body": "Task Step",
      "todo_category_id": 21,
      "all_day": false,
      "contact": {
        "id": 22,
        "name": "John Smith",
        "email": "john.smith@email.com"
      },
      "start_at": "2019-05-17T21:00:00Z"
    }
  ],
  "total_count": 2
}
```

This endpoint retrieves all activities related to a contact.

### HTTP Request
`GET https://app.karmacrm.com/api/v3/activities/related.json`

### Query Parameters

Parameter | Description
--------- | -----------
page | Gets a specific page of activities
per_page | Number of activities per page
api_token | The token to authenticate request
filters[due_category] | Filter based on "due_at" date i.e. `overdue`, `today_and_overdue`, `today`, `this_week`, `upcoming` 
filters[todo_category_id][values][] | Filter based on todo category ids
filters[user_id] | Filter based "user_id" i.e, `mine`, or user_id
sorts[due_at] | Sort by "due_at" date `asc` and `desc`
columns[] | Include columns in results i.e. `all_day`, `body`, `complete`, `end_at`, etc

## Get Related Activities (for a Contact)

```shell
curl "https://app.karmacrm.com/api/v3/activities/related.json?api_token=oGscoGFsdS54mProUdDz&record_type=Contact&record_id=22&per_page=100&page=1" \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "results": [
    {
      "id": 34,
      "body": "Task from Template",
      "user_id": 4,
      "created_by_id": 4,
      "todo_category_id": 21,
      "complete": false,
      "todo_template_step_id": 1,
      "start_at": "2019-05-17T21:00:00Z",
      "created_at": "2019-05-17T16:50:56Z",
      "source": "Task Template",
      "participants": [
        {
          "id": 91,
          "label": "John Smith",
          "participater_id": 22,
          "participater_type": "Contact"
        }
      ],
      "reminders":[
        {
          "id": 10,
          "reminder_type_id": 5,
          "time_increment": 10,
          "interval": "minutes"
        }
      ]
    },
    {
      "id": 35,
      "body": "Task from Campaign",
      "created_by_id": 4,
      "complete": false,
      "campaign_step_id": 5,
      "start_at": "2019-05-17T06:00:00Z",
      "created_at": "2019-05-17T16:51:08Z",
      "source": "Task Campaign",
      "participants": [
        {
          "id": 93,
          "label": "John Smith",
          "participater_id": 22,
          "participater_type": "Contact"
        }
      ]
    }
  ],
  "total_count":2
}
```

This endpoint retrieves all activities related to a contact.

### HTTP Request
`GET https://app.karmacrm.com/api/v3/activities/related.json`

### Query Parameters

Parameter | Description
--------- | -----------
page | Gets a specific page of activities
per_page | Number of activities per page
api_token | The token to authenticate request
record_type | Record Type (i.e. `Contact`)
record_id | Record ID

## Get a Specific Activity

```shell
curl "
https://app.karmacrm.com/api/v3/activities/48.json?api_token=oGscoGFsdS54mProUdDz" \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "id": 48,
  "body": "My Activity Body",
  "description": "My Activity Notes",
  "todo_category_id": 17,
  "user_id": 4,
  "organization_id": 2,
  "created_by_id": 4,
  "activity_type": "Todo",
  "recurrence": [],
  "where": "",
  "calendar_id": 4,
  "complete": false,
  "created_at": "2019-06-20T22:49:55Z",
  "updated_at": "2019-06-20T22:49:55Z",
  "reminders": [
    {
      "id": 14,
      "reminder_type_id": 2,
      "interval": "minutes",
      "time_increment": 15
    },
    {
      "id": 15,
      "reminder_type_id": 3,
      "interval": "days",
      "time_increment": 2
    }
  ],
  "participants": []
}
```

This endpoint retrieves a specific activity.

### HTTP Request
`GET https://app.karmacrm.com/api/v3/activities/related.json`

### Query Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

## Create an Activity

```shell
curl "https://app.karmacrm.com/api/v3/activities.json?api_token=oGscoGFsdS54mProUdDz" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"activity":{"body":"My Body","where":"","description":"My Notes","all_day":true,"user_id":36192,"todo_category_id":140844,"reminders":[{"reminder_type_id":"2","interval":"minutes","time_increment":"15"}],"participants":[{"participater_id":"10662866","participater_type":"Contact"}],"recurrence":[],"due_at":"2019-06-21 6:00:00Z","end_at":null,"calendar_id":53518,"complete":false}}'
```
> Successful activity creation response:

```json
{
  "id":2674024,
  "body":"My Body",
  "description":"My Notes",
  "todo_category_id":140844,
  "user_id":36192,
  "organization_id":13346,
  "created_by_id":36192,
  "all_day":true,
  "recurrence":[],
  "where":"",
  "calendar_id":53518,
  "complete":false,
  "start_at":"2019-06-21T06:00:00Z",
  "created_at":"2019-06-21T17:33:12Z",
  "updated_at":"2019-06-21T17:33:12Z",
  "reminders":[
    {
      "id":1767753,
      "reminder_type_id":2,
      "interval":"minutes",
      "time_increment":15
    }
  ],
  "participants":[
    {
      "id":18861339,
      "participater_type":"Contact",
      "participater_id":10662866,
      "label":"John Smith"
    }
  ]
}
```

### HTTP Request

`POST https://app.karmacrm.com/api/v3/activities.json`

### URL Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
activity[body] | Activity's body
activity[where] | Activity's location,
activity[description] | Activity's notes,
activity[all_day] | Boolean value for if the activity is all day
activity[user_id] | ID of activity's assigned user,
activity[todo_category_id] | ID of activity's todo category,
activity[reminders] | an array of reminder objects i.e. <br>`{"reminder_type_id":"3","interval":"minutes","time_increment":"15"}`
activity[participants] | an array of participant objects i.e.<br>`{"participater_id":36348,"participater_type":"User"}`
activity[due_at] | Activity's start time / due time
activity[end_at] | Activity's end time,
activity[calendar_id] |ID of calendar the activity belongs to,
activity[complete] | Boolean value for if the activity is completed,
activity[completed_at] | Activity's completion time if completed

## Update an Activity

```shell
curl "https://app.karmacrm.com/api/v3/activities/49.json?api_token=oGscoGFsdS54mProUdDz" \
  -X PUT \
  -H "Content-Type: application/json" \
  -d '{"id":49,"activity":{"body":"My Body","where":"","description":"My Notes","all_day":false,"user_id":36192,"todo_category_id":140847,"reminders":[{"id":1767725,"_destroy":false,"reminder_type_id":"2","interval":"minutes","time_increment":"15"}],"participants":[{"id":18861204,"participater_id":36192,"participater_type":"User","_destroy":true},{"participater_id":36348,"participater_type":"User"}],"recurrence":[],"due_at":"2019-06-21 18:30:00Z","end_at":"2019-06-21 20:00:00Z","calendar_id":53518,"complete":false}}'
```

This endpoint updates a specific activity.

### HTTP Request

`PUT https://app.karmacrm.com/api/v3/activities/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the activity to update
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
activity[body] | Activity's body
activity[where] | Activity's location,
activity[description] | Activity's notes,
activity[all_day] | Boolean value for if the activity is all day
activity[user_id] | ID of activity's assigned user,
activity[todo_category_id] | ID of activity's todo category,
activity[reminders] | an array of reminder objects i.e.<br><strong>update:</strong><br> `{"id":4,"reminder_type_id":"3","interval":"minutes","time_increment":"20"}`<br><strong>add new:</strong><br> `{"reminder_type_id":"3","interval":"hours","time_increment":"1"}`<br><strong>delete:</strong><br> `{"id":6,"reminder_type_id":"3","interval":"minutes","time_increment":"15","_destroy":true}`
activity[participants] | an array of participant objects i.e.<br><strong>update:</strong><br> `{"id":18,"participater_id":10,"participater_type":"Contact","_destroy":false`<br><strong>add new:</strong><br> `{"participater_id":36,"participater_type":"User"}`<br><strong>delete:</strong><br> `{"id":6,"participater_id":23,"participater_type":"User","_destroy":true}`
activity[due_at] | Activity's start time / due time
activity[end_at] | Activity's end time,
activity[calendar_id] |ID of calendar the activity belongs to,
activity[complete] | Boolean value for if the activity is completed,
activity[completed_at] | Activity's completion time if completed

### Return Codes

Code | Description
---- | -----------
204 |  No content

## Delete a Activity

```shell
curl "https://app.karmacrm.com/api/v3/activities/27.json?api_token=oGscoGFsdS54mProUdDz"
  -X DELETE \
  -H "Content-Type: application/json"
```

This endpoint deletes a specific activity.

### HTTP Request

`DELETE https://app.karmacrm.com/api/v3/activities/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the activity to delete
api_token | The token to authenticate request

### Return Codes

Code | Description
---- | -----------
204 |  No content
