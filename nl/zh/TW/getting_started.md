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

# 入門指導教學
{: #getting-started}

請完成下列步驟，以開始使用 {{site.data.keyword.composeEnterprise}}：

## 佈建 {{site.data.keyword.composeEnterprise}} 服務實例
{: #provisioning-compose-enterprise-instance}

您可以使用 {{site.data.keyword.cloud_notm}} 主控台或指令行，佈建新的 {{site.data.keyword.composeEnterprise}} 實例。

**附註：**若要佈建您的 {{site.data.keyword.composeEnterprise}} 叢集，最多可能需要 5-7 個營業日。

## 從 {{site.data.keyword.cloud_notm}} 主控台佈建 {{site.data.keyword.composeEnterprise}} 服務實例

[建立 {{site.data.keyword.composeEnterprise}} 實例](https://console.{DomainName}/catalog/services/compose-enterprise/)，確保您完成所有欄位。

**附註：**
- {{site.data.keyword.composeEnterprise}} 叢集名稱的長度最多為 19 個字元，而且只能包含英數字元。
- 當選擇*雲端提供者地區* 時，您選取的位置為將在其中部署 {{site.data.keyword.composeEnterprise}} 實例的 SoftLayer 資料中心。


## 從指令行佈建 {{site.data.keyword.composeEnterprise}} 服務實例

1. 下載並安裝 [{{site.data.keyword.cloud_notm}} CLI](https://console.{DomainName}/docs/cli/reference/bluemix_cli/download_cli.html) 工具。
2. 登入 {{site.data.keyword.cloud_notm}}。

  ```
  bx login
  ```

3. 切換至您要對新的 Compose 資料庫服務使用的組織及空間。

  ```
  bx target --cf
  ```

4. 使用 `create-service` 指令來佈建服務的實例：

  ```
  bx cf create-service service_name service_plan service_instance -c start_command
  ```

  指令選項如下：

  <dl>
    <dt>service_name</dt>
    <dd>
您要建立其實例之 {{site.data.keyword.cloud_notm}} 服務的名稱。此值必須是 `compose-enterprise`。
    </dd>
    <dt>service_plan</dt>
    <dd>
新服務的定價方案。此值必須是 `Enterprise`。
    </dd>
    <dt>service_instance</dt>
    <dd>
您要佈建之新 Compose 資料庫服務的名稱。
    </dd>
    <dt>-c start_command</dt>
    <dd>
start_command 包含您要佈建之 {{site.data.keyword.composeEnterprise}} 叢集的詳細資料。它會格式化為陣列，而且可以包含下列值：
      <dl>
        <dt>contact_name（必要）</dt>
        <dd>
{{site.data.keyword.composeEnterprise}} 叢集的擁有者名稱
        </dd>
        <dt>contact_phone（必要）</dt>
        <dd>
{{site.data.keyword.composeEnterprise}} 叢集擁有者的聯絡電話
        </dd>
        <dt>contact_email（必要）</dt>
        <dd>
{{site.data.keyword.composeEnterprise}} 叢集擁有者的電子郵件位址
        </dd>
        <dt>provider_region（必要）</dt>
        <dd>
您要在其中部署 {{site.data.keyword.composeEnterprise}} 實例的 SoftLayer 資料中心。有效值為：'amsterdam'、'chennai'、'dallas'、'frankfurt'、'hong kong'、'houston'、'london'、'melbourne'、'milan'、'montreal'、'oslo'、'paris'、'queretaro'、'san jose'、'sao paulo'、'seattle'、'seoul'、'singapore'、'sydney'、'tokyo'、'toronto'、'washington dc'。
        </dd>
        <dt>cluster_name（選用）</dt>
        <dd>
選擇您已佈建之 {{site.data.keyword.composeEnterprise}} 叢集的名稱。長度上限為 19 個字元，而且只能包含英數字元。
        </dd>
        <dt>notes（選用）</dt>
        <dd>
新增任何與叢集相關的附註，例如 'Bare Metal'。
        </dd>
      </dl>
    </dd>
  </dl>

範例 `bx cf create-service` 用法：

```
bx cf create-service compose-enterprise Enterprise myComposeEnterpriseServiceName -c '{"contact_name": "myName", "contact_phone": "888-888-8888", "contact_email": "myEmail@ibm.com", "provider_region": "dallas", "cluster_name": "myClusterName123", "notes": "Bare Metal" }'
```

當「{{site.data.keyword.composeEnterprise}} 叢集」可用時，您便能夠將 Compose {{site.data.keyword.cloud_notm}} 資料庫佈建至叢集，並享有下列好處：自動調整資料庫，以及在隔離的叢集內進行靜態及動態加密。

## 後續步驟。

既然已佈建並配置 {{site.data.keyword.composeEnterprise}} 叢集，您就可以開始將資料庫部署至叢集。

從任何一個現有的 Compose 資料庫 {{site.data.keyword.cloud_notm}} 服務建立新的資料庫時，您可以將 Compose {{site.data.keyword.cloud_notm}} 資料庫部署至 {{site.data.keyword.composeEnterprise}} 叢集。您可以使用 {{site.data.keyword.cloud_notm}} 主控台或指令行。如需如何部署資料庫的詳細資料，請參閱[將 Compose 資料庫部署至 {{site.data.keyword.composeEnterprise}} 叢集](./deploying.html)。






