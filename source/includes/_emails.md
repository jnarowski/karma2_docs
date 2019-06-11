# Emails

## Send an email

```shell
curl "https://app.karmacrm.com/api/v3/mailman_nylas/outgoing/messages.json?api_token=oGscoGFsdS54mProUdDz \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"message":{"to":[{"id":5,"type":"Contact","label":"John Smith","email":"john.smith@gmail.com"}],"authorization_id":1,"subject":"My subject","body":"<div>My HTML body</div>"}}'
```

This endpoint sends an email.

### HTTP Request

`POST https://app.karmacrm.com/api/v3/mailman_nylas/outgoing/messages/create_draft.json`

### URL Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
message[to] | array of 'to' recipients i.e. <br>`{`<br>&nbsp; `"label": "John Smith",`<br>&nbsp; `"type":"Contact",`<br>&nbsp; `"email":"john.smith@gmail.com"`<br>&nbsp; `"id":5`<br>`}`
message[authorization_id] | authorization id of sender (user)
message[subject] | Email subject
message[body] | Email body

### Response Code

Code | Description
---- | -----------
204 |  No content

## Create an Email Draft

```shell
curl "https://app.karmacrm.com/api/v3/mailman_nylas/outgoing/messages/create_draft.json?api_token=oGscoGFsdS54mProUdDz \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"message":{"to":[{"id":5,"type":"Contact","label":"John Smith","email":"john.smith@gmail.com"}],"authorization_id":1,"cc":[{"id":"46","type":"Contact","email":"jane.smith@gmail.com"}],"bcc":[{"id":"22","type":"Contact","email":"joe.smith@gmail.com"}],"subject":"My subject","body":"<div>My HTML body</div>"}}'
```
> Successful email draft creation response:

```json
{
  "id":171,
  "from":"Tom Smith <tom.smith@karmacrm.com>",
  "subject":"My subject",
  "body":"<div>My HTML body</div>",
  "to":[{"type":"Contact",
  "id":5,
  "label":"John Smith",
  "email":"jonh.smith@gmail.com"}],
  "cc":[{"type":"Contact",
  "id":46,
  "email":"jane.smith@gmail.com"}],
  "bcc":[{"type":"Contact",
  "id":22,
  "email":"joe.smith@gmail.com"}],
  "email_template_id":null,
  "authorization_id":1,
  "created_by_id":4,
  "organization_id":2,
  "created_at":"2019-06-05T12:31:54Z",
  "updated_at":"2019-06-05T12:31:54Z",
  "attachments":[]
}
```

This endpoint creates an email draft

### HTTP Request

`POST https://app.karmacrm.com/api/v3/mailman_nylas/outgoing/messages/create_draft.json`

### URL Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
message[to] | array of 'to' recipients i.e. <br>`{`<br>&nbsp; `"label": "John Smith",`<br>&nbsp; `"type":"Contact",`<br>&nbsp; `"email":"john.smith@gmail.com"`<br>&nbsp; `"id":5`<br>`}`
message[cc] | array of 'cc' recipients i.e. <br>`{`<br>&nbsp; `"type":"Contact",`<br>&nbsp; `"email":"john.smith@gmail.com"`<br>&nbsp; `"id":5`<br>`}`
message[bcc] | array of 'bcc' recipients i.e. <br>`{`<br>&nbsp; `"type":"Contact",`<br>&nbsp; `"email":"john.smith@gmail.com"`<br>&nbsp; `"id":5`<br>`}`
message[authorization_id] | authorization id of sender (user)
message[subject] | Email subject
message[body] | Email body

## Update an Email (and optionally sends later)

```shell
curl "https://app.karmacrm.com/api/v3/mailman_nylas/outgoing/messages/173.json?api_token=oGscoGFsdS54mProUdDz" \
  -X PUT \
  -H "Content-Type: application/json" \
  -d '{"message":{"to":[{"id":5,"type":"Contact","label":"John Smith","email":"john.smith@gmail.com"}],"subject":"My updated  subject","body":"<div>My updated HTML body</div>","reminders":[{"time_increment":"2","interval":"days","reminder_type_id":4}],"cc":[{"id":"46","type":"Contact","email":"jane.smith@gmail.com"}],"bcc":[{"id":"22","type":"Contact","email":"joe.smith@gmail.com"}],"deliver_at":"2019-06-05T08:56:41-06:00"}}'
```

