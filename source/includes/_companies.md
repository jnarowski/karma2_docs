# Companies

## Get All Companies

```shell
curl "https://app.karmacrm.com/api/v3/companies.json?api_token=oGscoGFsdS54mProUdDz&page=3&filters%5Bcontact_stage_id%5D=13&sorts%5Bfirst_name%5D=asc" \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "results": [
    {
      "id": 10,
      "name": "my company name",
      "background": "my background",
      "referral_source_id": 9,
      "user_id": 4,
      "created_by_id": 4,
      "private": false,
      "avatar_url": "/assets/company_thumb.jpg",
      "tags": [
        "local",
        "new"
      ],
      "created_at": "2019-06-18T16:18:03Z",
      "updated_at": "2019-06-18T16:18:03Z",
      "emails": [
        {
          "id": 31,
          "email": "my.company@email.com",
          "secondary_email_type_id": 1
        },
        {
          "id": 32,
          "email": "my.company2@email.com",
          "secondary_email_type_id": 1
        }
      ],
      "websites": [
        {
          "id": 11,
          "url": "mycompany.com",
          "secondary_website_type_id": 2
        },
        {
          "id": 12,
          "url": "mycompanywork.com",
          "secondary_website_type_id": 1
        }
      ],
      "phone_numbers": [
        {
          "id": 10,
          "number": "123-456-7890",
          "phone_number_type_id": 1
        },
        {
          "id": 11,
          "number": "321-654-0987",
          "phone_number_type_id": 1
        }
      ],
      "addresses": [
        {
          "id": 9,
          "country": "US",
          "state": "ST",
          "city": "City",
          "street": "123 A St",
          "postal_code": "12345"
        }
      ],
      "social_accounts": [
        {
          "id": 4,
          "name": "mycompany",
          "social_account_type_id": 1
        },
        {
          "id": 5,
          "name": "mycompany",
          "social_account_type_id": 2
        }
      ]
    }
  ],
  "total_count": 1
}
```

This endpoint retrieves all companies.

### HTTP Request
`GET https://app.karmacrm.com/api/v3/companies.json`

### Query Parameters

Parameter | Description
--------- | -----------
page | Gets a specific page of companies
api_token | The token to authenticate request


## Get a Specific Company
```shell
curl "https://app.karmacrm.com/api/v3/companies/10.json?api_token=oGscoGFsdS54mProUdDz" \
  -H "Content-Type: application/json"
```

> Example Response:

```json
{
  "id": 10,
  "name": "my company name",
  "background": "my background",
  "avatar_url": "/assets/company_thumb.jpg",
  "organization_id": 2,
  "referral_source_id": 9,
  "user_id": 4,
  "created_by_id": 4,
  "private": false,
  "tags": [
    "local",
    "new"
  ],
  "created_at": "2019-06-18T16:18:03Z",
  "updated_at": "2019-06-18T16:18:03Z",
  "emails": [
    {
      "id": 31,
      "email": "my.company@email.com",
      "position": 0,
      "email_type_id": 1
    },
    {
      "id": 32,
      "email": "my.company2@email.com",
      "position": 1,
      "email_type_id": 1
    }
  ],
  "websites": [
    {
      "id": 11,
      "url": "mycompany.com",
      "position": 0,
      "website_type_id": 2
    },
    {
      "id": 12,
      "url": "mycompanywork.com",
      "position": 1,
      "website_type_id": 1
    }
  ],
  "phone_numbers": [
    {
      "id": 10,
      "number": "123-456-7890",
      "phone_number_type_id": 1,
      "position": 0,
      "label": "work"
    },
    {
      "id": 11,
      "number": "321-654-0987",
      "phone_number_type_id": 1,
      "position": 1,
      "label": "school"
    }
  ],
  "addresses": [
    {
      "id": 9,
      "country": "US",
      "city": "City",
      "street": "123 A St",
      "postal_code": "12345",
      "position": 1811,
      "label": "work",
      "address_type_id": 1
    }
  ],
  "social_accounts": [
    {
      "id": 4,
      "name": "mycompany",
      "social_account_type_id": 1,
      "position": 0
    },
    {
      "id": 5,
      "name": "mycompany",
      "social_account_type_id": 2,
      "position": 1
    }
  ],
  "field_values": [],
  "permissions": [],
  "relationships": []
}
```

