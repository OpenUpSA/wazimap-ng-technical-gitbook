# December 2021

## Map panels update - 12/10/2021

{% file src="../../.gitbook/assets/wazimap-ng.webflow (map-panels - 12102021).zip" %}

#### Changes:

* Added map-bottom-items--v2 version with updated functionality and styling
* Removed various leaflet styling code from the webflow side
* Removed webflow interactions for opening and closing map option panels. Now controlled by devs using hidden classes.

## Various changes - 12/03/2021

{% file src="../../.gitbook/assets/wazimap-ng.webflow (various-changes-12032021).zip" %}

#### Map credit:

![Map credit in the bottom left corner.](<../../.gitbook/assets/image (45).png>)

* Added .map-credit to .map.
* This item is shown by default and the link directs to Wazimap NG product page.

#### Point filters: <a href="#changes" id="changes"></a>

![Point filters closed by default](<../../.gitbook/assets/image (56).png>)

* Added `.is--shown` and `.is--hidden` for the `.point-filters_content` element.
* Backend should toggle this to open and close the modal.
* Backend needs to hide show the arrow icons on the right hand side since this was controlled by interaction before.
* The `.is--hidden` class is applied as default.
* Removed the interaction that used to hide and show this content.
* Added `.point-filters__no-data` to the `.point-filters_content` block for when there is no data available.

#### Data mapper:

![](<../../.gitbook/assets/image (42).png>)

* Added `.map-options__no-data` to the `.map-options__filters_content`
* `.map-options__no-data` is hidden by default





