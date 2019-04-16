# Contacts

## Get All Contacts

```shell
curl "https://app.karmacrm.com/api/v3/contacts?api_token=oGscoGFsdS54mProUdDz&page=3&filters%5Blead_process_id%5D=13&sorts%5Bfirst_name%5D=asc" \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "results":[
    {
      "id":25,
      "first_name":"John",
      "last_name":"Smith",
      "avatar_url":"/assets/person_thumb.png",
      "department":"Development",
      "referral_source_id":8,
      "user_id":5,
      "created_by_id":4,
      "private":true,
      "position":"developer",
      "background":"Good developer with 3+ years of experience",
      "contact_status_id":13,
      "contact_process_id":13,
      "tags":["development","usa"],
      "company":{
        "id":5,
        "name":"Company A"
      },
      "created_at":"2019-03-28T02:45:39Z",
      "updated_at":"2019-03-28T05:07:19Z",
      "emails":[
        {
          "id":12,
          "email":"john.smith@example.com",
          "secondary_email_type_id":2
        }
      ],
      "websites":[
        {
          "id":4,
          "url":"example.com",
          "secondary_website_type_id":1
        }
      ],
      "phone_numbers":[
        {
          "id":6,
          "number":"+7 902 4321 2123",
          "phone_number_type_id":2
        }
      ],
      "addresses":[
        {
          "id":4,
          "country":"USA",
          "state":"Illinois",
          "city":"Chicago",
          "street":"South St",
          "postal_code":"60667"
        }
      ],
      "social_accounts":[
        {
          "id":3,
          "name":"john_smith",
          "social_account_type_id":1
        }
      ],
      "field_values":[
        {
          "id":7,
          "field_id":1,
          "field_type_id":5,
          "value":"value for custom text field"
        },
        {
          "id":13,
          "field_id":4,
          "field_type_id":3,
          "field_parent_id":2,
          "value":"4"
        }
      ],
      "permissions":[
        {
          "id":1,
          "permission":1,
          "accessor_id":5,
          "accessor_type":"User"
        },
        {
          "id":2,
          "permission":1,
          "accessor_id":4,
          "accessor_type":"User"
        }
      ]
    }
  ],
  "total_count":21
}
```

This endpoint retrieves all contacts.

### HTTP Request
`GET https://app.karmacrm.com/api/v3/contacts.json`

### Query Parameters

Parameter | Description
--------- | -----------
page | Gets a specific page of contacts
api_token | The token to authenticate request
filters[user_id] | Filters contacts by assigned user id
filters[contact_status_id] | Filters contacts by status id
filters[contact_process_id] | Filters contacts by stage id
filters[tag_list] | Filters contacts by tag list (i.e. `eastern,night`)
sorts[`<FIELD NAME>`] | Sort contacts on a specified field (i.e. `first_name`)<br>in ascending `asc` or descending `desc` order


## Get a Specific Contact
```shell
curl "https://app.karmacrm.com/api/v3/contacts/25.json?api_token=oGscoGFsdS54mProUdDz" \
  -H "Content-Type: application/json"
```

> Example Response:

