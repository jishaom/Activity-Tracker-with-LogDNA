---

copyright:
  years: 2019
lastupdated: "2019-05-21"

keywords: IBM Cloud, LogDNA, Activity Tracker, resource controller events

subcollection: logdnaat

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# Service instance events  
{: #at_events_rc}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full_notm}} service to track how users and applications interact with the {{site.data.keyword.cloud_notm}} services. 
{:shortdesc}

The {{site.data.keyword.at_full_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. To get started monitoring your user's actions, see [{{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started). 


## Events for provisioning and managing service instances
{: #rc_provision}

The following table lists the actions that generate an event:

| Action                                   | Description |
|------------------------------------------|---------|
| `service_name.instance.create`           | An event is generated when you provision a service instance. |
| `service_name.instance.update`           | An event is generated when you rename a service instance or when you change the service plan. |
| `service_name.instance.delete`           | An event is generated when a service instance is deleted. |
| `service_name.instance.schedule_reclaim` | An event is generated when a service instance is pending_reclamation. |
| `service_name.instance.restore`          | An event is generated when a service instance is restored. |


{: caption="Table 1. Actions that generate events" caption-side="top"} 


##  Events for managing aliases that are associated to a service instance
{: #rc_alias}

An alias is a connection between your IAM-managed service within a resource group and an application within an org or a space.

The following table lists the actions that generate an event:

| Action                         | Description |
|--------------------------------|---------|
| `service_name.alias.create` | An event is generated when an alias for an instance is created. |
| `service_name.alias.update` | An event is generated when an alias for an instance is updated. |
| `service_name.alias.delete` | An event is generated when an alias for an instance is deleted. |
{: caption="Table 2. Actions that generate events" caption-side="top"} 


##  Events for managing service credentials that are associated to a service instance
{: #rc_keys}

A service credential provides the necessary information to connect an application to a service instance. 

The following table lists the actions that generate an event:

| Action                         | Description |
|--------------------------------|---------|
| `service_name.key.create` | An event is generated when an API key is created for a service instance through the *Service credentials* section of the service instance UI. |
| `service_name.key.delete` | An event is generated when an API key that is associated with a service instance is deleted from the *Service credentials* section of the service instance UI. |
{: caption="Table 3. Actions that generate events" caption-side="top"} 



##  Events for binding and unbinding a service instance to an app
{: #rc_bind}

The following table lists the actions that generate an event:

| Action                         | Description |
|--------------------------------|---------|
| `service_name.binding.create` | An event is generated when you bind a service instance to an application. |
| `service_name.binding.delete` | An event is generated when you unbind a service instance from an application. |
{: caption="Table 4. Actions that generate events" caption-side="top"} 



## Where to look for the events
{: #rc_ui}

Events are available in the **Frankfurt (eu-de)** region. 

To view these events, you must [provision an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **Frankfurt (eu-de)** region. Then, you must [open the {{site.data.keyword.at_full_notm}} UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2). 



## Analyzing events
{: #rc_analyze}

**Action: service_name.instance.delete**

When a service instance is deleted, consider the following information:
* Other actions are automatically triggered to clean up IAM permissions. These actions remove policies that are configured for users and service IDs in the account to work with the service instance. 
* The initiator of these actions is an {{site.data.keyword.IBM_notm}} service ID.


When the service instance that is deleted does not have IAM policies configured for users and service IDs, the events that are automatically generated for any of these resources report an outcome of`failure` with a `404` outcome code. The following sample shows the events that are generated when a service instance that does not have policies configured in the account is deleted:

```
Apr 30 09:04:16 cloudcerts: delete instance Certificate Manager-v1
Apr 30 09:41:20 IAM Access Management: delete policy -failure
Apr 30 09:41:20 IAM Access Management: delete policy -failure
```
{: screen}



