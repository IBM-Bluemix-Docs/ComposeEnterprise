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

# 概説チュートリアル
{: #getting-started}

{{site.data.keyword.composeEnterprise}} の使用を開始するには、以下の手順を実行します。

## {{site.data.keyword.composeEnterprise}} サービス・インスタンスのプロビジョニング
{: #provisioning-compose-enterprise-instance}

{{site.data.keyword.composeEnterprise}} コンソールまたはコマンド・ラインを使用して、新しい {{site.data.keyword.cloud_notm}} インスタンスをプロビジョンできます。

**注:** {{site.data.keyword.composeEnterprise}} クラスターのプロビジョンには、5 から 7 営業日程度の時間がかかる場合があります。

## {{site.data.keyword.composeEnterprise}} コンソールからの {{site.data.keyword.cloud_notm}} サービス・インスタンスのプロビジョニング

すべてのフィールドに値を設定して、[{{site.data.keyword.composeEnterprise}} インスタンスを作成](https://console.{DomainName}/catalog/services/compose-enterprise/)します。

**注:**
- {{site.data.keyword.composeEnterprise}} クラスターの名前は最大 19 文字で、英数字だけを使用できます。
- *クラウド・プロバイダーの地域*を選択するときに選択するロケーションが、{{site.data.keyword.composeEnterprise}} インスタンスがデプロイされる SoftLayer データ・センターとなります。


## コマンド・ラインからの {{site.data.keyword.composeEnterprise}} サービス・インスタンスのプロビジョニング

1. [{{site.data.keyword.cloud_notm}} CLI](https://console.{DomainName}/docs/cli/reference/bluemix_cli/download_cli.html) ツールをダウンロードしてインストールします。
2. {{site.data.keyword.cloud_notm}} にログインします。

  ```
  bx login
  ```

3. 新しい Compose データベース・サービスで使用する組織とスペースに切り替えます。

  ```
  bx target --cf
  ```

4. 次のように、`create-service` コマンドを使用して、サービスのインスタンスをプロビジョンします。

  ```
  bx cf create-service service_name service_plan service_instance -c start_command
  ```

  コマンド・オプションは以下のとおりです。

  <dl>
    <dt>service_name</dt>
    <dd>
インスタンスを作成する {{site.data.keyword.cloud_notm}} サービスの名前。値は `compose-enterprise` でなければなりません。</dd>
    <dt>service_plan</dt>
    <dd>
新しいサービスの価格設定プラン。値は `Enterprise` でなければなりません。</dd>
    <dt>service_instance</dt>
    <dd>
プロビジョンする新しい Compose データベース・サービスの名前。</dd>
    <dt>-c start_command</dt>
    <dd>
start_command に、プロビジョンする {{site.data.keyword.composeEnterprise}} クラスターの詳細情報を組み込みます。これは、配列の形式で設定し、以下の値を組み込むことができます。<dl>
        <dt>contact_name (必須)</dt>
        <dd>
{{site.data.keyword.composeEnterprise}} クラスターの所有者の名前。</dd>
        <dt>contact_phone (必須)</dt>
        <dd>
{{site.data.keyword.composeEnterprise}} クラスター所有者の連絡先電話番号。</dd>
        <dt>contact_email (必須)</dt>
        <dd>
{{site.data.keyword.composeEnterprise}} クラスター所有者の E メール・アドレス。</dd>
        <dt>provider_region (必須)</dt>
        <dd>
{{site.data.keyword.composeEnterprise}} インスタンスをデプロイする SoftLayer データ・センター。有効な値は、'amsterdam'、'chennai'、'dallas'、'frankfurt'、'hong kong'、'houston'、'london'、'melbourne'、'milan'、'montreal'、'oslo'、 'paris'、'queretaro'、'san jose'、'sao paulo'、'seattle'、'seoul'、'singapore'、'sydney'、'tokyo'、'toronto'、'washington dc' です。</dd>
        <dt>cluster_name (オプション)</dt>
        <dd>
プロビジョンする {{site.data.keyword.composeEnterprise}} クラスターの名前を選択します。最大長は 19 文字で、英数字だけを使用できます。</dd>
        <dt>notes (オプション)</dt>
        <dd>
クラスターに関連する注釈 (「ベア・メタル」など) を追加します。</dd>
      </dl>
    </dd>
  </dl>

サンプル `bx cf create-service` の使用法:

```
bx cf create-service compose-enterprise Enterprise myComposeEnterpriseServiceName -c '{"contact_name": "myName", "contact_phone": "888-888-8888", "contact_email": "myEmail@ibm.com", "provider_region": "dallas", "cluster_name": "myClusterName123", "notes": "Bare Metal" }'
```

{{site.data.keyword.composeEnterprise}} クラスターが使用可能な状態になったら、そのクラスターに Compose {{site.data.keyword.cloud_notm}} データベースをプロビジョンして、独立したクラスターの中でデータベースの自動スケーリング機能や保存時/移動時の暗号化機能を利用することができるようになります。

## 次のステップ

{{site.data.keyword.composeEnterprise}} クラスターのプロビジョンと構成が完了したので、クラスターにデータベースをデプロイする準備が整ったことになります。

既存の Compose データベース {{site.data.keyword.cloud_notm}} サービスから新しいデータベースを作成する時に、Compose {{site.data.keyword.cloud_notm}} データベースを {{site.data.keyword.composeEnterprise}} クラスターにデプロイできます。{{site.data.keyword.cloud_notm}} コンソールまたはコマンド・ラインを使用することができます。データベースのデプロイ方法の詳細については、[{{site.data.keyword.composeEnterprise}} クラスターへの Compose データベースのデプロイ](./deploying.html)を参照してください。






