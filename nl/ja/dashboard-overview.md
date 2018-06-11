---

Copyright:
  Years: 2017, 2018
lastupdated: "2018-02-19"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# ダッシュボードの概要

サービス・ダッシュボードから {{site.data.keyword.composeEnterprise_full}} サービスを管理できます。

## クラスターの詳細

_「クラスターの詳細」_ パネルに、{{site.data.keyword.composeEnterprise}} クラスターの詳細が表示されます。

![クラスターの詳細](./images/enterprise-cluster-details-ready.png "「クラスターの詳細」パネルの表示画面")

### 名前

クラスターの内部 ID。

### タイプ

その他の Compose {{site.data.keyword.cloud_notm}} サービスは、このフィールドを使用して、サービスが提供するデータベースのタイプと、サービスが使用するデータベースのバージョンを表示します。 {{site.data.keyword.composeEnterprise}} サービスの場合は、値が常に_エンタープライズ・クラスター_になります。

### 状況

{{site.data.keyword.composeEnterprise}} クラスターの状況。

### 地域

{{site.data.keyword.composeEnterprise}} クラスターが存在する {{site.data.keyword.cloud_notm}} の地域。

## インスタンス管理 API

{{site.data.keyword.cloud_notm}} Compose API で {{site.data.keyword.composeForElasticsearch}} サービスを管理できます。

![クラスターの詳細](./images/enterprise-cluster-api.png "「インスタンス管理 API」の表示画面")

### ファウンデーション・エンドポイント

ファウンデーション・エンドポイントは、クラスターが存在する地域とクラスター ID で構成されます。 すべてのエンドポイントの先頭にあります。

### クラスター ID

クラスター ID は、ほとんどの呼び出しで必要になります。デプロイメント・インスタンスを特定するための ID です。

### 参照

{{site.data.keyword.cloud_notm}} Compose サービス全体にわたる {{site.data.keyword.cloud_notm}} Compose API の使用についての詳しい資料やリファレンスは、[ {{site.data.keyword.cloud_notm}} Compose API](https://www.compose.com/articles/the-ibm-cloud-compose-api/) を参照してください。
