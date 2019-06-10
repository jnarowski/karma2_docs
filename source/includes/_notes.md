# Notes

## Get All Notes (Histories)

```shell
curl "https://app.karmacrm.com/api/v2/histories.json?filters[external_type]=Note&filters[history_record_id]=46&filters[history_record_type]=Contact&page=1&api_token=oGscoGFsdS54mProUdDz \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "results": [
    {
      "history_record_label": "John Smith",
      "history_record_path": "contacts/46",
      "id": 179,
      "history_record_id": 46,
      "history_record_type": "Contact",
      "history_type_id": 3,
      "name": "Note",
      "description": null,
      "user_id": 4,
      "organization_id": 2,
      "lead_id": null,
      "created_at": "2019-06-04T22:48:15Z",
      "updated_at": "2019-06-04T22:48:15Z",
      "note_id": 160,
      "company_id": null,
      "external_id": 160,
      "external_type": "Note",
      "private": null,
      "created_by_id": 4,
      "group_id": null,
      "delta": false,
      "read": false,
      "notification": false,
      "parent_id": null,
      "occurred_at": "2019-06-04T22:48:15Z",
      "comment_count": 0,
      "history_category_id": 4,
      "secondary_history_record_id": null,
      "secondary_history_record_type": null,
      "old_entity_id": null,
      "activity_type": "",
      "external": {
        "subject": "",
        "contact_type_id": 3,
        "label": "My Note Content",
        "comments": [],
        "assets": []
      },
      "comments": [],
      "participants": [],
      "_score": null,
      "_type": "history",
      "_index": "histories_development",
      "_version": null,
      "sort": [1559688495000],
      "highlight": null,
      "_explanation": null,
      "history_record": {},
      "posted_by": "Posted by",
      "box_class": "note",
      "external_path": "notes/160",
      "history_type_name": "Created",
      "editable": true,
      "list_body": "My Note Content",
      "body": "My Note Content",
      "class_name": "History"
    }
  ],
  "total_count": 4,
  "filter": "external type 'Note' history record id '46' history record type 'Contact' "
}
```

This endpoint retrieves all contacts.

### HTTP Request
`GET https://app.karmacrm.com/api/v2/histories.json`

### Query Parameters

Parameter | Description
--------- | -----------
page | Gets a specific page of histories
api_token | The token to authenticate request
filters[external_type] | Type of history i.e. `Note`
filters[history_record_type] | Record type assocated with histories i.e. `Contact`, `Company`, etc
filters[history_record_id] | Record id associated with histories

## Get a Note (History)
```shell
curl "https://app.karmacrm.com/api/v2/histories/179.json?api_token=oGscoGFsdS54mProUdDz" \
  -H "Content-Type: application/json"
```

> Example Response:

```json
{
  "id": "179",
  "history_record_id": 46,
  "history_record_type": "Contact",
  "history_type_id": 3,
  "name": "Note",
  "description": null,
  "user_id": 4,
  "organization_id": 2,
  "lead_id": null,
  "created_at": "2019-06-04T22:48:15Z",
  "updated_at": "2019-06-04T22:48:15Z",
  "note_id": 160,
  "company_id": null,
  "external_id": 160,
  "external_type": "Note",
  "private": null,
  "created_by_id": 4,
  "group_id": null,
  "delta": false,
  "read": false,
  "notification": false,
  "parent_id": null,
  "occurred_at": "2019-06-04T22:48:15Z",
  "comment_count": 0,
  "history_category_id": 4,
  "secondary_history_record_id": null,
  "secondary_history_record_type": null,
  "old_entity_id": null,
  "activity_type": "",
  "external": {
    "id": 160,
    "label": "My Note Content",
    "subject": null,
    "body": "My Note Content",
    "contact_type_id": 3,
    "assets": []
  },
  "comments": [],
  "participants": [
    {
      "id": null,
      "participater_id": 46,
      "participater_type": "Contact",
      "label": "John Smith"
    }
  ],
  "_type": "history",
  "_index": "histories_development",
  "_version": 2,
  "history_record_label": "John Smith",
  "history_record_path": "contacts/46",
  "occurred_at_short": "06/04",
  "class_name": "History",
  "posted_by": "Posted by",
  "occurred_at_long": "06/04/2019 at  4:48pm",
  "updated_at_formatted": "06/04/2019",
  "box_class": "note",
  "editable": true,
  "list_body": "My Note Content",
  "body": "My Note Content",
  "attachments": []
}
```

