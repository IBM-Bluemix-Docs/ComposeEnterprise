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

# Déploiement d'une base de données Compose dans un cluster {{site.data.keyword.composeEnterprise}}

## Déploiement à partir de la console {{site.data.keyword.cloud_notm}}

Si vous avez déjà créé un cluster {{site.data.keyword.composeEnterprise_full}} à l'aide d'{{site.data.keyword.cloud}}, vous pouvez mettre votre nouvelle base de données Compose {{site.data.keyword.cloud_notm}} à disposition dans le cluster. Sélectionnez le nom du cluster {{site.data.keyword.composeEnterprise}} dans la liste des emplacements disponibles de la liste déroulante de *sélection d'un emplacement pour le déploiement* lorsque vous créez la nouvelle instance de service de base de données Compose {{site.data.keyword.cloud_notm}}.

## Déploiement à partir de la ligne de commande

Pour créer une nouvelle instance d'un service de base de données Compose et la mettre à disposition dans un cluster {{site.data.keyword.composeEnterprise}} à partir de la ligne de commande, vous devez commencer par installer l'interface de ligne de commande {{site.data.keyword.cloud_notm}}, puis obtenir et utiliser l'ID de cluster {{site.data.keyword.composeEnterprise}}.

## 1. Configuration de l'interface de ligne de commande {{site.data.keyword.cloud_notm}} 

1. Téléchargez et installez l'outil [Interface de ligne de commande {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/cli/reference/bluemix_cli/download_cli.html).
2. Connectez-vous à {{site.data.keyword.cloud_notm}}

    ```
    bx login
    ```

3. Accédez à l'organisation et à l'espace que vous voulez utiliser pour votre nouveau service de base de données Compose.

    ```
    bx target --cf
    ```

## 2. Obtenez un jeton d'API {{site.data.keyword.cloud_notm}}.

Pour utiliser l'API {{site.data.keyword.cloud_notm}} Compose, nécessaire pour déployer une base de données dans votre cluster, vous avez besoin d'un jeton d'API {{site.data.keyword.cloud_notm}}. Si vous ne disposez pas d'un jeton d'API utilisable, vous pouvez en créer un comme suit :

1. Connectez-vous au tableau de bord [{{site.data.keyword.cloud_notm}}](console.{DomainName}.bluemix.net).
2. Sélectionnez **Gérer** -> **Sécurité** -> **Clés d'API {{site.data.keyword.cloud_notm}}**
3. Cliquez sur **Créer**
4. Entrez un nom et une description pour votre clé, puis cliquez sur **Créer**. Copiez la clé générée ; vous en aurez besoin ultérieurement.

## 3. Obtention de l'ID de cluster

1. Tout d'abord, vous devez vous procurer l'ID d'instance de service de votre instance {{site.data.keyword.composeEnterprise}} avec la commande suivante :

    ```
    bx cf service COMPOSE_ENTERPRISE_SERVICE_NAME --guid
    ```

    La commande renvoie une chaîne. Il s'agit de l'identificateur global unique de l'instance de service, dont vous aurez besoin ultérieurement pour obtenir l'ID de cluster.

2. A l'aide de votre jeton d'API {{site.data.keyword.cloud_notm}}, utilisez l'API {{site.data.keyword.cloud_notm}} Compose pour échanger l'ID d'instance de service contre la valeur d'ID de cluster (`cluster_id`) Compose Enterprise.

    ```
    curl -s -X GET -H ‘authorization: Bearer ’$IBM_CLOUD_API_TOKEN -H ‘content-type: application/json’ https://composebroker-dashboard-public.eu-gb.mybluemix.net/api/2016-07/instances/$SERVICE_GUID/
    ```

    L'objet renvoyé par cet appel API inclut la valeur `cluster_id` dont vous avez besoin.

## 4. Mise à disposition d'une base de données dans votre cluster avec la commande `create-service` :

Maintenant que vous disposez de l'ID de cluster (`cluster_id`), vous pouvez utiliser la commande `create-service` pour créer un service de base de données {{site.data.keyword.cloud_notm}} Compose et le déployer dans votre cluster Compose Enterprise.


```
bx cf create-service service_name service_plan service_instance [-c PARAMETERS_AS_JSON]
```

Les options de la commande sont les suivantes :

<dl>
<dt>nom_service (requis)</dt>
<dd>
Nom du service de base de données Compose. Il doit s'agir de l'une des valeurs suivantes :
    <ul>
        <li>`compose-for-elasticsearch`</li>
        <li>`compose-for-etcd`</li>
        <li>`compose-for-janusgraph`</li>
        <li>`compose-for-mongodb`</li>
        <li>`compose-for-myqsl`</li>
        <li>`compose-for-postgresql`</li>
        <li>`compose-for-rabbitmq`</li>
        <li>`compose-for-redis`</li>
        <li>`compose-for-rethinkdb`</li>
        <li>`compose-for-scylladb`</li>
    </ul>
</dd>
<dt>plan_service (requis)</dt>
<dd>
    Plan de tarification du nouveau service. La valeur de cette option doit être `Enterprise` pour déployer la base de données dans un cluster {{site.data.keyword.composeEnterprise}}.
</dd>
<dt>instance_service (requis)</dt>
<dd>
Nom du nouveau service de base de données Compose à mettre à disposition.
</dd>
<dt>[-c PARAMETERS_AS_JSON] (requis)</dt>
<dd>
Les paramètres se présentent sous forme de tableau et doivent contenir les valeurs suivantes :
    <dl>
    <dt>cluster_id (requis)</dt>
    <dd>ID de votre cluster {{site.data.keyword.composeEnterprise}}. Cette valeur figure dans le tableau de bord de votre instance de service {{site.data.keyword.composeEnterprise}}.
    </dd>
    </dl>
</dd>
</dl>

Par exemple, pour déployer un service {{site.data.keyword.composeForElasticsearch}} nommé 'myComposeForEnterpriseService' dans un cluster {{site.data.keyword.composeEnterprise}}, si `cluster_id` a la valeur '123456781234567812345678', utilisez la commande suivante :

```
bx cf create-service compose-for-elasticsearch Enterprise myComposeForEnterpriseService -c '{"cluster_id": "123456781234567812345678"}'
```

## Etapes suivantes

Rien à confirmer ?
