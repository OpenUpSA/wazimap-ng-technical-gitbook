# NGP7 - Wazimap profile domain management

**Proposed by:**&#x20;

**Date:**&#x20;

**Status: Proposed**

### **Context**

As wazimap scales in the number of profiles it hosts, we will need to serve on more and more hostnames.  Each hostname we serve has to be valid for the TLS certificate, and traffic for that hostname has to be routed to the Wazimap NG frontend. That imposes the following requirements for adding a new profile:

1. **Come up with an appropriate hostname**
   * currently: usually a geo. prefix to the client's domain
   * also: a sandbox-geo. prefix for a second profile to use as sandbox
   * often: initially just a projectname.wazimap.openup.org.za subdomain to get things moving quickly
2. **Relate the hostname to the relevant profile in Wazimap admin**
   * A Profile Admin level user can do this. It's currently JSON but can be made simpler.
3. **Configure the frontend web server to serve that hostname**
   * currently: add it as a custom domain in netlify
4. **Provision a new TLS certificate which includes the new domain as a Subject Alternate Name**
   * currently: Click renew certificate, then verify DNS, then renew certificate, perhaps a number of times, until it's happy - in netlify

#### Problems with this approach:

* A networking-aware developer has to do the DNS and custom domain configuration
* Stale domains can break certificate renewal
* Netlify has a limit to the number of custom domains allowed - they have warned us not to add more than 100
* The Certificate is growing bigger and bigger. We aren't sure of the consequences of this.

#### Anticipated scale over the next 1-3 years:

* We are aiming for 40 profile subscriptions by the end of 2022-2023 financial year.
* Pending: Feedback from current profile owners on the importance of custom domains for their profiles.
* Based on the current profiles, we guess that at least 50% would consider custom domains important.

#### Relevant [Let's Encrypt limits](https://letsencrypt.org/docs/rate-limits/):

* **Certificates per Registered Domain** (50 per week) - Only really relevant if we try to have a distinct certificate per wazimap.co.za subdomain instead of a wildcard certificate for that domain. Renewal could be staggered. This would probably happen naturally by renewing daily a month before expiry as is currently done.
* **Names per Certificate** (100) - Relevant if all domains are on a single certificate. This (all domains added as Subject Alternative Name values on a single certificate for the app) is the usual approach dokku-letsencrypt and netlify uses for domains added to the same app.
* **Failed Validation** limit of 5 failures per account, per hostname, per hour. - Relevant if one certificate is used for multiple domains, and DNS for one of the domains is not resolving to us yet. We'd need to be careful about accidental or intentional denial of service here.

#### Limits on Netlify:

* Wildcard domains are supported on Pro, but not at the same time as custom domains
* TLS Certificates can only be handled by Netlify if Netlify DNS is used for the wildcard cart
* Only 100 custom domains are supported on a site. (Possibly due to letsencrypt Names per Cert limit)

#### Similar functionality on competitors/related tools

| Product                                                       | Subdomains | Custom domains |
| ------------------------------------------------------------- | ---------- | -------------- |
| Power BI                                                      |            |                |
| Carto                                                         |            |                |
|                                                               |            |                |
| Tableau                                                       |            |                |
| [https://storymaps.com/](https://storymaps.com)               |            |                |
| [https://storymaps.arcgis.com/](https://storymaps.arcgis.com) |            |                |
| [https://www.arcgis.com/](https://www.arcgis.com)             |            |                |

## **Proposed Solution 1 - Only allow subdomains of our base domain**

Requirements:

* Once-off wildcard DNS for the base domain, e.g. \*.wazimap.co.za
  * Supported by netlify, dokku
* 2-monthly wildcard TLS certificate for the wildcard domain
  * Supported by netlify, dokku
* Wildcard reverse proxying to the frontend web server
  * Supported by netlify, dokku

### **Benefits**

### **Disadvantages**

## **Proposed Solution 2 - Allow subdomain of our base domain for new sites, and legacy custom domains**

**Requirements:**

* Same as solution 1 for wildcard DNS/cert/proxying
* The solution 1 requirements for about 5 custom domains
  * Supported by dokku
  * Not supported by netlify (["You can’t use domain aliases on a site with wildcard subdomains enabled"](https://answers.netlify.com/t/support-for-wildcard-domains-and-multiple-custom-domains/31331/9))

### **Benefits**

### **Disadvantages**

### **Other implications**

## **Proposed Solution 3 - subdomains by default, option of custom domains on dokku added manually**

**Approach**

* DNS
  * Wildcard DNS for subdomains of our base domain
  * Any DNS CNAME to to our frontend web server
* Virtual hosting (reverse proxy or static server)
  * Subdomains are handled automatically by dokku/nginx wicard domain
  * Custom domains: ??? manually-added or automated?
* TLS certificate
  * dokku letsencrypt - wildcard + up to 99 custom domains via dokku letsencrypt (100 30-char domains like [e.g youthexplorer.wazimap.co.za](https://youthexplorer.wazimap.co.za) is 3kb baggage per new TLS connection)
  * alternative to dokku letsencrypt: certbot + vhost per custom domain + dokku app listening on a host port for non-dokku reverse proxy

Adding/removing a domain manually would entail

1. Add the domain to the profile in Admin
2. Add CNAME record pointing to the server, or ask the client to do so
3. SSH to the server
4. Add domain to dokku/nginx vhost
5. Renew TLS certificate

For 20 custom domains, we might have to do this on average 30 times or just over once every 2 weeks.

### Benefits

### Disadvantages

## **Proposed Solution 4 - subdomains by default, option of custom domains on dokku automated**

Same as Solution 3 but instead of adding/removing domains manually by SSHing to the server, we automate that, triggered by domain modifications in admin.

Approach:

* Add the domain to the profile in Admin
* Add CNAME record pointing to the server, or ask the client to do so
* ...Automation to add/remove domain config to server
* ...Automation to renew certificate
* ...Automation to let admin know it's all up and running or feed back errors

### Benefits

### Disadvantages

## **Proposed Solution 5**

### Benefits

### Disadvantages

## **Resolution**

This problem was finally addressed by ...&#x20;

## Further reading

* [https://discuss.httparchive.org/t/san-certificates-how-many-alt-names-are-too-many/1867](https://discuss.httparchive.org/t/san-certificates-how-many-alt-names-are-too-many/1867)
* [Someone exploring many of the same questions on Netlify](https://answers.netlify.com/t/support-for-wildcard-domains-and-multiple-custom-domains/31331/9)
