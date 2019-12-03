---

copyright:
  years: 2015, 2019
lastupdated: "2019-05-20"

keywords: disaster recovery, IBM Cloud, Insights for Medical Literature

subcollection: wh-iml

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:generic: .ph data-hd-programlang='generic'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:curl: .ph data-hd-programlang='curl'}
{:middle: .ph data-hd-position='middle'}
{:right: .ph data-hd-position='right'}

# High availability and disaster recovery
{: ha-dr}
The {{site.data.keyword.wh-iml_full}} service is highly available within any IBM Cloud location.  Recovering from potential disasters that affect an entire location requires planning and preparation.

The instance owner is [responsible](/docs/overview?topic=overview-shared-responsibilities) for understanding the configuration, customization, and usage of the service.  Instance owners are responsible for provisioning a service instance in a new IBM Cloud location when necessary and restoring their data to the same location.

## High_availability
{: high availability}
{{site.data.keyword.wh-iml_short}} is hosted in the [Dallas and Washington locations](/docs/resources?topic=resources-services_region#services_region).  Traffic to any instance is load-balanced across multiple [data centers](/docs/overview?topic=overview-zero-downtime#zero-downtime).

## Disaster recovery
{: disaster_recovery}
Disaster recovery can become a necessity if an IBM Cloud location experiences a significant failure that includes the potential loss of data.  

### Detecting a location outage
{: outage_detection}
The {{site.data.keyword.wh-iml_full}} service provides a [health check API](/apidocs/wh-iml#determine-if-service-is-running-correctly) that can be called repeatedly to ensure the service is available.  Successive internal service error responses from the API could be used as indicator that the service is no longer available in a specific location.

### Lite and Standard plan recovery
{: lite_standard_recovery}
Disaster recovery for a lite and standard plan can be accomplished by either provisioning an instance of the service in multiple locations or provisioning an instance in a new location if a location becomes unavailable.  The URL and and apikey for the new location need to be provided to the solution accessing the service to complete the recovery from one location to another.

### Custom plan recovery
{: custom _recovery}
Disaster recovery of a custom plan requires restoring a backup of any custom corpora in use and restoring it to a new location in addition to provisioning a service instance in a new location.

#### Backing up custom corpora
{: backing_up}
Custom corpora are stored and backed up in an instance of [IBM Cloud Database for Elasticsearch](/docs/services/databases-for-elasticsearch?topic=cloud-databases-dashboard-backups).  Instance owners are responsible for maintaining an up to date backup of the custom corpora outside of IBM Cloud or keeping instances in multiple IBM Cloud locations in sync.

#### Recovery
{: recovery}
The instance owner must ensure the custom corpora is available in the new location prior to recovering a custom {{site.data.keyword.wh-iml_short}} instance.

To recover a custom instance:
  1.  Provision a custom instance in the new location.
  2.  Invoke the configure API to establish connectivity to the custom corpora instance in the new location.