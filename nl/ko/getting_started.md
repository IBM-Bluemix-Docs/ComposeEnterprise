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

# 시작하기 튜토리얼
{: #getting-started}

{{site.data.keyword.composeEnterprise}}를 시작하려면 다음 단계를 완료하십시오.

## {{site.data.keyword.composeEnterprise}} 서비스 인스턴스 프로비저닝
{: #provisioning-compose-enterprise-instance}

{{site.data.keyword.cloud_notm}} 콘솔 또는 명령행을 사용하여 새 {{site.data.keyword.composeEnterprise}} 인스턴스를 프로비저닝할 수 있습니다.

**참고:** {{site.data.keyword.composeEnterprise}} 클러스터가 프로비저닝되는 데는 최대 5 - 7영업일이 소요될 수 있습니다.

## {{site.data.keyword.cloud_notm}} 콘솔에서 {{site.data.keyword.composeEnterprise}} 서비스 인스턴스 프로비저닝

모든 필드를 완료하여 [{{site.data.keyword.composeEnterprise}} 인스턴스를 작성](https://console.{DomainName}/catalog/services/compose-enterprise/)하십시오.

**참고:**
- {{site.data.keyword.composeEnterprise}} 클러스터 이름의 최대 길이는 19자이며 영숫자 문자만 포함할 수 있습니다.
- *클라우드 제공자 지역*을 선택할 때 선택하는 위치는 {{site.data.keyword.composeEnterprise}} 인스턴스가 배치될 SoftLayer 데이터 센터입니다.


## 명령행에서 {{site.data.keyword.composeEnterprise}} 서비스 인스턴스 프로비저닝

1. [{{site.data.keyword.cloud_notm}} CLI](https://console.{DomainName}/docs/cli/reference/bluemix_cli/download_cli.html) 도구를 다운로드하여 설치하십시오.
2. {{site.data.keyword.cloud_notm}}에 로그인하십시오.

  ```
  bx login
  ```

3. 새 Compose 데이터베이스 서비스에 대해 사용할 조직 및 영역으로 전환하십시오.

  ```
  bx target --cf
  ```

4. `create-service` 명령을 사용하여 서비스의 인스턴스를 프로비저닝하십시오.

  ```
  bx cf create-service service_name service_plan service_instance -c start_command
  ```

  명령 옵션은 다음과 같습니다.

  <dl>
    <dt>service_name</dt>
    <dd>
    인스턴스를 작성할 {{site.data.keyword.cloud_notm}} 서비스의 이름입니다. 이 값은 `compose-enterprise`여야 합니다.
    </dd>
    <dt>service_plan</dt>
    <dd>
    새 서비스의 가격 책정 플랜입니다. 이 값은 `Enterprise`여야 합니다.
    </dd>
    <dt>service_instance</dt>
    <dd>
    프로비저닝할 새 Compose 데이터베이스 서비스의 이름입니다.
    </dd>
    <dt>-c start_command</dt>
    <dd>
    start_command는 프로비저닝할 {{site.data.keyword.composeEnterprise}} 클러스터의 세부사항을 포함합니다. 이는 배열로 형식화되며 다음 값을 포함할 수 있습니다.
      <dl>
        <dt>contact_name(필수)</dt>
        <dd>
        {{site.data.keyword.composeEnterprise}} 클러스터 소유자의 이름입니다.
        </dd>
        <dt>contact_phone(필수)</dt>
        <dd>
        {{site.data.keyword.composeEnterprise}} 클러스터 소유자의 연락처 전화번호입니다.
        </dd>
        <dt>contact_email(필수)</dt>
        <dd>
        {{site.data.keyword.composeEnterprise}} 클러스터 소유자의 이메일 주소입니다.
        </dd>
        <dt>provider_region(필수)</dt>
        <dd>
        {{site.data.keyword.composeEnterprise}} 인스턴스를 배치할 SoftLayer 데이터 센터입니다. 올바른 값은 'amsterdam', 'chennai', 'dallas', 'frankfurt', 'hong kong', 'houston', 'london', 'melbourne', 'milan', 'montreal', 'oslo', 'paris', 'queretaro', 'san jose', 'sao paulo', 'seattle', 'seoul', 'singapore', 'sydney', 'tokyo', 'toronto', 'washington dc'입니다.
        </dd>
        <dt>cluster_name(선택사항)</dt>
        <dd>
        프로비저닝되는 {{site.data.keyword.composeEnterprise}} 클러스터의 이름을 선택하십시오. 최대 길이는 19자이며 영숫자 문자만 포함할 수 있습니다.
        </dd>
        <dt>notes(선택사항)</dt>
        <dd>
        'Bare Metal'과 같이, 클러스터와 관련된 참고사항을 추가합니다.
        </dd>
      </dl>
    </dd>
  </dl>

샘플 `bx cf create-service` 사용법:

```
bx cf create-service compose-enterprise Enterprise myComposeEnterpriseServiceName -c '{"contact_name": "myName", "contact_phone": "888-888-8888", "contact_email": "myEmail@ibm.com", "provider_region": "dallas", "cluster_name": "myClusterName123", "notes": "Bare Metal" }'
```

{{site.data.keyword.composeEnterprise}} 클러스터가 사용 가능하게 되면 Compose {{site.data.keyword.cloud_notm}} 데이터베이스를 클러스터에 프로비저닝하여, 격리된 클러스터에서의 저장 시 및 전송 시 암호화를 사용하는 Auto-Scaling 데이터베이스의 이점을 누릴 수 있습니다.

## 다음 단계

{{site.data.keyword.composeEnterprise}} 클러스터를 프로비저닝하여 구성하고 나면 클러스터에 데이터베이스를 배치할 준비가 된 것입니다.

사용자는 기존 Compose 데이터베이스 {{site.data.keyword.cloud_notm}} 서비스로부터 새 데이터베이스를 작성할 때 Compose {{site.data.keyword.cloud_notm}} 데이터베이스를 {{site.data.keyword.composeEnterprise}} 클러스터에 배치할 수 있습니다. 이 경우 {{site.data.keyword.cloud_notm}} 콘솔 또는 명령행을 사용할 수 있습니다. 데이터베이스 배치 방법에 대한 세부사항은 [{{site.data.keyword.composeEnterprise}} 클러스터에 Compose 데이터베이스 배치](./deploying.html)를 참조하십시오.






