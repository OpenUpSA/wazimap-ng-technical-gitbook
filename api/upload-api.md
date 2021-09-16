---
description: How to upload new and update existing datasets
---

# Upload API

### Authorization

Authoritation is done in the header via an user-based token. The token can be generated via the Admin Interface

```text
Authorization : Token yourtoken
```

{% api-method method="post" host="" path="/api/v1/datasets/" %}
{% api-method-summary %}
Create new dataset
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="file" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="profile" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Update existing dataset

```text
POST /api/v1/datasets/:id/upload/
```

#### Parameters

| Name | Description | required |
| :--- | :--- | :--- |
| file | the file you want to update | True |
| update | not just update the dataset but also update the corresponding Indicator Data | False |
| overwrite | remove the previous data \(including the Indicator Data\) and replace with new data from dataset | False |

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
curl --location --request POST 'http://production.wazimap-ng.openup.org.za/api/v1/datasets/84/upload/' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Token yourtoken' \
--form 'file=@/covid_next.csv' \
--form 'update=True' \
--form 'overwrite=True'
```



