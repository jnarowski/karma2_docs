# Authorizations

## Get all authorizations

```shell
curl "https://app.karmacrm.com/api/v2/settings/integrations.json?api_token=oGscoGFsdS54mProUdDz" 
```

> Successful response

```json
[
  {
    "last_synced_at_formatted": "Monday Apr, 22nd at  9:06am",
    "id": 1,
    "user_id": 4,
    "provider": "nylas_mailman",
    "uid": "khulani@karmacrm.com",
    "created_at": "2019-03-12T14:21:46-06:00",
    "updated_at": "2019-05-13T10:52:47-06:00",
    "token": "mJKFXxe6PXexkVM2fse5FHu3JrVK9r",
    "secret": null,
    "account": "khulani@karmacrm.com",
    "organization_id": 2,
    "settings": {
      "send_copy": null,
      "signature": null,
      "open_tracking": true,
      "click_tracking": null,
      "incoming_emails_enabled": true,
      "outgoing_emails_enabled": true,
      "import_past_emails": false,
      "incoming_emails_notifications_enabled": null,
      "privacy": "private"
    },
    "active": true,
    "refreshing": false,
    "last_synced_at": "2019-04-22T09:06:56-06:00",
    "error_message": "{\"incoming\":null,\"outgoing\":null}",
    "refresh_token": "rwlesmklasdwapp6zizx1fo9",
    "old_entity_id": null,
    "position": 0,
    "error_code": null,
    "domain": null,
    "private": null,
    "contextio_account_id": "7642p8a4ciwbfs5tl0qkd7dmk",
    "contextio_source_label": null,
    "state": null,
    "timestamp": null
  },
  {
    "last_synced_at_formatted": "Tuesday Mar, 19th at 11:51am",
    "id": 2,
    "user_id": 4,
    "provider": "google_contacts",
    "uid": "109333742401691400392",
    "created_at": "2019-03-19T10:37:50-06:00",
    "updated_at": "2019-03-19T11:51:28-06:00",
    "token": "ya67.GlvRBqzYwxjnncMqf3PB_6FPd3xsdXlfnoWRvwrKhjqSUUhiaIvY1bLhiQJIxJ9EI2yufMUOZeFY7DciVq89TiAWaecZtUHKmZHBZpq8zTR3Yj2sHSDJGxkTtq7_",
    "secret": null,
    "account": "khulani@karmacrm.com",
    "organization_id": 2,
    "settings": {
      "google_contact_groups": [
        {
          "href": "http://www.google.com/m8/feeds/groups/khulani%40karmacrm.com/base/6",
          "title": "System Group: My Contacts",
          "content": "System Group: My Contacts"
        },
        {
          "href": "http://www.google.com/m8/feeds/groups/khulani%40karmacrm.com/base/d",
          "title": "System Group: Friends",
          "content": "System Group: Friends"
        },
        {
          "href": "http://www.google.com/m8/feeds/groups/khulani%40karmacrm.com/base/e",
          "title": "System Group: Family",
          "content": "System Group: Family"
        },
        {
          "href": "http://www.google.com/m8/feeds/groups/khulani%40karmacrm.com/base/f",
          "title": "System Group: Coworkers",
          "content": "System Group: Coworkers"
        }
      ],
      "selected_google_contact_groups": [
        "http://www.google.com/m8/feeds/groups/khulani%40karmacrm.com/base/6"
      ],
      "sync_method": "import"
    },
    "active": true,
    "refreshing": false,
    "last_synced_at": "2019-03-19T11:51:26-06:00",
    "error_message": null,
    "refresh_token": "1/JgVweYDDFWs5biaukM4ndi0vK4V_mfvzXbyEa5RjTpjJuryp3KoLhhuEWSSF_pxz",
    "old_entity_id": null,
    "position": 0,
    "error_code": null,
    "domain": null,
    "private": null,
    "contextio_account_id": null,
    "contextio_source_label": null,
    "state": null,
    "timestamp": null
  },
  {
    "id": 3,
    "user_id": 4,
    "provider": "sparkpost",
    "uid": null,
    "created_at": "2019-04-08T15:53:09-06:00",
    "updated_at": "2019-04-08T15:53:09-06:00",
    "token": null,
    "secret": null,
    "account": null,
    "organization_id": 2,
    "settings": null,
    "active": true,
    "refreshing": false,
    "last_synced_at": null,
    "error_message": null,
    "refresh_token": null,
    "old_entity_id": null,
    "position": 0,
    "error_code": null,
    "domain": null,
    "private": null,
    "contextio_account_id": null,
    "contextio_source_label": null,
    "state": null,
    "timestamp": null
  },
  {
    "id": 6,
    "user_id": 4,
    "provider": "mailchimp",
    "uid": "14fe08de6b94402fef9b9ecdc",
    "created_at": "2019-04-25T07:13:31-06:00",
    "updated_at": "2019-04-25T07:13:31-06:00",
    "token": "748340185da250c1021661bc0a6147ac",
    "secret": null,
    "account": "khulani@karmacrm.com",
    "organization_id": 2,
    "settings": {
      "api_endpoint": "https://us20.api.mailchimp.com"
    },
    "active": true,
    "refreshing": false,
    "last_synced_at": null,
    "error_message": null,
    "refresh_token": null,
    "old_entity_id": null,
    "position": 0,
    "error_code": null,
    "domain": null,
    "private": null,
    "contextio_account_id": null,
    "contextio_source_label": null,
    "state": null,
    "timestamp": null
  }
]
```

This endpoint gets authorizations.

### HTTP Request
`GET https://app.karmacrm.com/api/v2/settings/integrations.json`

### Query Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request