This endpoint retrieves a specific company.

### HTTP Request

`GET https://app.karmacrm.com/api/v3/companies/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the company to retrieve
api_token | The token to authenticate request

## Create a Company

```shell
curl "https://app.karmacrm.com/api/v3/companies.json?api_token=oGscoGFsdS54mProUdDz" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"company":{"name":"My Company Name","background":"My Company Background","tags":["local","support"],"referral_source_id":7,"user_id":4,"emails":[{"email":"email@mycompany.com","label":"work","email_type_id":1,"position":0},{"email":"email2@mycompany.com","label":"support","email_type_id":1,"position":1}],"social_accounts":[{"name":"mycompany","social_account_type_id":"1","position":0},{"name":"mycompany","social_account_type_id":"2","position":1}],"phone_numbers":[{"number":"123-456-7890","label":"work","phone_number_type_id":1,"position":0},{"number":"321-654-0987","label":"mobile","phone_number_type_id":2,"position":1}],"addresses":[{"street":"123 A St.","city":"City","state":"ST","postal_code":"12345","country":"US","label":"work","address_type_id":1,"position":3002},{"street":"456 B St.","city":"City","state":"ST","postal_code":"12345","country":"","label":"support","address_type_id":3,"position":3008}],"websites":[{"url":"mycompanywebsite.com","label":"work","website_type_id":1,"position":0},{"url":"mycompanysupportwebsite.com","label":"support","website_type_id":1,"position":1}],"permissions":[{"accessor_id":"4","accessor_type":"User","permission":"1"},{"accessor_id":"5","accessor_type":"User","permission":"0"}],"private":true,"notify_user":false}}'
```
> Successful company creation response:

```json
{
  "id":13,
  "name":"My Company Name",
  "background":"My Company Background",
  "avatar_file_name":null,
  "private_notes":null,
  "organization_id":2,
  "referral_source_id":7,
  "user_id":4,
  "created_by_id":4,
  "industry_id":null,
  "private":true,
  "tags":["local","support"],
  "created_at":"2019-06-19T14:28:49Z",
  "updated_at":"2019-06-19T14:28:49Z",
  "emails":[
    {
      "id":34,
      "email":"email@mycompany.com",
      "email_type_id":1
    },
    {
      "id":35,
      "email":"email2@mycompany.com",
      "email_type_id":1
    }
  ],
  "websites":[
    {
      "id":16,
      "url":"mycompanywebsite.com",
      "website_type_id":1
    },
    {
      "id":17,
      "url":"mycompanysupportwebsite.com",
      "website_type_id":1
    }
  ],
  "phone_numbers":[
    {
      "id":13,
      "number":"123-456-7890",
      "phone_number_type_id":1
    },
    {
      "id":14,
      "number":"321-654-0987",
      "phone_number_type_id":2
    }
  ],
  "addresses":[
    {
      "id":12,
      "country":"US",
      "city":"City",
      "street":"123 A St.",
      "street_2":null,
      "postal_code":"12345",
      "address_type_id":1
    },
    {
      "id":13,
      "country":"",
      "city":"City",
      "street":"456 B St.",
      "street_2":null,
      "postal_code":"12345",
      "address_type_id":3
    }
  ],
  "social_accounts":[
    {
      "id":7,
      "name":"mycompany",
      "social_account_type_id":1
    },
    {
      "id":8,
      "name":"mycompany",
      "social_account_type_id":2
    }
  ],
  "field_values":[],
  "permissions":[
    {
      "id":4,
      "permission":1,
      "accessor_id":4,
      "accessor_type":"User"
    },
    {
      "id":5,
      "permission":0,
      "accessor_id":5,
      "accessor_type":"User"
    }
  ]
}
```

### HTTP Request

`POST https://app.karmacrm.com/api/v3/companies.json`

