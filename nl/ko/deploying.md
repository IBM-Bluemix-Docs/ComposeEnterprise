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

# {{site.data.keyword.composeEnterprise}} 클러스터에 Compose 데이터베이스 배치

## {{site.data.keyword.cloud_notm}} 콘솔에서 배치

이미 {{site.data.keyword.cloud}}를 사용하여 {{site.data.keyword.composeEnterprise_full}}를 작성한 경우에는 새 Compose {{site.data.keyword.cloud_notm}} 데이터베이스가 클러스터에 프로비저닝되도록 지정할 수 있습니다. 새 Compose {{site.data.keyword.cloud_notm}} 데이터베이스 서비스 인스턴스를 작성할 때는 *배치 위치 선택* 드롭 다운의 사용 가능한 위치 목록에서 {{site.data.keyword.composeEnterprise}} 클러스터의 이름을 선택하십시오.

## 명령행에서 배치

명령행에서 Compose 데이터베이스 서비스의 새 인스턴스를 작성하여 {{site.data.keyword.composeEnterprise}} 클러스터에 프로비저닝하려면 먼저 {{site.data.keyword.cloud_notm}} 명령행 인터페이스(CLI)를 설치한 후 {{site.data.keyword.composeEnterprise}} 클러스터 ID를 가져와 사용해야 합니다.

## 1. {{site.data.keyword.cloud_notm}} 명령행 인터페이스(CLI) 설정 

1. [{{site.data.keyword.cloud_notm}} CLI](https://console.bluemix.net/docs/cli/reference/bluemix_cli/download_cli.html) 도구를 다운로드하여 설치하십시오.
2. {{site.data.keyword.cloud_notm}}에 로그인하십시오.

    ```
    bx login
    ```

3. 새 Compose 데이터베이스 서비스에 대해 사용할 조직 및 영역으로 전환하십시오.

    ```
    bx target --cf
    ```

## 2. {{site.data.keyword.cloud_notm}} API 토큰 가져오기

클러스터에 데이터베이스를 배치하기 위해 {{site.data.keyword.cloud_notm}} Compose API를 사용하려면 {{site.data.keyword.cloud_notm}} API 토큰이 필요합니다. 사용할 수 있는 API 토큰이 아직 없는 경우에는 이를 작성할 수 있습니다.

1. [{{site.data.keyword.cloud_notm}}](console.{DomainName}.bluemix.net) 대시보드에 로그인하십시오.
2. **관리** -> **보안** -> **{{site.data.keyword.cloud_notm}} API 키**를 선택하십시오.
3. **작성**을 클릭하십시오.
4. 키의 이름 및 설명을 입력하고 **작성**을 클릭하십시오. 생성된 키는 나중에 필요하므로 이를 복사하십시오.

## 3. 클러스터 ID 가져오기

1. 먼저 {{site.data.keyword.composeEnterprise}} 인스턴스의 서비스 인스턴스 ID를 가져와야 합니다.

    ```
    bx cf service COMPOSE_ENTERPRISE_SERVICE_NAME --guid
    ```

    이 명령은 문자열을 리턴합니다. 이 문자열은 서비스 인스턴스의 GUID이며, 이는 나중에 클러스터 ID를 가져오는 데 필요합니다.

2. {{site.data.keyword.cloud_notm}} API 토큰을 사용해, {{site.data.keyword.cloud_notm}} Compose API를 사용하여 서비스 인스턴스 ID를 Compose Enterprise `cluster_id`와 교환하십시오.

    ```
    curl -s -X GET -H ‘authorization: Bearer ’$IBM_CLOUD_API_TOKEN -H ‘content-type: application/json’ https://composebroker-dashboard-public.eu-gb.mybluemix.net/api/2016-07/instances/$SERVICE_GUID/
    ```

    이 API 호출에서 리턴된 오브젝트에는 필요한 `cluster_id` 값이 포함되어 있습니다.

## 4. `create-service` 명령을 사용하여 클러스터에 데이터베이스 프로비저닝

이제 `cluster_id`가 있으므로 `create-service` 명령을 사용하여 {{site.data.keyword.cloud_notm}} Compose 데이터베이스를 작성하고 이를 Compose Enterprise 클러스터에 배치할 수 있습니다.


```
bx cf create-service service_name service_plan service_instance [-c PARAMETERS_AS_JSON]
```

명령 옵션은 다음과 같습니다.

<dl>
<dt>service_name (필수)</dt>
<dd>
Compose 데이터베이스 서비스의 이름입니다. 이 값은 다음 항목 중 하나여야 합니다. 
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
<dt>service_plan (필수)</dt>
<dd>
새 서비스의 가격 책정 플랜입니다. 데이터베이스를 {{site.data.keyword.composeEnterprise}} 클러스터에 배치하려면 이 값이 `Enterprise`여야 합니다.
</dd>
<dt>service_instance (필수)</dt>
<dd>
프로비저닝할 새 Compose 데이터베이스 서비스의 이름입니다.
</dd>
<dt>[-c PARAMETERS_AS_JSON] (필수)</dt>
<dd>
매개변수는 배열로 형식화되어야 하며 다음 값을 포함해야 합니다.
    <dl>
    <dt>cluster_id (필수)</dt>
    <dd>{{site.data.keyword.composeEnterprise}} 클러스터의 클러스터 ID입니다. 이 값은 {{site.data.keyword.composeEnterprise}} 서비스 인스턴스의 대시보드에서 찾을 수 있습니다.
    </dd>
    </dl>
</dd>
</dl>

예를 들어, 'myComposeForEnterpriseService'라는 {{site.data.keyword.composeForElasticsearch}} 서비스를 {{site.data.keyword.composeEnterprise}} 클러스터에 배치하려 하며 `cluster_id`가 '123456781234567812345678'인 경우에는 다음 명령을 사용합니다.

```
bx cf create-service compose-for-elasticsearch Enterprise myComposeForEnterpriseService -c '{"cluster_id": "123456781234567812345678"}'
```
