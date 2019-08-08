---
copyright:
  years: 2019
lastupdated: "2019-03-26"

keywords: developer overview tutorial, IBM Cloud, Insights for Medical Literature

subcollection: wh-iml

---

# Overview for developers
{: #developer-overview}

You can use the {{site.data.keyword.wh-iml_short}}  service via an HTTP Representational State Transfer (REST) API.  Software Development Kits (SDKs) are also available to simply application development in various languages.

## Programming with the service
{: #service-programming}
To develop an application over {{site.data.keyword.wh-iml_short}}  a sequence of API calls will be needed.  The API calls accept parameters and / or JSON content.  The service will return the output in JSON format.  To produce an application several APIs will need to be strung together to provide suggested search criteria, generate results, and retrieve content.

IMPORTANT:  All API calls require the version parameter to be set in the URI.

Error handling needs are minimal as the service only uses data stored in the corpus.  While the service can return 400 or 404 errors for bad requests (invalid parameters) or objects not found those errors are typically seen in development rather than production.  See the troubleshooting guide for more details.

## Using software Development Kits
{: #sdk-usage}

SDKs are available for the {{site.data.keyword.wh-iml_short}}  service to simply application development.  {{site.data.keyword.ibmwatson}} SDKs are available for many popular programming languages and platforms.

For a complete lis of SDKs and GitHub links see 
For detailed information about all {{site.data.keyword.wh-iml_short}}  server methods see the API reference.