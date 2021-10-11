# Changing the Geography level name

If a geography label needs to change, e.g. Districts => Districts and Metros, follow the following steps:

1. `Geography.objects.filter(level="district", version="2011 Boundaries").update(level="Districts and Metros")`Make sure you select the appropriate version
2. Change the preferred_children object in the Profile configuration json for each profile that uses that geography hierarchy, e.g.:

```
"preferred_children": {
    "country": [
      "province"
    ],
    "province": [
      "Districts and Metros",
      "municipality"
    ],
    "mainplace": [
      "subplace"
    ],
    "municipality": [
      "mainplace",
      "ward"
    ],
    "Districts and Metros": [
      "municipality",
      "mainplace",
      "ward"
    ]
  }
```

3\. from a python terminal run the following: `from django.core.cache import cache; cache.clear()`

Done
