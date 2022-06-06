# NGP8 - Replacing Webflow as frontend framework

Using webflow as the frontend framework makes concurrent frontend development error-prone and requires complicated synchronisation between team members to plan changes. It also often requires multiple round-trips between Matt making changes in Webflow, frontend devs trying to use those changes, Matt then having to make tweaks, until it is done. Each change requires a webflow export, sharing a big zip file, requiring an import which may bring surprise changes in the diff introduced by webflow, adding cognitive load to the code review.

The plan thus far has been to introduce React for the next interactive component we need to modify or introduce.

We have added a small non-interactive component successfully using custom Javascript creating requisite markup, and custom CSS in a project-specific CSS bundle.

We are now looking at introducing a frontend framework, or the frontend libraries, needed to eventually be completely free from Webflow in our frontend dev process.

### Current components

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
  * Point Mapper
    * Point theme (n)
      * Enable-all toggle-switch
      * Profile (point) collection button (n)
  * Data Mapper
    * Category (n)
      * Subcategory (n)
        * Subindicator (n)
* Map
* "Map Chip" (Non-modal fixed dialogue for data mapper controls)
* "Point filters dialogue"
* Breadcrumbs / Profile highlights container
* Feedback button
* Download button
