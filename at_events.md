---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-23"

subcollection: wh-iml
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

<!-- Name your file `at-events.md` and include it in the Reference nav group in your toc file. -->

# {{site.data.keyword.wh-iml_short}} events
{: #at_events}

Use the {{site.data.keyword.cloudaccesstrailfull}} service to track how users and applications interact with the {{site.data.keyword.wh-iml_short}} service in {{site.data.keyword.Bluemix}}.
{: shortdesc}

## List of events
{: #events}

<!-- Make sure you introduce the table with a detailed description that immediately precedes it. For example, see https://cloud.ibm.com/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf. -->
When the repository connection is provided for a provisioned premium plan the service will connect to the remote environment and track the event.

| Action | Description |
|:-----------------|:-----------------|
| wh-iml.repository.configure | Configure the premium plan data repository. |
| wh-iml.repository.create | Add data to the premium plan data repository. |
| wh-iml.repository.disable | Disable read event tracking. |
| wh-iml.repository.enable | Enable read event tracking. |
| wh-iml.repository.monitor | Enable premium plan monitoring. |
| wh-iml.repository.read | Repository data was searched. |
| wh-iml.repository.delete | Delete a premium corpus from repository. |


{: caption="Table 1. Actions that generate events" caption-side="top"}

## Where to view the events
{: #ui}

{{site.data.keyword.cloudaccesstrailshort}} events are available in the {{site.data.keyword.cloudaccesstrailshort}} **account domain** that is available in the {{site.data.keyword.Bluemix_notm}} region where the events are generated.
