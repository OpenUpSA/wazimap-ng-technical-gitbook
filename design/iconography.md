---
description: >-
  Guidance for decision making around choosing the correct icon and using it in
  a way that makes sense.
---

# Iconography

### Icon choice

When choosing an icon, the following things should be taken into consideration.

1. The icon should be generalized and not reliant on knowledge of a specific language or region.
2. The icon should follow established norms for icons of it's type in similar applications.
3. When the choice deviates from a norm, it should only be done for very good reasons.
4. Icons should be made distinct enough from others in the UI\


#### Some examples:

<div align="left">

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption><p>Poor icon choice: An example of a legacy icon that was poorly chosen as it is specific to a region and not generalized. </p></figcaption></figure>

</div>

<div align="left">

<figure><img src="../.gitbook/assets/image (69).png" alt=""><figcaption><p>Good icon choice: Example of an icon that follows regular norms and is widely understood.</p></figcaption></figure>

</div>

### Size

Icons should generally have the following size properties:

1. Icons should be no larger than 24px wide and 24px tall.
2. Icons that are smaller than 24px in size, should fit within a bounding box that is 24px.
3. This is generally the approach taken for icon sets like [Material](https://fonts.google.com/icons) and [FontAwesome](https://fontawesome.com/).

<div align="left">

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption><p>A 24px bounding box with an icon that is actually smaller than 24px wide.</p></figcaption></figure>

</div>

### Visual weight

Visual weight refers to the amount of prevalence an icon has when looking at it's role in the UI combined with how important the action that icon represents is to the user. When deciding on the visual weight of an icon, the following considerations need to be made.

**How unique is the icon in the UI**

If there is only 1 instance of this icon in the entire UI, it generally denotes it requiring a higher visual weight. eg. search, data mapper,  rich data view.

<figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption><p>When an icon appears multiple times in the UI, it needs to be given less visual weight (left) in order to not overwhelm the user and attract undue attention (right). In this case, the icon was shaded in a lighter colour.</p></figcaption></figure>

**How important is the action the icon represents**

If the action has high importance it should generally be given more weight in the UI, either through, size, colour or containing element settings (eg. size of button, space around button etc.).&#x20;

<div align="left">

<figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption><p>Download is given similar weight to zoom in/out when placed in the same context as "map options"</p></figcaption></figure>

</div>

<div align="left">

<figure><img src="../.gitbook/assets/image (4) (2).png" alt=""><figcaption><p>Core functions have a larger button size and are given more space and prominence.</p></figcaption></figure>

</div>



