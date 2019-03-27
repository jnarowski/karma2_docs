# Contacts

## Get All Contacts

```shell
curl "https://app.karmacrm.com/api/v2/contacts?columns%5B%5D=first_name&columns%5B%5D=last_name&columns%5B%5D=company_id&columns%5B%5D=lead_status_id&columns%5B%5D=tag_list&page=1&report_id=19"
```

> The above command returns JSON structured like this:

```json
{
  "results":[
    {
      "id":"1",
      "permission":1,
      "first_name":"John",
      "last_name":"Doe",
      "company_id":null,
      "lead_status_id":null,
      "tag_list":"",
      "class_name":"Contact",
      "created_at":null,
      "updated_at":null,
      "note_last_added_at":null,
      "avatar_url":"/assets/person_thumb.png",
      "company":null,
      "emails":[],
      "websites":[],
      "addresses":[]
    },
    {
      "id":"2",
      "permission":1,
      "first_name":"Jane",
      "last_name":"Doe",
      "company_id":7,
      "lead_status_id":13,
      "tag_list":"tag1,tag2",
      "class_name":"Contact",
      "created_at":null,
      "updated_at":null,
      "note_last_added_at":null,
      "avatar_url":"/assets/person_thumb.png",
      "company":null,
      "emails":[],
      "websites":[],
      "addresses":[]
    }
  ],
  "total_count":18,
  "filter":""
}
```

This endpoint retrieves all contacts.

### HTTP Request
`GET https://app.karmacrm.com/api/v3/contacts`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
columns[] | | Determines contact details returned in results. (i.e. first_name, last_name, etc)
page | 1 | Gets a specific page of contacts
report_id | 19 | Report Id


## Get a Specific Contact
```shell
curl "https://app.karmacrm.com/api/v3/contacts/10198487"
```

> The above command returns JSON structured like this:

```json
{
  "id":10198487,
  "first_name":"Dorothy",
  "last_name":"Chesterfield",
  "avatar_url":"/assets/person_thumb.png",
  "organization_id":13051,
  "referral_source_id":337712,
  "user_id":35666,
  "private":false,
  "permission":1,
  "engagements_count":0,
  "label":"Dorothy Chesterfield",
  "name":"Dorothy Chesterfield",
  "class_name":"Contact",
  "tag_list":"mastermind",
  "company":{
    "id":3511195,
    "name":"Cowan & Kelly"
  },
  "created_at":"2018-10-31T18:15:15Z",
  "updated_at":"2018-12-21T17:09:59Z",
  "bucket_ids":[],
  "contact_buckets":[],
  "secondary_emails":[
    {
      "id":8101666,
      "email":"dorothy@cox.net",
      "secondary_email_type_id":1,
      "label":"work",
      "position":0
    }
  ],
  "secondary_websites":[
    {
      "id":2947157,
      "url":"http://www.cowankelly.com",
      "secondary_website_type_id":1,
      "label":"work",
      "position":0
    }
  ],
  "phone_numbers":[
    {
      "id":8869438,
      "number":"858-617-7834",
      "phone_number_type_id":1,
      "primary_item":false,
      "label":"work",
      "position":0
    },
    {
      "id":8869439,
      "number":"858-732-1884",
      "phone_number_type_id":3,
      "primary_item":false,
      "label":"home",
      "position":0
    }
  ],
  "addresses":[
    {
      "id":6993304,
      "label":"work",
      "city":"San Diego",
      "street":"469 Outwater Ln",
      "state":"CA",
      "postal_code":"92126",
      "address_type":1,
      "position":0
    }
  ],
  "social_accounts":[],
  "custom_field_200336":{
    "id":16738768,
    "value":"Audience",
    "field_parent_id":200336,
    "field_id":200337
  },
  "custom_field_200340":{
    "id":16738769,
    "value":"No",
    "field_parent_id":200340,
    "field_id":200342
  },
  "custom_field_200365":{
    "id":16738767,
    "value":"San Diego",
    "field_parent_id":null,
    "field_id":200365
  },
  "permissions":[],
  "relationships":[],
  "important_dates":[]
}
```

This endpoint retrieves a specific contact.

### HTTP Request

`GET https://app.karmacrm.com/api/v3/contacts/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to retrieve

## Delete a Specific Contact

```shell
curl " https://app.karmacrm.com/api/v2/contacts/23"
  -X DELETE
```

This endpoint deletes a specific contact.

### HTTP Request

`DELETE https://app.karmacrm.com/api/v2/contacts/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to delete

### Return Codes

Code | Description
---- | -----------
204 |  No content
