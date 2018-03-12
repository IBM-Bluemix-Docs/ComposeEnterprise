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

# Tutorial de introdução
{: #getting-started}

Conclua estas etapas para obter uma introdução ao {{site.data.keyword.composeEnterprise}}:

## Provisionando uma instância de serviço do {{site.data.keyword.composeEnterprise}}
{: #provisioning-compose-enterprise-instance}

É possível provisionar uma nova instância do {{site.data.keyword.composeEnterprise}} usando o console do {{site.data.keyword.cloud_notm}} ou a linha de comandos.

**Nota:** pode levar até 5-7 dias úteis para seu cluster do {{site.data.keyword.composeEnterprise}} ser provisionado.

## Provisionando uma instância de serviço do {{site.data.keyword.composeEnterprise}} por meio do console do {{site.data.keyword.cloud_notm}}

[Crie uma instância do {{site.data.keyword.composeEnterprise}}](https://console.{DomainName}/catalog/services/compose-enterprise/), assegurando-se de concluir todos os campos.

**Notas:**
- O nome do cluster do {{site.data.keyword.composeEnterprise}} pode ter um comprimento máximo de 19 caracteres e pode conter apenas caracteres alfanuméricos.
- Ao escolher uma *Região do provedor em nuvem*, o local selecionado será o data center do SoftLayer no qual a instância do {{site.data.keyword.composeEnterprise}} será implementada.


## Provisionando uma instância de serviço do {{site.data.keyword.composeEnterprise}} por meio da linha de comandos

1. Faça download e instale a ferramenta [{{site.data.keyword.cloud_notm}} CLI](https://console.{DomainName}/docs/cli/reference/bluemix_cli/download_cli.html).
2. Efetue login no {{site.data.keyword.cloud_notm}}

  ```
  bx login
  ```

3. Alterne para a organização e o espaço que você deseja usar para o seu novo serviço de banco de dados do Compose.

  ```
  bx target --cf
  ```

4. Provisione uma instância do serviço com o comando `create-service`:

  ```
  bx cf create-service service_name service_plan service_instance -c start_command
  ```

  As opções de comando são:

  <dl>
    <dt>service_name</dt>
    <dd>
    O nome do serviço {{site.data.keyword.cloud_notm}} do qual você deseja criar uma instância. O valor deve ser `compose-enterprise`.
    </dd>
    <dt>service_plan</dt>
    <dd>
    O plano de precificação para o novo serviço. O valor deve ser `Enterprise`.
    </dd>
    <dt>service_instance</dt>
    <dd>
    O nome do novo serviço de banco de dados do Compose que você deseja provisionar.
    </dd>
    <dt>-c start_command</dt>
    <dd>
    O start_command contém os detalhes do cluster do {{site.data.keyword.composeEnterprise}} que você deseja provisionar. Ele é formatado como uma matriz e pode conter os valores a seguir:
      <dl>
        <dt>contact_name (necessário)</dt>
        <dd>
        O nome do proprietário do cluster do {{site.data.keyword.composeEnterprise}}
        </dd>
        <dt>contact_phone (necessário)</dt>
        <dd>
        Um número de telefone de contato para o proprietário do cluster do {{site.data.keyword.composeEnterprise}}
        </dd>
        <dt>contact_email (necessário)</dt>
        <dd>
        Um endereço de e-mail para o proprietário do cluster do {{site.data.keyword.composeEnterprise}}
        </dd>
        <dt>provider_region (necessário)</dt>
        <dd>
        O data center do SoftLayer no qual você deseja que a instância do {{site.data.keyword.composeEnterprise}} seja implementada. Os valores válidos são: 'amsterdam', 'chennai', 'dallas', 'frankfurt', 'hong kong', 'houston', 'london', 'melbourne', 'milan', 'montreal', 'oslo', 'paris', 'queretaro', 'san jose', 'sao paulo', 'seattle', 'seoul', 'singapore', 'sydney', 'tokyo', 'toronto', 'washington dc'.
        </dd>
        <dt>cluster_name (opcional)</dt>
        <dd>
        Escolha um nome para seu cluster provisionado do {{site.data.keyword.composeEnterprise}}. O comprimento máximo é 19 caracteres e pode conter apenas caracteres alfanuméricos.
        </dd>
        <dt>notes (opcional)</dt>
        <dd>
        Inclua quaisquer notas relacionadas ao seu cluster, por exemplo 'Bare Metal'.
        </dd>
      </dl>
    </dd>
  </dl>

Amostra de uso de `bx cf create-service`:

```
bx cf create-service compose-enterprise Enterprise myComposeEnterpriseServiceName -c '{"contact_name": "myName", "contact_phone": "888-888-8888", "contact_email": "myEmail@ibm.com", "provider_region": "dallas", "cluster_name": "myClusterName123", "notes": "Bare Metal" }'
```

Quando o cluster do {{site.data.keyword.composeEnterprise}} estiver disponível, você será capaz de provisionar bancos de dados do Compose do {{site.data.keyword.cloud_notm}} no cluster e aproveitar os benefícios de bancos de dados de auto-scaling com criptografia inativa e em movimento dentro de um cluster isolado.

## Próximas etapas.

Agora que seu cluster do {{site.data.keyword.composeEnterprise}} está provisionado e configurado, você está pronto para implementar bancos de dados no cluster.

É possível implementar um banco de dados do Compose do {{site.data.keyword.cloud_notm}} em um cluster do {{site.data.keyword.composeEnterprise}} ao criar um novo banco de dados de qualquer um dos serviços existentes do {{site.data.keyword.cloud_notm}} do banco de dados do Compose. É possível usar o console ou a linha de comandos do {{site.data.keyword.cloud_notm}}. Para obter detalhes sobre como implementar bancos de dados, veja [Implementando um banco de dados do Compose em um cluster do {{site.data.keyword.composeEnterprise}}](./deploying.html).






