---
title: "Configurer le pack de fonctionnalités | Documents Microsoft"
description: "Installer et configurer le pack de fonctionnalités 1 du feature pack 2. Consultez la liste des fonctionnalités nouvelles, y compris la gestion des API, déploiement de services d’équipe, nouveaux adaptateurs Azure, les sauvegardes, etc. dans BizTalk Server 2016"
ms.custom: 
ms.date: 11/22/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1027bfa6-49b9-4f58-a2e2-3e0ae2fc3bf3
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5b4164cf1f1355ab9a0d2f350aa5b3b5ce411e0
ms.sourcegitcommit: f4c0d7bc4b617688c643101a34062db90014851a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2017
---
# <a name="configure-the-feature-pack"></a>Configurer le pack de fonctionnalités

## <a name="overview"></a>Vue d'ensemble

[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]utilise des packs de fonctionnalités pour fournir une intégration plus étroite avec Azure, fonctionnalités et améliorations. Ces packs de fonctionnalités étendent les fonctionnalités dans des domaines clés, telles que le déploiement, la sécurité, analytique, runtime et sauvegarde. 

> [!NOTE]
> Les packs de fonctionnalités sont disponibles dans les éditions Enterprise et Developer de [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] lorsque : 
> 
> - Utilisé avec Software Assurance (SA), ou
> - En cours d’exécution [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] dans Azure à l’aide d’un contrat entreprise
> 
> Les packs de fonctionnalités ne sont pas disponibles pour n’importe quel autre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] Édition ou tout autre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version. 

## <a name="download-and-install"></a>Téléchargez et installez

Les packs de fonctionnalités sont cumulatifs. Par conséquent, lorsque installer feature pack 2, vous obtenez également les fonctionnalités et les mises à jour dans le feature pack 1.

