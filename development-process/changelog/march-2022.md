# March 2022

## Removal of dummy data charts - 03/24/2022

{% file src="../../.gitbook/assets/wazimap-ng.webflow (removal-of-dummy-data-03242022-reupload).zip" %}

Changelog:

* Removed ".bar-chart" from ".indicator-chart" to prevent it from accidentally ending up in production.
* Changed all styles panel text to "Loading..." where there was any risk of it ending up in production.
