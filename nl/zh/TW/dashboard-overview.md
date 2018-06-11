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

# 儀表板概觀

您可以從服務儀表板管理您的 {{site.data.keyword.composeEnterprise_full}} 服務。

## 叢集詳細資料

_叢集詳細資料_ 畫面顯示 {{site.data.keyword.composeEnterprise}} 叢集的詳細資料。

![叢集詳細資料](./images/enterprise-cluster-details-ready.png "「叢集詳細資料」畫面的視圖")

### 名稱

叢集的內部 ID。

### 類型

其他 Compose {{site.data.keyword.cloud_notm}} 服務會使用此欄位，以顯示服務所提供的資料庫類型，以及服務使用的資料庫版本。若為 {{site.data.keyword.composeEnterprise}} 服務，值一律是_企業叢集_。

### 狀態

{{site.data.keyword.composeEnterprise}} 叢集的狀態。

### 地區

{{site.data.keyword.composeEnterprise}} 叢集所在的 {{site.data.keyword.cloud_notm}} 地區。

## 實例管理 API

您可以透過 {{site.data.keyword.cloud_notm}} Compose API 管理 {{site.data.keyword.composeForElasticsearch}} 服務。

![叢集詳細資料](./images/enterprise-cluster-api.png "「實例管理 API」的視圖")

### 基礎端點

基礎端點是由叢集所在地區及叢集 ID 所組成。可在每個端點的開頭處找到它。

### 叢集 ID

大部分呼叫都需要叢集 ID，其可識別特定的部署實例。

### 參考資訊

如需如何在所有 {{site.data.keyword.cloud_notm}} Compose 服務中使用 {{site.data.keyword.cloud_notm}} Compose API 的其他文件及參照，請閱讀 [{{site.data.keyword.cloud_notm}} Compose API](https://www.compose.com/articles/the-ibm-cloud-compose-api/)。
