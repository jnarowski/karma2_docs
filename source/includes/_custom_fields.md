# Custom Fields

## Custom Text Field - Create

Create a resource with a custom text field

```
{
  "contact" : {
    ...
    "field_values": [
      ...
      {
        "field_id": 1,
        "value": "custom text value"
      },
      ...
    ]
    ...
  }
}
```

> Response object

```
{
  "id": 38,
  ...
  "field_values": [
    ...
    {
      "id": 45,
      "field_id": 1,
      "field_type_id": 5,
      "field_parent_id": null,
      "value": "custom text value"
    },
    ...
  ],
  ...
}
```

### Request Payload

Parameter | Description
--------- | -----------
field_id | id of custom text field
value | value for custom text field

## Custom Text Field - Update

Update a resource with a custom text field

```
{
  "contact" : {
    ...
    "field_values": [
      ...
      {
        "id": 45,
        "value": "custom text value update",
        "field_id": 1
      },
      ...
    ],
    ...
  }
}
```

> Response

```
204 No Content
```

### Request Payload

Parameter | Description
--------- | -----------
id | id of custom text value
field_id | id of custom text field
value | value for custom text field


## Custom Checkbox - Create

Create a resource with a custom checkbox

```
{
  "contact" : {
    ...
    "field_values": [
      ...
      {
        "value": "4",
        "field_id": 4,
        "field_parent_id": 2
      },
      {
        "value": "5",
        "field_id": 5,
        "field_parent_id": 2
      ,
      ...
    ]
    ...
  }
}
```

> Response object

```
{
  "id": 38,
  ...
  "field_values": [
    ...
    {
      "id": 46,
      "field_id": 4,
      "field_type_id": 3,
      "field_parent_id": 2,
      "value": 4
    },
    {
      "id": 47,
      "field_id": 5,
      "field_type_id": 3,
      "field_parent_id": 2,
      "value": 5
    },
    ...
  ],
  ...
}
```

### Request Payload

Parameter | Description
--------- | -----------
field_id | id of custom checkbox selection
field_parent_id | id of custom checkbox field
value | value for custom checkbox selection

## Custom Checkbox - Update

Update a resource with a custom checkbox

```
{
  "contact" : {
    ...
    "field_values": [
      ...
      {
        "value": "3",
        "field_id": 3,
        "field_parent_id": 2
      },
      {
        "id": 46,
        "value": "4",
        "field_id": 1,
        "field_parent_id": 2,
        "_destroy": true
      },
      {
        "id": 47,
        "value":" 5",
        "field_id": 5,
        "field_parent_id": 2
      },
      ...
    ],
    ...
  }
}
```

> Response

```
204 No Content
```

### Request Payload

Parameter | Description
--------- | -----------
id | id of checkbox field record
field_id | id of custom checkbox selection
field_parent_id | id of custom checkbox field
value | value for custom checkbox selection
\_destroy | boolean to uncheck checkbox selection

## Custom Date Field - Create

Create a resource with a custom text field

```
{
  "contact" : {
    ...
    "field_values": [
      ...
      {
        "field_id": 6,
        "value": "2019-04-24"
      },
      ...
    ]
    ...
  }
}
```

> Response object

```
{
  "id": 38,
  ...
  "field_values": [
    ...
    {
      "id": 48,
      "field_id": 6,
      "field_type_id": 7,
      "field_parent_id": null,
      "value": "2019-04-24"
    },
    ...
  ],
  ...
}
```

### Request Payload

Parameter | Description
--------- | -----------
field_id | id of custom date field
value | value for custom date field

## Custom Date Field - Update

Update a resource with a custom date field

```
{
  "contact" : {
    ...
    "field_values": [
      ...
      {
        "id": 48,
        "value": "2019-04-25",
        "field_id": 6
      },
      ...
    ],
    ...
  }
}
```

> Response

```
204 No Content
```

### Request Payload

Parameter | Description
--------- | -----------
id | id of custom date record
field_id | id of custom date field
value | value for custom date field

## Custom Text Area Field - Create

Create a resource with a custom text area field

```
{
  "contact" : {
    ...
    "field_values": [
      ...
      {
        "field_id": 15,
        "value": "custom text area value"
      },
      ...
    ]
    ...
  }
}
```

> Response object

```
{
  "id": 38,
  ...
  "field_values": [
    ...
    {
      "id": 49,
      "field_id": 15,
      "field_type_id": 4,
      "field_parent_id": null,
      "value": "custom text area value"
    },
    ...
  ],
  ...
}
```

### Request Payload

Parameter | Description
--------- | -----------
field_id | id of custom text area field
value | value for custom text area field

## Custom Text Area Field - Update

Update a resource with a custom text area field

```
{
  "contact" : {
    ...
    "field_values": [
      ...
      {
        "id": 49,
        "value": "custom text area value update",
        "field_id": 15
      },
      ...
    ],
    ...
  }
}
```

> Response

```
204 No Content
```

### Request Payload

Parameter | Description
--------- | -----------
id | id of custom text area record
field_id | id of custom text area field
value | value for custom text area field

## Custom Currency Field - Create

Create a resource with a custom currency field

```
{
  "contact" : {
    ...
    "field_values":[
      ...
      {
        "value": "13",
        "field_id": 17
      },
      ...
    ]
    ...
  }
}
```

> Response object

```
{
  "id": 38,
  ...
  "field_values": [
    ...
    {
      "id": 50,
      "field_id": 17,
      "field_type_id": 8,
      "field_parent_id": null,
      "value": "13"
    },
    ...
  ],
  ...
}
```

### Request Payload

Parameter | Description
--------- | -----------
field_id | id of custom currency field
value | value for custom currency field

## Custom Currency Field - Update

Update a resource with a custom currency field

```
{
  "contact" : {
    ...
    "field_values": [
      ...
      {
        "id": 50,
        "value": "15",
        "field_id": 17
      }
      ...
    ],
    ...
  }
}
```

> Response

```
204 No Content
```

### Request Payload

Parameter | Description
--------- | -----------
id | id of custom currency record
field_id | id of custom currency field
value | value for custom currency field

## Custom Select Field - Create

Create a resource with a custom select field

```
{
  "contact" : {
    ...
    "field_values":[
      ...
      {
        "value": "13",
        "field_id": 13,
        "field_parent_id": 11
      },
      ...
    ]
    ...
  }
}
```

> Response object

```
{
  "id": 38,
  ...
  "field_values": [
    ...
    {
      "id": 51,
      "field_id": 13,
      "field_type_id": 2,
      "field_parent_id": 11,
      "value": 13
    },
    ...
  ],
  ...
}
```

### Request Payload

Parameter | Description
--------- | -----------
field_id | id of custom select selection
field_parent_id | id of custom select field
value | value for custom checkbox selection

## Custom Select Field - Update

Update a resource with a custom select field

```
{
  "contact" : {
    ...
    "field_values": [
      ...
      {
        "id": 51,
        "value": "12",
        "field_id": 12,
        "field_parent_id": 11
      }
      ...
    ],
    ...
  }
}
```

> Response

```
204 No Content
```

### Request Payload

Parameter | Description
--------- | -----------
id | id of custom select record
field_id | id of custom select selection
field_parent_id | id of custom select field
value | value for custom checkbox selection
\_destroy | boolean to unselect a selection
