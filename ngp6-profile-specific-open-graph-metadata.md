# NGP6 - Profile-specific open graph metadata

**Proposed by: JD Bothma**

**Date: 2022-04-21**

**Status: Spike probable solution**

### **Context**

We would like to be able to serve open graph metadata specific to each wazimap NG profile. Wazimap profiles are designed as stand-alone sites or sub-sites often set up as subdomains of other sites. Open graph metadata can significantly increase the chance of someone clicking a link to a wazimap profile found in social media or search engines. While Google takes Open Graph metadata updated client-side using javascript into account, we are not aware of social media or other search engines that do that. To reach any of these audiences except Google, we need to serve open graph metadata specific to a profile server-side.

The fields that would benefit from being served this way are

* Page title - often used as an emphasised heading
* Image - very effective at being eye-catching and drawing interest from potential users
* Description - this can both convince users that something might be worth clicking, and also set their expectations to reduce surprise and this bouncing from the site.
* Favicon - some tools like bookmark and link aggregators and search engines also use this. While browsers support dynamically-set favicons, it's not clear how many other tools do.

Open Graph Metadata also help SEO. Additional content that can help SEO is the introductory content currently located on the profile landing pages.

#### Current state

**Landing pages**

Most sites have a landing page made in webflow or Wordpress. These can easily serve profile-specific branded metadata to accomplish most of the above. This then links to the relevant wazimap profile with a clear call to action. This content can be quite effective for SEO.

We would like to move these into wazimap NG to be able to maintain that content from one interface, reduce the jumps users have to make, and reduce the hosting costs of a wazimap profile. If we move these into wazimap NG, we lose this ability to serve the open graph metadata need.

**Hardcoded metadata**

The open graph metadata is currently the same for all wazimap profiles, hardcoded on the webflow side and imported to the frontend app from there. This can be updated both in webflow and overridden in the import script in the frontend app.

Updating this to something that is at least sensible as generic content is a high priority until this content is dynamic and profile-specific.

#### Levels of achievement

In ascending order of value:

1. Better hardcoded metadata (get rid of the webflow favicon, ensuring webflow changes don't introduce odd things like "2021" in the title
2. Profile-specific metadata, e.g. "Youth Explorer" or "Vulekamali Geospatial data viewer" in the title, branding and screenshot in the image, etc.
3. Profile- and geography-specific metadata, e.g. "Tswhane - Youth Explorer" or "Eastern Cape - Vulekamali Geospatial".
4. Specific indicator and geography, e.g. "Multidimensional youth poverty - Tshwane - Youth Explorer" in the title, perhaps some or all of the indicator description in the open graph metadata
5. dynamic image, e.g. the selected geography on the map, perhaps dynamically-branded; perhaps a choropleth or rich data view chart image for the selected geography and indicator.

We're aiming around level 2 for now.

Level 3 depends on changing from fragment identifier (#geo:CPT) to querystring (?geo=CPT)

## **Proposed Solution 1 -** Server-side rendering (SSR) for the frontend app using node.js in a dokku app

The frontend would be deployed as it currently is, but Javascript is executed server-side to inspect the request, fetch the profile-specific data via the API, templates the metadata into the HTML page, and serves the response.

[https://www.npmjs.com/package/mustache-express](https://www.npmjs.com/package/mustache-express)

A prerequisite for next.js would be replacing webflow or horrid hacks to import our webflow export as a [custom "Document"](https://nextjs.org/docs/advanced-features/custom-document).

### **Benefits**

* a lot of people are doing this these days
* the frontend remains rather decoupled from the backend
* Very little changes in terms of developing on the frontend - it remains just a `yarn start` kind of process

### **Disadvantages**

* Do we have experience of serving stuff with node.js in prod?

## **Proposed Solution 2 -** Server-side rendering for the frontend app using node.js on netlify and similar

Same as above, but on a (not so?)-static hosting platform like netlify or Cloudflare apps instead of a dokku server.

### **Benefits**

### **Disadvantages**

### **Other implications**

* Each profile hostname has to be added as a custom domain in Netlify or whatever the platform is. Netlify doesn't support more than 100 custom domains (it's not clear what the technical limit is) on an app and we have already had issues with their restriction of the apex domain being allowed only on one netlify team without manual intervention from their support. See [NGP7 - Wazimap profile domain management.](ngp7-wazimap-profile-domain-management.md)

## **Proposed Solution 3 -** Serving HTML, CSS and JS using the (currently) backend django app

Index.html becomes a django template. Django templates in the data before serving /

The backend will need to respond to requests for all profile hostnames, affecting how the backend infra gets configured.

### Benefits

* We have lots of experience of this
* no additional api requests to serve / - it can access django models immediately.

### Disadvantages

* frontend dev can easily get coupled with running the backend, needing at least a basic backend setup to run, even if subsequent requests to the api go to another backend (e.g. prod). But this can add confusion and/or complexity (**it is possible to keep them separate. Just hard.)**

## **Resolution**

Proposal:

1. Quick win with minimal interruption:
   1. Use minimal server-side templating like express-handlebars to query and render profile details
   2. enables all achievement levels but certainly 2-3
2. eventually consider full-blown server-side rendering next.js style
   1. enables pre-rendering javascript-drawn content, skipping several data roundtrips
   2. watch out: next.js is possibly not the right tool - apparently more page-content oriented than SPA.