This endpoint retrieves a specific contact.

### HTTP Request

`GET https://app.karmacrm.com/api/v2/histories/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to retrieve
api_token | The token to authenticate request

## Create a Note

```shell
curl "https://app.karmacrm.com/api/v2/notes.json??api_token=oGscoGFsdS54mProUdDz \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"result_type":"backbone","note":{"body":"My Note Content","contact_type_id":3,"date":"2019-06-12","participants":[{"label":"John Smith","participater_type":"User","participater_id":4}],"user_ids":[4],"parent_type":"Contact","parent_id":11}}'
```
> Successful note creation response:

```json
{
  "id": 153,
  "to": null,
  "from": null,
  "bcc": null,
  "cc": null,
  "body": "My Note Content",
  "subject": null,
  "date": null,
  "lead_id": 11,
  "user_id": 4,
  "contact_type_id": 3,
  "organization_id": 2,
  "created_at": "2019-06-04T10:16:18-06:00",
  "updated_at": "2019-06-04T10:16:18-06:00",
  "from_lead": false,
  "created_by_id": 4,
  "html_email": false,
  "sent_at": null,
  "draft": false,
  "dropbox": false,
  "signature": false,
  "email_template_id": null,
  "asset_count": 0,
  "email_filename": null,
  "company_id": null,
  "message_id": null,
  "viewed_at": null,
  "token": null,
  "old_entity_id": null,
  "options": null,
  "note_type": null,
  "email": null,
  "opened_at": null,
  "incoming": null,
  "contextio_message_id": null,
  "private": false,
  "deliver_at": null,
  "replied_at": null,
  "campaign_entry_step_id": null,
  "bounced": false,
  "delivery_attempts": 0,
  "class_name": "Decorators::Note",
  "history": {
    "id": 172,
    "history_record_id": 11,
    "history_record_type": "Contact",
    "history_type_id": 3,
    "name": "Note",
    "description": null,
    "user_id": 4,
    "organization_id": 2,
    "lead_id": null,
    "created_at": "2019-06-04T10:16:18-06:00",
    "updated_at": "2019-06-04T10:16:18-06:00",
    "note_id": 153,
    "company_id": null,
    "external_id": 153,
    "external_type": "Note",
    "private": null,
    "created_by_id": 4,
    "group_id": null,
    "delta": false,
    "read": false,
    "notification": false,
    "parent_id": null,
    "occurred_at": "2019-06-12T10:16:00-06:00",
    "comment_count": 0,
    "history_category_id": 4,
    "secondary_history_record_id": null,
    "secondary_history_record_type": null,
    "old_entity_id": null,
    "additional_information": {},
    "activity_type": "",
    "occurred_at_utc": "2019-06-12T16:16:00Z",
    "class_name": "History",
    "posted_by": "Posted by",
    "box_class": "note",
    "editable": true,
    "list_body": "My Note Content",
    "body": "My Note Content"
  }
}
```

### HTTP Request

`POST https://app.karmacrm.com/api/v2/notes.json`

### URL Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
note[body] | Note Content
note[contact_type_id] | type id for note i.e `3` to add a note, `2` log a call
note[date] | Date added to note
note[time] | Time added to note
note[parent_type] | Record Type associated with note i.e. `Contact`, `Company`, etc
note[parent_id] | Record ID associated with note
note[user_ids] | User IDs to receive email notification
note[participants] | array of participants, i.e. <br>`{`<br>&nbsp; `"label": "John Smith",`<br>&nbsp; `"participater_type":"User",`<br>&nbsp; `"participater_id":4`<br>`}`

## Update a Note (History)

