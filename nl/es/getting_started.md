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

# Guía de aprendizaje de iniciación
{: #getting-started}

Siga estos pasos para iniciarse a {{site.data.keyword.composeEnterprise}}:

## Suministro de una instancia de servicio de {{site.data.keyword.composeEnterprise}}
{: #provisioning-compose-enterprise-instance}

Puede suministrar una nueva instancia de {{site.data.keyword.composeEnterprise}} utilizando la consola o la línea de mandatos de {{site.data.keyword.cloud_notm}}.

**Nota:** Puede llevar entre 5 y 7 días hábiles el suministro para su clúster de {{site.data.keyword.composeEnterprise}}.

## Suministro de una instancia de servicio de {{site.data.keyword.composeEnterprise}} desde la consola de {{site.data.keyword.cloud_notm}}

[Crear una instancia de {{site.data.keyword.composeEnterprise}}](https://console.{DomainName}/catalog/services/compose-enterprise/), asegurándose de que haya completado todos los campos.

**Notas:**
- El nombre del clúster de {{site.data.keyword.composeEnterprise}} puede tener una longitud máxima de 19 caracteres, y solo puede contener caracteres alfanuméricos.
- Cuando se elija una *Región de proveedor de nube*, la ubicación que seleccione es el centro de datos de SoftLayer en el que se desplegará la instancia de {{site.data.keyword.composeEnterprise}}.


## Suministro de una instancia de servicio de {{site.data.keyword.composeEnterprise}} desde la línea de mandatos

1. Descargue e instale la herramienta [CLI de {{site.data.keyword.cloud_notm}}](https://console.{DomainName}/docs/cli/reference/bluemix_cli/download_cli.html).
2. Inicie sesión en {{site.data.keyword.cloud_notm}}

  ```
  bx login
  ```

3. Vaya a la organización y al espacio que desee utilizar para el nuevo servicio de base de datos de Compose.

  ```
  bx target --cf
  ```

4. Suministre una instancia del servicio con el mandato `create-service`:

  ```
  bx cf create-service service_name service_plan service_instance -c start_command
  ```

  Las opciones del mandato son:

  <dl>
    <dt>service_name</dt>
    <dd>
    El nombre del servicio de {{site.data.keyword.cloud_notm}} del que desea crear una instancia. El valor debe ser `compose-enterprise`.
    </dd>
    <dt>service_plan</dt>
    <dd>
    El plan de precios para el nuevo servicio. El valor debe ser `Enterprise`.
    </dd>
    <dt>service_instance</dt>
    <dd>
    El nombre del nuevo servicio de base de datos de Compose que desea suministrar.
    </dd>
    <dt>-c start_command</dt>
    <dd>
    El start_command contiene los detalles del clúster de {{site.data.keyword.composeEnterprise}} que desea suministrar. Está formateado como una matriz y puede contener los valores siguientes:
      <dl>
        <dt>contact_name (necesario)</dt>
        <dd>
        El nombre del propietario del clúster de {{site.data.keyword.composeEnterprise}}
        </dd>
        <dt>contact_phone (necesario)</dt>
        <dd>
        Un número de teléfono de contacto para el propietario del clúster de {{site.data.keyword.composeEnterprise}}
        </dd>
        <dt>contact_email (necesario)</dt>
        <dd>
        Una dirección de correo electrónico para el propietario del clúster de {{site.data.keyword.composeEnterprise}}
        </dd>
        <dt>provider_region (necesario)</dt>
        <dd>
        El centro de datos de SoftLayer en el que desea que se despliegue la instancia de {{site.data.keyword.composeEnterprise}}. Los valores válidos son: 'amsterdam', 'chennai', 'dallas', 'frankfurt', 'hong kong', 'houston', 'london', 'melbourne', 'milan', 'montreal', 'oslo', 'paris', 'queretaro', 'san jose', 'sao paulo', 'seattle', 'seoul', 'singapore', 'sydney', 'tokyo', 'toronto', 'washington dc'.
        </dd>
        <dt>cluster_name (opcional)</dt>
        <dd>
        Elija un nombre para el clúster de {{site.data.keyword.composeEnterprise}} suministrado. La longitud máxima es de 19 caracteres, y solo puede contener caracteres alfanuméricos.
        </dd>
        <dt>notes (opcional)</dt>
        <dd>
        Añada las notas relativas a su clúster, por ejemplo 'Bare Metal'.
        </dd>
      </dl>
    </dd>
  </dl>

Uso de `bx cf create-service` de ejemplo:

```
bx cf create-service compose-enterprise Enterprise myComposeEnterpriseServiceName -c '{"contact_name": "myName", "contact_phone": "888-888-8888", "contact_email": "myEmail@ibm.com", "provider_region": "dallas", "cluster_name": "myClusterName123", "notes": "Bare Metal" }'
```

Cuando el clúster de {{site.data.keyword.composeEnterprise}} esté disponible, podrá suministrar las bases de datos de {{site.data.keyword.cloud_notm}} Compose en el clúster y disfrutar de los beneficios de las bases de datos de escalado automático con cifrado en descanso y en movimiento dentro de un clúster aislado.

## Siguientes pasos.

Ahora que tiene el clúster de {{site.data.keyword.composeEnterprise}} suministrado y configurado, está listo para desplegar bases de datos en el clúster.

Puede desplegar una base de datos de {{site.data.keyword.cloud_notm}} Compose en un clúster de {{site.data.keyword.composeEnterprise}} al crear una nueva base de datos desde cualquiera de los servicios de {{site.data.keyword.cloud_notm}} de bases de datos de Compose existentes. Puede utilizar la consola o la línea de mandatos de {{site.data.keyword.cloud_notm}}. Para obtener detalles sobre cómo desplegar bases de datos, consulte [Despliegue de una base de datos de Compose en un clúster de {{site.data.keyword.composeEnterprise}}](./deploying.html).