### URL Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
company[name] | Company's name
company[background] | Company's background info
company[tags] | array of company's tags i.e. `["development","usa"]`
company[referral_source_id] | ID of company's referral source
company[user_id] | ID for company's assigned user
company[addresses] | array of company's addresses, i.e. <br>`{`<br>&nbsp; `"street":"South St",`<br>&nbsp; `"city":"Chicago",`<br>&nbsp; `"state":"Illinois",`<br>&nbsp; `"country":"USA",`<br>&nbsp; `"postal_code":"60667",`<br>&nbsp; `"address_type_id": 2,`<br>&nbsp; `"label": "New Custom Label",`<br>&nbsp; `"position": 0,` (optional: adds custom label)<br>`}`
company[phone_numbers] | array of company's phone_numbers, i.e. (with optional custom label)<br> `{"number":"+7 902 4321 2123","phone_number_type_id":2,"label":"New Custom Label","position":0}`
company[emails] | array of company's emails, i.e. (with optional custom label)<br> `{"email":"john.smith@example.com","email_type_id":2,"label":"New Custom Label","position":0}`
company[social_accounts] | array of company's social accounts, i.e.<br> `{"name":"john_smith","social_account_type_id":1,"position":0}`
company[websites] | array of company's websites, i.e. (with optional custom label)<br> `{"url":"example.com","website_type_id":1,"label":"New Custom Label","position":0}`
company[field_values] | array of company's custom field values, i.e <br>`{"field_id":1,"value":"custom info"}` <br>`{"value":"5","field_id":5,"field_parent_id":2}` (with parent field)
company[permissions] | array of permission granting access to company's info i.e.<br>`{`<br>&nbsp; `"accessor_id": 4,`<br>&nbsp; `"accessor_type": "User",`<br>&nbsp; `"permission": 1`<br>}
company[private] | boolean value for whether company permissions is private

## Update a Company

```shell
curl "https://app.karmacrm.com/api/v3/companies/13.json?api_token=oGscoGFsdS54mProUdDz" \
  -X PUT \
  -H "Content-Type: application/json" \
  -d '{"id":13,"company":{"name":"My Company Name","background":"My Company Background","tags":["local","support"],"referral_source_id":7,"user_id":4,"emails":[{"id":34,"email":"email@mycompany.com","label":"work","email_type_id":1,"_destroy":false,"position":0},{"id":35,"email":"email2@mycompany.com","label":"support","email_type_id":1,"_destroy":false,"position":1}],"social_accounts":[{"id":7,"name":"mycompany","social_account_type_id":"1","_destroy":false,"position":0},{"id":8,"name":"mycompany","social_account_type_id":"2","_destroy":false,"position":1}],"phone_numbers":[{"id":13,"number":"123-456-7890","label":"work","phone_number_type_id":1,"_destroy":false,"position":0},{"id":14,"number":"321-654-0987","label":"mobile","phone_number_type_id":2,"_destroy":false,"position":1}],"addresses":[{"id":12,"street":"123 A St.","city":"City","state":"ST","postal_code":"12345","country":"US","label":"work","address_type_id":1,"_destroy":false,"position":1152},{"id":13,"street":"456 B St.","city":"City","state":"ST","postal_code":"12345","country":"","label":"support","address_type_id":3,"_destroy":false,"position":1158}],"websites":[{"id":16,"url":"mycompanywebsite.com","label":"work","website_type_id":1,"_destroy":false,"position":0},{"id":17,"url":"mycompanysupportwebsite.com","label":"support","website_type_id":1,"_destroy":false,"position":1}],"permissions":[{"id":4,"accessor_id":4,"accessor_type":"User","permission":"1"},{"id":5,"accessor_id":5,"accessor_type":"User","permission":"0"}],"private":true,"field_values":[{"value":"custom text field value","field_id":52}],"notify_user":false}}'
```

