---
copyright:
  years: 2019
  lastupdated: "2019-03-26"

keywords: developer overview tutorial, IBM Cloud, Insights for Medical Literature

subcollection: wh-iml

---
# Authentication
{: #authentication}

Insights for Medical Literature uses token-based Identify and Access Management (IAM) authentication.

Accessing a service instance requires the caller to pass the token on every call.  The token can be passed in an Authorization header or an API key.  If passing an API key, use apikey for the username and the value of the API key as the password.

These security schemes are only secure if the connection is protected with SSL/TLS (e.g., https).

## Roles
{: #roles}
All instances of Insights for Medical Literature will have the Writer role applied which will allow solutions to send GET and POST requests.  No other IAM roles are needed for the service.


