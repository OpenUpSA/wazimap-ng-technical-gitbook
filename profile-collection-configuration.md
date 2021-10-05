# Profile Collection Configuration

Configuration of the theme points can be set using the `Configuration` field of profile collections e.g. [https://staging.wazimap-ng.openup.org.za/admin/points/profilecategory/580/change/](https://staging.wazimap-ng.openup.org.za/admin/points/profilecategory/580/change/)

### Filterable Fields

For a point attribute to be filterable, it needs to be included in `filterable_fields` array of the configuration. In default none of the fields are filterable

```text
  "filterable_fields": [
    "campus"
  ]
```

![](.gitbook/assets/image%20%2883%29.png)

The values in `filterable_fields` array that are not attributes of the category will be ignored

```text
  "filterable_fields": [
    "campus", "random", "values", "facility type"
  ]
```

![](.gitbook/assets/image%20%2884%29.png)

