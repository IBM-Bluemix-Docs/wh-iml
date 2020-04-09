---
copyright:
  years: 2019
lastupdated: "2019-03-26"

keywords: responsibilities, IBM Cloud, Insights for Medical Literature

subcollection: wh-iml

---
# Responsibilities by using Insights for Medical Literature
{: #responsibilities}

Learn about the management responsibilities and terms and conditions that you have when you use {{site.data.keyword.wh-iml_full}} (IML). For a high-level view of the service types in {{site.data.keyword.Bluemix}} and the breakdown of responsibilities between the customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).

Review the following sections for the specific responsibilities for you and for {{site.data.keyword.IBM_notm}} when you use {{site.data.keyword.wh-iml_short}}. For the overall terms of use, see [{{site.data.keyword.Bluemix}} Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).

## Incidents and operations management
{: #cloud-infrastructure}

| Task | IBM Responsibilities | Your Responsibilities |
|------------------|-----------|-------------------------|
| Monitoring | {{site.data.keyword.wh-iml_short}} is responsible for hosting monitoring and health services. | The customer is responsible for integrating with the Monitoring, Activity Tracker and Logging services. |
| High Availability | {{site.data.keyword.wh-iml_short}} is responsible for deploying service instances in a Multi-Zone Region (MZR), or across hosts in a Single-Zone Region (SZR) | The customer is responsible for deploying to multiple regions and determining when their application should switch between deployed regional instances. |
{: caption="Table 1.  Responsibilities for IBM Cloud infrastructure" caption-side="top"}

## Change management
{: #iml-change-management}

| Task | IBM Responsibilities | Your Responsibilities |
|------------------|-----------|-----------------------------|
| API Version changes | {{site.data.keyword.wh-iml_short}} is responsible for versioning the service APIs. | The customer is responsible for integrating with the desired version of service APIs. |
{: caption="Table 2. Responsibilities for change management" caption-side="top"}

## Identity and Access Management
{: #iml-iam}

| Task | IBM Responsibilities | Your Responsibilities |
|------------------|-----------|-----------------------------|
| Apikey generation | {{site.data.keyword.wh-iml_short}} is responsible for generating an apikey to access a provisioned instance. | The customer is responsible for managing the security of the apikey. The customer is also responsible for generating and managing additional apikeys for provisioned instances. |
| Apikey deletion | {{site.data.keyword.wh-iml_short}} is responsible for deleting the provisioned instance apikey when the service is deprovisioned. | The customer is responsible for removing the apikey(s) from applications or access chains. |
{: caption="Table 3. Responsibilities for change management" caption-side="top"}

## Security and regulation compliance
{: #security-regulation}

| Task | IBM Responsibilities | Your Responsibilities |
|------------------|-----------|--------------------------|
| Emcryption  | {{site.data.keyword.wh-iml_short}} is responsible for encrypting data on disk and in motion. | The customer is responsible for integrating and managing application level encryption and security keys. |
| Security | {{site.data.keyword.wh-iml_short}} is responsible for ensuring data security on disk and in motion. | The customer is responsible for managing IBM Cloud credentials and keeping them secure.  The customer is also responsible for configuring private endpoints for dedicated instances. |
{: caption="Table 4. Responsibilities for a security rich environment" caption-side="top"}

## Disaster and recovery
{: #disaster-recovery}

| Task | IBM Responsibilities | Your Responsibilities |
|--------|-------------------------|------------------|
| Backups | {{site.data.keyword.wh-iml_short}} is responsible for backups of shared instances. | The customer is responsible for data backups of premium plan instances. |
| Recovery | {{site.data.keyword.wh-iml_short}} is responsible for restoring the service within a region that experienced an outage. | The customer is responsible for provisioning instances in multiple regions and managing their application(s) connectivity to active instances.  The customer is also responsible for restoring data for premium plan instances. |
{: caption="Table 5. Responsibilities for disaster recovery" caption-side="top"}
