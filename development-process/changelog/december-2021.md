# December 2021

## Various changes - 12/03/2021

{% file src="../../.gitbook/assets/wazimap-ng.webflow (various-changes-12032021).zip" %}

![Map credit in the bottom left corner.](<../../.gitbook/assets/image (90).png>)

#### Changes:

* Added .map-credit to .map.
* This item is shown by default and the link directs to Wazimap NG product page.

![Point filters closed by default with th](<../../.gitbook/assets/image (89).png>)

#### Changes: <a href="#changes" id="changes"></a>

* Added `.is--shown` and `.is--hidden` for the `.point-filters_content` element.
* Backend should toggle this to open and close the modal.
* Backend needs to hide show the arrow icons on the right hand side since this was controlled by interaction before.
* The `.is--hidden` class is applied as default.
* Removed the interaction that used to hide and show this content.
* Added `.point-filters__no-data` to the `.point-filters_content` block for when there is no data available.