This endpoint updates a specific company.

### HTTP Request

`PUT https://app.karmacrm.com/api/v3/companies/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the company to update
api_token | The token to authenticate request

### Request Payload

Parameter | Description
--------- | -----------
company[name] | Company's name
company[background] | Company's background info
company[tags] | array of company's tags i.e. `["development","usa"]`
company[referral_source_id] | ID of company's referral source
company[user_id] | ID for company's assigned user
company[addresses] | array of company's addresses i.e. <br>`{`<br>&nbsp; `"id":4,`<br>&nbsp; `"street":"South St",`<br>&nbsp; `"city":"Chicago",`<br>&nbsp; `"state":"Illinois",`<br>&nbsp; `"country":"USA",`<br>&nbsp; `"postal_code":"60667",`<br>&nbsp; `"address_type_id": 2,`<br>&nbsp; `"label": "New Custom Label",` (optional: adds custom label)<br>&nbsp; `"_destroy": true` (optional: deletes address)<br>`}`<br>
company[phone_numbers] | array of company's phone_numbers, i.e.<br><strong>update:</strong><br> `{"id":6,"number":"+7 902 4321 2123","phone_number_type_id":2}`<br><strong>add new:</strong><br> `{"number":"+7 902 4321 2123","phone_number_type_id":2,"label":"New Custom Label"}`<br><strong>delete:</strong><br> `{"id":7,"number":"+7 902 4321 2123","phone_number_type_id":2, "_destroy":true}`
company[emails] | array of company's emails, i.e.<br><strong>update:</strong><br> `{"id":12,"email":"update.email@example.com","email_type_id":2}`<br><strong>add new:</strong><br> `{"email":"add.email  @example.com","email_type_id":2,"label":"New Label"}`<br><strong>delete:</strong><br> `{"id":14,"email":"delete.email@example.com","email_type_id":2,"_destroy":true}`
company[social_accounts] | array of company's social accounts, i.e.<br><strong>update:</strong><br> `{"id":3,"name":"update name","social_account_type_id":1}`<br><strong>add new:</strong><br> `{name":"new name","social_account_type_id":3}`<br><strong>delete:</strong><br> `{"id":3,"name":"delete name","social_account_type_id":1,"_delete":true}`
company[websites] | array of company's websites, i.e.<br><strong>update:</strong><br> `{"id":4,"url":"update.com","website_type_id":2}`<br><strong>add new:</strong><br> `{"url":"addnew.com","website_type_id":1, 'New Label'}`<br><strong>delete:</strong><br> `{"id":6,"url":"delete.com","website_type_id":1, "_destroy":true}`
company[field_values] | array of company's custom field values, i.e<br><strong>update:</strong><br> `{"id":7,"field_id":1,"value":"update value for text field"}`<br><strong>add/check new (checkbox choice):</strong><br> `{"value":"5","field_id":5,"field_parent_id":2}`<br>
company[permissions] | array of permission granting access to company's info i.e.<br>`{`<br>&nbsp; `"id":1,`<br>&nbsp; `"accessor_id": 4,`<br>&nbsp; `"accessor_type": "User",`<br>&nbsp; `"permission": 1`<br>&nbsp; `"_destroy": true` (optional: deletes permission)<br>`}`

### Return Codes

Code | Description
---- | -----------
204 |  No content

## Delete a Company

```shell
curl "https://app.karmacrm.com/api/v2/companies/27.json?api_token=oGscoGFsdS54mProUdDz"
  -X DELETE \
  -H "Content-Type: application/json"
```

This endpoint deletes a specific company.

### HTTP Request

`DELETE https://app.karmacrm.com/api/v2/companies/<ID>.json`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the company to delete
api_token | The token to authenticate request

### Return Codes

Code | Description
---- | -----------
204 |  No content
