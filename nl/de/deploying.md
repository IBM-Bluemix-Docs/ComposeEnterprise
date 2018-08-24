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

# Compose-Datenbank in einem {{site.data.keyword.composeEnterprise}}-Cluster bereitstellen

## Über die {{site.data.keyword.cloud_notm}}-Konsole bereitstellen

Wenn Sie bereits einen {{site.data.keyword.composeEnterprise_full}}-Cluster mithilfe von {{site.data.keyword.cloud_notm}} erstellt haben, können Sie angeben, dass Ihre neue Compose-Datenbank unter {{site.data.keyword.cloud_notm}} in diesem Cluster bereitgestellt wird. Wählen Sie den Namen des {{site.data.keyword.composeEnterprise}}-Clusters aus der Liste der verfügbaren Positionen im Dropdown-Menü *Standort für die Bereitstellung auswählen* aus, wenn Sie die neue Compose-Datenbankserviceinstanz unter {{site.data.keyword.cloud_notm}} erstellen.

## Über die Befehlszeile bereitstellen

Zum Erstellen einer neuen Instanz eines Compose-Datenbankservice und Bereitstellen dieser Instanz im {{site.data.keyword.composeEnterprise}}-Cluster über die Befehlszeile, müssen Sie zuerst die {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle (CLI) installieren und dann die {{site.data.keyword.composeEnterprise}}-Cluster-ID abrufen und verwenden.

## 1. Richten Sie die {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle (CLI) ein. 

1. Laden Sie das [{{site.data.keyword.cloud_notm}}-CLI](https://console.bluemix.net/docs/cli/reference/bluemix_cli/download_cli.html)-Tool herunter und installieren Sie es.
2. Melden Sie sich bei {{site.data.keyword.cloud_notm}} an.

    ```
    bx login
    ```

3. Wechseln Sie zu der Organisation und dem Bereich, die/den Sie für Ihren neuen Compose-Datenbankservice verwenden wollen.

    ```
    bx target --cf
    ```

## 2. Rufen Sie die Cluster-Serviceinstanz-ID ab.

1. Sie müssen die Cluster-Serviceinstanz-ID für Ihre {{site.data.keyword.composeEnterprise}}-Instanz wie folgt abrufen:

    ```
    bx cf service COMPOSE_ENTERPRISE_SERVICE_NAME --guid
    ```

    Dieser Befehl gibt eine Zeichenfolge zurück. Dies ist die GUID der Serviceinstanz, die Sie später noch zum Abrufen der Cluster-ID benötigen.

## 3. Stellen Sie eine Datenbank in Ihrem Cluster mit dem Befehl `create-service` bereit:

Nachdem Sie jetzt über die Angabe für `cluster_service_instance_id` verfügen, können Sie den Befehl `create-service` verwenden, um einen {{site.data.keyword.cloud_notm}} Compose-Datenbankservice zu erstellen und in Ihrem {{site.data.keyword.composeEnterprise}}-Cluster bereitzustellen.


```
bx cf create-service service_name service_plan service_instance [-c PARAMETERS_AS_JSON]
```

Die Befehlsoptionen sind:

<dl>
<dt>service_name (erforderlich)</dt>
<dd>
Der Name des Compose-Datenbankservice. Einer der folgenden Werte muss angegeben werden: 
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
<dt>service_plan (erforderlich)</dt>
<dd>
Der Preistarif für den neuen Service. Hier muss der Wert `Enterprise` angegeben werden, damit die Datenbank in einem {{site.data.keyword.composeEnterprise}}-Custer bereitgestellt wird.
</dd>
<dt>service_instance (erforderlich)</dt>
<dd>
Der Name des neuen Compose-Datenbankservice, den Sie bereitstellen wollen.
</dd>
<dt>[-c PARAMETERS_AS_JSON] (erforderlich)</dt>
<dd>
Die Parameter werden als JSON-Objekt formatiert und sollten einen der folgenden Werte enthalten:
    <dl>
    <dt>cluster_service_instance_id</dt>
    <dd>Die Cluster-Serviceinstanz-ID Ihres {{site.data.keyword.composeEnterprise}}-Clusters. Diesen Wert können Sie durch Ausführen von Schritt 2 in diesem Handbuchs abrufen.
    </dd>
    </dl>
    <dl>
    <dt>cluster_id</dt>
    <dd>Die Cluster-ID Ihres {{site.data.keyword.composeEnterprise}}-Clusters. Sie finden diesen Wert im Dashboard Ihrer {{site.data.keyword.composeEnterprise}}-Serviceinstanz.
    </dd>
    </dl>
</dd>
</dl>

Zum Bereitstellen eines {{site.data.keyword.composeForElasticsearch}}-Service mit dem Namen 'myComposeForEnterpriseService' in einem {{site.data.keyword.composeEnterprise}}-Cluster, wobei `cluster_service_instance_id` den Wert '12345678-90ab-cdef-1234567890a' hat, würden Sie zum Beispiel den folgenden Befehl verwenden:

```
bx cf create-service compose-for-elasticsearch Enterprise myComposeForEnterpriseService -c '{"cluster_service_instance_id": "12345678-90ab-cdef-1234567890a"}'
```
