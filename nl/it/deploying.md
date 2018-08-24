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

Se hai già creato un cluster {{site.data.keyword.composeEnterprise_full}} utilizzando {{site.data.keyword.cloud_notm}}, puoi specificare che venga eseguito il provisioning del tuo nuovo database Compose {{site.data.keyword.cloud_notm}} nel cluster. Seleziona il nome del cluster {{site.data.keyword.composeEnterprise}} dall'elenco delle ubicazioni disponibili nel menu a discesa *Select Location for Deployment* quando stai creando la nuova istanza del servizio del database {{site.data.keyword.cloud_notm}}.

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

## 2. Ottieni l'ID dell'istanza del servizio cluster

1. Dovrai ottenere l'ID dell'istanza del servizio cluster per la tua istanza {{site.data.keyword.composeEnterprise}}:

    ```
    bx cf service COMPOSE_ENTERPRISE_SERVICE_NAME --guid
    ```

    Il comando restituisce una stringa. Questo è il GUID dell'istanza del servizio e ne avrai bisogno più tardi per ottenere l'ID del cluster.

## 3. Esegui il provisioning di un database nel tuo cluster con il comando `create-service`:

Ora che hai il tuo `cluster_service_instance_id` puoi utilizzare il comando `create-service` per creare un servizio del database {{site.data.keyword.cloud_notm}} Compose e distribuirlo nel tuo cluster {{site.data.keyword.composeEnterprise}}.


```
bx cf create-service service_name service_plan service_instance [-c PARAMETRI_AS_JSON]
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
        <li>`compose-for-mysql`</li>
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
<dt>[-c PARAMETRI_COME_JSON] (obbligatorio)</dt>
<dd>
I parametri sono formattati come un oggetto JSON e devono contenere uno dei seguenti valori:
    <dl>
    <dt>cluster_service_instance_id</dt>
    <dd>L'ID dell'istanza del servizio cluster del tuo cluster {{site.data.keyword.composeEnterprise}}. Puoi ottenere questo valore attenendoti al passo 2 di questa guida.
    </dd>
    </dl>
    <dl>
    <dt>cluster_id</dt>
    <dd>L'ID cluster del tuo cluster {{site.data.keyword.composeEnterprise}}. Puoi trovare questo valore nel dashboard della tua istanza del servizio {{site.data.keyword.composeEnterprise}}.
    </dd>
    </dl>
</dd>
</dl>

Ad esempio, per distribuire un servizio {{site.data.keyword.composeForElasticsearch}} denominato 'myComposeForEnterpriseService' in un cluster {{site.data.keyword.composeEnterprise}}, dove `cluster_service_instance_id` è '12345678-90ab-cdef-1234567890a', utilizzerai il seguente comando.

```
bx cf create-service compose-for-elasticsearch Enterprise myComposeForEnterpriseService -c '{"cluster_service_instance_id": "12345678-90ab-cdef-1234567890a"}'
```
