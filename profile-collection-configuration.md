# Profile Collection Configuration

Configuration of the theme points can be set using the `Configuration` field of profile collections e.g. [https://staging.wazimap-ng.openup.org.za/admin/points/profilecategory/580/change/](https://staging.wazimap-ng.openup.org.za/admin/points/profilecategory/580/change/)

### Filterable Fields

For a point attribute to be filterable, it needs to be included in `filterable_fields` array of the configuration. In default none of the fields are filterable

```
  "filterable_fields": [
    "campus"
  ]
```

![](<.gitbook/assets/image (83).png>)

The values in `filterable_fields` array that are not attributes of the category will be ignored

```
  "filterable_fields": [
    "campus", "random", "values", "facility type"
  ]
```

![](<.gitbook/assets/image (84).png>)

### Field Types

We can define field type in profile collection config.\
There are 2 types of type supported currently.

* Text - renders data as text
* HTML - clean up tags according to allowed tags and renders HTML

```
"field_type": {
    "more info": "html",
    "report error": "text"
}
```

Here `more info & report error` are key for data fields in locations object.

**Allowed Tags** : `a, b, em, span, i, div, p, ul, li, ol, table, tr, td, th`

**Allowed Attrs** : `class, target, href, data-*, style`

\
How to add HTML to the data field of locations:

* File upload: Add HTML to extra fields of points upload and it will be saved in DB
* Editing location object in admin: If we want to change data for some specific location.\
  We can edit the location object in the points admin

&#x20;
