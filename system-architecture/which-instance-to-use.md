# Determine which instance to use

Wazimap-NG is multi-tenanted. A single backend can host multiple profiles, e.g. [https://beta.youthexplorer.org.za](https://beta.youthexplorer.org.za) and [http://sifar.openup.org.za](https://sifar.openup.org.za) both use the same server and database.

In order to determine which profile to use, the client sends a `wm-hostname`header with this api call: `/api/v1/profile_by_url/?format=json`this is received by the server which then matches the hostname with available profiles. You can determine which profiles are currently served by a particular backend using the following url: `/api/v1/profiles/`. It will return a list of profiles with their configurations, e.g.

```
{
    ...
    "results": [
        {
            "id": 2,
            "name": "Vulekamali",
            ...
            "configuration": {
                "urls": [
                    "geo.vulekamali.gov.za"
                ],
                ...
            }
        },
        {
            "id": 3,
            "name": "Cape Town Against Covid-19",
            ...
            "configuration": {
                "urls": [
                    "capetownagainstcovid19.openup.org.za"
                ],
                ...
            }
        },
        ...
}
```

In this case, when the server receives `wm-hostname` set to geo.vulekamali.gov.za, it returns profile 2. A single profile may match multiple urls.
