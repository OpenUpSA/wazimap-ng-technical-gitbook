# Point data API

Point data is arranged in the following structure below a given Wazimap NG Profile:

* Themes
  * Categories
    * Points

A common way to fetch points is to

1. Fetch the point themes for a profile, which includes their categories
2. Fetch the points in a category.

Example themes:

![](../.gitbook/assets/screenshot_2021-08-26_15-03-42.png)

Example point categories

![](../.gitbook/assets/screenshot_2021-08-26_15-03-53.png)

{% hint style="info" %}
**Profile Collections vs Categories**

Note that what is called Profile Collections in Admin is called Categories in the points API.
{% endhint %}

{% hint style="info" %}
**Point data identifiers and updates**

Point data themes and collections are continually curated to provide the best user experience.

Avoid hard-coding theme, category and point IDs without documented agreement with profile maintainers that those will remain consistent. Rather agree on names for themes and categories, and notification procedures for updates.

To update points in-place rather than replace entire categories of points, agree on a consistent unique identifier that will be available in the point data fields with the profile administrators.
{% endhint %}

{% api-method method="get" host="https://production.wazimap-ng.openup.org.za" path="/api/v1/profiles/" %}
{% api-method-summary %}
Fetch Profile ID
{% endapi-method-summary %}

{% api-method-description %}
Profile id is required to make requests to points API.  
Get the ID of the profile from the Profile list.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "count": 2,
    "next": "https://production.wazimap-ng.openup.org.za/api/v1/profiles/?page=2",
    "previous": null,
    "results": [
        {
            "id": :profile_id,
            "name": "Profile1",
            "permission_type": "public",
            "requires_authentication": false,
            "geography_hierarchy": {
                "id": 2,
                "name": "2016 SA Boundaries",
                "root_geography": {
                    "name": "South Africa",
                    "code": "ZA",
                    "level": "country",
                    "version": "2016 Boundaries"
                },
                "description": ""
            },
            "description": "",
            "configuration": {}
        },
        {
            "id": :profile_id,
            "name": "Profile2",
            "permission_type": "public",
            "requires_authentication": false,
            "geography_hierarchy": {
                "id": 2,
                "name": "2016 SA Boundaries",
                "root_geography": {
                    "name": "South Africa",
                    "code": "ZA",
                    "level": "country",
                    "version": "2016 Boundaries"
                },
                "description": ""
            },
            "description": "",
            "configuration": {}
        },
        
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

| Field | Detail |
| :--- | :--- |
| id | ID of the Profile |
| name | Profile Name |
| permission\_type | Public \| Private - Profile Admin can specify which type of user should be able to view data linked to profile |
| requires\_authentication | Boolean - Decides if the user needs authentication to view data |
| geography\_hierarchy | Hierarchy for the Profile |
| description | TextField - Contains short intro about Profile |
| configuration | Profile configurations set up by profile admin |

{% api-method method="get" host="https://production.wazimap-ng.openup.org.za/" path="api/v1/profile/:profile\_id/points/themes/" %}
{% api-method-summary %}
Get Themes for a Profile
{% endapi-method-summary %}

{% api-method-description %}
This API endpoint will return all Themes that are linked to specific Profile  
A Profile can be linked to multiple themes and Themes contains multiple categories.  
  
Example request:  
`GET https://production.wazimap-ng.openup.org.za/api/v1/profile/8/points/themes/`  
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="profile\_id" type="number" required=true %}
ID of the profile
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
[
    {
        "id": :theme_id,
        "categories": [
            {
                "id": :category_id,
                "name": "Healthcare Facilities",
                "description": "Representation of data gathered from various sources",
                "theme": {
                    "id": :theme_id,
                    "name": "Health",
                    
                },
                "metadata": {
                    "source": "",
                    "description": "",
                    "licence": null,
                    "icon": "local_hospital"
                },
                "color": "",
                "visible_tooltip_attributes": []
            }
        ],
        "created": "2020-08-28T07:36:30+0000",
        "updated": "2021-06-08T16:30:14+0000",
        "name": "Health",
        "icon": "local_hospital",
        "order": 1    ,
        "profile": :profile_id
    },
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

| Field | Description |
| :--- | :--- |
| ID | Theme ID |
| name | Name of the Theme |
| icon | Icon used to display on Theme |
| order | Order in which themes are displayed in UI |
| profile | ID of the Linked Profile |
| categories | List of sub-data that displays more information and points available for a Theme  |

{% api-method method="get" host="https://production.wazimap-ng.openup.org.za/" path="api/v1/profile/:profile\_id/points/theme/:theme\_id/profile\_categories/" %}
{% api-method-summary %}
Get Categories for a Theme
{% endapi-method-summary %}

{% api-method-description %}
Get all categories under a Theme
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="profile\_id" type="number" required=true %}
ID of the Profile
{% endapi-method-parameter %}

