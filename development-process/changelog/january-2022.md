# January 2022

## Class renaming - 01/18/2022

{% file src="../../.gitbook/assets/wazimap-ng.webflow (class-renaming - 01182022).zip" %}

Changed class name `.hdden` to `.hidden` for `.mapping-options__add-filter`.

## Transition CSS - 01/14/2022

{% file src="../../.gitbook/assets/wazimap-ng.webflow (transition-css-01142022).zip" %}

Added transition styling to the v2 data mapper content items and made max-height on closed !important.

## Data mapper v2 - 01/13/2022

{% file src="../../.gitbook/assets/wazimap-ng.webflow (data-mapper-v2-01132022) (2).zip" %}

![New item in the styles panel. Select data-category--v2 to use class controlled interactions](<../../.gitbook/assets/image (60).png>)

#### Changes:

* Added v2 versions of all clickable triggers and content blocks:
  * data-category\_\_h1\_trigger--v2
  * data-category\_\_h1\_content--v2
  * data-category\_\_h2\_trigger--v2
  * data-category\_\_h2\_content--v2
  * data-category\_\_h3\_trigger--v2
  * data-category\_\_h3\_content--v2

{% hint style="warning" %}
Use the class `.is--closed` on the content blocks to toggle them to closed.&#x20;
{% endhint %}

* The arrow icons in .data-category\_\_h1\_trigger--v2 is controlled by adding or removing is--closed to BOTH icons. This will hide the one and show the other.&#x20;
