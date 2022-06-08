# NGP8 - Replacing Webflow as frontend framework

**Proposed by: JD Bothma**

**Date: 2022-04-21**

**Status: Spike probable solution**

### **Context**

Using webflow as the frontend framework makes concurrent frontend development error-prone and requires complicated synchronisation between team members to plan changes. It also often requires multiple round-trips between Matt making changes in Webflow, frontend devs trying to use those changes, Matt then having to make tweaks, until it is done. Each change requires a webflow export, sharing a big zip file, requiring an import which may bring surprise changes in the diff introduced by webflow, adding cognitive load to the code review.

The plan thus far has been to introduce React for the next interactive component we need to modify or introduce.

We have added a small non-interactive component successfully using custom Javascript creating requisite markup, and custom CSS in a project-specific CSS bundle.

We are now looking at introducing a frontend framework, or the frontend libraries, needed to eventually be completely free from Webflow in our frontend dev process.

### Current components

(n) means there can be multiple instances

* Page header
  * Logo
  * Search box
  * Tutorial button
* Panels (on the left)
  * Rich Data View
    * Point data summary
      * Total point and profile (point) collection count
      * Download all button
      * Show services button
      * Point theme card (n)
        * Profile (point) collection item (n)
    * Category (n)
      * Subcategory (n)
        * Indicator (n)
          * Filters Section
          * Chart
          * Description
          * Source
          * Table
  * Point Mapper
    * Point theme (n)
      * Enable-all toggle-switch
      * Profile (point) collection button (n)
  * Data Mapper
    * Category (n)
      * Subcategory (n)
        * Subindicator (n)
* Map
  * Map Download button
* "Map Chip" (Non-modal fixed dialogue for data mapper controls)
* "Point filters dialogue"
* Breadcrumbs / Profile highlights container
* Feedback button

### Upcoming components

![](<.gitbook/assets/WaziCompare - Mockup 1 (3) (1).png>) ![](<.gitbook/assets/image (22) (2).png>) ![](<.gitbook/assets/image (21) (1).png>) ![](<.gitbook/assets/indicator-panel-contracted-filter-reset (1).jpg>)

### Libraries and tech to consider

* Web components
* [https://polymer-library.polymer-project.org/3.0/docs/devguide/feature-overview](https://polymer-library.polymer-project.org/3.0/docs/devguide/feature-overview)
  * Maintenance mode, referring to Lit.
  * [https://github.com/PolymerElements](https://github.com/PolymerElements) is a github org of component repos
* [https://lit.dev/](https://lit.dev/)
* [https://semantic-ui.com/](https://semantic-ui.com/)
* [https://material.io/components?platform=web](https://material.io/components?platform=web)
* [https://github.com/material-components/material-web](https://github.com/material-components/material-web)
  * > IMPORTANT: Material Web is a work in progress and subject to major changes until 1.0 release.

## Spike

* Try the [MUI react material UI component library](https://mui.com/material-ui/)
* Try the [Semantic UI component library](https://semantic-ui.com/) with React integration
* Implement the search/select-one component and style accordingly
  * &#x20;![](<.gitbook/assets/image (22) (2).png>)
* Implement the filter-reset snackbar
  * &#x20;![](<.gitbook/assets/indicator-panel-contracted-filter-reset (1).jpg>)
* Do either of them risk breaking styling of existing parts?
* Does it look like both approaches to styling scale nicely - Is consistent styling convenient enough with both options as we eventually replace all components on the site?

## Resolution

* **Interactive/reactive markup library:** React
* **Component library:** To be determined - see spike above
* **Styling/CSS:** To be determined - see spike above
* **State management:** custom event system and controller until enough of UI is react that changing to something standard is easier than maintaining the custom approach
* **Framework:** Nothing more than what we have for now. Revisit things like next.js but for SPAs when most of the webflow dependency is gone

## See also

* [Using the same Redux store for multiple React instances](https://stackoverflow.com/questions/59743168/multiple-instances-of-react-application-on-the-same-page) (in our case this is probably desirable)