{% api-method-parameter name="theme\_id" type="number" required=true %}
ID of the theme
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
[
    {
        "id": :category_id,
        "name": "Healthcare Facilities",
        "description": "Representation of data gathered from various sources",
        "theme": {
            "id": :theme_id,
            "name": "Health",
            "icon": "local_hospital"
        },
        "metadata": {
            "source": "",
            "description": "Representation of data gathered from various sources",
            "licence": null
        },
        "color": "",
        "visible_tooltip_attributes": []
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

| Field | Description |
| :--- | :--- |
| ID | Category ID |
| name | Name of category |
| description | Description to explain info about category |
| theme | Linked Theme obj Details |
| Metadata | Information about the source of data |

{% api-method method="get" host="https://production.wazimap-ng.openup.org.za/" path="api/v1/profile/:profile\_id/points/category/:category\_id/points/" %}
{% api-method-summary %}
Get Points for a Category
{% endapi-method-summary %}

{% api-method-description %}
Get coordinates and location details for a category.  
Example request:  
`GET https://production.wazimap-ng.openup.org.za/api/v1/profile/8/points/category/578/points/`
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="profile\_id" type="number" required=true %}
ID of the Profile
{% endapi-method-parameter %}

{% api-method-parameter name="category\_id" type="number" required=true %}
ID of the Category
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "type": "FeatureCollection",
    "features": [
        {
            "id": :location_id,
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    26.643601,
                    -27.748028
                ]
            },
            "properties": {
                "data": [],
                "name": "ALLANRIDGE",
                "url": null,
                "image": null
            }
        },
        {
            "id": :location_id,
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    29.110443,
                    -22.680732
                ]
            },
            "properties": {...}
        },
        {
            "id": :location_id,
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    28.131317,
                    -26.318641
                ]
            },
            "properties": {...}
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">features</td>
      <td style="text-align:left">List of coordinates inside a category</td>
    </tr>
    <tr>
      <td style="text-align:left">features &gt; id</td>
      <td style="text-align:left">Location ID</td>
    </tr>
    <tr>
      <td style="text-align:left">features &gt; geometry</td>
      <td style="text-align:left">Coordinate details for a Location</td>
    </tr>
    <tr>
      <td style="text-align:left">features &gt; properties</td>
      <td style="text-align:left">
        <p>Data associated with coordinates. It can include anything profile admin
          wants to display in association with location. ex: Name, Phone number,
          Detailed address etc.</p>
        <p>There is also option for profile admin to have url and image in feature
          properties</p>
      </td>
    </tr>
  </tbody>
</table>

{% api-method method="get" host="https://production.wazimap-ng.openup.org.za/" path="api/v1/profile/:profile\_id/points/geography/:geography\_code/points/" %}
{% api-method-summary %}
Get Categories & Points for a Geography
{% endapi-method-summary %}

{% api-method-description %}
Get points within a Geography.  
API returns Categories within Geography with all the points associated with specific Category inside requested Geo Code
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="profile\_id" type="number" required=true %}
ID of the profile
{% endapi-method-parameter %}

{% api-method-parameter name="geography\_code" type="string" required=true %}
Geo Code for Geography
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    count: 2,
    results: [
        {
            type: "FeatureCollection",
            features: [
                {
                    "id": :location_id,
                    "type": "Feature",
                    "geometry": {
                        "type": "Point",
                        "coordinates": [
                            26.643601,
                            -27.748028
                        ]
                    },
                    "properties": {...}
                },
            ],
            category: "Post Office service points"
        },
        {
            type: "FeatureCollection",
            features: [...],
            category: "SASSA Pay Points"
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

| Field | Description |
| :--- | :--- |
| count | Total Number of Categories with in a Geography |
| results | List of Detailed points collection for Categories |
| results &gt; category | Category Name |
| results &gt; features | List of locations with details for a category within Geography |

{% api-method method="get" host="https://production.wazimap-ng.openup.org.za/" path="api/v1/profile/:profile\_id/points/category/:category\_id/geography/:geography\_code/points/" %}
{% api-method-summary %}
Get Points for a Category within a Geography
{% endapi-method-summary %}

{% api-method-description %}
Get all Points for a Category within a specific Geo Code
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="profile\_id" type="number" required=true %}
ID of the Profile
{% endapi-method-parameter %}

{% api-method-parameter name="category\_id" type="number" required=true %}
ID for the Category
{% endapi-method-parameter %}

{% api-method-parameter name="geography\_code" type="string" required=true %}
Geo Code for Geography
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "type": "FeatureCollection",
    "features": [
        {
            "id": :location_id,
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    27.877098,
                    -25.800849
                ]
            },
            "properties": {
                "data": [],
                "name": "BROEDERSTROOM",
                "url": null,
                "image": null
            }
        },
        {
            "id": :location_id,
            "type": "Feature",
            "geometry":{...},
            "properties": {...}
        },
        {
            "id": :location_id,
            "type": "Feature",
            "geometry":{...},
            "properties": {...}
        }   
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

