# Authentication

## Sign in

```shell
curl "https://app.karmacrm.com/accounts/sign_in.json" \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"account":{"email":"user@example.com","password":"xyz"}}'
```

> Successful sign in response:

```json
{
  "activity_churn_started_at": null,
  "activity_churn_stopped_at": null,
  "avatar": {
    "url": null,
    "thumb": {
      "url": null
    },
    "medium": {
      "url": null
    },
    "large": {
      "url": null
    }
  },
  "business_phone": "555-1212",
  "clicky_token": null,
  "created_at": "2019-03-11T21:48:46Z",
  "current_user_id": 4,
  "distinct_id": "52WzU7kkugXcx85DbHtUSeh17LKmf3cfGFNADtzhUX7djXmQxzg4fG4AB9PWVS1vFo4",
  "email": "john@example.com",
  "email_type": null,
  "first_name": "John",
  "id": 4,
  "last_name": "Smith",
  "last_request_at": null,
  "locale": "en",
  "per_page": 10,
  "phone": null,
  "phone_carrier": null,
  "settings": {
    "date_format": "mm/dd/yy",
    "default_currency": "USD",
    "phone_number_app": "skype",
    "phone_number_code": null
  },
  "support_agent_id": 10794,
  "time_zone": null,
  "unread_product_updates": null,
  "updated_at": "2019-03-27T19:33:18Z",
  "use_24h_time": false,
  "version": 1,
  "current_organization_id": 2,
  "beta": false,
  "api_token": "oGscoGFsdS54mProUdDz",
  "current_user_role_name": "owner",
  "current_user_role_type": null,
  "current_user_objective": null,
  "current_user_dropbox_id": 4832250,
  "current_user_mixpanel_person_id": "yq4RvpuQW6SHoHwGa2AEz6YY7fAnQUdrfEMz96vDzkqdb5s5x_TJsx6qdk6Zg8ipv3k"
}
```

> Unsuccessful sign in response:

```json
{
  "error": "Invalid email or password."
}
```

This endpoint retrieves all contacts.

### HTTP Request
`POST https://app.karmacrm.com/accounts/sign_in.json`

### Request Payload

Parameter | Description
--------- | -----------
account[email] | User's email
account[password] | User's password
