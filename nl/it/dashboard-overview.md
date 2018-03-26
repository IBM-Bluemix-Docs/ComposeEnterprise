---

Copyright:
  Years: 2017, 2018
lastupdated: "2018-01-30"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Panoramica sul dashboard

Puoi gestire il tuo servizio {{site.data.keyword.composeEnterprise_full}} dal dashboard del servizio.

## Dettagli cluster

Il pannello _Cluster Details_ mostra i dettagli del tuo cluster {{site.data.keyword.composeEnterprise}}.

![Dettagli cluster](./images/enterprise-cluster-details-ready.png "Una vista del pannello dei dettagli del cluster")

### Nome

Un identificativo interno per il cluster.

### Tipo

Altri servizi Compose {{site.data.keyword.cloud_notm}} utilizzano questo campo per visualizzare il tipo di database offerto dal servizio e la versione del database che il servizio utilizza. Per un servizio {{site.data.keyword.composeEnterprise}}, il valore è sempre _Enterprise Cluster_.

### Stato

Lo stato del tuo cluster {{site.data.keyword.composeEnterprise}}.

### Regione

La regione {{site.data.keyword.cloud_notm}} in cui risiede il cluster {{site.data.keyword.composeEnterprise}}.

## API di gestione dell'istanza

Puoi gestire il tuo servizio {{site.data.keyword.composeForElasticsearch}} tramite l'API {{site.data.keyword.cloud_notm}} Compose.

![Dettagli cluster](./images/enterprise-cluster-api.png "Una vista dell'API di gestione dell'istanza")

### Endpoint fondazione 

L'endpoint fondazione è formato dalla regione in cui risiede il cluster e l'ID del cluster. Può essere trovato all'inizio di ogni endpoint.

### ID cluster

L'ID del cluster è necessario per la maggior parte delle chiamate e identifica l'istanza di distribuzione specifica.

### Riferimenti

Per ulteriore documentazione e i riferimenti sull'utilizzo dell'API {{site.data.keyword.cloud_notm}} Compose, in tutti i servizi {{site.data.keyword.cloud_notm}} Compose, leggi [The {{site.data.keyword.cloud_notm}} Compose API](https://www.compose.com/articles/the-ibm-cloud-compose-api/).
