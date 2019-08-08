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

# Disaster and Recovery
The {{site.data.keyword.wh-iml_full}} service is deployed to a single region in {{site.data.keyword.IBM}}.  In the event of a disaster in that region the recovery process is to rebuild the resources in that region and restore the enriched corpora from cloud storage.  The service will be unavailable during the recovery process.