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

If you have already created an {{site.data.keyword.composeEnterprise_full}} cluster using {{site.data.keyword.cloud_notm}}, you can specify that your new Compose {{site.data.keyword.cloud_notm}} database is provisioned into the cluster. Select the name of the {{site.data.keyword.composeEnterprise}} cluster from the list of available locations in the *Select Location for Deployment* drop-down when you are creating the new Compose {{site.data.keyword.cloud_notm}} database service instance.

## Deploying from the command line

To create a new instance of a Compose database service and provision it into a {{site.data.keyword.composeEnterprise}} cluster, from the command line you'll need to first install the {{site.data.keyword.cloud_notm}} command line interface (CLI), then get and use the {{site.data.keyword.composeEnterprise}} cluster ID.

## 1. Set up the {{site.data.keyword.cloud_notm}} command line interface (CLI) 

1. Download and install the [{{site.data.keyword.cloud_notm}} CLI](https://console.bluemix.net/docs/cli/reference/bluemix_cli/download_cli.html) tool.
2. Log in to {{site.data.keyword.cloud_notm}}

    ```
    bx login
    ```

3. Switch to the organization and space you want to use for your new Compose database service.

    ```
    bx target --cf
    ```

## 2. Get the cluster service instance ID

1. You'll need to get the cluster service instance ID for your {{site.data.keyword.composeEnterprise}} instance:

    ```
    bx cf service COMPOSE_ENTERPRISE_SERVICE_NAME --guid
    ```

    The command returns a string. This is the GUID of the service instance, and you'll need it later on to get the cluster ID.

## 3. Provision a database into your cluster with the `create-service` command:

Now that you have your `cluster_service_instance_id` you can use the `create-service` command to create an {{site.data.keyword.cloud_notm}} Compose database service and deploy it into your {{site.data.keyword.composeEnterprise}} cluster.


```
bx cf create-service service_name service_plan service_instance [-c PARAMETERS_AS_JSON]
```

The command options are:

<dl>
<dt>service_name (required)</dt>
<dd>
The name of the Compose database service. The value must be one of the following: 
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
The pricing plan for the new service. The value here must be `Enterprise` in order to deploy the database into a {{site.data.keyword.composeEnterprise}} cluster.
</dd>
<dt>service_instance (required)</dt>
<dd>
The name of the new Compose Database service that you want to provision.
</dd>
<dt>[-c PARAMETERS_AS_JSON] (required)</dt>
<dd>
The parameters are formatted as a JSON object and should contain either of the following values:
    <dl>
    <dt>cluster_service_instance_id</dt>
    <dd>The Cluster Service Instance ID of your {{site.data.keyword.composeEnterprise}} cluster. You can obtain this value by following step 2 of this guide.
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
