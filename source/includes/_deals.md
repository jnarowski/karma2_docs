# Deals

## Get All Deals

```shell
curl "https://app.karmacrm.com/api/v3/deals.json?api_token=oGscoGFsdS54mProUdDz&page=3&since=2019-06-02" \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "results": [
    {
      "id": 20,
      "name": "Deal Title",
      "created_at": "2019-06-19T15:58:33Z",
      "updated_at": "2019-06-19T16:15:45Z",
      "field_values": [
        {
          "id": 60,
          "field_id": 53,
          "field_type_id": 5,
          "value": "Custom Text Field Value"
        }
      ]
    },
    {
      "id": 21,
      "name": "Deal Title Two",
      "created_at": "2019-06-19T16:16:20Z",
      "updated_at": "2019-06-19T16:16:20Z",
      "field_values": [
        {
          "id": 61,
          "field_id": 53,
          "field_type_id": 5,
          "value": "Custom Text Field Value Two"
        }
      ]
    }
  ],
  "total_count": 2
}
```

This endpoint retrieves all deals.

### HTTP Request
`GET https://app.karmacrm.com/api/v3/deals.json`

### Query Parameters

Parameter | Description
--------- | -----------
page | Gets a specific page of deals
api_token | The token to authenticate request
since | Filters deals after a specified date


## Get a Specific Deal
```shell
curl "https://app.karmacrm.com/api/v3/deals/20.json?api_token=oGscoGFsdS54mProUdDz" \
  -H "Content-Type: application/json"
```

> Example Response:

```json
{
  "id": 20,
  "name": "Deal Title",
  "description": "Deal Description",
  "deal_stage_id": 15,
  "currency": "USD",
  "organization_id": 2,
  "user_id": 4,
  "created_by_id": 4,
  "private": false,
  "due_on": "2019-06-30",
  "probability": 18.0,
  "price": 10.0,
  "stages": [
    {
      "id": 11,
      "name": "Pending",
      "position": 1
    },
    {
      "id": 12,
      "name": "Won",
      "position": 2
    },
    {
      "id": 13,
      "name": "Lost",
      "position": 3
    },
    {
      "id": 14,
      "name": "Holding",
      "position": 4
    },
    {
      "id": 15,
      "name": "Sent",
      "date": "2019-06-19",
      "position": 0
    },
    {
      "id": 16,
      "name": "Changed",
      "position": 5
    }
  ],
  "deal_syncs": [],
  "tag_list": "local,support",
  "contact": {
    "id": 11,
    "first_name": "Fred",
    "last_name": "Derf",
    "avatar_url": "/assets/person_thumb.png",
    "emails": [],
    "websites": [],
    "phone_numbers": [],
    "addresses": [],
    "social_accounts": [],
    "tags": []
  },
  "contact_id": 11,
  "created_at": "2019-06-19T15:58:33Z",
  "updated_at": "2019-06-19T16:15:45Z",
  "field_values": [
    {
      "id": 60,
      "field_id": 53,
      "field_type_id": 5,
      "value": "Custom Text Field Value"
    }
  ],
  "important_dates": [
    {
      "id": 21,
      "date": "2019-06-19",
      "to_status_id": 15
    }
  ]
}
```

This endpoint retrieves a specific deal.

### HTTP Request

`GET https://app.karmacrm.com/api/v3/deals/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the deal to retrieve
api_token | The token to authenticate request

## Create a Deal

```shell
curl "https://app.karmacrm.com/api/v3/deals.json?api_token=oGscoGFsdS54mProUdDz" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"deal":{"name":"Deal Title","contact_id":5,"company_id":7,"deal_stage_id":15,"probability":18,"price":10,"currency":"USD","description":"Deal Description","tags":["local","support"],"user_id":4,"private":false,"field_values":[{"value":"Custom Text Field Value","field_id":53}],"due_on":"2019-06-30"}}'
```
> Successful deal creation response:

```json
{
  "id":20,
  "name":"Deal Title",
  "description":"Deal Description",
  "deal_stage_id":15,
  "contact_id":5,
  "company_id":7,
  "price":10.0,
  "currency":"USD",
  "organization_id":2,
  "user_id":4,
  "created_by_id":4,
  "private":false,
  "due_on":"2019-06-30",
  "probability":18.0,
  "tags":["local","support"],
  "created_at":"2019-06-19T15:58:33Z",
  "updated_at":"2019-06-19T15:58:33Z",
  "field_values":[
    {
      "id":60,
      "field_id":53,
      "field_type_id":5,
      "field_parent_id":null,
      "value":"Custom Text Field Value"
    }
  ],
  "important_dates":[
    {
      "id":21,
      "date":"2019-06-19",
      "from_status_id":null,
      "to_status_id":15
    }
  ]
}
```

### HTTP Request

`POST https://app.karmacrm.com/api/v3/deals.json`

### URL Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
deal[name] | Deal's name
deal[probablity] | Deal's probablity value
deal[price] | Deal's price
deal[currency] | Deal's currency
deal[description] | Deal's description
deal[due_on] | Date deal is due on
deal[tags] | array of deal's tags i.e. `["development","usa"]`
deal[deal_stage_id] | ID of deal's stage 
deal[contact_id] | ID of contact the deal is for 
deal[company_id] | ID of company the deal is for <br>(Note: company and contact must be associated with each other if both are provided.)
deal[user_id] | ID for deal's assigned user
deal[field_values] | array of deal's custom field values, i.e <br>`{"field_id":1,"value":"custom info"}` <br>`{"value":"5","field_id":5,"field_parent_id":2}` (with parent field)

## Update a Deal

```shell
curl "https://app.karmacrm.com/api/v3/deals/20.json?api_token=oGscoGFsdS54mProUdDz" \
  -X PUT \
  -H "Content-Type: application/json" \
  -d '{"id":20,"deal":{"name":"Deal Title","contact_id":11,"company_id":null,"deal_stage_id":15,"probability":18,"price":10,"currency":"USD","description":"Deal Description","tags":["local","support"],"user_id":4,"private":false,"field_values":[{"id":60,"value":"Custom Text Field Value","field_id":53}],"due_on":"2019-06-30"}}'
```

This endpoint updates a specific deal.

### HTTP Request

`PUT https://app.karmacrm.com/api/v3/deals/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the deal to update
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
deal[name] | Deal's name
deal[probablity] | Deal's probablity value
deal[price] | Deal's price
deal[currency] | Deal's currency
deal[description] | Deal's description
deal[due_on] | Date deal is due on
deal[tags] | array of deal's tags i.e. `["development","usa"]`
deal[deal_stage_id] | ID of deal's stage 
deal[contact_id] | ID of contact the deal is for 
deal[company_id] | ID of company the deal is for <br>(Note: company and contact must be associated with each other if both are provided.)
deal[user_id] | ID for deal's assigned user
deals[field_values] | array of deals's custom field values, i.e<br><strong>update:</strong><br> `{"id":7,"field_id":1,"value":"update value for text field"}`<br><strong>add/check new (checkbox choice):</strong><br> `{"value":"5","field_id":5,"field_parent_id":2}`<br>

### Return Codes

Code | Description
---- | -----------
204 |  No content

## Delete a Deal

```shell
curl "https://app.karmacrm.com/api/v2/deals/27.json?api_token=oGscoGFsdS54mProUdDz"
  -X DELETE \
  -H "Content-Type: application/json"
```

This endpoint deletes a specific deal.

### HTTP Request

`DELETE https://app.karmacrm.com/api/v2/deals/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the deal to delete
api_token | The token to authenticate request

### Return Codes

Code | Description
---- | -----------
204 |  No content
