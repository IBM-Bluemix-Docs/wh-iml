---
copyright:
  years: 2019
lastupdated: "2019-03-26"

keywords: troubleshooting, IBM Cloud, Insights for Medical Literature

subcollection: wh-iml

---

# Troubleshooting
{: #troubleshoot}
General problems with using {{site.data.keyword.wh-iml_short}} might include repository connection errors or validation errors with the Search API context.  While it is possible to see 400 or 404 errors (bad request or object not found) with the other APIs they are much more likely in development than production as the service only returns and expects data stored in the repository.

## How do I resolve a 400 bad request error ?
{: #400-entry}
Invoked an {{site.data.keyword.wh-iml_short}} API and received a 400 error

Review the reason message of the error to see if a required parameter was missed or a misspelling occurred.

## How do I resolve a 401 unauthorized error ?
{: #401-entry}
Invoked an {{site.data.keyword.wh-iml_short}} API and received a 401 error

Confirm the apikey being passed is accurate for the environment.

## How do I resolve a 404 object not found error ?
{: #404-entry}
Invoked an {{site.data.keyword.wh-iml_short}} and received a 404 error

Review the request and reason message to identify which object was not found and confirm a misspelling did not occur.

## How do I resolve a 500 error ?
{: #500-entry}
Invoked an {{site.data.keyword.wh-iml_short}} API and received a 500 error

Try the request again after a few minutes.  If the problem continues contact the instance owner.
