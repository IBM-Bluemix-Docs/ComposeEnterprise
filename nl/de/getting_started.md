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

# Lernprogramm 'Einführung'
{: #getting-started}

Führen Sie zum Einstieg in {{site.data.keyword.composeEnterprise}} die folgenden Schritte aus:

## {{site.data.keyword.composeEnterprise}}-Serviceinstanz bereitstellen
{: #provisioning-compose-enterprise-instance}

Sie können eine neue {{site.data.keyword.composeEnterprise}}-Instanz über die {{site.data.keyword.cloud_notm}}-Konsole oder die Befehlszeile bereitstellen.

**Hinweis:** Es kann zwischen 5-7 Werktage bis zur Bereitstellung Ihres {{site.data.keyword.composeEnterprise}}-Clusters dauern.

##  {{site.data.keyword.composeEnterprise}}-Serviceinstanz über die {{site.data.keyword.cloud_notm}}-Konsole bereitstellen

[Erstellen Sie eine {{site.data.keyword.composeEnterprise}}-Instanz](https://console.{DomainName}/catalog/services/compose-enterprise/) und achten Sie darauf, dass Sie alle Felder ausfüllen. 

**Hinweise:**
- Der Name Ihres {{site.data.keyword.composeEnterprise}}-Clusters darf maximal 19 Zeichen lang sein und nur alphanumerische Zeichen enthalten.
- Wenn Sie eine *Cloud-Provider-Region* wählen, ist der ausgewählte Standort das SoftLayer-Rechenzentrum, in dem die {{site.data.keyword.composeEnterprise}}-Instanz bereitgestellt wird. 


## {{site.data.keyword.composeEnterprise}}-Serviceinstanz über die Befehlszeile bereitstellen

1. Laden Sie das [{{site.data.keyword.cloud_notm}}-CLI](https://console.{DomainName}/docs/cli/reference/bluemix_cli/download_cli.html)-Tool herunter und installieren Sie es.
2. Melden Sie sich bei {{site.data.keyword.cloud_notm}} an.

  ```
  bx login
  ```

3. Wechseln Sie zu der Organisation und dem Bereich, die/den Sie für Ihren neuen Compose-Datenbankservice verwenden wollen.

  ```
  bx target --cf
  ```

4. Stellen Sie eine Instanz des Service mit dem Befehl `create-service` bereit:

  ```
  bx cf create-service service_name service_plan service_instance -c start_command
  ```

  Die Befehlsoptionen sind:

  <dl>
    <dt>service_name</dt>
    <dd>
    Der Name des {{site.data.keyword.cloud_notm}}-Service, von dem Sie eine Instanz erstellen möchten. Der Wert muss `compose-enterprise` sein.
    </dd>
    <dt>service_plan</dt>
    <dd>
    Der Preistarif für den neuen Service. Der Wert muss `Enterprise` sein.
    </dd>
    <dt>service_instance</dt>
    <dd>
    Der Name des neuen Compose-Datenbankservice, den Sie bereitstellen möchten.
    </dd>
    <dt>-c start_command</dt>
    <dd>
    Der Startbefehl enthält die Details für den neuen {{site.data.keyword.composeEnterprise}}-Cluster, den Sie bereitstellen möchten. Er ist als ein Array formatiert und kann die folgenden Werte enthalten:
      <dl>
        <dt>contact_name (erforderlich)</dt>
        <dd>
        Der Name des {{site.data.keyword.composeEnterprise}}-Clustereigners
        </dd>
        <dt>contact_phone (erforderlich)</dt>
        <dd>
        Eine Telefonnummer für den Kontakt mit dem {{site.data.keyword.composeEnterprise}}-Clustereigner
        </dd>
        <dt>contact_email (erforderlich)</dt>
        <dd>
        Eine E-Mail-Adresse für den {{site.data.keyword.composeEnterprise}}-Clustereigner
        </dd>
        <dt>provider_region (erforderlich)</dt>
        <dd>
        Das SoftLayer-Rechenzentrum, in dem die {{site.data.keyword.composeEnterprise}}-Instanz bereitgestellt werden soll. Gültige Werte sind: 'amsterdam', 'chennai', 'dallas', 'frankfurt', 'hong kong', 'houston', 'london', 'melbourne', 'milan', 'montreal', 'oslo', 'paris', 'queretaro', 'san jose', 'sao paulo', 'seattle', 'seoul', 'singapore', 'sydney', 'tokyo', 'toronto', 'washington dc'.
        </dd>
        <dt>cluster_name (optional)</dt>
        <dd>
        Wählen Sie einen Name für Ihren bereitgestellten {{site.data.keyword.composeEnterprise}}-Cluster. Der Name darf maximal 19 Zeichen lang sein und nur alphanumerische Zeichen enthalten.
        </dd>
        <dt>notes (optional)</dt>
        <dd>
        Fügen Sie Hinweise bezogen auf Ihren Cluster hinzu, wie zum Beispiel 'Bare-Metal'.
        </dd>
      </dl>
    </dd>
  </dl>

Beispielsyntax für `bx cf create-service`:

```
bx cf create-service compose-enterprise Enterprise myComposeEnterpriseServiceName -c '{"contact_name": "myName", "contact_phone": "888-888-8888", "contact_email": "myEmail@ibm.com", "provider_region": "frankfurt", "cluster_name": "myClusterName123", "notes": "Bare-Metal" }'
```

Sobald Ihr {{site.data.keyword.composeEnterprise}}-Cluster verfügbar ist, können Sie Compose-Datenbanken unter {{site.data.keyword.cloud_notm}} im Cluster bereitstellen und die Vorteile automatisch skalierter Datenbanken mit Verschlüsselung ruhender und bewegter Daten innerhalb eines isolierten Clusters genießen.

## Nächste Schritte.

Nun, da Sie Ihren {{site.data.keyword.composeEnterprise}}-Cluster bereitgestellt und konfiguriert haben, können Sie Datenbanken in Ihrem Cluster bereitstellen.

Sie können eine Compose-Datenbank unter {{site.data.keyword.cloud_notm}} in einem {{site.data.keyword.composeEnterprise}}-Cluster bereitstellen, wenn Sie eine neue Datenbank über einen der vorhandenen Compose-Datenbankservices unter {{site.data.keyword.cloud_notm}} erstellen. Dazu können Sie die {{site.data.keyword.cloud_notm}}-Konsole oder die Befehlszeile verwenden. Details zum Bereitstellen von Datenbanken finden Sie in Abschnitt [Compose-Datenbank in einem {{site.data.keyword.composeEnterprise}}-Cluster bereitstellen](./deploying.html).






