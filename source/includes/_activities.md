# Activities

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