```shell
curl "https://app.karmacrm.com/api/v2/histories/177.json?api_token=oGscoGFsdS54mProUdDz" \
  -X PUT \
  -H "Content-Type: application/json" \
  -d '{"result_type":"backbone","history":{"date":"2019-06-19","time":"4:30am","external":{"type":"Note","id":158,"label":"My Updated Note Content","private":false,"body":"My Updated Note Content"}}}'
```
> Successful note update response:

```json
{
  "id":177,
  "history_record_id":11,
  "history_record_type":"Contact",
  "history_type_id":3,
  "name":"Phone Call",
  "description":null,
  "user_id":4,
  "organization_id":2,
  "lead_id":null,
  "created_at":"2019-06-04T12:48:52-06:00",
  "updated_at":"2019-06-04T12:57:07-06:00",
  "note_id":158,
  "company_id":null,
  "external_id":158,
  "external_type":"Note",
  "private":null,
  "created_by_id":4,
  "group_id":null,
  "delta":false,
  "read":false,
  "notification":false,
  "parent_id":null,
  "occurred_at":"2019-06-19T10:30:00Z",
  "comment_count":0,
  "history_category_id":6,
  "secondary_history_record_id":null,
  "secondary_history_record_type":null,
  "old_entity_id":null,
  "additional_information":{},
  "activity_type":"phone_call_created",
  "history_record_label":"Fred Derf",
  "history_record_path":"contacts/11",
  "occurred_at_short":"06/19",
  "class_name":"History",
  "posted_by":"Posted by",
  "occurred_at_long":"06/19/2019 at  4:30am",
  "updated_at_formatted":"06/04/2019",
  "box_class":"phone-call",
  "editable":true,
  "list_body":"My Updated Note Content",
  "body":"My Updated Note Content",
  "external":{
    "id":158,
    "to":null,
    "from":null,
    "bcc":null,
    "cc":null,
    "body":"My Updated Note Content",
    "subject":null,
    "date":null,
    "lead_id":11,
    "user_id":4,
    "contact_type_id":2,
    "organization_id":2,
    "created_at":"2019-06-04T12:48:52-06:00",
    "updated_at":"2019-06-04T12:57:07-06:00",
    "from_lead":false,
    "created_by_id":4,
    "html_email":false,
    "sent_at":null,
    "draft":false,
    "dropbox":false,
    "signature":false,
    "email_template_id":null,
    "asset_count":0,
    "email_filename":null,
    "company_id":null,
    "message_id":null,
    "viewed_at":null,
    "token":null,
    "old_entity_id":null,
    "options":null,
    "note_type":null,
    "email":null,
    "opened_at":null,
    "incoming":null,
    "contextio_message_id":null,
    "private":false,
    "deliver_at":null,
    "replied_at":null,
    "campaign_entry_step_id":null,
    "bounced":false,
    "delivery_attempts":0
  },
  "attachments":[],
  "participants":[
    {
      "id":null,
      "participater_id":11,
      "participater_type":"Contact",
      "label":"Fred Derf"
    },
    {
      "id":197,
      "participater_id":7,
      "participater_type":"User",
      "label":"khulani@gmail.com malone"
    }
  ]
}
```

This endpoint updates a specific note (history).

### HTTP Request

`PUT https://app.karmacrm.com/api/v2/histories/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to delete
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
result_type | result type (...may not be required) i.e. `backbone`
history[date] | Date added to note
history[time] | Time added to note
history[external][type] | `Note`
history[external][id] | Note id
history[external][body] | Note content
history[external][label] | Note content (same value as body)

## Delete a Note (History)

```shell
curl "https://app.karmacrm.com/api/v2/histories/172.json?api_token=oGscoGFsdS54mProUdDz"
  -X DELETE \
  -H "Content-Type: application/json"
```

This endpoint deletes a specific note (history).

### HTTP Request

`DELETE https://app.karmacrm.com/api/v2/histories/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to delete
api_token | The token to authenticate request

### Return Codes

Code | Description
---- | -----------
204 |  No content
