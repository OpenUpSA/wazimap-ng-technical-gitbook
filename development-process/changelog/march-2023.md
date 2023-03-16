# March 2023

### 2023/03/16 - Location tag scroll bar fix

{% file src="../../.gitbook/assets/wazimap-ng.webflow (location-bar-scroll-fix).zip" %}

* Adjusted the alignment of the "map-location\_\_tags" to fix the scrolling issue on mobile
* Adjusted the width of "location-highlight" to not be a fixed width and cause wrapping issues

### 2023/03/15 - Various mobile changes

{% file src="../../.gitbook/assets/wazimap-ng.webflow (various-mobile-changes-updated-3).zip" %}

* Made map location chips panel overflow with items aligned right so that the current filter shows first
* Made the .map-bottom-items and map-bottoms-items have a the correct width and padding to make sure its contents does not overlap with other items on small screens. The only thing i couldnt test was whether the zoom buttons are working fine after this change. This seemed like a better way of handling the “map-options” change suggested as this would ensure no items in that parent div overlap rather than just 1.
* Positioning of the left side panel toggles is fixed on may side, they are lower and dont hit the map location chips
* Changed the position of the geo select and its z index. This should be changed to be more dynamic and responsive to the state of other items at the bottom, but for not it should make the mobile experience better.
* Set max width on rich data content as per suggestion.
