# Point data API

Point data is arranged in the following structure below a given Wazimap NG Profile:

* Themes
  * Categories
    * Points

A common way to fetch points is to

1. Fetch the point themes for a profile, which includes their categories
2. Fetch the points in a category.

Example themes:

![](../.gitbook/assets/screenshot\_2021-08-26\_15-03-42.png)

Example point categories

![](../.gitbook/assets/screenshot\_2021-08-26\_15-03-53.png)

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

{% swagger baseUrl="https://production.wazimap-ng.openup.org.za" path="/api/v1/profiles/" method="get" summary="Fetch Profile ID" %}
{% swagger-description %}
Profile id is required to make requests to points API.

\


Get the ID of the profile from the Profile list.
{% endswagger-description %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

| Field                   | Detail                                                                                                         |
| ----------------------- | -------------------------------------------------------------------------------------------------------------- |
| id                      | ID of the Profile                                                                                              |
| name                    | Profile Name                                                                                                   |
| permission_type         | Public \| Private - Profile Admin can specify which type of user should be able to view data linked to profile |
| requires_authentication | Boolean - Decides if the user needs authentication to view data                                                |
| geography_hierarchy     | Hierarchy for the Profile                                                                                      |
| description             | TextField - Contains short intro about Profile                                                                 |
| configuration           | Profile configurations set up by profile admin                                                                 |

{% swagger baseUrl="https://production.wazimap-ng.openup.org.za/" path="api/v1/profile/:profile_id/points/themes/" method="get" summary="Get Themes for a Profile" %}
{% swagger-description %}
This API endpoint will return all Themes that are linked to specific Profile

\


A Profile can be linked to multiple themes and Themes contains multiple categories.

\




\


Example request:

\




`GET https://production.wazimap-ng.openup.org.za/api/v1/profile/8/points/themes/`

\



{% endswagger-description %}

{% swagger-parameter in="path" name="profile_id" type="number" %}
ID of the profile
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

| Field      | Description                                                                       |
| ---------- | --------------------------------------------------------------------------------- |
| ID         | Theme ID                                                                          |
| name       | Name of the Theme                                                                 |
| icon       | Icon used to display on Theme                                                     |
| order      | Order in which themes are displayed in UI                                         |
| profile    | ID of the Linked Profile                                                          |
| categories | List of sub-data that displays more information and points available for a Theme  |

{% swagger baseUrl="https://production.wazimap-ng.openup.org.za/" path="api/v1/profile/:profile_id/points/theme/:theme_id/profile_categories/" method="get" summary="Get Categories for a Theme" %}
{% swagger-description %}
Get all categories under a Theme
{% endswagger-description %}

{% swagger-parameter in="path" name="profile_id" type="number" %}
ID of the Profile
{% endswagger-parameter %}

{% swagger-parameter in="path" name="theme_id" type="number" %}
ID of the theme
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

| Field       | Description                                |
| ----------- | ------------------------------------------ |
| ID          | Category ID                                |
| name        | Name of category                           |
| description | Description to explain info about category |
| theme       | Linked Theme obj Details                   |
| Metadata    | Information about the source of data       |

{% swagger baseUrl="https://production.wazimap-ng.openup.org.za/" path="api/v1/profile/:profile_id/points/category/:category_id/points/" method="get" summary="Get Points for a Category" %}
{% swagger-description %}
Get coordinates and location details for a category.

\


Example request:

\




`GET https://production.wazimap-ng.openup.org.za/api/v1/profile/8/points/category/578/points/`
{% endswagger-description %}

{% swagger-parameter in="path" name="profile_id" type="number" %}
ID of the Profile
{% endswagger-parameter %}

{% swagger-parameter in="path" name="category_id" type="number" %}
ID of the Category
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

| Field                 | Description                                                                                                                                                                                                                                                          |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| features              | List of coordinates inside a category                                                                                                                                                                                                                                |
| features > id         | Location ID                                                                                                                                                                                                                                                          |
| features > geometry   | Coordinate details for a Location                                                                                                                                                                                                                                    |
| features > properties | <p>Data associated with coordinates. It can include anything profile admin wants to display in association with location. ex: Name, Phone number, Detailed address etc.</p><p>There is also option for profile admin to have url and image in feature properties</p> |

{% swagger baseUrl="https://production.wazimap-ng.openup.org.za/" path="api/v1/profile/:profile_id/points/geography/:geography_code/points/" method="get" summary="Get Categories & Points for a Geography" %}
{% swagger-description %}
Get points within a Geography.

\


API returns Categories within Geography with all the points associated with specific Category inside requested Geo Code
{% endswagger-description %}

{% swagger-parameter in="path" name="profile_id" type="number" %}
ID of the profile
{% endswagger-parameter %}

{% swagger-parameter in="path" name="geography_code" type="string" %}
Geo Code for Geography
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

| Field              | Description                                                    |
| ------------------ | -------------------------------------------------------------- |
| count              | Total Number of Categories with in a Geography                 |
| results            | List of Detailed points collection for Categories              |
| results > category | Category Name                                                  |
| results > features | List of locations with details for a category within Geography |

{% swagger baseUrl="https://production.wazimap-ng.openup.org.za/" path="api/v1/profile/:profile_id/points/category/:category_id/geography/:geography_code/points/" method="get" summary="Get Points for a Category within a Geography" %}
{% swagger-description %}
Get all Points for a Category within a specific Geo Code
{% endswagger-description %}

{% swagger-parameter in="path" name="profile_id" type="number" %}
ID of the Profile
{% endswagger-parameter %}

{% swagger-parameter in="path" name="category_id" type="number" %}
ID for the Category
{% endswagger-parameter %}

{% swagger-parameter in="path" name="geography_code" type="string" %}
Geo Code for Geography
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}
