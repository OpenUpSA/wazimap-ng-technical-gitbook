---
description: Shapefiles to load geographies and boundaries into geography hierarchies
---

# Geographies/Shapefiles

These are already simplified and have the right fields to import to Wazimap.

See [the tutorial for how to format with the appropriate attributes and simplify shapefiles](tutorials/loading-new-geographies.md) similarly.

## South Africa 2020 demarcation

The zip file says 2021 because that's the election when it took effect but the files are labeled 2020 because that's when the changes were announced by the demarcation board.

* ZA
* Provinces
* Districts - district and metro municipalities
* LocalMuni
* Wards

Attributes

* Name
* Code
* Parent\_cod
* Area

{% file src=".gitbook/assets/2021-demarcation.zip" %}

## South Africa 2016 demarcation

* za - parent is NULL to make it a root in the hierarchy
* pr
* dc - district and metro municipalities
* local-mn
* Wards\_2016_\__geomfix

Attributes

* code
* `parent_cod` except ZA which has `parent`
* name
* area

{% file src=".gitbook/assets/2016-demarcation.zip" %}

## South Africa 2011 demarcation

## Equal area hexagons (Uber H3 resolution 7)

Attributes:

* code
* parent\_cod
* area
* name

Resolution 7 hexagons.

Only hexagons overlapping with metros in the South Africa 2016 demarcation are included.

The metro with the greatest overlapping area was selected when multiple options were available using the _QGIS Processing Toolbox > Join Attributes by location_ tool.

<figure><img src=".gitbook/assets/Screenshot_2022-09-16_16-06-43.png" alt=""><figcaption></figcaption></figure>

{% file src=".gitbook/assets/hexagons-metro-children (1).zip" %}

&#x20;
