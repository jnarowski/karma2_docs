# Histories

## Get All Histories

```shell
curl "https://app.karmacrm.com/api/v3/histories.json?api_token=oGscoGFsdS54mProUdDz&per_page=3&page=1&include_external=true" \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "results": [
    {
      "id": 137,
      "name": "Todo",
      "user_id": 4,
      "created_by_id": 4,
      "history_category_id": 8,
      "history_type_id": 3,
      "history_record_id": 34,
      "history_record_type": "Todo",
      "external_id": 34,
      "external_type": "Todo",
      "history_record_label": "Task Step",
      "external": {
        "label": "Task Step"
      },
      "created_at": "2019-05-17T16:50:56Z",
      "occurred_at": "2019-05-17T16:50:56Z",
      "participants": [
        {
          "id": 92,
          "participater_id": 22,
          "participater_type": "Contact",
          "label": "Fresh Koolaid"
        }
      ]
    },
    {
      "id": 136,
      "name": "Email",
      "user_id": 4,
      "created_by_id": 4,
      "history_category_id": 5,
      "history_type_id": 8,
      "history_record_id": 5,
      "history_record_type": "Contact",
      "external_id": 111,
      "external_type": "Note",
      "history_record_label": "Khulani Malone",
      "external": {
        "body": "<div><br></div><div>Malone</div>",
        "contact_type_id": 1
      },
      "created_at": "2019-05-17T01:26:25Z",
      "occurred_at": "2019-05-17T01:26:21Z",
      "participants": [
        {
          "id": 90,
          "participater_id": 7,
          "participater_type": "Company",
          "label": "Khulani Malone Company"
        }
      ]
    },
    {
      "id": 128,
      "name": "Notification",
      "user_id": 5,
      "created_by_id": 4,
      "history_category_id": 3,
      "history_type_id": 5,
      "history_record_id": 44,
      "history_record_type": "Contact",
      "external_id": 44,
      "external_type": "Contact",
      "history_record_label": "Webhook First",
      "external": {
        "label": "Webhook First"
      },
      "created_at": "2019-05-13T17:02:36Z",
      "occurred_at": "2019-05-13T17:02:36Z"
    }
  ],
  "total_count": 100
}
```

This endpoint retrieves all histories.

### HTTP Request
`GET https://app.karmacrm.com/api/v3/histories.json`

### Query Parameters

Parameter | Description
--------- | -----------
page | Gets a specific page of contacts
per_page | Number of contacts per page
api_token | The token to authenticate request
include_external | Boolean value to include external info

## Get Related Histories (for a Contact)

```shell
curl "https://app.karmacrm.com/api/v3/histories/related?api_token=oGscoGFsdS54mProUdDz&record_type=Contact&record_id=22&per_page=100&page=1" \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "results": [
    {
      "id": 137,
      "name": "Todo",
      "user_id": 4,
      "created_by_id": 4,
      "history_category_id": 8,
      "history_type_id": 3,
      "occurred_at": "2019-05-17T16:50:56Z",
      "external": {
        "type": "Todo",
        "id": 34,
        "label": "Task Step"
      }
    },
    {
      "id": 127,
      "name": "Email",
      "user_id": 7,
      "created_by_id": 7,
      "history_category_id": 5,
      "history_type_id": 8,
      "occurred_at": "2019-05-13T16:57:55Z",
      "record": {
        "type": "Contact",
        "id": 22,
        "label": "John Smith"
      },
      "external": {
        "type": "Note",
        "id": 71,
        "label": "<div>testing</div>",
        "note_type": "email",
        "subject": "local email test",
        "private": false,
        "incoming": false,
        "reminders": [],
        "meta": {
          "id": 53
        }
      }
    },
    {
      "id": 35,
      "name": "Contact",
      "user_id": 4,
      "created_by_id": 4,
      "history_category_id": 2,
      "history_type_id": 3,
      "occurred_at": "2019-03-22T18:49:07Z",
      "record": {
        "type": "Contact",
        "id": 22,
        "label": "John Smith"
      },"external":  {
        "type": "Contact",
        "id": 22,
        "label": "John Smith"
      }
    }
  ],
  "total_count": 3
}
```

This endpoint retrieves all histories related to a contact.

### HTTP Request
`GET https://app.karmacrm.com/api/v3/histories/related.json`

### Query Parameters

Parameter | Description
--------- | -----------
page | Gets a specific page of contacts
per_page | Number of contacts per page
api_token | The token to authenticate request
record_type | Record Type (i.e. `Contact`)
record_id | Record ID