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

# 将 Compose 数据库部署到 {{site.data.keyword.composeEnterprise}} 集群

## 通过控制台 {{site.data.keyword.cloud_notm}} 进行部署

如果您已经使用 {{site.data.keyword.cloud_notm}} 创建了 {{site.data.keyword.composeEnterprise_full}} 集群，那么可以指定将新的 Compose {{site.data.keyword.cloud_notm}} 数据库供应到该集群中。创建新的 Compose {{site.data.keyword.cloud_notm}} 数据库服务实例时，请从*选择部署位置*下拉列表中的可用位置列表中选择 {{site.data.keyword.composeEnterprise}} 集群的名称。

## 通过命令行进行部署

要通过命令行创建新的 Compose 数据库服务实例并将其供应到 {{site.data.keyword.composeEnterprise}} 集群中，您需要首先安装 {{site.data.keyword.cloud_notm}} 命令行界面 (CLI)，然后获取并使用 {{site.data.keyword.composeEnterprise}} 集群标识。

## 1. 设置 {{site.data.keyword.cloud_notm}} 命令行界面 (CLI) 

1. 下载并安装 [{{site.data.keyword.cloud_notm}} CLI](https://console.bluemix.net/docs/cli/reference/bluemix_cli/download_cli.html) 工具。
2. 登录到 {{site.data.keyword.cloud_notm}}。

    ```
    bx login
    ```

3. 切换到要用于新 Compose 数据库服务的组织和空间。

    ```
    bx target --cf
    ```

## 2. 获取集群服务实例标识

1. 您需要获取 {{site.data.keyword.composeEnterprise}} 实例的集群服务实例标识：

    ```
    bx cf service COMPOSE_ENTERPRISE_SERVICE_NAME --guid
    ```

    该命令会返回一个字符串。这是服务实例的 GUID，稍后您需要将其用于获取集群标识。

## 3. 使用 `create-service` 命令将数据库供应到集群中：

现在，您有了 `cluster_service_instance_id`，可以使用 `create-service` 命令来创建 {{site.data.keyword.cloud_notm}} Compose 数据库服务，并将其部署到 {{site.data.keyword.composeEnterprise}} 集群中。


```
bx cf create-service service_name service_plan service_instance [-c PARAMETERS_AS_JSON]
```

命令选项包括：

<dl>
<dt>service_name（必需）</dt>
<dd>
Compose 数据库服务的名称。值必须为以下其中一项：
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
<dt>service_plan（必需）</dt>
<dd>
新服务的价格套餐。在此，值必须为 `Enterprise`，才能将数据库部署到 {{site.data.keyword.composeEnterprise}} 集群中。
</dd>
<dt>service_instance（必需）</dt>
<dd>
要供应的新 Compose 数据库服务的名称。
</dd>
<dt>[-c PARAMETERS_AS_JSON]（必需）</dt>
<dd>
参数的格式设置为 JSON 对象，并且应该包含以下任一值：
    <dl>
    <dt>cluster_service_instance_id</dt>
    <dd>{{site.data.keyword.composeEnterprise}} 集群的集群服务实例标识。您可以通过遵循本指南的步骤 2 来获取此值。
    </dd>
    </dl>
    <dl>
    <dt>cluster_id</dt>
    <dd>{{site.data.keyword.composeEnterprise}} 集群的集群标识。您可以在 {{site.data.keyword.composeEnterprise}} 服务实例的仪表板中找到此值。
    </dd>
    </dl>
</dd>
</dl>

例如，要将名为“myComposeForEnterpriseService”的 {{site.data.keyword.composeForElasticsearch}} 服务部署到 {{site.data.keyword.composeEnterprise}} 集群（其中 `cluster_service_instance_id` 为“12345678-90ab-cdef-1234567890a”），应该使用以下命令。

```
bx cf create-service compose-for-elasticsearch Enterprise myComposeForEnterpriseService -c '{"cluster_service_instance_id": "12345678-90ab-cdef-1234567890a"}'
```
