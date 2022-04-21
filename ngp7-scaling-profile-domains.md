# NGP7 - Scaling profile domains

**Proposed by:**&#x20;

**Date:**&#x20;

**Status: Proposed**

### **Context**

As wazimap scales in the number of profiles it hosts, we will need to serve on more and more hostnames.  Each hostname we serve has to be valid for the TLS certificate, and traffic for that hostname has to be routed to the Wazimap NG frontend. That imposes the following requirements for adding a new profile:

* **Come up with an appropriate hostname**
  * currently: usually a geo. prefix to the client's domain
  * also: a sandbox-geo. prefix for a second profile to use as sandbox
  * often: initially just a projectname.wazimap.openup.org.za subdomain to get things moving quickly
* **Configure the frontend web server to serve that hostname**
  * currently: add it as a custom domain in netlify
* **Provision a new TLS certificate which includes the new domain as a Subject Alternate Name**
  * currently: Click renew certificate, then verify DNS, then renew certificate, perhaps a number of times, until it's happy - in netlify

#### Problems with this approach:

* A networking-aware developer has to do the DNS and custom domain configuration
* Stale domains can break certificate renewal
* Netlify has a limit to the number of custom domains allowed - they have warned us not to add more than 100
* The Certificate is growing bigger and bigger. We aren't sure of the consequences of this.

Anticipated scale over the next 1-3 years:

## **Proposed Solution 1**

### **Benefits**

### **Disadvantages**

## **Proposed Solution 2**

### **Benefits**

### **Disadvantages**

### **Other implications**

## **Proposed Solution 3**

### Benefits

### Disadvantages

## **Resolution**

This problem was finally addressed by ...&#x20;
