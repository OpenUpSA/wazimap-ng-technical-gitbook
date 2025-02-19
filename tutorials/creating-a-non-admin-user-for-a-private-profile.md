---
description: >-
  A Wazimap-NG instance can be set to private, which means that a user will
  require credentials to login and view the data.
---

# Creating a non-admin user for a private profile

One can create a non-admin account as follows:

1. Navigate to the user creation page: [https://api.wazimap.com/admin/auth/user/add/](https://api.wazimap.com/admin/auth/user/add/)
2. Select a username and password (this will be a temporary password or can be generated from [https://passwordsgenerator.net/](https://passwordsgenerator.net/) if you'd prefer to do so)
3. Press **Save**
4. Copy the link to send to the user to change their password (see image below). **NOTE: This link is specific to the user and should not be shared with anyone but that user.**

![](<../.gitbook/assets/image (55).png>)

1. Add details under **Personal Information** (optional)
2. Under **Permissions**, **DO NOT** assign Staff or Superuser status!&#x20;
3. In the **Groups** selector, add the groups applicable for the user. In the screenshot below, the user has been given access to the SIOC dashboard and SIOC dashboard SANDBOX groups. This means that the user will only be able to log into those instances of Wazimap-NG.

![](<../.gitbook/assets/image (65).png>)

7\. When done, press **Save**
