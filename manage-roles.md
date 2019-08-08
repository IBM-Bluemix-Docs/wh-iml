---
copyright:
  years: 2019
lastupdated: "2019-04-12"

keywords: getting started tutorial, IBM Cloud, Insights for Medical Literature

subcollection: wh-iml

---
{:pre: .pre}
{:url: data-credential-placeholder='url'}
{:apikey: data-credential-placeholder='apikey'}
{:corpus: data-credential-placeholder='corpus'}
{:hide-dashboard: .hide-dashboard}

# Managing Access Roles
{: #manage-roles}

You can secure services within {{site.data.keyword.cloud_notm}} by allowing only users with specific access roles to complete certain actions.

## Platform access roles
{: #platform-roles}
You can use platform access roles for enabling users to complete tasks on platform resources like provisioning and de-provisioning instances in your {{site.data.keyword.cloud_notm}} account.

| Action                                                        | Role                                |
|---------------------------------------------------------------|-------------------------------------|
| View instances of {{site.data.keyword.wh-iml_short}}          | Operator, Administrator, Editor.    |
| Provision an instance of {{site.data.keyword.wh-iml_short}}.  | Administrator, Editor               |
| De-provision an instance of {{site.data.keyword.wh-iml_short}}| Administrator, Editor               |

## Service access roles
{: #service-roles}
You can use service access roles to enable users to perform service actions in the form of HTTP requests.

| Action                                | Role                                 |
|---------------------------------------|--------------------------------------|
| GET /wh-iml                           | Manager, Reader, Writer              |
| PUT /wh-iml                           | Manager, Writer                      |
| POST /wh-iml                          | Manager, Writer                      |
| DELETE /wh-iml                        | Manager                              |