```json
{
  "id":25,
  "first_name":"John",
  "last_name":"Smith",
  "background":"Good developer with 3+ years of experience",
  "position":"developer",
  "avatar_url":"/assets/person_thumb.png",
  "department":"Development",
  "organization_id":2,
  "referral_source_id":8,
  "user_id":5,
  "created_by_id":4,
  "private":true,
  "contact_status_id":13,
  "contact_stage_id":13,
  "tags":["development","usa"],
  "company":{
    "id":5,
    "name":"Company A"
  },
  "created_at":"2019-03-28T02:45:39Z",
  "updated_at":"2019-03-28T05:07:19Z",
  "bucket_ids":[],
  "emails":[
    {
      "id":12,
      "email":"john.smith@example.com",
      "label":"home",
      "email_type_id":2
    }
  ],
  "websites":[
    {
      "id":4,
      "url":"example.com",
      "label":"work",
      "website_type_id":1
    }
  ],
  "phone_numbers":[
    {
      "id":6,
      "number":"+7 902 4321 2123",
      "phone_number_type_id":2,
      "label":"mobile"
    }
  ],
  "addresses":[
    {
      "id":4,
      "label":"home",
      "country":"USA",
      "city":"Chicago",
      "street":"South St",
      "state":"Illinois",
      "postal_code":"60667",
      "address_type_id":2
    }
  ],
  "social_accounts":[
    {
      "id":3,
      "name":"john_smith",
      "social_account_type_id":1
    }
  ],
  "field_values":[
    {
      "id":7,
      "field_id":1,
      "field_type_id":5,
      "value":"Updated text curl2"
    },
    {
      "id":13,
      "field_id":4,
      "field_type_id":3,
      "field_parent_id":2,
      "value":"4"
    }
  ],
  "permissions":[
    {
      "id":1,
      "permission":1,
      "accessor_id":5,
      "accessor_type":"User"
    },
    {
      "id":2,
      "permission":1,
      "accessor_id":4,
      "accessor_type":"User"
    }
  ],
  "relationships":[],
  "important_dates":[]
}
```

This endpoint retrieves a specific contact.

### HTTP Request

`GET https://app.karmacrm.com/api/v3/contacts/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to retrieve
api_token | The token to authenticate request

## Create a Contact

```shell
curl "http://app.karmacrm.com/api/v3/contacts.json?api_token=oGscoGFsdS54mProUdDz" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"contact":{"first_name":"John","last_name":"Smith","position":"developer","background":"Good developer with 3+ years of experience","contact_stage_id":13,"contact_status_id":13,"referral_source_id":8,"department":"Development","industry_id":null,"company":{"name":"Company A"},"tags":["development","usa"],"addresses":[{"street":"South St","city":"Chicago","state":"Illinois","country":"USA","postal_code":"60667","address_type_id":2}],"phone_numbers":[{"number":"+7 902 4321 2123","phone_number_type_id":2}],"emails":[{"email":"john.smith@example.com","email_type_id":2}],"social_accounts":[{"name":"john_smith","social_account_type_id":1}],"websites":[{"url":"example.com","website_type_id":1},{"url":"another.com","label":"New Label"}],"field_values":[{"field_id":1,"value":"Updated text"},{"field_parent_id":2,"field_id":4}],"permissions":[{"accessor_id":5,"accessor_type":"User","permission":1}]}}'
```
> Successful contact creation response:

```json
{
  "id": 25,
  "first_name": "John",
  "last_name": "Smith",
  "background": "Good developer with 3+ years of experience",
  "position": "developer",
  "private_notes": null,
  "department": "Development",
  "organization_id": 2,
  "referral_source_id": 8,
  "user_id": 4,
  "created_by_id": 4,
  "industry_id": null,
  "private": true,
  "contact_status_id": 13,
  "contact_stage_id": 13,
  "tags": ["development", "usa"],
  "company": {
    "id": 5,
    "name": "Company A"
  },
  "created_at": "2019-03-28T02: 45: 39Z",
  "updated_at": "2019-03-28T02: 45: 39Z",
  "emails": [
    {
      "id": 12,
      "email": "john.smith@example.com",
      "email_type_id": 2
    }
  ],
  "websites": [
    {
      "id": 4,
      "url": "example.com",
      "website_type_id": 1
    }
  ],
  "phone_numbers": [
    {
      "id": 6,
      "number": "+7 902 4321 2123",
      "phone_number_type_id": 2
    }
  ],
  "addresses": [
    {
      "id": 4,
      "country": "USA",
      "city": "Chicago",
      "street": "South St",
      "street_2": null,
      "postal_code": "60667",
      "address_type_id": 2
    }
  ],
  "social_accounts": [
    {
      "id": 3,
      "name": "john_smith",
      "social_account_type_id": 1
    }
  ],
  "field_values": [
    {
      "id": 7,
      "field_id": 1,
      "field_type_id": 5,
      "field_parent_id": null,
      "value": "Updated text"
    },
    {
      "id": 8,
      "field_id": 4,
      "field_type_id": 3,
      "field_parent_id": 2,
      "value": 4
    }
  ],
  "bucket_ids": [],
  "permissions": [
    {
      "id": 1,
      "permission": 1,
      "accessor_id": 5,
      "accessor_type": "User"
    }
  ]
}
```
> Unsuccessful contact creation response:

```json
{
  "message": "Validation error",
  "errors": {
    "contact_status_id": [
      "given contact status doesn't exist in organization"
    ]
  }
}
```


### HTTP Request

`POST https://app.karmacrm.com/api/v3/contacts.json`

