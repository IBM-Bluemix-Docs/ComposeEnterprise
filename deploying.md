---

copyright:
  years: 2017, 2018
lastupdated: "2018-02-08"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Deploying a Compose database into a {{site.data.keyword.composeEnterprise}} cluster

## Deploying from the {{site.data.keyword.cloud_notm}} console

If you already have an {{site.data.keyword.composeEnterprise_full}} cluster, you can specify that your new Compose {{site.data.keyword.cloud_notm}} database is provisioned into the cluster. Select the name of the {{site.data.keyword.composeEnterprise}} cluster from the list of available locations in the *Select Location for Deployment* drop-down when you are creating the new Compose {{site.data.keyword.cloud_notm}} database service instance.

## Deploying from the command line

To create a new instance of a Compose database service and provision it into a {{site.data.keyword.composeEnterprise}} cluster, from the command line you need to first install the {{site.data.keyword.cloud_notm}} command line interface (CLI), then get and use the {{site.data.keyword.composeEnterprise}} cluster ID.

## Step 1. Set up the {{site.data.keyword.cloud_notm}} command line interface (CLI) 

1. Download and install the [{{site.data.keyword.cloud_notm}} CLI](https://console.bluemix.net/docs/cli/reference/bluemix_cli/download_cli.html) tool.

2. Log in to {{site.data.keyword.cloud_notm}}

    ```
    bx login
    ```

3. Switch to the organization and space you want to use for your new Compose database service.

    ```
    bx target --cf
    ```

## Step 2. Get the cluster service instance ID
{: #step-2}

1. You need to get the cluster service instance ID for your {{site.data.keyword.composeEnterprise}} instance.

    ```
    bx cf service COMPOSE_ENTERPRISE_SERVICE_NAME --guid
    ```

    The command returns a string, which is the GUID of the service instance. You use this value later to get the cluster ID value.

## Step 3. Provision a database into your cluster with the `create-service` command

Now that you have your `cluster_service_instance_id` you can use the `create-service` command to create an {{site.data.keyword.cloud_notm}} Compose database service and deploy it into your {{site.data.keyword.composeEnterprise}} cluster.


```
bx cf create-service service_name service_plan service_instance [-c PARAMETERS_AS_JSON]
```

### Command options

<dl>
<dt>service_name (required)</dt>
<dd>
The name of the Compose database service. You must use one of the following values: 
    <ul>
        <li>`compose-for-elasticsearch`</li>
        <li>`compose-for-etcd`</li>
        <li>`compose-for-janusgraph`</li>
        <li>`compose-for-mongodb`</li>
        <li>`compose-for-mysql`</li>
        <li>`compose-for-postgresql`</li>
        <li>`compose-for-rabbitmq`</li>
        <li>`compose-for-redis`</li>
        <li>`compose-for-rethinkdb`</li>
        <li>`compose-for-scylladb`</li>
    </ul>
</dd>
<dt>service_plan (required)</dt>
<dd>
The pricing plan for the new service. The value must be `Enterprise` to deploy the database into a {{site.data.keyword.composeEnterprise}} cluster.
</dd>
<dt>service_instance (required)</dt>
<dd>
The name of the new Compose database service that you want to provision.
</dd>
<dt>[-c PARAMETERS_AS_JSON] (required)</dt>
<dd>
The parameters are formatted as a JSON object and must contain either of the following values:
    <dl>
    <dt>cluster_service_instance_id</dt>
    <dd>The Cluster Service Instance ID of your {{site.data.keyword.composeEnterprise}} cluster. You can obtain the value by following [Step 2: Get the cluster service instance ID](#step2).
    </dd>
    </dl>
    <dl>
    <dt>cluster_id</dt>
    <dd>The Cluster ID of your {{site.data.keyword.composeEnterprise}} cluster. You can find this value in the dashboard of your {{site.data.keyword.composeEnterprise}} service instance.
    </dd>
    </dl>
</dd>
</dl>

For example, to deploy a {{site.data.keyword.composeForElasticsearch}} service called 'myComposeForEnterpriseService' into a {{site.data.keyword.composeEnterprise}} cluster, where the `cluster_service_instance_id` is '12345678-90ab-cdef-1234567890a', you would use the following command.

```
bx cf create-service compose-for-elasticsearch Enterprise myComposeForEnterpriseService -c '{"cluster_service_instance_id": "12345678-90ab-cdef-1234567890a"}'
```
