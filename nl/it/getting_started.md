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

# Esercitazione introduttiva
{: #getting-started}

Completa questa procedura per iniziare ad utilizzare {{site.data.keyword.composeEnterprise}}:

## Provisioning di una istanza del servizio {{site.data.keyword.composeEnterprise}}
{: #provisioning-compose-enterprise-instance}

Puoi eseguire il provisioning di una nuova istanza {{site.data.keyword.composeEnterprise}} utilizzando la console {{site.data.keyword.cloud_notm}} o la riga di comando.

**Nota:** sono necessario fino a 5-7 giorni lavorativi per il provisioning del tuo cluster {{site.data.keyword.composeEnterprise}}.

## Provisioning di una istanza del servizio {{site.data.keyword.composeEnterprise}} dalla console {{site.data.keyword.cloud_notm}}

[Crea una istanza {{site.data.keyword.composeEnterprise}}](https://console.{DomainName}/catalog/services/compose-enterprise/), assicurati di aver completato tutti i campi.

**Note:**
- Il nome del tuo cluster {{site.data.keyword.composeEnterprise}} può avere al massimo una lunghezza di 19 caratteri e può contenere solo caratteri alfanumerici.
- Quando scegli una *Cloud Provider Region*, l'ubicazione che selezioni è il data center SoftLayer in cui l'istanza {{site.data.keyword.composeEnterprise}} sarà distribuita.


## Provisioning di una istanza del servizio {{site.data.keyword.composeEnterprise}} dalla riga di comando

1. Scarica e installa lo strumento [CLI {{site.data.keyword.cloud_notm}}](https://console.{DomainName}/docs/cli/reference/bluemix_cli/download_cli.html).
2. Accedi a {{site.data.keyword.cloud_notm}}

  ```
  bx login
  ```

3. Passa all'organizzazione e allo spazio che vuoi utilizzare per il tuo nuovo servizio del database Compose.

  ```
  bx target --cf
  ```

4. Provisioning di una istanza del servizio con il comando `create-service`:

  ```
  bx cf create-service service_name service_plan service_instance -c start_command
  ```

  Le opzioni del comando sono:

  <dl>
    <dt>service_name</dt>
    <dd>
    Il nome del servizio {{site.data.keyword.cloud_notm}} di cui desideri creare una istanza. Il valore deve essere `compose-enterprise`.
    </dd>
    <dt>service_plan</dt>
    <dd>
    Il piano dei prezzi per il nuovo servizio. Il valore deve essere `Enterprise`.
    </dd>
    <dt>service_instance</dt>
    <dd>
    Il nome del nuovo servizio del database Compose di cui vuoi eseguire il provisioning.
    </dd>
    <dt>-c start_command</dt>
    <dd>
    start_command contiene i dettagli del cluster {{site.data.keyword.composeEnterprise}} di cui vuoi eseguire il provisioning. Viene formattato come un array e può contenere i seguenti valori:
      <dl>
        <dt>contact_name (obbligatorio)</dt>
        <dd>
        Il nome del proprietario del cluster {{site.data.keyword.composeEnterprise}}
        </dd>
        <dt>contact_phone (obbligatorio)</dt>
        <dd>
        Un numero di telefono del proprietario del cluster {{site.data.keyword.composeEnterprise}}
        </dd>
        <dt>contact_email (obbligatorio)</dt>
        <dd>
        Un indirizzo email del proprietario del cluster {{site.data.keyword.composeEnterprise}}
        </dd>
        <dt>provider_region (obbligatorio)</dt>
        <dd>
        Il data center SoftLayer in cui desideri venga distribuita l'istanza {{site.data.keyword.composeEnterprise}}. I valori validi sono: 'amsterdam', 'chennai', 'dallas', 'frankfurt', 'hong kong', 'houston', 'london', 'melbourne', 'milan', 'montreal', 'oslo', 'paris', 'queretaro', 'san jose', 'sao paulo', 'seattle', 'seoul', 'singapore', 'sydney', 'tokyo', 'toronto', 'washington dc'.
        </dd>
        <dt>cluster_name (facoltativo)</dt>
        <dd>
        Scegli un nome per il tuo cluster {{site.data.keyword.composeEnterprise}} fornito. La lunghezza massima è 19 caratteri e può contenere solo caratteri alfanumerici.
        </dd>
        <dt>notes (facoltativo)</dt>
        <dd>
        Aggiungi eventuali note relative al tuo cluster, ad esempio 'Bare Metal'.
        </dd>
      </dl>
    </dd>
  </dl>

Utilizzo di esempio di `bx cf create-service`:

```
bx cf create-service compose-enterprise Enterprise myComposeEnterpriseServiceName -c '{"contact_name": "myName", "contact_phone": "888-888-8888", "contact_email": "myEmail@ibm.com", "provider_region": "dallas", "cluster_name": "myClusterName123", "notes": "Bare Metal" }'
```

Quando il tuo cluster {{site.data.keyword.composeEnterprise}} è disponibile, potrai eseguire il provisioning dei database Compose {{site.data.keyword.cloud_notm}} nel cluster e godere dei benefici dei database di ridimensionamento automatico con la crittografia inattiva e attiva all'interno di un cluster isolato.

## Passi successivi.

Ora che hai eseguito il provisioning e configurato il tuo cluster {{site.data.keyword.composeEnterprise}} sei pronto per distribuire i database nel cluster.

Puoi distribuire un database Compose {{site.data.keyword.cloud_notm}} in un cluster {{site.data.keyword.composeEnterprise}} quando crei un nuovo database da uno qualsiasi dei servizi {{site.data.keyword.cloud_notm}} del database Compose esistenti. Puoi utilizzare la riga di comando o la console {{site.data.keyword.cloud_notm}}. Per i dettagli su come distribuire i database, consulta [Distribuzione di un database Compose in un cluster {{site.data.keyword.composeEnterprise}}](./deploying.html).