### URL Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
contact[first_name] | Contact's first name
contact[last_name] | Contact's last name
contact[position] | Contact's title
contact[background] | Contact's background information
contact[contact_stage_id] | ID for contact's stage
contact[contact_status_id] | ID for contact's status
contact[referral_source_id] | ID for contact's referral source
contact[user_id] | ID for contact's assigned user
contact[department] | Contact's department
contact[industry_id] | ID for contact's industry
contact[company] | Contact's company object i.e. `{"name":"Company A"}`
contact[tags] | array of contact's tags i.e. `["development","usa"]`
contact[addresses] | array of contact's addresses, i.e. <br>`{`<br>&nbsp; `"street":"South St",`<br>&nbsp; `"city":"Chicago",`<br>&nbsp; `"state":"Illinois",`<br>&nbsp; `"country":"USA",`<br>&nbsp; `"postal_code":"60667",`<br>&nbsp; `"address_type_id": 2,`<br>&nbsp; `"label": "New Custom Label",` (optional: adds custom label)<br>`}`
contact[phone_numbers] | array of contact's phone_numbers, i.e. (with optional custom label)<br> `{"number":"+7 902 4321 2123","phone_number_type_id":2,"label":"New Custom Label"}`
contact[emails] | array of contact's emails, i.e. (with optional custom label)<br> `{"email":"john.smith@example.com","email_type_id":2,"label":"New Custom Label"}`
contact[social_accounts] | array of contact's social accounts, i.e.<br> `{"name":"john_smith","social_account_type_id":1}`
contact[websites] | array of contact's websites, i.e. (with optional custom label)<br> `{"url":"example.com","website_type_id":1,"label":"New Custom Label"}`
contact[field_values] | array of contact's custom field values, i.e <br>`{"field_id":1,"value":"custom info"}` <br>`{"value":"5","field_id":5,"field_parent_id":2}` (with parent field)
contact[permissions] | array of permission granting access to contact's info i.e.<br>`{`<br>&nbsp; `"accessor_id": 4,`<br>&nbsp; `"accessor_type": "User",`<br>&nbsp; `"permission": 1`<br>}

## Update a Contact

```shell
curl "http://app.karmacrm.com/api/v3/contacts/24.json?api_token=oGscoGFsdS54mProUdDz" \
  -X PUT \
  -H "Content-Type: application/json" \
  -d '{"contact":{"first_name":"John","last_name":"Smith","background":"Good developer with 3+ years of experience","position":"developer","private_notes":null,"department":"Development","referral_source_id":8,"user_id":4,"industry_id":null,"private":true,"contact_status_id":13,"contact_stage_id":13,"tags":["development","usa"],"company":{"id":5,"name":"Company A"},"emails":[{"id":12,"email":"john.smith@example.com","email_type_id":2}],"websites":[{"id":4,"url":"example.com","website_type_id":1}],"phone_numbers":[{"id":6,"number":"+7 902 4321 2123","phone_number_type_id":2}],"addresses":[{"id":4,"country":"USA","city":"Chicago","street":"South St","postal_code":"60667","address_type_id":2}],"social_accounts":[{"id":3,"name":"john_smith","social_account_type_id":1}],"field_values":[{"id":7,"field_id":1,"value":"Updated text curl2"},{"id":13,"field_id":4,"field_parent_id":2,"value":"4"}],"permissions":[{"id":1,"permission":1,"accessor_id":5,"accessor_type":"User"}]}}'
```

This endpoint updates a specific contact.

### HTTP Request

