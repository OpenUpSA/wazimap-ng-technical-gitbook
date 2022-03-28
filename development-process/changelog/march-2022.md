# March 2022

## Remove dummy tutorial content - 03/28/2022

{% file src="../../.gitbook/assets/wazimap-ng.webflow (remove-tutorial-dummy - 03282022).zip" %}

Changelog:

* Created "tutorial-modal--v2" and replaced all dummy content with "Loading..."
* Created "tutorial\_\_slide-image--v2" and removed the default background image.
* Left the same number of slides to not break the JS.
* Removed "municipality" dummy text from ".map-tooltip\_\_geography-chip"
* Removed "location type" dummy text from ".location-tag\_\_type"

![](<../../.gitbook/assets/image (63).png>)

![](<../../.gitbook/assets/image (61).png>)

![](<../../.gitbook/assets/image (62).png>)

## Removal of dummy data charts - 03/24/2022

{% file src="../../.gitbook/assets/wazimap-ng.webflow (removal-of-dummy-data-03242022-reupload).zip" %}

Changelog:

* Removed ".bar-chart" from ".indicator-chart" to prevent it from accidentally ending up in production.
* Changed all styles panel text to "Loading..." where there was any risk of it ending up in production.
