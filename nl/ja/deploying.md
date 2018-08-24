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

# {{site.data.keyword.composeEnterprise}} クラスターへの Compose データベースのデプロイ

## {{site.data.keyword.cloud_notm}} コンソールからのデプロイ

{{site.data.keyword.cloud_notm}} を使用して {{site.data.keyword.composeEnterprise_full}} クラスターをすでに作成している場合は、新しい Compose {{site.data.keyword.cloud_notm}} データベースをそのクラスターにプロビジョンするよう指定できます。 新しい Compose {{site.data.keyword.cloud_notm}} データベース・サービス・インスタンスを作成する時に、*「デプロイメントのロケーションの選択 (Select Location for Deployment)」*ドロップダウンにある使用可能なロケーションのリストから {{site.data.keyword.composeEnterprise}} クラスターの名前を選択してください。

## コマンド・ラインからのデプロイ

コマンド・ラインから Compose データベース・サービスの新しいインスタンスを作成して {{site.data.keyword.composeEnterprise}} クラスターにプロビジョンするには、まず {{site.data.keyword.cloud_notm}} コマンド・ライン・インターフェース (CLI) をインストールしてから、{{site.data.keyword.composeEnterprise}} クラスター ID を取得して使用する必要があります。

## 1. {{site.data.keyword.cloud_notm}} コマンド・ライン・インターフェース (CLI) をセットアップします。 

1. [{{site.data.keyword.cloud_notm}} CLI](https://console.bluemix.net/docs/cli/reference/bluemix_cli/download_cli.html) ツールをダウンロードしてインストールします。
2. {{site.data.keyword.cloud_notm}} にログインします。

    ```
    bx login
    ```

3. 新しい Compose データベース・サービスで使用する組織とスペースに切り替えます。

    ```
    bx target --cf
    ```

## 2. クラスター・サービス・インスタンス ID を取得します

1. {{site.data.keyword.composeEnterprise}} インスタンスのクラスター・サービス・インスタンス ID を取得する必要があります。

    ```
    bx cf service COMPOSE_ENTERPRISE_SERVICE_NAME --guid
    ```

    このコマンドからストリングが返されます。 それがサービス・インスタンスの GUID であり、後でクラスター ID を取得する時に必要になります。

## 3. `create-service` コマンドを使用して、データベースをクラスターにプロビジョンします。

`cluster_service_instance_id` を取得できたので、`create-service` コマンドを使用して、{{site.data.keyword.cloud_notm}} Compose データベース・サービスを作成して {{site.data.keyword.composeEnterprise}} クラスターにデプロイできます。


```
bx cf create-service service_name service_plan service_instance [-c PARAMETERS_AS_JSON]
```

コマンド・オプションは以下のとおりです。

<dl>
<dt>service_name (必須)</dt>
<dd>
Compose データベース・サービスの名前。 値は以下のいずれかでなければなりません。 
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
<dt>service_plan (必須)</dt>
<dd>
新しいサービスの価格設定プラン。 {{site.data.keyword.composeEnterprise}} クラスターにデータベースをデプロイする場合は、`Enterprise` という値にしなければなりません。
</dd>
<dt>service_instance (必須)</dt>
<dd>
プロビジョンする新しい Compose データベース・サービスの名前。
</dd>
<dt>[-c PARAMETERS_AS_JSON] (必須)</dt>
<dd>
パラメーターは JSON オブジェクトの形式に設定し、以下のいずれかの値を含める必要があります。
    <dl>
    <dt>cluster_service_instance_id</dt>
    <dd>{{site.data.keyword.composeEnterprise}} クラスターのクラスター・サービス・インスタンス ID。 このガイドのステップ 2 に従うと、この値を入手することができます。
    </dd>
    </dl>
    <dl>
    <dt>cluster_id</dt>
    <dd>{{site.data.keyword.composeEnterprise}} クラスターのクラスター ID。 この値は、{{site.data.keyword.composeEnterprise}} サービス・インスタンスのダッシュボードで確認できます。
    </dd>
    </dl>
</dd>
</dl>

例えば、myComposeForEnterpriseService という名前の {{site.data.keyword.composeForElasticsearch}} サービスを 12345678-90ab-cdef-1234567890a という `cluster_service_instance_id` の {{site.data.keyword.composeEnterprise}} クラスターにデプロイするには、以下のコマンドを使用します。

```
bx cf create-service compose-for-elasticsearch Enterprise myComposeForEnterpriseService -c '{"cluster_service_instance_id": "12345678-90ab-cdef-1234567890a"}'
```