* Téléchargez le [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 2](https://aka.ms/bts2016fp2).

* Téléchargez le [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100).

#### <a name="install"></a>Install

1. Exécutez le programme d’installation en tant qu’administrateur.
2. Dans **Bienvenue**, sélectionnez **suivant**. 
3. Acceptez le contrat de licence et sélectionnez **Suivant**. 
4. Poursuivez l’installation. Pendant l’installation, plusieurs fenêtres de commande peuvent ouvrir et fermer. Lorsque vous avez terminé, vous êtes invité à **Terminer**.

Un journal d’installation est créé dans `C:\ProgramData\Microsoft\E-Business Servers Updates\Updates\Uninstall4014788-FP2\setup.log`.

>[!TIP]
> Pour obtenir des instructions complètes sur l’installation, consultez le [installation pas à pas de Feature Pack](https://blog.sandro-pereira.com/2017/04/27/microsoft-biztalk-server-2016-feature-pack-1-step-by-step-installation/) billet de blog.

## <a name="feature-pack-2-updates"></a>Fonctionnalité des mises à jour du Pack 2

#### <a name="expose-soap-endpoints-with-api-managementcoreconnect-to-azure-api-managementmd"></a>[Exposer des points de terminaison SOAP avec la gestion des API](../core/connect-to-azure-api-management.md)

En développant sur l’intégration de gestion des API avec Feature Pack 1, vous pouvez exposer un WCF-BasicHTTP réception en tant que point de terminaison SOAP à l’aide de la console Administration de BizTalk Server. 

#### <a name="use-the-event-hub-adapterevent-hubs-adaptermd"></a>[Utilisation de l’adaptateur de concentrateur d’événements](event-hubs-adapter.md)

Envoyer des messages à partir de BizTalk à Azure Event Hubs et recevoir des messages à partir d’Azure Event Hubs à BizTalk Server. Lorsque vous configurez les propriétés de transport, vous pouvez facilement vous connecter à votre compte Azure et sélectionnent automatiquement votre espace de noms Azure Event Hubs et le concentrateur d’événements.

#### <a name="backup-to-azure-blob-accountcorehow-to-configure-the-backup-biztalk-server-jobmd"></a>[Sauvegarde sur le compte d’objets blob Azure](../core/how-to-configure-the-backup-biztalk-server-job.md)
Le travail de sauvegarde de BizTalk Server sauvegarde les fichiers journaux et les bases de données BizTalk. Lorsque vous configurez ce travail de l’Agent SQL, vous pouvez entrer un compte de stockage d’objets blob Azure dans les propriétés du travail. Cela vous donne une autre option pour sauvegarder vos données, au lieu d’utiliser un disque physique local. 

#### <a name="multi-machine-deployment-using-vstscoreconfigure-automatic-deployment-with-visual-studio-team-services-in-biztalkmd"></a>[Déploiement de plusieurs ordinateur à l’aide de VSTS](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)
À l’aide de groupes de déploiement, vous pouvez déployer vos applications à plusieurs serveurs BizTalk Server. Vous pouvez également définir le nom de l’application dans le projet d’application et installer votre application en entrant votre serveur d’administration.

[Groupes de déploiement](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index) fournit plus de détails sur la façon de procéder dans VSTS.  

#### <a name="use-service-bus-premiumcoresb-messaging-adaptermd"></a>[Utiliser Service Bus Premium](../core/sb-messaging-adapter.md)

L’adaptateur de Bus de Service prend en charge le Service Bus Premium, y compris l’envoi de messages vers des rubriques et files d’attente partitionnées. [Service Bus Premium et les niveaux de messagerie Standard](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-premium-messaging) détails plus sur Service Bus Premium. 

#### <a name="use-named-instances-with-application-insightscoresend-tracking-data-to-azure-application-insights-using-biztalk-servermd"></a>[Utiliser les instances nommées avec Application Insights](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)
Lorsque vous activez l’Analytique et que vous entrez la clé d’Application Insights, vous obtiendrez l’erreur : 

```
Group settings were not applied. (A database failure occurred due to database connectivity problems.)
```

Cela se produit lorsque vous utilisez des instances nommée de SQL. Il est résolu dans ce feature pack ; Vous pouvez utiliser des instances par défaut SQL, et les instances nommées de SQL. 

#### <a name="tls-12-support"></a>Prise en charge de TLS 1.2

TLS 1.2 est entièrement pris en charge dans BizTalk Server, y compris toutes les cartes et tous les accélérateurs. Vous pouvez désactiver SSL, TLS 1.0 et 1.1 du protocole TLS sur le serveur BizTalk. 

Informations de clé : 

* Les systèmes externes communique également avec BizTalk doivent prendre en charge de TLS 1.2
* N’importe quel code personnalisé, tels que des fonctoids, peut-être être mise à jour pour prendre en charge TLS 1.2

[Description du protocole TLS/SSL](https://support.microsoft.com/kb/3155464) explique comment configurer un environnement TLS 1.2. 

#### <a name="use-latest-newtonsoft-json"></a>Utiliser la dernière JSON Newtonsoft 
Newtonsoft est une infrastructure JSON pour .NET. Dans ce feature pack, la prise en charge pour la version 10.0.3 est inclus. [Téléchargement v. 10.0.3](https://www.nuget.org/packages/Newtonsoft.Json/10.0.3) directement à partir de NuGet. 


## <a name="feature-pack-1-updates"></a>Fonctionnalité des mises à jour du Pack 1

#### <a name="send-tracking-data-to-application-insightscoresend-tracking-data-to-azure-application-insights-using-biztalk-servermd"></a>[Envoyer des données de suivi à Application Insights](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)

Envoyer des données de suivi à Azure Application Insights pour utiliser ses fonctionnalités, telles qu’analytique, apprentissage, diagnostics et bien plus encore. 

#### <a name="configure-the-operational-data-feed-using-power-bicoreconfigure-the-operational-data-feed-for-power-bi-with-biztalk-servermd"></a>[Configurer les données opérationnelles de flux à l’aide de Power BI](../core/configure-the-operational-data-feed-for-power-bi-with-biztalk-server.md)

Envoyer des données de suivi à Power BI à l’aide d’oData. Par exemple, obtenir une représentation visuelle de vos données de suivi à partir de vos orchestrations et les ports. 

#### <a name="connect-to-the-management-rest-apis-in-biztalkcoreinstall-and-configure-the-management-rest-apis-in-biztalk-servermd"></a>[Se connecter à l’API REST dans BizTalk management](../core/install-and-configure-the-management-rest-apis-in-biztalk-server.md)

Utiliser l’API REST pour gérer à distance vos artefacts BizTalk, y compris les accords, les instances suspendues, orchestrations désinscrits et bien plus encore.

#### <a name="configure-advanced-schedulingcoreconfigure-the-time-zone-and-recurrence-scheduling-in-biztalk-servermd"></a>[Configurer la planification avancée](../core/configure-the-time-zone-and-recurrence-scheduling-in-biztalk-server.md)

Activer avancé de planification dans vos emplacements de réception. Par exemple, définir le fuseau horaire, ou définir une fenêtre de service de récurrence d’un jour spécifique sur un mois spécifique.

#### <a name="configure-automatic-deployments-with-vstscoreconfigure-automatic-deployment-with-visual-studio-team-services-in-biztalkmd"></a>[Configurer des déploiements automatiques avec VSTS](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  

Visual Studio Team Services (VSTS) permet de déployer automatiquement vos solutions, ou mettre à jour des applications existantes. VSTS communique avec un agent installé sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].

#### <a name="connect-to-sql-server-always-encrypted-columns-with-biztalk-servercoreconnect-to-sql-server-always-encrypted-columns-with-biztalk-servermd"></a>[Se connecter à SQL Server Always Encrypted des colonnes avec BizTalk Server](../core/connect-to-sql-server-always-encrypted-columns-with-biztalk-server.md)  

Utiliser l’adaptateur WCF-SQL pour interroger des colonnes chiffrées à partir d’une base de données Always Encrypted dans SQL Server.

#### <a name="integrate-with-api-managementcoreconnect-to-azure-api-managementmd"></a>[Intégrer la gestion des API](../core/connect-to-azure-api-management.md)

Au sein de votre service de gestion des API Azure, vous pouvez créer et exposent une API en tant que WSDL et utiliser l’URI vers un point de terminaison SOAP BizTalk.  