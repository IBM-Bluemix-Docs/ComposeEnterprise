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

# Distribuzione di un database Compose in un cluster {{site.data.keyword.composeEnterprise}} 

## Distribuzione dalla console {{site.data.keyword.cloud_notm}} 

Se hai già creato un cluster {{site.data.keyword.composeEnterprise_full}} utilizzando {{site.data.keyword.cloud}}, puoi specificare che venga eseguito il provisioning del tuo nuovo database Compose {{site.data.keyword.cloud_notm}} nel cluster. Seleziona il nome del cluster {{site.data.keyword.composeEnterprise}} dall'elenco delle ubicazioni disponibili nel menu a discesa *Select Location for Deployment* quando stai creando la nuova istanza del servizio del database {{site.data.keyword.cloud_notm}}.

## Distribuzione dalla riga di comando

Per creare una nuova istanza di un servizio del database Compose ed eseguirne il provisioning in un cluster {{site.data.keyword.composeEnterprise}}, dalla riga di comando dovrai prima installare l'interfaccia riga di comando (CLI) {{site.data.keyword.cloud_notm}}, poi ottenere ed utilizzare l'ID del cluster {{site.data.keyword.composeEnterprise}}.

## 1. Configura l'interfaccia riga di comando (CLI) {{site.data.keyword.cloud_notm}}  

1. Scarica e installa lo strumento [CLI {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/cli/reference/bluemix_cli/download_cli.html).
2. Accedi a {{site.data.keyword.cloud_notm}}

    ```
    bx login
    ```

3. Passa all'organizzazione e allo spazio che vuoi utilizzare per il tuo nuovo servizio del database Compose.

    ```
    bx target --cf
    ```

## 2. Ottieni un token dell'API {{site.data.keyword.cloud_notm}}.

Per utilizzare l'API {{site.data.keyword.cloud_notm}} Compose, di cui avrai bisogno per distribuire un database in un cluster, avrai bisogno di un token dell'API {{site.data.keyword.cloud_notm}}. Se non disponi ancora di un token dell'API che puoi utilizzare, puoi crearne uno:

1. Accedi al dashboard [{{site.data.keyword.cloud_notm}}](console.{DomainName}.bluemix.net).
2. Seleziona **Manage** -> **Security** -> **{{site.data.keyword.cloud_notm}} API Keys**
3. Fai clic su **Create**
4. Immetti un nome e una descrizione per la tua chiave e fai clic su **Create**. Copia la chiave generata - che ti servirà più tardi.

## 3. Ottieni l'ID del cluster

1. Per prima cosa, dovrai ottenere l'ID dell'istanza del servizio per la tua istanza {{site.data.keyword.composeEnterprise}}:

    ```
    bx cf service COMPOSE_ENTERPRISE_SERVICE_NAME --guid
    ```

    Il comando restituisce una stringa. Questo è il GUID dell'istanza del servizio e ne avrai bisogno più tardi per ottenere l'ID del cluster.

2. Utilizzando il tuo token API {{site.data.keyword.cloud_notm}}, utilizza l'API {{site.data.keyword.cloud_notm}} per scambiare l'ID dell'istanza del servizio per il `cluster_id` Compose Enterprise.

    ```
    curl -s -X GET -H ‘authorization: Bearer ’$IBM_CLOUD_API_TOKEN -H ‘content-type: application/json’ https://composebroker-dashboard-public.eu-gb.mybluemix.net/api/2016-07/instances/$SERVICE_GUID/
    ```

    L'oggetto che viene restituito da questa chiamata API include il valore `cluster_id` che stai cercando.

## 4. Esegui il provisioning di un database nel tuo cluster con il comando `create-service`:

Ora che hai il `cluster_id` puoi utilizzare il comando `create-service` per creare un servizio del database {{site.data.keyword.cloud_notm}} Compose e distribuirlo nel tuo cluster Compose Enterprise.


```
bx cf create-service service_name service_plan service_instance [-c PARAMETERS_AS_JSON]
```

Le opzioni del comando sono:

<dl>
<dt>service_name (obbligatorio)</dt>
<dd>
Il nome del servizio del database Compose. Il valore deve essere uno dei seguenti.
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
<dt>service_plan (obbligatorio)</dt>
<dd>
Il piano dei prezzi per il nuovo servizio. Questo valore deve essere `Enterprise` per distribuire il database in un cluster {{site.data.keyword.composeEnterprise}}.
</dd>
<dt>service_instance (obbligatorio)</dt>
<dd>
Il nome del nuovo servizio Compose Database di cui vuoi eseguire il provisioning.
</dd>
<dt>[-c PARAMETERS_AS_JSON] (obligatorio)</dt>
<dd>
I parametri vengono formattati come un array e devono contenere i seguenti valori:
    <dl>
    <dt>cluster_id (obbligatorio)</dt>
    <dd>L'ID cluster del tuo cluster {{site.data.keyword.composeEnterprise}}. Puoi trovare questo valore nel dashboard della tua istanza del servizio {{site.data.keyword.composeEnterprise}}.
    </dd>
    </dl>
</dd>
</dl>

Ad esempio, per distribuire un servizio {{site.data.keyword.composeForElasticsearch}} denominato 'myComposeForEnterpriseService' in un cluster {{site.data.keyword.composeEnterprise}}, dove `cluster_id` è '123456781234567812345678', dorai utilizzare il seguente comando.

```
bx cf create-service compose-for-elasticsearch Enterprise myComposeForEnterpriseService -c '{"cluster_id": "123456781234567812345678"}'
```

## Passi successivi

Qualsiasi TBC?
