---
copyright:
  years: 2019
lastupdated: "2019-04-12"

keywords: information security, IBM Cloud, Insights for Medical Literature

subcollection: wh-iml

---

{:new_window: target="_blank"}
{:important: .important}

# Information Security
{: #information-security}

{{site.data.keyword.IBM}} is committed to providing our clients and partners with innovative data privacy, security and governance solutions.

Clients are responsible for ensuring their own compliance with various laws and regulations, including the European Union General Data Protection Regulation. Clients are solely responsible for obtaining advice of competent legal counsel as to the identification and interpretation of any relevant laws and regulations that may affect the clients’ business and any actions the clients may need to take to comply with such laws and regulations. {: important}

The products, services, and other capabilities described herein are not suitable for all client situations and may have restricted availability. {{site.data.keyword.IBM_notm}} does not provide legal, accounting or auditing advice or represent or warrant that its services or products will ensure that clients are in compliance with any law or regulation.

If you need to request GDPR support for {{site.data.keyword.cloud}} {{site.data.keyword.watson}} resources that are created

•	In the European Union (EU), see [Requesting support for {{site.data.keyword.cloud_notm}} Watson resources created in the European Union](/docs/services/watson?topic=watson-gdpr-sar#request-EU){: new_window}.

•	Outside of the EU, see [Requesting support for resources outside the European Union](/docs/services/watson?topic=watson-gdpr-sar#request-non-EU){: new_window}.


## European Union General Data Protection Regulation (GDPR)
{: #gdpr}

{{site.data.keyword.IBM_notm}} is committed to providing our clients and partners with innovative data privacy, security and governance solutions to assist them on their journey to GDPR compliance.

Learn more about {{site.data.keyword.IBM_notm}}'s own GDPR readiness journey and our GDPR capabilities and offerings to support your compliance journey [here ![External link icon](../../icons/launch-glyph.svg "External link icon")](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/gdpr){: new_window}.

## Data Retention
{: #data-retention}

{{site.data.keyword.wh-iml_full}} can be provisioned using the custom plan which connects the service to a customer provided {{site.data.keyword.databases-for-elasticsearch_full}} instance.  The {{site.data.keyword.wh-iml_short}} instance will build an in-memory cache of ontology artifacts discovered in the enriched corpora stored on the customer's {{site.data.keyword.databases-for-elasticsearch}} instance.  When the {{site.data.keyword.wh-iml_short}} instance is deprovisioned the service environment is immediately deleted.  In addition the policy that allows access between {{site.data.keyword.wh-iml_short}} and {{site.data.keyword.databases-for-elasticsearch}} can be dissolved by the instance owner at any time.

{{site.data.keyword.wh-iml_short}} does not support search and retrieval of personal information.  Customers are responsible for ensuring any custom enriched corpora stored in a provided {site.data.keyword.databases-for-elasticsearch}} instance do not contain personal information.

## Data Deletion
{: #data-deletion}
The {{site.data.keyword.wh-iml_short}} lite and standard plans do not store any user data.  The custom plan can store and backup two categories of user data.  The first is a set of connectivity data which is used to read IML configured indices from a customer provided {{site.data.keyword.databases-for-elasticsearch_full}} instance and is created or removed using the service [corpora configure API](/apidocs/wh-iml#define-a-custom-corpus-repository-connection).  The second category is an optional read-only Identify and Access Management (IAM) apikey that is used for automated monitoring of the service instance and is created or removed using the service [corpora monitor API](/apidocs/wh-iml#enable-monitoring-for-a-custom-instance).  Specifying a value of 'none' for either API will result in the deletion of the stored configuration data.

When a custom plan instance is deprovisioned the data and any backups will be deleted within 60 days.
