# Webflow exports & changelog

##

## 10/11/2021 - Filter truncation

{% file src="../../.gitbook/assets/wazimap-ng.webflow (truncation-fix).zip" %}
Webflow export
{% endfile %}

#### Changes:

* Added truncation to long filters
* Removed generic-modal

## 10/06/2021 - Cluster scroll fix

{% file src="../../.gitbook/assets/wazimap-ng.webflow-cluster-scroll-fix-10062021-.zip" %}
Webflow export
{% endfile %}

#### Changed:

Added a element .facility-tooltip\_\_scroll inside .facility-tooltip is--cluster which has overflow: auto to accommodate a long scrolling list.&#x20;

## 10/06/2021 - Point mapper truncation fix

{% file src="../../.gitbook/assets/wazimap-ng.webflow-pointmapper-truncation-100621-.zip" %}
Webflow export
{% endfile %}

Ensured that point mapper labels are correctly truncated.

![](<../../.gitbook/assets/image (85).png>)

## 10/01/2021 - Map data version support

{% file src="../../.gitbook/assets/wazimap-ng.webflow-indicator-version-10012021- (1).zip" %}

{% hint style="info" %}
Documentation of indicator version: [https://wazimap-ng.webflow.io/documentation#rich-data](https://wazimap-ng.webflow.io/documentation#rich-data)
{% endhint %}

{% hint style="info" %}
Documentation of highlight element: [https://wazimap-ng.webflow.io/documentation#utility](https://wazimap-ng.webflow.io/documentation#utility)
{% endhint %}

{% hint style="info" %}
Documentation of generic modal: [https://wazimap-ng.webflow.io/documentation#modals](https://wazimap-ng.webflow.io/documentation#modals)
{% endhint %}

**Generic Modal:**

![Added generic modal (.generic-modal)](<../../.gitbook/assets/image (79).png>)

![Element structure](<../../.gitbook/assets/image (78).png>)

![.profile-indicator\_\_version](<../../.gitbook/assets/image (76).png>)

{% hint style="info" %}
Documentation of indicator version: [https://wazimap-ng.webflow.io/documentation#rich-data](https://wazimap-ng.webflow.io/documentation#rich-data)
{% endhint %}

![Added highlight element that notifies users as to where they can change options in future (.highlight)](<../../.gitbook/assets/image (77).png>)

## 09/23/2021 - Facilities loading state

{% file src="../../.gitbook/assets/wazimap-ng.webflow-facilities-loading-state-fixed-2-09232021-.zip" %}

**Fixed:**

* Fixed a small bug where the facilities facet number was being pushed too far left if there was not a download button visible. Now, if the download button is hidden, the facet will align correctly with the right side of the panel. This fix was imlemented by changing the display of the parent from `display: grid` to `display: flex `

**Changed:**

* Added loading state **(hidden)** for the location facilities title (.location\_\_facilities\_title--loading)
* Added loading state **(hidden)** for hide/show facilities button (.location-facilities\_\_trigger--loading)
* Added loading state **(hidden)** for location facility block items (.location-facility\_\_item--loading)

![Loading state for title and show locations button](<../../.gitbook/assets/image (75).png>)

![location-facility\_\_item\_loading for loading indicator on each row](<../../.gitbook/assets/image (74).png>)

## 09/16/2021 - Point mapper dropdown icon colour fix

{% file src="../../.gitbook/assets/wazimap-ng.webflow-icon-colour-fix-09162021-.zip" %}
Webflow Export
{% endfile %}

#### Changed:

* Fixed what colour is automatically inherited for the point mapper dropdown headers so that it is not overridden with grey when using a theme colour.

## 09/16/2021 - Cluster tooltip

{% file src="../../.gitbook/assets/wazimap-ng.webflow-icon-colour-fix-09162021- (1).zip" %}

{% hint style="info" %}
Documentation: [https://wazimap-ng.webflow.io/documentation#tooltips](https://wazimap-ng.webflow.io/documentation#tooltips)
{% endhint %}

![](<../../.gitbook/assets/image (22).png>)

#### Added:

* `.facility-tooltip is--cluster` to the styles panel for use when clustering nearby points on the map.

## 09/15/2021 - Point mapper dropdown and filters

{% file src="../../.gitbook/assets/wazimap-ng.webflow-point-mapper-dropdown-filters-09152021-.zip" %}
Webflow export
{% endfile %}

{% hint style="info" %}
Documentation: [https://wazimap-ng.webflow.io/documentation#point-mapper](https://wazimap-ng.webflow.io/documentation#point-mapper)
{% endhint %}

#### Point mapper dropdown with toggle:

![](<../../.gitbook/assets/image (68).png>)

#### Point filters:

![](<../../.gitbook/assets/image (12).png>)

#### Changes:

* Added `.point-mapper__h1_checkbox` that is hidden by default
* Added `.point-filters panel` in `.map-bottom-items` (hidden by default)

## 08/31/2021 - Fix for tutorial modal height

{% file src="../../.gitbook/assets/wazimap-ng.webflow-tutorial-modal-fix-08312021-.zip" %}
Webflow export
{% endfile %}

#### Changes:

* Restricted max height to 90vh on the tutorial modal

![](<../../.gitbook/assets/image (37).png>)

## 08/25/2021 - Rich Data Nav Fix

{% file src="../../.gitbook/assets/wazimap-ng.webflow-richdata-nav-fix-.zip" %}
Webflow export
{% endfile %}

{% hint style="info" %}
Feature preview: [https://wazimap-ng.webflow.io/feature-previews/rich-data-nav-fix#top](https://wazimap-ng.webflow.io/feature-previews/rich-data-nav-fix#top)
{% endhint %}

Changed:

* Made the section nav scroll when height is restricted

![](<../../.gitbook/assets/image (18).png>)

## 08/12/2021 - Print CSS test&#x20;

{% file src="../../.gitbook/assets/wazimap-ng.webflow-print-css-test- (1).zip" %}
Webflow export
{% endfile %}

Changed:

* add the following code to the print css:

```css
@media print {
  .page-break-before {
    break-before: page;
  }

  body, .main, .rich-data, .rich-data-content, .rich-data-content .section, .profile-indicator{
    float: none !important;
    display: block !important;
  }

  .rich-data__print, .tab-notice{
    display: none;
  }

  .rich-data[style*="display: none;"]{
    display: none !important;
  }

  .facility-info[style*="display: none;"]{
    display: none !important;
  }

  .facility-info[style*="display: flex;"]{
    display: inline-table;
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    background-color: #fff;
    max-height: 100%;
    max-width: 100%;
  }

  .facility-info__view-google-map, .facility-info__print, .facility-info__close{
    display: none;
  }
}
```



## 07/19/2021- Point-legend, table margin, z-depth bottom-items

{% file src="../../.gitbook/assets/wazimap-ng.webflow-z-depth-legend-table-margin-legend-fix-07192021-.zip" %}

![Added margin below tables to improve spacing in rich data panel](<../../.gitbook/assets/image (47).png>)

![Hid icon by default](<../../.gitbook/assets/image (59).png>)

![Added .slide-info\_\_introduction to all tutorial slides](<../../.gitbook/assets/image (6).png>)

#### Changed:

* Added margin-bottom to `.profile-indicator__table_inner` to fix spacing issues in the rich-data panel
* z-depth: 999 added to items within the `.map-bottoms-items` panel
* Added `.point-legend__remove` to the .point-legend contained within the `.map-print` panel and added a `.hidden` class to it. It has also been moved further down the DOM so that the `.point-legend` that gets copied is the correct one.
* Added `.hidden` class to `.data-category__h1_icon` by default to avoid incorrect icons
* Added `.slide-info__introduction` to every tutorial slide

## 07/13/2021- Fixed rich data filter buttons to resemble map-options

{% file src="../../.gitbook/assets/wazimap-ng.webflow-rich-data-filter-feature-preview-purge-07132021- (2).zip" %}

{% hint style="info" %}
There was a miscommunication about what options users preferred and we implemented the incorrect solution. This update implements the map-options filtering approach in the rich-data panel.&#x20;
{% endhint %}

{% hint style="warning" %}
Please note that due to slow performance and export speeds, the **backlog of old feature previews has been purged**. I have created a backup on the webflow side to revert back if this causes any issues. I don't foresee there being a problem. Hopefully the performance issues are noticeable.
{% endhint %}

![Preview of rich-data profile-indicator filters](<../../.gitbook/assets/image (55).png>)

#### Changed:

* Reverted to old implementation of `.map-options__filters`&#x20;
* Changed `.profile-indicator__new-filter` to be a wide button to replicate the map-options button



## 07/12/2021- Remove map options tooltip and change filter buttons

{% file src="../../.gitbook/assets/wazimap-ng.webflow-remove-options-tooltip-add-filter-buttons-07122021-.zip" %}
Webflow export
{% endfile %}

![Preview of changes](<../../.gitbook/assets/image (53).png>)

Changed:&#x20;

* Removed the indicator context tooltip from the bottom right of the map-options panel
* Changed the way we implement filter buttons in the map-options panel to bring it in line with the rich-data panel
* Added `.mapping-options__filter-buttons` with the following buttons:
  * `.mapping-options__new-filter`
  * `.mapping-options__remove-filter` (hidden by default)

![](<../../.gitbook/assets/image (52).png>)

## 07/05/2021- Disabled state for map download button

{% file src="../../.gitbook/assets/wazimap-ng.webflow-map-download-disabled-07052021-.zip" %}
Webflow export
{% endfile %}

![Preview of disabled state](<../../.gitbook/assets/image (20).png>)

* Added `.disabled` state to `.map-download` button by default.&#x20;
* Remove this class to set state to enabled.

## 07/05/2021- Removed filter disabled&#x20;

{% file src="../../.gitbook/assets/wazimap-ng.webflow-filter-disabled-07052021-.zip" %}
Webflow Export
{% endfile %}

* Removed the `.disabled` class from `.dropdown-menu__trigger`
* The disabled class is now only on `.mapping-options__filter`
* Added code to disabled filters that have the disabled class:

```css
.mapping-options__filter.disabled {
	pointer-events: none;
  }
```

## 07/02/2021 - Map options filters

{% file src="../../.gitbook/assets/wazimap-ng.webflow-map-options-filters-07022021-.zip" %}
Webflow Export
{% endfile %}

{% hint style="warning" %}
Please note that this element was changed as per a feature request: [https://app.gitbook.com/@openup/s/wazi-ng-technical/\~/drafts/-Md\_pTCg5RT4tBx8Ni2q/development-process/changelog#05-21-2021-additive-filtering](https://app.gitbook.com/@openup/s/wazi-ng-technical/\~/drafts/-Md\_pTCg5RT4tBx8Ni2q/development-process/changelog#05-21-2021-additive-filtering)
{% endhint %}

![](<../../.gitbook/assets/image (31).png>)

#### Changed:

* Added `.map-options__filters_content` back into `.map-options__filters` in the `.map-options` panel.
* `.map-options__filters_content` is hidden by default using the `.hidden` class

## 06/28/2021 - Table content truncation

{% file src="../../.gitbook/assets/wazimap-ng.webflow-table-cell-truncation-07012021- (1).zip" %}
Webflow Export
{% endfile %}

#### Changed:

* Added code to force truncation on the table cells

```css
  .profile-indicator__table_cell {
			width: 100%;
			white-space: nowrap;
			overflow: hidden;
			text-overflow: ellipsis;
	}
```

![](<../../.gitbook/assets/image (21).png>)

## 06/28/2021 - Location tag width

{% file src="../../.gitbook/assets/wazimap-ng.webflow-location-tag-width-06282021-.zip" %}
Webflow Export
{% endfile %}

![Example of issue](<../../.gitbook/assets/image (15).png>)

![Preview of fix](<../../.gitbook/assets/image (50).png>)

#### Changed:

* Set text within `.map-tooltip__geography-chip` to `breaking: no-wrap;`

## 06/22/2021 - SVG console error fix

{% file src="../../.gitbook/assets/wazimap-ng.webflow-svg-size-fix-06222021-.zip" %}
Webflow export
{% endfile %}

#### Changed:

* Adjusted the svg height value for `.location-facility__icon` to 24px to avoid console errors.
* Removed wazimap-ng.css script call

![Old console errors](<../../.gitbook/assets/image (26).png>)

![Console errors after fix](<../../.gitbook/assets/image (46).png>)

## 06/21/2021 - .is--disabled to .disabled

{% file src="../../.gitbook/assets/wazimap-ng.webflow-disbaled-fix-06212021-.zip" %}
Webflow export
{% endfile %}

#### Changed:

* renamed the disabled class on the rich-text dropdowns to `.disabled` from `.is--disabled`

## 06/11/2021 - Map options truncation fix

{% file src="../../.gitbook/assets/wazimap-ng.webflow-map-options-truncation-06112021-.zip" %}
Webflow export
{% endfile %}

#### Fixed:

Fixed the short truncation on map options title. It now extends the full width of the panel.

#### Changed:

Removed capitalization on the map options title.

![](<../../.gitbook/assets/image (9).png>)

## 05/25/2021 - Changes to map options filters

{% file src="../../.gitbook/assets/wazimap-ng.webflow-map-options-filters-05252021-.zip" %}
Webflow export
{% endfile %}

{% hint style="info" %}
This feature change was requested because dropdowns were not working due to them being duplicates and not being cloned from the styles panel (similar to how it is handled in the rich-data panel).
{% endhint %}

#### Changed:

![Removed the filters content section from the map-options div](<../../.gitbook/assets/image (32).png>)

![Added map-options\_\_filters\_content to the styles panel for cloning](<../../.gitbook/assets/image (7).png>)

* The backend will need to clone the `.map-options__filters_content` in the styles panel for the map-options panel as needed. The hope is that this will prevent the dropdowns from breaking.

## 05/21/2021 - Additive filtering&#x20;

{% file src="../../.gitbook/assets/wazimap-ng.webflow-additive-filtering-05212021-.zip" %}
Webflow export
{% endfile %}

{% hint style="info" %}
Feature preview: [https://wazimap-ng.webflow.io/feature-previews/additive-filters-05212021](https://wazimap-ng.webflow.io/feature-previews/additive-filters-05212021)
{% endhint %}

![Additive filter preview in rich-data panel](<../../.gitbook/assets/image (42).png>)

![Additive filter preview in map-options](<../../.gitbook/assets/image (41).png>)

#### Added:

These two implementation of this feature work in a similar ways

* `.profile-indicator__filter-labels` now contains the column labels for each filter column
* Each filter row is now within `.profile-indicator__filter-row` and `.mapping-options__filter-row`
* Possible buttons to the right of the filters (add filter and remove filter) are within `.profile-indicator__filter-buttons` and `.mapping-options__filter-buttons`
  * These buttons are `.profile-indicator__remove-filter` and `.profile-indicator__new-filter` in the rich data panel
  * These buttons are `.mapping-options__remove-filter` in the mapping options
  * `.profile-indicator__new-filter`is visible by default in the rich data panel
  * `.profile-indicator__remove-filter` is hidden by default in the rich data panel

#### Changed:

* Added `border-bottom: 1px;` and `padding-bottom: 12px;` to `.profile-indicator__header`

## 04/29/2021 - Data attributes and classes for Point Mapper and locations

{% file src="../../.gitbook/assets/wazimap-ng.webflow-data-classes-and-attributes-04292021- (2).zip" %}

{% hint style="info" %}
This change was requested by Mila directly and does not have an associated trello card or feature preview.
{% endhint %}

#### Changed:

* Added class="i18n" to all instances of "Point Mapper" and "locations"
  * Point mapper panel and toggle tooltips
  * Locations section in the rich data view (includes the Locations count and the buttons)
* Added data-i18n="Point Mapper" to all instances of "Point Mapper"
* Added data-i18n="locations" to all instances of "locations"

#### Fixed:

* Changed the wording of "Download all facilities" to "Download all locations" in the rich data view.

## 04/22/2021 - Download all facilities

{% file src="../../.gitbook/assets/wazimap-ng.webflow-download-all-facilities-04222021-.zip" %}
Webflow export
{% endfile %}

{% hint style="info" %}
Feature preview: [https://wazimap-ng.webflow.io/feature-previews/download-all-facilities-04222021](https://wazimap-ng.webflow.io/feature-previews/download-all-facilities-04222021)
{% endhint %}

![Preview of "Download all facilities" button](<../../.gitbook/assets/image (11).png>)

#### Changes:

* Added `.location__facilities_download.location__facilities_download-all--header` button to `.location__facilities_header`. This button is only visible on desktop. On mobile it hides and the button moves down to below the location cards. This is because downloading takes less priority on mobile devices.
* Added `.location__facilities_download.location__facilities_download-all--footer`. This button shows on smaller screen sizes.
* `.location__facilities_header-wrapper` to contain the icon and title. **Please note** that this may cause integrations with backend data to break.

![Revised structure of the facilities header](<../../.gitbook/assets/image (29).png>)

## 04/22/2021 - Chart menu data attributes

{% file src="../../.gitbook/assets/wazimap-ng.webflow-dropdown-data-id-04222021-.zip" %}
Webflow export
{% endfile %}

#### Changes:

* Added data attributes to the buttons in the chart dropdown menu
* The following "data-id" attributes have been added:
  * data-id="Percentage"
  * data-id="Value"
  * data-id="csv"
  * data-id="excel"
  * data-id="json"

## 04/09/2021 - Rich data tables&#x20;

{% file src="../../.gitbook/assets/wazimap-ng.webflow-rich-data-tables-04092021-.zip" %}
Rich data tables
{% endfile %}

#### Changes:

* Added `.profile-indicator__table` to the `.styles` section&#x20;

![Preview of the table (component has the "load more rows" button and showing info hidden) ](<../../.gitbook/assets/image (23).png>)

#### Documentation:

* `.profile-indicator__table_row.profile-indicator__table_row--header` is the header row for the table and styles the row accordingly.&#x20;
* At the moment, **only 3 column tables are supported**
* `.profile-indicator__table_row`'s contain `.profile-indicator__table_cell`'s
* The first `.profile-indicator__table_cell` in each row has the class `.profile-indicator__table_cell--first` applied in order to apply specific styling.
* By default the `.profile-indicator__table_show-more` is hidden (comprised of the "Load more rows" and "Showing" info).
* When the table exceeds a certain number of rows (dev decision), subsequent rows are not shown and can be toggled to show using the load more rows button.
* There is no functionality from the Webflow side to handle this "expansion". Please advise if there is anything on my end that would assist in getting this functionality working.&#x20;

## 03/09/2021 - Print and google maps button for location&#x20;

{% file src="../../.gitbook/assets/wazimap-ng.webflow-03092021-location-print-and-google-maps-.zip" %}
Location print and google maps button
{% endfile %}

{% hint style="info" %}
Feature preview: [https://wazimap-ng.webflow.io/feature-previews/google-map-link-02242021](https://wazimap-ng.webflow.io/feature-previews/google-map-link-02242021)
{% endhint %}

![Print button and google maps button](<../../.gitbook/assets/image (17).png>)

### Added:

* Added print button to `.facility-info`
  * `.facility-info__print` is now a child of `.facility-info__header`
* Added `.facility-info__view-google-map` as a child of  `.facility-info`.
  * Component has class `.hidden` applied by default and can be removed to show when available

![.facility-info\_\_print as a child of .facility-info\_\_header](<../../.gitbook/assets/image (54).png>)

## 03/01/2021 - Explicit print button in rich data

{% file src="../../.gitbook/assets/wazimap-ng.webflow-03012021-explicit-print-button-.zip" %}
Explicit print button
{% endfile %}

{% hint style="info" %}
Trello card: [https://trello.com/c/qEwQAdRg](https://trello.com/c/qEwQAdRg)
{% endhint %}

### Changed

* Added `.rich-data__print` to the rich data panel

![Explicit print button within rich-data panel](<../../.gitbook/assets/image (30).png>)

![Structure of rich-data and print button](<../../.gitbook/assets/image (39).png>)

## 03/01/2021 - Rich data location buttons

{% file src="../../.gitbook/assets/wazimap-ng.webflow-03012021-rich-data-location-buttons-.zip" %}
Rich data location buttons
{% endfile %}

### Changed

{% hint style="info" %}
Trello cards: [https://trello.com/c/iqyaamZj](https://trello.com/c/PjRb7JD0) + [https://trello.com/c/AllyWK4N](https://trello.com/c/AllyWK4N)
{% endhint %}

{% hint style="info" %}
Feature preview: [https://wazimap-ng.webflow.io/feature-previews/rich-data-location-button-03012021](https://wazimap-ng.webflow.io/feature-previews/rich-data-location-button-03012021)
{% endhint %}

![Preview of new implementation](<../../.gitbook/assets/image (49).png>)

* Info text changed from  "This **location** has 0000 locations in 0000 categories." to  "This **area** has 0000 locations in 0000 categories."
* Button colour changed to green
* Button wording changed from "facilities" to "locations"

## 02/18/2021 - Map legend always showing

{% file src="../../.gitbook/assets/wazimap-ng.webflow-map-legend-02182021-.zip" %}
Map legend always showing
{% endfile %}

### Changed

{% hint style="info" %}
Trello card: [https://trello.com/c/iqyaamZj](https://trello.com/c/iqyaamZj)
{% endhint %}

#### 1. Map legend always showing:

{% hint style="info" %}
Feature preview: [https://wazimap-ng.webflow.io/feature-previews/map-legend-02122021](https://wazimap-ng.webflow.io/feature-previews/map-legend-02122021)
{% endhint %}

![Preview of the .point-legend showing as part of the non-print ui](<../../.gitbook/assets/image (63).png>)

![Structure of new .map-bottom-items div](<../../.gitbook/assets/image (40).png>)

* Made `.map-options` and `.map-point-legend` children of `.map-bottom-items` (new div)
* `.map-options` and `.map-point-legend` have a `.hidden` applied by default while waiting for the user to add a point layer or choropleth to the map.
* Changes to `.map-options` to make it's width consistent with other items of the ui
  * `.map-options` now stretches to the width of its parent `.map-bottom-items`
  * `width: 95%; max-width: 650px;`
* Added `.point-legend__remove` to the `.point-legend` so that the user can remove a point layer from the map without needing to open the point mapper tab
  * This functionality needs to be added on the backend
  * If this functionality is not ready for deployment, the `.point-legend__remove` item can be hidden before cloning

![point-legend\_\_remove added to point-legend](<../../.gitbook/assets/image (57).png>)

#### 2. Version of the point-legend without a remove button for print

![print version of .point-legend without the remove button](<../../.gitbook/assets/image (65).png>)

![structure of .point-legend for print version](<../../.gitbook/assets/image (67).png>)

## 02/18/2021 - Map legend

{% file src="../../.gitbook/assets/wazimap-ng.webflow-map-print-legend-02182021-.zip" %}
Map legend
{% endfile %}

### Changed

{% hint style="info" %}
Trello card: [https://trello.com/c/iqyaamZj](https://trello.com/c/iqyaamZj)
{% endhint %}

#### 1. Map print legend:

* Added `.map-print` to the `.map` div
* Added `.map-print__point-legend` to `.map-print`&#x20;
* `.map-print` has a `.hidden` class by default which is removed when required

![map-print contents](<../../.gitbook/assets/image (48).png>)

![map-print in loading configuration](<../../.gitbook/assets/image (1).png>)

![Duplicated point-legend](<../../.gitbook/assets/image (62).png>)

#### 2. Point legend:

* `.point-legend` contains `.point-legend__color` and `.point-legend__text`
  * `.point-legend__text` has a default state of loading...
  * `.point-legend__color` is `fill: rgba(0, 0, 0, 0.06)` by default
  * `.point-legend__color` fill must be updated to the value of the point&#x20;
  * `.point-legend` can be duplicated for every instance required

#### 3. Choropleth legend:

* This item has been added to map-print to accommodate functionality that was being hacked together previously.
* The functionality for this item is the same as the default choropleth legend.
* Please contact Matthew if you have any questions about the intention of this component.



## 02/17/2021 - Added data attributes to hover menu items

{% file src="../../.gitbook/assets/wazimap-ng.webflow-data-attributes-01172021-.zip" %}
Hover menu data-attributes
{% endfile %}

### Changed

#### Added data attributes to hover menu components:

{% hint style="info" %}
Trello card: [https://trello.com/c/m1uc8zOh](https://trello.com/c/m1uc8zOh)
{% endhint %}

* Added `data-element="chart-value-select"` to the hover menu chart value type selector
* Added `data-element="chart-download-data"` to hover menu download data options

![](<../../.gitbook/assets/image (2).png>)

![](<../../.gitbook/assets/image (51).png>)

### Fixed

* Removed `.webflow` from `.hover-menu__content` that was not removed before previous export
* This class is used to show items when working on them in webflow. This will mean that the hover menu will start off open. With this fix it should return to a default of closed.

## 02/16/2021 - Hiding and styling content in chart hover menus

{% file src="../../.gitbook/assets/wazimap-ng.webflow-hover-menu-content-styling-02162021-.zip" %}
Hover menu content styling
{% endfile %}

{% hint style="info" %}
Webflow feature preview: [https://wazimap-ng.webflow.io/feature-previews/chart-dropdown-percentage-02162021](https://wazimap-ng.webflow.io/feature-previews/chart-dropdown-percentage-02162021)
{% endhint %}

### Changed

#### 1. Hover menu groups for chart-value and download-data

{% hint style="info" %}
Trello card: [https://trello.com/c/tNa3oDXM/654-provide-css-to-allow-hiding-of-the-chart-type-toggles-in-the-chart-context-menu](https://trello.com/c/tNa3oDXM/654-provide-css-to-allow-hiding-of-the-chart-type-toggles-in-the-chart-context-menu)
{% endhint %}

![Preview of the change to the hover-menu structure](<../../.gitbook/assets/image (16).png>)

* Added a div for `.hover-menu__chart-value` and `.hover-menu__download-data`
* Add `.hidden` to remove this group from the menu



#### 2. Changed css for active state on hover menu list items

{% hint style="info" %}
Trello card: [https://trello.com/c/KV0Yk0hR/655-fix-the-active-css-for-the-value-toggle-on-the-chart-context-menu](https://trello.com/c/KV0Yk0hR/655-fix-the-active-css-for-the-value-toggle-on-the-chart-context-menu)
{% endhint %}

![Old approach](<../../.gitbook/assets/image (4).png>)

![New approach](<../../.gitbook/assets/image (5).png>)

* Changed the way the `.last` class is applied to `.hover-menu__content_list-item` to make the active class behave as intended.&#x20;
  * Old method was a single class `.hover-menu__content_list-item--last`
  * New approach is a combo class added. eg. `.hover-menu__content_list-item.last`
* To make the a list-item "active", just add the active class&#x20;
  * eg.`.hover-menu__content_list-item.last.active`



## 02/12/2021 - Tab notice and map title

{% file src="../../.gitbook/assets/wazimap-ng.webflow-tab-notice-map-title-02122021-.zip" %}
Tab notice and map title adjustments
{% endfile %}

### Changed

#### Map title:

{% hint style="info" %}
Related Trello card: [https://trello.com/c/KqAdJ01z](https://trello.com/c/KqAdJ01z)
{% endhint %}

{% hint style="info" %}
Webflow feature preview: [https://wazimap-ng.webflow.io/feature-previews/map-title-14012021](https://wazimap-ng.webflow.io/feature-previews/map-title-14012021)
{% endhint %}

* Changed default state for `.map-title` to `display: block`
* Added `.hidden` class to `.block-title` to hide by default.&#x20;
* Remove `.hidden` to show

#### Tab notice:

{% hint style="info" %}
Related Trello card: [https://trello.com/c/0tGnWAkN](https://trello.com/c/0tGnWAkN)
{% endhint %}

{% hint style="info" %}
Webflow feature preview: [https://wazimap-ng.webflow.io/feature-previews/tab-notice](https://wazimap-ng.webflow.io/feature-previews/tab-notice)
{% endhint %}

![Tab notice in loading state](<../../.gitbook/assets/image (8).png>)

* Added `.tab-notice` as a child of `.main`
* Added `.hidden` class to `.tab-notice` to hide by default.
* Remove `.hidden` to show
* Adjust `<a>` on `.tab-notice__content` to adjust the link of the notice
* Adjust `.tab-notice__text` to adjust the text within the notice (default is "loading...")





