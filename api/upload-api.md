---
description: How to upload new and update existing datasets
---

# Upload API

### Authorization

Authoritation is done in the header via an user-based token. The token can be generated via the Admin Interface

```
Authorization : Token yourtoken
```

## Create new dataset

<mark style="color:green;">`POST`</mark> `/api/v1/datasets/`

#### Headers

| Name          | Type   | Description |
| ------------- | ------ | ----------- |
| Authorization | string |             |

#### Request Body

| Name    | Type   | Description |
| ------- | ------ | ----------- |
| file    | string |             |
| profile | string |             |

{% tabs %}
{% tab title="200 " %}
```
```
{% endtab %}
{% endtabs %}

### Update existing dataset

```
POST /api/v1/datasets/:id/upload/
```

#### Parameters

| Name      | Description                                                                                    | required |
| --------- | ---------------------------------------------------------------------------------------------- | -------- |
| file      | the file you want to update                                                                    | True     |
| update    | not just update the dataset but also update the corresponding Indicator Data                   | False    |
| overwrite | remove the previous data (including the Indicator Data) and replace with new data from dataset | False    |

#### Example Response

```javascript
{
    "id": 78,
    "created": "2021-04-28T09:57:01+0000",
    "updated": "2021-04-28T09:57:10+0000",
    "name": "Cases",
    "groups": [
        "date"
    ],
    "permission_type": "private",
    "profile": 1,
    "geography_hierarchy": 1,
    "upload_task_id": "44ceb2d8acd04343bbcb7ca8f0468b6c",
}
```

#### Example

```bash
curl --location --request POST 'http://api.wazimap.com/api/v1/datasets/84/upload/' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Token yourtoken' \
--form 'file=@/covid_next.csv' \
--form 'update=True' \
--form 'overwrite=True'
```

