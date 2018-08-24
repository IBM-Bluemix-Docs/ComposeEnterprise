---

copyright:
  years: 2017, 2018
lastupdated: "2018-02-20"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Getting started tutorial
{: #getting-started}

Complete these steps to get started with {{site.data.keyword.composeEnterprise}}:

## Provisioning a {{site.data.keyword.composeEnterprise}} service instance
{: #provisioning-compose-enterprise-instance}

You can provision a new {{site.data.keyword.composeEnterprise}} instance by using the {{site.data.keyword.cloud_notm}} console or the command line.

**Note:** It can take up to 5-7 business days for your {{site.data.keyword.composeEnterprise}} cluster to be provisioned.

## Provisioning a {{site.data.keyword.composeEnterprise}} service instance from the {{site.data.keyword.cloud_notm}} console

[Create a {{site.data.keyword.composeEnterprise}} instance](https://console.{DomainName}/catalog/services/compose-enterprise/), ensuring that you complete all the fields.

**Notes:**
- The name of your {{site.data.keyword.composeEnterprise}} cluster can have a maximum length of 19 characters, and can contain only alphanumeric characters.
- When you choose a *Cloud Provider Region*, the location that you select is the IBM Cloud data center in which the {{site.data.keyword.composeEnterprise}} instance is deployed.


## Provisioning a {{site.data.keyword.composeEnterprise}} service instance from the command line

1. Download and install the [{{site.data.keyword.cloud_notm}} CLI](https://console.{DomainName}/docs/cli/reference/bluemix_cli/download_cli.html) tool.
2. Log in to {{site.data.keyword.cloud_notm}}.

  ```
  bx login
  ```

3. Switch to the organization and space you want to use for your new Compose database service.

  ```
  bx target --cf
  ```

4. Provision an instance of the service with the `create-service` command.

  ```
  bx cf create-service service_name service_plan service_instance -c start_command
  ```

### Command options

  <dl>
    <dt>service_name</dt>
    <dd>
    The name of the {{site.data.keyword.cloud_notm}} service you want to create an instance of. The value must be `compose-enterprise`.
    </dd>
    <dt>service_plan</dt>
    <dd>
    The pricing plan for the new service. The value must be `Enterprise`.
    </dd>
    <dt>service_instance</dt>
    <dd>
    The name of the new Compose database service that you want to provision.
    </dd>
    <dt>-c start_command</dt>
    <dd>
    The start_command contains the details of the {{site.data.keyword.composeEnterprise}} cluster that you want to provision. It is formatted as an array and can contain the following values:
      <dl>
        <dt>contact_name (required)</dt>
        <dd>
        The name of the owner of the {{site.data.keyword.composeEnterprise}} cluster
        </dd>
        <dt>contact_phone (required)</dt>
        <dd>
        A contact telephone number for the {{site.data.keyword.composeEnterprise}} cluster owner
        </dd>
        <dt>contact_email (required)</dt>
        <dd>
        An email address for the {{site.data.keyword.composeEnterprise}} cluster owner
        </dd>
        <dt>provider_region (required)</dt>
        <dd>
        The IBM Cloud data center in which you want the {{site.data.keyword.composeEnterprise}} instance to be deployed. Valid values are: <code>amsterdam</code>, <code>chennai</code>, <code>dallas</code>, <code>frankfurt</code>, <code>hong kong</code>, <code>houston</code>, <code>london</code>, <code>melbourne</code>, <code>milan</code>, <code>montreal</code>, <code>oslo</code>, <code>paris</code>, <code>queretaro</code>, <code>san jose</code>, <code>sao paulo</code>, <code>seattle</code>, <code>seoul</code>, <code>singapore</code>, <code>sydney</code>, <code>tokyo</code>, <code>toronto</code>, <code>washington dc</code>.
        </dd>
        <dt>cluster_name (optional)</dt>
        <dd>
        Choose a name for your provisioned {{site.data.keyword.composeEnterprise}} cluster. The maximum length is 19 characters, and can contain only alphanumeric characters.
        </dd>
        <dt>notes (optional)</dt>
        <dd>
        Add any notes that relate to your cluster, for example <code>Bare Metal</code>.
        </dd>
      </dl>
    </dd>
  </dl>

### Sample `bx cf create-service` usage

```
bx cf create-service compose-enterprise Enterprise myComposeEnterpriseServiceName -c '{"contact_name": "myName", "contact_phone": "888-888-8888", "contact_email": "myEmail@ibm.com", "provider_region": "dallas", "cluster_name": "myClusterName123", "notes": "Bare Metal" }'
```

When your {{site.data.keyword.composeEnterprise}} Cluster is available, you can provision Compose {{site.data.keyword.cloud_notm}} databases into the cluster and enjoy the benefits of auto-scaling databases with encryption at rest and in motion within an isolated cluster.

## Next steps.

Now that you have your {{site.data.keyword.composeEnterprise}} cluster is provisioned and configured, you are ready to deploy databases into the cluster.

You can deploy a Compose {{site.data.keyword.cloud_notm}} database into a {{site.data.keyword.composeEnterprise}} cluster when you create a new database from any of the existing Compose database {{site.data.keyword.cloud_notm}} services. You can use the {{site.data.keyword.cloud_notm}} console or the command line. For more information about how to deploy databases, see [Deploying a Compose database into a {{site.data.keyword.composeEnterprise}} cluster](./deploying.html).





