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
page | Gets a specific page of contacts
per_page | Number of contacts per page
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
page | Gets a specific page of contacts
per_page | Number of contacts per page
api_token | The token to authenticate request
record_type | Record Type (i.e. `Contact`)
record_id | Record ID