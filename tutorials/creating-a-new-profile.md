---
description: Quick tutorial on creating a new profile.
---

# Creating a new profile

Here is a quick tutorial that explains how to create a new profile. There are two parts, a) the frontend site and b) the backend profile.

## Setting up the frontend

Create a new domain name and point it to the Wazimap-NG server. In this case I am creating a new CNAME DNS entry called [covid.openup.org.za](https://covid.openup.org.za) that redirects to Netlify which is currently hosting the Wazi-NG frontend.

![Adding a CNAME DNS entry](<../.gitbook/assets/Screen Shot 2020-09-12 at 09.16.37.png>)

Add the new domain name to the Netlify configuration.

![Create a new domain alias on Netlify](<../.gitbook/assets/Screen Shot 2020-09-12 at 09.21.53.png>)

Done. Your frontend is ready!

## Setting up the backend

The backend is also simple to create. Login at [https://production.wazimap-ng.openup.org.za/admin](https://production.wazimap-ng.openup.org.za/admin) and add a new profile [https://production.wazimap-ng.openup.org.za/admin/profile/profile/add/](https://production.wazimap-ng.openup.org.za/admin/profile/profile/add/).&#x20;

![](<../.gitbook/assets/Screen Shot 2020-09-12 at 09.12.33.png>)

Provide a useful name for the profile - this one will be called Covid. Choose a [Geography Hierarchy](../system-architecture/geography-hierarchies.md). I am choosing the pre-installed **2016 boundaries with wards** hierarchy. This uses boundaries used in the 2016 South African municipal elections.

![](<../.gitbook/assets/Screen Shot 2020-09-12 at 09.24.39.png>)

Assign the new domain name created above in the config field

```
{
  "urls": [
    "covid.openup.org.za"
  ]
}
```

Here is my completed profile screen

![](<../.gitbook/assets/Screen Shot 2020-09-12 at 09.30.57.png>)

Save and you're done.

Visit [http://covid.openup.org.za/](http://covid.openup.org.za) to see if everything is setup. It should look like the image below.

![](<../.gitbook/assets/Screen Shot 2020-09-12 at 09.32.29.png>)
