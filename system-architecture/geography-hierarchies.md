# Geography Hierarchies

CookieMismatchThe central unit of analysis in NG is a **geography**. These represent spatial boundaries which can be associated with data that describes it. For example, a typical geography may represent a **Province**. Associated data may include demographics in the area, the crime rate, economic activity, education, or any other arbitrary data.

Geographies are related to each other in a tree-like structure (strictly a directed acyclic graph) where each geography in a **level** is either a root node or has exactly one parent.![](https://lh5.googleusercontent.com/o2p2V_Q8bl2gL48ORYc1HnyMQmyW8mqi7IColSlle1peNCyEgLc9uBT69yJdywHQq-EKQ_JWyyqXedpYZ\_\_52ajqF7vDHKRYfY6-b2lgLqkCJd2MbO80LDhrjXFucKe9OvKOn3ps)****\
****

The most common hierarchy that we use for the South African context starts with **Country** at the top. This is followed by **Provinces**, all of which are non-overlapping and completely contained with **Country**. Below **Province** we find **District**, **Municipality**, **Mainplace** and **Subplace**. Another path may be **Municipality** -> **Ward**.\
****

The assumption about the geographical hierarchy is as follows:

1. It is a directed acyclic graph (DAG)
2. Child geographies are completely contained by their parent.
3. Sibling geographies do not overlap.
4. Each geography has only one parent.\
   ****

Forks can occur at any part of the hierarchy and are dependent on the current geographical hierarchy in use. For the purpose of illustration, here is a more extensive hierarchy:\


![](https://lh4.googleusercontent.com/m_NsorMiAHrK42gcglOmNpK9HKPZgTX2vnHpTop16SKmAQtt_gcYdiNDPwFkRVkyIvFxf9b4pKSTPIYRPV16wu5kD5Opb-YLzbJe-qonldvS2Hiikwx8fKDf7qS_XxeTo_Owo-cE)

\


Each Geography in a hierarchy should have the follow four fields:

**Code** - An identifier (not necessarily unique). Where possible, this code should follow an existing standard such as the [ISO 3166](https://www.iban.com/country-codes) for countries.** **

**Boundaries** - A spatial boundary definition.

**Parent Geography** - A reference to its parent, or null if it is a root geography. This reference should use the parent’s code.

**Version **-** **For a number of reasons, boundaries may change while codes remain the same. For instance, municipal boundaries in South Africa change every 5 years based on population growth and migration patterns. In some cases, old municipalities may disappear and new ones are created. In other cases minor boundary changes are made to existing geographies. In these cases, it is important to record an identifier that reflects this ‘version’ change, even when the code remains the same.

The approach in NG is to define a geographical hierarchy which then associates the various levels. When a request is received for a particular geography, it sends a list of its children to enable drilling downwards into the hierarchy.\


## **Hierarchical Structure**

### **Not linear**

Hierarchies are not linear but are usually considered to be tree-like although strictly directed acyclic graphs. This means that one parent can have many types of levels - e.g. Municipality may have Wards and Mainplaces. These levels overlap. Less common is for a child to have multiple parent levels, e.g. A Ward can be a child of either Metro or a Municipality.

### **No universal levels**

There is no assumption that every parent level will have the same child levels. For example, when exploring a world geography, each country may have different levels specific to it. 

### **No wall-to-wall coverage**

Boundaries do not need to cover the entire area of their parent, holes are possible.

### **Multiple simultaneously display levels**

Many levels are not compatible with each other as they overlap, Wards and Mainplaces are one such example. There are however instances where they do not overlap such as Districts and Metros. In each case, it is up to the client to decide how these should be rendered.

## Technical Details

### Backend

[Treebeard](https://github.com/django-treebeard/django-treebeard) is used to manage the [**Geography**](https://github.com/OpenUpSA/wazimap-ng/blob/staging/wazimap_ng/datasets/models/geography.py) model. Then enables fast querying of hierarchies which is usually hard to do in naive SQL table structures. Spatial data is stored in [GeographyBoundary](https://github.com/OpenUpSA/wazimap-ng/blob/staging/wazimap_ng/boundaries/models.py) objects. Geographies are [serialized](https://github.com/OpenUpSA/wazimap-ng/blob/staging/wazimap_ng/boundaries/serializers.py) to GeoJSON before being served to the client. 

#### Compression

Overly detailed geographies can result in large downloads. The GeographyBoundary models uses a [CachedMultipolygonField](https://github.com/OpenUpSA/wazimap-ng/blob/staging/wazimap_ng/boundaries/models.py#L23) to automatically compress boundaries everytime the model is [saved](https://github.com/OpenUpSA/wazimap-ng/blob/staging/wazimap_ng/boundaries/fields.py#L33). Downloads are still often large and can be reduced further by converting to TopoJSON. A custom serializer needs to be written to do this. Leaflet will also need a plugin to be able to convert TopoJSON to GeoJSON.

### Frontend

**Geographies** are displayed on a Leaflet map drawn using Canvas. The client receives a `preferred_children` configuration key which provides guidance for which **level** to display when there are multiple options. For example:

```
"preferred_children": {
    "country": [
      "province"
    ],
    "district": [
      "municipality",
      "mainplace",
      "ward"
    ],
    "province": [
      "district",
      "municipality"
    ],
    "mainplace": [
      "subplace"
    ],
    "municipality": [
      "mainplace",
      "ward"
    ]
  }
```

every key represents a level, following by an ordered list of children that it can display. A **municipality** has two types of children **mainplace **and** ward. **According to this configuration, **mainplaces** should be preferred to **wards** and will be displayed as default. A toggle exists on the user interface to switch between **geographies**. If data for a particular **level **is not available then that should not be shown to the user.

## Discussions

{% content-ref url="../ngp2-presenting-geographical-hierarchies-to-users.md" %}
[ngp2-presenting-geographical-hierarchies-to-users.md](../ngp2-presenting-geographical-hierarchies-to-users.md)
{% endcontent-ref %}

{% content-ref url="../ngp3-change-geography-hierarchies.md" %}
[ngp3-change-geography-hierarchies.md](../ngp3-change-geography-hierarchies.md)
{% endcontent-ref %}

{% content-ref url="../tutorials/loading-new-geographies.md" %}
[loading-new-geographies.md](../tutorials/loading-new-geographies.md)
{% endcontent-ref %}



