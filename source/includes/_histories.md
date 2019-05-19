# Histories

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
`GET https://app.karmacrm.com/api/v3/activities/related.json`

### Query Parameters

Parameter | Description
--------- | -----------
page | Gets a specific page of contacts
per_page | Number of contacts per page
api_token | The token to authenticate request
record_type | Record Type (i.e. `Contact`)
record_id | Record ID