This endpoint updates a specific outgoing email draft.

### HTTP Request

`PUT https://app.karmacrm.com/api/v3/mailman_nylas/outgoing/messages/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to delete
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
message[to] | array of 'to' recipients i.e. <br>`{`<br>&nbsp; `"label": "John Smith",`<br>&nbsp; `"type":"Contact",`<br>&nbsp; `"email":"john.smith@gmail.com"`<br>&nbsp; `"id":5`<br>`}`
message[cc] | array of 'cc' recipients i.e. <br>`{`<br>&nbsp; `"type":"Contact",`<br>&nbsp; `"email":"john.smith@gmail.com"`<br>&nbsp; `"id":5`<br>`}`
message[bcc] | array of 'bcc' recipients i.e. <br>`{`<br>&nbsp; `"type":"Contact",`<br>&nbsp; `"email":"john.smith@gmail.com"`<br>&nbsp; `"id":5`<br>`}`
message[authorization_id] | authorization id of sender (user)
message[subject] | Email subject
message[body] | Email body
message[reminders] | array of reminders i.e. <br>`{`<br>&nbsp; `"time_increment":"2",`<br>&nbsp; `"interval":"days"`<br>&nbsp; `"reminder_type_id":4`<br>`}`
message[deliver_at] | optional time to send email at i.e. `2019-06-05T08:56:41-06:00`

### Response Code

Code | Description
---- | -----------
204 |  No content

## Update and Deliver Email (Now)

```shell
curl "https://app.karmacrm.com/api/v3/mailman_nylas/outgoing/messages/173/update_and_deliver.json?api_token=oGscoGFsdS54mProUdDz" \
  -X PUT \
  -H "Content-Type: application/json" \
  -d '{"message":{"to":[{"id":5,"type":"Contact","label":"John Smith","email":"john.smith@gmail.com"}],"subject":"My updated  subject","body":"<div>My updated HTML body</div>","reminders":[{"time_increment":"2","interval":"days","reminder_type_id":4}],"cc":[{"id":"46","type":"Contact","email":"jane.smith@gmail.com"}],"bcc":[{"id":"22","type":"Contact","email":"joe.smith@gmail.com"}]}}'
```

This endpoint updates and delivers messages.

### HTTP Request

`PUT https://app.karmacrm.com/api/v3/mailman_nylas/outgoing/messages/<ID>/update_and_deliver.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to delete
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
message[to] | array of 'to' recipients i.e. <br>`{`<br>&nbsp; `"label": "John Smith",`<br>&nbsp; `"type":"Contact",`<br>&nbsp; `"email":"john.smith@gmail.com"`<br>&nbsp; `"id":5`<br>`}`
message[cc] | array of 'cc' recipients i.e. <br>`{`<br>&nbsp; `"type":"Contact",`<br>&nbsp; `"email":"john.smith@gmail.com"`<br>&nbsp; `"id":5`<br>`}`
message[bcc] | array of 'bcc' recipients i.e. <br>`{`<br>&nbsp; `"type":"Contact",`<br>&nbsp; `"email":"john.smith@gmail.com"`<br>&nbsp; `"id":5`<br>`}`
message[authorization_id] | authorization id of sender (user)
message[subject] | Email subject
message[body] | Email body
message[reminders] | array of reminders i.e. <br>`{`<br>&nbsp; `"time_increment":"2",`<br>&nbsp; `"interval":"days"`<br>&nbsp; `"reminder_type_id":4`<br>`}`

### Response Code

Code | Description
---- | -----------
204 |  No content

## Delete an Email Draft

```shell
curl "https://app.karmacrm.com/api/v3/mailman_nylas/outgoing/messages/172.json?api_token=oGscoGFsdS54mProUdDz"
  -X DELETE \
  -H "Content-Type: application/json"
```

This endpoint deletes an email draft.

### HTTP Request

`DELETE https://app.karmacrm.com/api/v3/mailman_nylas/outgoing/messages/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to delete
api_token | The token to authenticate request

### Response Code

Code | Description
---- | -----------
204 |  No content
