---
description: 'Stable version: ... | Latest version: https://wazi-rich-data.webflow.io/'
---

# Webflow Integration

## General

**Rationale for recent structure update:**\
The latest version of wazimap has been reworked to ensure we can include the following features:

1. In-page anchor linking and page navigation
2. A component based approach to populating pages
3. An improved mobile experience
4. Filtering of sub-indicator

<div align="left"><img src="../.gitbook/assets/image (108).png" alt="Overall page structure. "></div>

## Styles section

The functional styles div resides on the main mapping page (hidden using .hidden). A copy of it can be found here ([https://wazi-rich-data.webflow.io/styles](https://wazi-rich-data.webflow.io/styles)). This copy needs to be updated as elements are added to the main section or visa versa.\
\
Elements can be called as needed into different areas. This approach was aimed at improving loading times and initial states that would have incorrect information.

<div align="left"><img src="../.gitbook/assets/image (3).png" alt="The individual components ready to be cloned."></div>

## Rich Data Panel

Every other element is arranged in relation to this panel (using position fixed). This is so that we can maintain in page anchor linking and page navigation.

<div align="left"><img src="../.gitbook/assets/image (14).png" alt="The styled components for the rich data panel"></div>

### 1. Rich data nav items

These items sit on the left hand side of the rich data panel and act as anchors to jump to different content. They also allow users to know which section they are currently in.

{% hint style="info" %}
**Default state:** .rich-data-nav\_\_ list will be populated with the .rich-data-nav\_\_item "summary" and the location pin icon. This item links to the top of the rich data panel using the anchor link #top.

**Anchor links:** Anchor link named need to be added when implementing a component. They should be added to **.section-link** within **.section** within **.rich-data\_\_content** as they are brought into the page. See image below. Position adjustment has been made to this .section-link to ensure users scroll to the correct position, taking into account navigation elements etc.
{% endhint %}

<div align="left"><img src="../.gitbook/assets/image (95).png" alt=".section-link within a .section"></div>

<div align="left"><img src="../.gitbook/assets/image (102).png" alt="Example nav items"></div>

<div align="left"><img src="../.gitbook/assets/image (94).png" alt="Structure of the .rich-data-nav"></div>

#### How to implement this component:

Call **.rich-data-nav\_\_item** into **.rich-data-nav\_\_list**

```
$ give me super-powers
```

Once you're strong enough, save the world:

{% code title="hello.sh" %}
```bash
# Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```
{% endcode %}

