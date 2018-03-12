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

# Tutoriel d'initiation
{: #getting-started}

Exécutez les étapes décrites ci-dessous pour commencer à utiliser {{site.data.keyword.composeEnterprise}} :

## Mise à disposition d'une instance de service {{site.data.keyword.composeEnterprise}}
{: #provisioning-compose-enterprise-instance}

Vous pouvez mettre à disposition une nouvelle instance {{site.data.keyword.composeEnterprise}} à l'aide de la console {{site.data.keyword.cloud_notm}} ou de la ligne de commande.

**Remarque :** 5 à 7 jours ouvrés peuvent être nécessaires pour mettre à disposition votre cluster {{site.data.keyword.composeEnterprise}}.

## Mise à disposition d'une instance de service {{site.data.keyword.composeEnterprise}} à partir de la console {{site.data.keyword.cloud_notm}}

[Créez une instance {{site.data.keyword.composeEnterprise}}](https://console.{DomainName}/catalog/services/compose-enterprise/) en veillant à renseigner toutes les zones.

**Remarques :**
- Le doit de votre cluster {{site.data.keyword.composeEnterprise}} doit contenir au maximum 19 caractères alphanumériques uniquement.
- Lorsque vous choisissez une *région de fournisseur de cloud*, l'emplacement sélectionné est le centre de données dans lequel l'instance {{site.data.keyword.composeEnterprise}} sera déployée.


## Mise à disposition d'une instance de service {{site.data.keyword.composeEnterprise}} à partir de la ligne de commande

1. Téléchargez et installez l'outil [d'interface de ligne de commande {{site.data.keyword.cloud_notm}}](https://console.{DomainName}/docs/cli/reference/bluemix_cli/download_cli.html).
2. Connectez-vous à {{site.data.keyword.cloud_notm}}

  ```
  bx login
  ```

3. Accédez à l'organisation et à l'espace que vous voulez utiliser pour votre nouveau service de base de données Compose.

  ```
  bx target --cf
  ```

4. Mettez une instance du service à disposition avec la commande `create-service` :

  ```
  bx cf create-service service_name service_plan service_instance -c start_command
  ```

  Les options de la commande sont les suivantes :

  <dl>
    <dt>service_name</dt>
    <dd>
    Nom du service {{site.data.keyword.cloud_notm}} dont vous voulez créer une instance. La valeur doit être `compose-enterprise`.
    </dd>
    <dt>service_plan</dt>
    <dd>
    Plan de tarification du nouveau service. La valeur doit être `Entreprise`.
    </dd>
    <dt>service_instance</dt>
    <dd>
    Nom du nouveau service de base de données Compose à mettre à disposition.
    </dd>
    <dt>-c start_command</dt>
    <dd>
    Contient les détails du cluster {{site.data.keyword.composeEnterprise}} à mettre à disposition. Cette option se présente sous forme de tableau qui peut contenir les valeurs suivantes :
      <dl>
        <dt>contact_name (requis)</dt>
        <dd>
        Nom du propriétaire du cluster {{site.data.keyword.composeEnterprise}}
        </dd>
        <dt>contact_phone (requis)</dt>
        <dd>
        Numéro de téléphone du propriétaire du cluster {{site.data.keyword.composeEnterprise}}
        </dd>
        <dt>contact_email (requis)</dt>
        <dd>
        Adresse électronique du propriétaire du cluster {{site.data.keyword.composeEnterprise}}
        </dd>
        <dt>provider_region (requis)</dt>
        <dd>
        Centre de données SoftLayer dans lequel vous voulez déployer l'instance {{site.data.keyword.composeEnterprise}}. Les valeurs admises sont : 'amsterdam', 'chennai', 'dallas', 'frankfurt', 'hong kong', 'houston', 'london', 'melbourne', 'milan', 'montreal', 'oslo', 'paris', 'queretaro', 'san jose', 'sao paulo', 'seattle', 'seoul', 'singapore', 'sydney', 'tokyo', 'toronto', 'washington dc'.
        </dd>
        <dt>cluster_name (facultatif)</dt>
        <dd>
        Choisissez un nom pour cluster {{site.data.keyword.composeEnterprise}} mis à disposition. Ce nom peut contenir au maximum 19 caractères alphanumériques uniquement.
        </dd>
        <dt>notes (facultatif)</dt>
        <dd>
        Ajoutez éventuellement des remarques concernant votre cluster, par exemple 'Bare Metal'.
        </dd>
      </dl>
    </dd>
  </dl>

Exemple d'utilisation de `bx cf create-service` :

```
bx cf create-service compose-enterprise Enterprise myComposeEnterpriseServiceName -c '{"contact_name": "myName", "contact_phone": "888-888-8888", "contact_email": "myEmail@ibm.com", "provider_region": "dallas", "cluster_name": "myClusterName123", "notes": "Bare Metal" }'
```

Une fois votre cluster {{site.data.keyword.composeEnterprise}} disponible, vous pouvez mettre à disposition des bases de données provision Compose {{site.data.keyword.cloud_notm}} dans le cluster et profiter des avantage des base de données à mise à l'échelle automatique avec chiffrement au repos et en action au sein d'un cluster isolé.

## Etapes suivantes.

Maintenant que votre cluster {{site.data.keyword.composeEnterprise}} a été mis à disposition et configuré, vous pouvez déployer des bases de données dans le cluster.

Vous pouvez déployer une base de données Compose {{site.data.keyword.cloud_notm}} dans un cluster {{site.data.keyword.composeEnterprise}} lorsque vous créez une nouvelle base de données à partir de n'importe quel service de base de données Compose {{site.data.keyword.cloud_notm}} existant. Pour ce faire, vous pouvez utiliser la console {{site.data.keyword.cloud_notm}} ou la ligne de commande. Pour plus d'informations sur le déploiement de bases de données, voir [Déploiement d'une base de données Compose dans un cluster {{site.data.keyword.composeEnterprise}}](./deploying.html).






