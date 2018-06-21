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

# 대시보드 개요

서비스 대시보드에서 {{site.data.keyword.composeEnterprise_full}} 서비스를 관리할 수 있습니다.

## 클러스터 세부사항

_클러스터 세부사항_ 패널은 {{site.data.keyword.composeEnterprise}} 클러스터의 세부사항을 보여줍니다.

![클러스터 세부사항](./images/enterprise-cluster-details-ready.png "클러스터 세부사항 패널의 보기")

### 이름

클러스터의 내부 ID입니다.

### 유형

다른 Compose {{site.data.keyword.cloud_notm}} 서비스는 서비스에서 제공하는 데이터베이스의 유형과 사용자의 서비스가 사용하는 데이터베이스 버전을 표시하기 위해 이 필드를 사용합니다. {{site.data.keyword.composeEnterprise}} 서비스의 경우 이 값은 항상 _엔터프라이즈 클러스터_입니다.

### 상태

{{site.data.keyword.composeEnterprise}} 클러스터의 상태입니다.

### 지역

{{site.data.keyword.composeEnterprise}} 클러스터가 있는 {{site.data.keyword.cloud_notm}} 지역입니다.

## 인스턴스 관리 API

{{site.data.keyword.cloud_notm}} Compose API를 통해 {{site.data.keyword.composeForElasticsearch}} 서비스를 관리할 수 있습니다.

![클러스터 세부사항](./images/enterprise-cluster-api.png "인스턴스 관리 API의 보기")

### 기반 엔드포인트

기반 엔드포인트는 클러스터가 있는 지역과 클러스터 ID로 구성됩니다. 이는 모든 엔드포인트의 시작 부분에서 볼 수 있습니다.

### 클러스터 ID

클러스터 ID는 대부분의 호출에 필요하며, 특정 배치 인스턴스를 식별합니다.

### 참조

모든 {{site.data.keyword.cloud_notm}} Compose 서비스에서 {{site.data.keyword.cloud_notm}} Compose API를 사용하는 데 대한 추가 문서 및 참조를 보려면 [{{site.data.keyword.cloud_notm}} Compose API](https://www.compose.com/articles/the-ibm-cloud-compose-api/)를 읽어 보십시오.
