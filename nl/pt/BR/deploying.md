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

# Implementando um banco de dados do Compose em um cluster do {{site.data.keyword.composeEnterprise}}

## Implementando por meio do console do {{site.data.keyword.cloud_notm}}

Se você já tiver criado um cluster do {{site.data.keyword.composeEnterprise_full}} usando o {{site.data.keyword.cloud_notm}}, será possível especificar que seu novo banco de dados do {{site.data.keyword.cloud_notm}} do Compose seja provisionado para o cluster. Selecione o nome do cluster do {{site.data.keyword.composeEnterprise}} na lista de locais disponíveis na lista suspensa *Selecionar local para implementação* quando estiver criando a nova instância de serviço de banco de dados do Compose do {{site.data.keyword.cloud_notm}}.

## Implementando por meio da linha de comandos

Para criar uma nova instância de um serviço de banco de dados do Compose e provisioná-la em um cluster do {{site.data.keyword.composeEnterprise}}, na linha de comandos, você precisará primeiramente instalar a interface da linha de comandos (CLI) do {{site.data.keyword.cloud_notm}} e, em seguida, obter e usar o ID do cluster do {{site.data.keyword.composeEnterprise}}.

## 1. Configurar a interface da linha de comandos (CLI) do {{site.data.keyword.cloud_notm}} 

1. Faça download e instale a ferramenta [{{site.data.keyword.cloud_notm}} CLI](https://console.bluemix.net/docs/cli/reference/bluemix_cli/download_cli.html).
2. Efetue login no {{site.data.keyword.cloud_notm}}

    ```
    bx login
    ```

3. Alterne para a organização e o espaço que você deseja usar para o seu novo serviço de banco de dados do Compose.

    ```
    bx target --cf
    ```

## 2. Obter o ID da instância de serviço do cluster

1. Será necessário obter o ID da instância de serviço do cluster para sua instância do {{site.data.keyword.composeEnterprise}}:

    ```
    bx cf service COMPOSE_ENTERPRISE_SERVICE_NAME --guid
    ```

    O comando retorna uma sequência. Este é o GUID da instância de serviço, que será necessário mais tarde para obter o ID do cluster.

## 3. Provisionar um banco de dados em seu cluster com o comando `create-service`:

Agora que você tem seu `cluster_service_instance_id`, é possível usar o comando `create-service` para criar um serviço de banco de dados do {{site.data.keyword.cloud_notm}} Compose e implementá-lo no cluster do {{site.data.keyword.composeEnterprise}}.


```
bx cf create-service service_name service_plan service_instance [-c PARAMETERS_AS_JSON]
```

As opções de comando são:

<dl>
<dt>service_name (obrigatório)</dt>
<dd>
O nome do serviço de banco de dados do Compose. O valor deve ser um dos seguintes: 
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
<dt>service_plan (obrigatório)</dt>
<dd>
O plano de precificação para o novo serviço. O valor aqui deve ser `Enterprise` para implementar o banco de dados em um cluster do {{site.data.keyword.composeEnterprise}}.
</dd>
<dt>service_instance (obrigatório)</dt>
<dd>
O nome do novo serviço de banco de dados do Compose que você deseja provisionar.
</dd>
<dt>[-c PARAMETERS_AS_JSON] (necessário)</dt>
<dd>
Os parâmetros são formatados como um objeto JSON e devem conter um dos valores a seguir:
    <dl>
    <dt>cluster_service_instance_id</dt>
    <dd>O ID da instância de serviço do cluster de seu cluster do {{site.data.keyword.composeEnterprise}}. É possível obter esse valor seguindo a etapa 2 deste guia.
    </dd>
    </dl>
    <dl>
    <dt>cluster_id</dt>
    <dd>O ID do cluster do cluster do {{site.data.keyword.composeEnterprise}}. É possível localizar esse valor no painel de sua instância de serviço do {{site.data.keyword.composeEnterprise}}.
    </dd>
    </dl>
</dd>
</dl>

Por exemplo, para implementar um serviço {{site.data.keyword.composeForElasticsearch}} chamado 'myComposeForEnterpriseService' em um cluster do {{site.data.keyword.composeEnterprise}}, em que o `cluster_service_instance_id` é '12345678-90ab-cdef-1234567890a', você usaria o comando a seguir.

```
bx cf create-service compose-for-elasticsearch Enterprise myComposeForEnterpriseService -c '{"cluster_service_instance_id": "12345678-90ab-cdef-1234567890a"}'
```
