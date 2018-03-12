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

# 入门教程
{: #getting-started}

完成以下步骤，以开始使用 {{site.data.keyword.composeEnterprise}}：

## 供应 {{site.data.keyword.composeEnterprise}} 服务实例
{: #provisioning-compose-enterprise-instance}

您可以使用 {{site.data.keyword.cloud_notm}} 控制台或命令行来供应新的 {{site.data.keyword.composeEnterprise}} 实例。

**注：**供应 {{site.data.keyword.composeEnterprise}} 集群可能需要最长 5-7 个工作日。

## 通过 {{site.data.keyword.cloud_notm}} 控制台供应 {{site.data.keyword.composeEnterprise}} 服务实例

[创建 {{site.data.keyword.composeEnterprise}} 实例](https://console.{DomainName}/catalog/services/compose-enterprise/)，确保填写所有字段。

**注：**
- {{site.data.keyword.composeEnterprise}} 集群名称的最大长度为 19 个字符，并且只能包含字母数字字符。
- 选择*云提供者区域*时，选择的位置是 SoftLayer 数据中心，在其中将部署 {{site.data.keyword.composeEnterprise}} 实例。


## 通过命令行供应 {{site.data.keyword.composeEnterprise}} 服务实例

1. 下载并安装 [{{site.data.keyword.cloud_notm}} CLI](https://console.{DomainName}/docs/cli/reference/bluemix_cli/download_cli.html) 工具。
2. 登录到 {{site.data.keyword.cloud_notm}}。

  ```
  bx login
  ```

3. 切换到要用于新 Compose 数据库服务的组织和空间。

  ```
  bx target --cf
  ```

4. 使用 `create-service` 命令供应服务实例：

  ```
  bx cf create-service service_name service_plan service_instance -c start_command
  ```

  命令选项包括：

  <dl>
    <dt>service_name</dt>
    <dd>
    要创建其实例的 {{site.data.keyword.cloud_notm}} 服务的名称。值必须是 `compose-enterprise`。
    </dd>
    <dt>service_plan</dt>
    <dd>
    新服务的价格套餐。值必须是 `Enterprise`。
    </dd>
    <dt>service_instance</dt>
    <dd>
    要供应的新 Compose 数据库服务的名称。
    </dd>
    <dt>-c start_command</dt>
    <dd>
    start_command 包含要供应的 {{site.data.keyword.composeEnterprise}} 集群的详细信息。其格式设置为数组，并且可以包含以下值：
      <dl>
        <dt>contact_name（必需）</dt>
        <dd>
        {{site.data.keyword.composeEnterprise}} 集群所有者的名称
        </dd>
        <dt>contact_phone（必需）</dt>
        <dd>
        {{site.data.keyword.composeEnterprise}} 集群所有者的联系电话号码
        </dd>
        <dt>contact_email（必需）</dt>
        <dd>
        {{site.data.keyword.composeEnterprise}} 集群所有者的电子邮件地址
        </dd>
        <dt>provider_region（必需）</dt>
        <dd>
        要在其中部署 {{site.data.keyword.composeEnterprise}} 实例的 SoftLayer 数据中心。有效值为：“amsterdam”、“chennai”、“dallas”、“frankfurt”、“hong kong”、“houston”、“london”、“melbourne”、“milan”、“montreal”、“oslo”、“paris”、“queretaro”、“san jose”、“sao paulo”、“seattle”、“seoul”、“singapore”、“sydney”、“tokyo”、“toronto”、“washington dc”。
        </dd>
        <dt>cluster_name（可选）</dt>
        <dd>
        选择已供应 {{site.data.keyword.composeEnterprise}} 集群的名称。名称的最大长度为 19 个字符，并且只能包含字母数字字符。
        </dd>
        <dt>notes（可选）</dt>
        <dd>
        添加与集群相关的任何注释，例如“裸机”。
        </dd>
      </dl>
    </dd>
  </dl>

样本 `bx cf create-service` 用法：

```
bx cf create-service compose-enterprise Enterprise myComposeEnterpriseServiceName -c '{"contact_name": "myName", "contact_phone": "888-888-8888", "contact_email": "myEmail@ibm.com", "provider_region": "dallas", "cluster_name": "myClusterName123", "notes": "Bare Metal" }'
```

{{site.data.keyword.composeEnterprise}} 集群可用时，您能将 Compose {{site.data.keyword.cloud_notm}} 数据库供应到集群中，并受益于在隔离集群中使用静态和动态加密来自动扩展数据库。

## 后续步骤

现在，您已供应并配置了 {{site.data.keyword.composeEnterprise}} 集群，可随时将数据库部署到集群中。

通过任何现有的 Compose 数据库 {{site.data.keyword.cloud_notm}} 服务创建新的数据库时，可以将 Compose {{site.data.keyword.cloud_notm}} 数据库部署到 {{site.data.keyword.composeEnterprise}} 集群中。您可以使用 {{site.data.keyword.cloud_notm}} 控制台或命令行。有关如何部署数据库的详细信息，请参阅[将 Compose 数据库部署到 {{site.data.keyword.composeEnterprise}} 集群](./deploying.html)。






