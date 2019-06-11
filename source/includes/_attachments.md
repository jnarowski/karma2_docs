# Attachments

## Download an Attachment

```shell
curl "https://app.karmacrm.com/api/v2/assets/5/download?api_token=oGscoGFsdS54mProUdDz" 
```

This endpoint downloads a specific file attachment.

### HTTP Request
`GET https://app.karmacrm.com/api/v2/assets/5/download`

### Query Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

## Create an Attachment

```shell
curl "https://app.karmacrm.com/api/v2/attachments" \
  -X POST \
  -H "Content-Type: multipart/form-data" \
  -F "attachment[record_type]=Contact" \
  -F "attachment[record_id]=5" \
  -F "attachment[file]=@/home/user1/Desktop/photo.jpeg"
```
> Successful attachment creation response:

```json
{
  "id": 11,
  "asset_id": 10,
  "uuid": null,
  "class_name": "Attachment",
  "name": null,
  "description": null,
  "data_file_name": "photo.jpeg",
  "data_file_size": 280930,
  "data_content_type": "image/jpeg",
  "created_at": "2019-05-28T14:17:10-06:00",
  "private": false,
  "created_at_formatted": "05/28/2019"
}
```

### HTTP Request

`POST https://app.karmacrm.com/api/v2/attachments`

### URL Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request

### Form Data

Parameter | Description
--------- | -----------
attachment[record_type] | Type of record associated w/ attachment i.e. Contact
attachment[record_id] | ID of Record associated w/ attachment
attachment[file] | File being attached (binary)

## Delete an Attachment

```shell
curl "https://app.karmacrm.com/api/v2/attachments/27?api_token=oGscoGFsdS54mProUdDz" \
  -X DELETE 
```

This endpoint deletes a specific attachment file.

### HTTP Request

`DELETE https://app.karmacrm.com/api/v2/attachments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the contact to delete
api_token | The token to authenticate request

### Return Codes

Code | Description
---- | -----------
204 |  No content
