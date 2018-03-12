---

Copyright:
  Years: 2017, 2018
lastupdated: "2018-01-30"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 仪表板概述

您可以从服务仪表板管理 {{site.data.keyword.composeEnterprise_full}} 服务。

## 集群详细信息

_集群详细信息_面板显示 {{site.data.keyword.composeEnterprise}} 集群的详细信息。

![集群详细信息](./images/enterprise-cluster-details-ready.png "“集群详细信息”面板的视图")

### 名称

集群的内部标识。

### 类型

其他 Compose {{site.data.keyword.cloud_notm}} 服务使用此字段来显示服务所提供的数据库类型，以及服务所使用的数据库版本。对于 {{site.data.keyword.composeEnterprise}} 服务，值始终为_企业集群_。

### 状态

{{site.data.keyword.composeEnterprise}} 集群的状态。

### 区域

{{site.data.keyword.composeEnterprise}} 集群所在的 {{site.data.keyword.cloud_notm}} 区域。

## 实例管理 API

您可以通过 {{site.data.keyword.cloud_notm}} Compose API 来管理 {{site.data.keyword.composeForElasticsearch}} 服务。

![集群详细信息](./images/enterprise-cluster-api.png "实例管理 API 的视图")

### 基础端点

基础端点由集群所在的区域和集群标识组成。基础端点位于每个端点的开头。

### 集群标识

集群标识对于大多数调用都是必需的，用于标识特定的部署实例。

### 参考

有关在所有 {{site.data.keyword.cloud_notm}} Compose 服务上使用 {{site.data.keyword.cloud_notm}} Compose API 的更多文档和参考信息，请参阅 [{{site.data.keyword.cloud_notm}} Compose API](https://www.compose.com/articles/the-ibm-cloud-compose-api/)。
