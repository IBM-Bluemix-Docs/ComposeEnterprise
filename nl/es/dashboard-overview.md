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

# Visión general del panel de control

Puede gestionar el servicio {{site.data.keyword.composeEnterprise_full}} desde el panel de control del servicio.

## Detalles del clúster

El panel _Detalles del clúster_ muestra detalles del clúster {{site.data.keyword.composeEnterprise}}.

![Detalles del clúster](./images/enterprise-cluster-details-ready.png "Una vista del panel Detalles del clúster")

### Nombre

Un identificador interno para el clúster.

### Tipo

Otros servicios de Compose {{site.data.keyword.cloud_notm}} utilizan este campo para mostrar el tipo de base de datos que ofrece el servicio, y la versión de base de datos que utiliza el servicio. Para un servicio de {{site.data.keyword.composeEnterprise}}, el valor es siempre _Clúster empresarial_.

### Estado

El estado de su clúster de {{site.data.keyword.composeEnterprise}}.

### Región

La región de {{site.data.keyword.cloud_notm}} en la que reside el clúster de {{site.data.keyword.composeEnterprise}}.

## API de administración de instancias

Puede gestionar el servicio de {{site.data.keyword.composeForElasticsearch}} a través de la API de {{site.data.keyword.cloud_notm}} Compose.

![Detalles del clúster](./images/enterprise-cluster-api.png "Una vista de la API de administración de instancias")

### Punto final de la fundación

El punto final de la fundación está compuesto por la región donde reside el clúster y el ID de clúster. Se puede encontrar al inicio de cada punto final.

### ID de clúster

El ID de clúster es necesario para la mayoría de las llamadas, e identifica la instancia de despliegue específica.

### Referencia

Para obtener más documentación y referencia para utilizar la API de {{site.data.keyword.cloud_notm}}, en todos los servicios de {{site.data.keyword.cloud_notm}} Compose, lea [La API de {{site.data.keyword.cloud_notm}} Compose](https://www.compose.com/articles/the-ibm-cloud-compose-api/).
