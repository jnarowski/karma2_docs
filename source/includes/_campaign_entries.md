# Campaign Entries

## Apply Campaign (Create a Campaign Entries)

```shell
curl "https://app.karmacrm.com/api/v3/campaign_entries/apply?api_token=oGscoGFsdS54mProUdDz" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"campaign_entry":{"record_id":10662866,"record_type":"Contact","campaign_id":"142"}}'
```
> Response for successfully applying a campaign:

```json
{
  "id": 9646,
  "record_id": 10662866,
  "record_type": "Contact",
  "campaign_id": 142,
  "current_campaign_entry_step_id": 67223,
  "created_at": "2019-04-02T22:25:05Z",
  "updated_at": "2019-04-02T22:25:05Z",
  "campaign_entry_steps": [
    {
      "id": 67223,
      "activity_type": "Note",
      "activity_id": 10419189,"
      campaign_entry_id": 9646,"
      campaign_step_id": 719
    },
    {
      "id": 67224,
      "campaign_entry_id": 9646,
      "campaign_step_id": 720
    },
    {
      "id": 67225,
      "campaign_entry_id": 9646,
      "campaign_step_id": 721
    }
  ]
}
```

### HTTP Request

`POST https://app.karmacrm.com/api/v3/campaign_entries/apply`

### URL Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
campaign_entry[record_id] | Record's ID to apply campaign to
campaign_entry[record_type] | Record's type to apply campaign to (i.e. Contact)
campaign_entry[campaign_id] | ID of campaign being applied

## Cancel a Campaign Entry

```shell
curl "https://app.karmacrm.com/api/v3/campaign_entries/9646/cancel.json?api_token=oGscoGFsdS54mProUdDz" \
  -X PUT \
  -H "Content-Type: application/json" \
  -d '{"id":9646}'
```

This endpoint updates a specific contact.

### HTTP Request

`PUT https://app.karmacrm.com/api/v3/campaign_entries/<ID>/cancel.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the campaign entry to cancel
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
id | Campaign entry's id

### Return Codes

Code | Description
---- | -----------
204 |  No content