`PUT https://app.karmacrm.com/api/v3/contacts/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to delete
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
contact[first_name] | Contact's first name
contact[last_name] | Contact's last name
contact[position] | Contact's title
contact[background] | Contact's background information
contact[private_notes] | Contact's private notes
contact[contact_stage_id] | ID for contact's stage
contact[contact_status_id] | ID for contact's status
contact[referral_source_id] | ID for contact's referral source
contact[user_id] | ID for contact's user
contact[department] | Contact's department
contact[industry_id] | ID for contact's industry
contact[company] | Contact's company object i.e. `{"id":5,"name":"Company A"}`
contact[tags] | array of contact's tags i.e. `["development","usa"]`
contact[addresses] | array of contact's addresses i.e. <br>`{`<br>&nbsp; `"id":4,`<br>&nbsp; `"street":"South St",`<br>&nbsp; `"city":"Chicago",`<br>&nbsp; `"state":"Illinois",`<br>&nbsp; `"country":"USA",`<br>&nbsp; `"postal_code":"60667",`<br>&nbsp; `"address_type_id": 2,`<br>&nbsp; `"label": "New Custom Label",` (optional: adds custom label)<br>&nbsp; `"_destroy": true` (optional: deletes address)<br>`}`<br>
contact[phone_numbers] | array of contact's phone_numbers, i.e.<br><strong>update:</strong><br> `{"id":6,"number":"+7 902 4321 2123","phone_number_type_id":2}`<br><strong>add new:</strong><br> `{"number":"+7 902 4321 2123","phone_number_type_id":2,"label":"New Custom Label"}`<br><strong>delete:</strong><br> `{"id":7,"number":"+7 902 4321 2123","phone_number_type_id":2, "_destroy":true}`
contact[emails] | array of contact's emails, i.e.<br><strong>update:</strong><br> `{"id":12,"email":"update.email@example.com","email_type_id":2}`<br><strong>add new:</strong><br> `{"email":"add.email  @example.com","email_type_id":2,"label":"New Label"}`<br><strong>delete:</strong><br> `{"id":14,"email":"delete.email@example.com","email_type_id":2,"_destroy":true}`
contact[social_accounts] | array of contact's social accounts, i.e.<br><strong>update:</strong><br> `{"id":3,"name":"update name","social_account_type_id":1}`<br><strong>add new:</strong><br> `{name":"new name","social_account_type_id":3}`<br><strong>delete:</strong><br> `{"id":3,"name":"delete name","social_account_type_id":1,"_delete":true}`
contact[websites] | array of contact's websites, i.e.<br><strong>update:</strong><br> `{"id":4,"url":"update.com","website_type_id":2}`<br><strong>add new:</strong><br> `{"url":"addnew.com","website_type_id":1, 'New Label'}`<br><strong>delete:</strong><br> `{"id":6,"url":"delete.com","website_type_id":1, "_destroy":true}`
contact[field_values] | array of contact's custom field values, i.e<br><strong>update:</strong><br> `{"id":7,"field_id":1,"value":"update value for text field"}`<br><strong>add/check new (checkbox choice):</strong><br> `{"value":"5","field_id":5,"field_parent_id":2}`<br>
contact[permissions] | array of permission granting access to contact's info i.e.<br>`{`<br>&nbsp; `"id":1,`<br>&nbsp; `"accessor_id": 4,`<br>&nbsp; `"accessor_type": "User",`<br>&nbsp; `"permission": 1`<br>&nbsp; `"_destroy": true` (optional: deletes permission)<br>`}`

### Return Codes

Code | Description
---- | -----------
204 |  No content

## Delete a Contact

```shell
curl "https://app.karmacrm.com/api/v3/contacts/27.json?api_token=oGscoGFsdS54mProUdDz"
  -X DELETE \
  -H "Content-Type: application/json"
```

This endpoint deletes a specific contact.

### HTTP Request

`DELETE https://app.karmacrm.com/api/v3/contacts/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to delete
api_token | The token to authenticate request

### Return Codes

Code | Description
---- | -----------
204 |  No content
