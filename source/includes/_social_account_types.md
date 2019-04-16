# Social Account Types

## Get All Social Account Types

```shell
curl "https://app.karmacrm.com/api/v2/settings/social_account_types.json?api_token=oGscoGFsdS54mProUdDz" \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "results": [
    {
      "id": 104,
      "name": "AngelList",
      "index": "angellist"
    },
    {
      "id": 1,
      "name": "Twitter",
      "index": "twitter"
    },
    {
      "id": 2,
      "name": "Facebook",
      "index": "facebook"
    },
    {
      "id": 3,
      "name": "LinkedIn",
      "index": "linkedin"
    },
    {
      "id": 4,
      "name": "Gravatar",
      "index": "gravatar"
    },
    {
      "id": 5,
      "name": "Google Plus",
      "index": "google_plus"
    },
    {
      "id": 8,
      "name": "AOLChat",
      "index": "aOLChat"
    },
    {
      "id": 10,
      "name": "Bithucket",
      "index": "bithucket"
    },
    {
      "id": 14,
      "name": "DevianArt",
      "index": ""
    },
    {
      "id": 15,
      "name": "Digg",
      "index": ""
    },
    {
      "id": 25,
      "name": "Flickr",
      "index": ""
    },
    {
      "id": 29,
      "name": "Friendster",
      "index": ""
    },
    {
      "id": 35,
      "name": "Github",
      "index": "github"
    },
    {
      "id": 4,
      "name": "Gravatar",
      "index": "gravatar"
    },
    {
      "id": 105,
      "name": "Instagram",
      "index": "instagram"
    },
    {
      "id": 49,
      "name": "Imdb",
      "index": ""
    },
    {
      "id": 54,
      "name": "Lastfm",
      "index": ""
    },
    {
      "id": 56,
      "name": "Livejournal",
      "index": ""
    },
    {
      "id": 58,
      "name": "Meetup",
      "index": ""
    },
    {
      "id": 63,
      "name": "Myspace",
      "index": ""
    },
    {
      "id": 66,
      "name": "Other",
      "index": ""
    },
    {
      "id": 67,
      "name": "Pandora",
      "index": ""
    },
    {
      "id": 68,
      "name": "Picasa",
      "index": ""
    },
    {
      "id": 70,
      "name": "Pinterest",
      "index": ""
    },
    {
      "id": 76,
      "name": "Quora",
      "index": ""
    },
    {
      "id": 77,
      "name": "Reddit",
      "index": ""
    },
    {
      "id": 80,
      "name": "Scribd",
      "index": ""
    },
    {
      "id": 82,
      "name": "Skype",
      "index": "skype"
    },
    {
      "id": 85,
      "name": "Soundcloud",
      "index": ""
    },
    {
      "id": 87,
      "name": "Stackoverflow",
      "index": ""
    },
    {
      "id": 92,
      "name": "Tumblr",
      "index": ""
    },
    {
      "id": 96,
      "name": "Vimeo",
      "index": ""
    },
    {
      "id": 98,
      "name": "Wordpress",
      "index": ""
    },
    {
      "id": 100,
      "name": "Yahoo",
      "index": "Yahoo"
    },
    {
      "id": 102,
      "name": "Yelp",
      "index": "Yelp"
    },
    {
      "id": 103,
      "name": "YouTube",
      "index": "youtube"
    }
  ],
  "total_count": 101,
  "timestamp": 1552263193
}
```

This endpoint retrieves all social account types.

### HTTP Request
`GET https://app.karmacrm.com/api/v2/settings/social_account_types.json`

### Query Parameters

Parameter | Description
--------- | -----------
api_token | The token to authenticate request
