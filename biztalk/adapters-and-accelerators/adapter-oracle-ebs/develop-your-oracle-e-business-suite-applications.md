---
title: "Développer vos applications Oracle E-Business Suite dans BizTalk | Documents Microsoft"
description: "Créer des applications Oracle eBusiness Suite à l’aide de WCF, ou BizTalk Server avec le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7b1ebff-b3f8-4e07-a089-d1d5bfb78d56
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc72e5adbef300115189119ba77821a08883999a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-your-oracle-e-business-suite-applications"></a>Développer vos applications Oracle E-Business Suite

## <a name="overview"></a>Vue d'ensemble
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison. Les applications clientes peuvent consommer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour appeler des opérations sur les artefacts d’Oracle E-Business Suite. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] peuvent être utilisés :  
  
-   Via une liaison de port physique dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   En appelant des méthodes sur une instance d’un proxy client.  
  
-   En envoyant des messages SOAP via une instance de canal dans le code qui utilise le modèle de canal WCF.  

## <a name="biztalk-vs-wcf-service-vs-wcf-channel"></a>Canal WCF vs du service WCF BizTalk vs 
  
 Le tableau suivant :  
  
-   Répertorie les différentes opérations qui peuvent être effectuées sur Oracle E-Business Suite à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
-   Fournit des liens vers les rubriques contenant des informations sur l’exécution de la tâche à l’aide de l’approche choisie ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], modèle de canal de modèle de service WCF ou WCF).  
  
|Opération|BizTalk Server|Modèle de Service WCF|Modèle de canal WCF|  
|---|---|---|---|  
|Exécution d’opérations sur les tables d’interface et les vues | [Insérer, mettre à jour, supprimer ou sélectionnez des tables d’interface et les vues de l’interface avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-or-select-on-interface-tables-and-views-with-oracle-ebs.md) |[Insérer, mettre à jour, supprimer ou sélectionner des opérations sur les tables d’interface et les vues à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)|[Exécuter une opération d’insertion sur une table d’interface dans Oracle E-Business Suite à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-ebs/insert-on-an-interface-table-in-oracle-ebs-using-the-wcf-channel-model.md)|  
|Exécution d’opérations sur les tables et les vues avec les types de données volumineuses | [Effectuer des opérations sur les tables avec des types de données de grande taille dans Oracle E-Business Suite à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md) |[Effectuer des opérations sur les tables avec des types de données de grande taille dans Oracle E-Business Suite à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md)||  
|Effectuer des opérations composites sur la base de données Oracle | [Effectuer des opérations composites sur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/complete-composite-operations-on-oracle-e-business-suite.md)|||  
|Appeler des programmes simultanés dans Oracle E-Business Suite | [Appeler des programmes simultanés dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-concurrent-programs-in-oracle-e-business-suite.md) | [Appeler des programmes simultanés dans Oracle E-Business Suite à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/run-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model.md)||  
|Appel de demande définit dans Oracle E-Business Suite | [Appeler des ensembles de requêtes dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-request-sets-in-oracle-e-business-suite.md) | [Appeler des ensembles de requêtes dans Oracle E-Business Suite à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-request-sets-in-oracle-e-business-suite-using-the-wcf-service-model.md)||  
|Exécution d’opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery| [Opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/executereader-executescalar-or-executenonquery-in-oracle-e-business-suite.md) |[Opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans Oracle E-Business Suite à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/executereader-executescalar-executenonquery-in-oracle-ebs-with-a-wcf-service.md)||  
|Oracle de l’interrogation de la base de données à l’aide de BizTalk Server|[Interrogation Oracle E-Business Suite à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)|[Interrogation Oracle E-Business Suite à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)||  
|Recevoir des notifications de modification de base de données à partir d’Oracle E-Business Suite|[Recevoir des Notifications de modification de base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)|[Recevoir des notifications de modification de base de données Oracle E-Business Suite à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-the-wcf-service-model.md)|[Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT avec le modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement-with-the-wcf-channel-model.md)|  

## <a name="next-steps"></a>Étapes suivantes  
 Les rubriques de cette section fournissent des informations, des procédures et des exemples pour vous aider à développer des applications qui consomment le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] dans les deux [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et solutions de programmation .NET. 
  
-   [Créer une connexion à Oracle eBusiness Suite](create-a-connection-to-oracle-e-business-suite.md)
-   [Obtenir les métadonnées pour les opérations d’Oracle eBusiness Suite dans Visual Studio](get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)
-   [Utilisez les propriétés de liaison](read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)
-   [Recevoir des messages d’interrogation de données modifiées](receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md)
-   [Activer les transactions à l’aide de MSDTC](enable-ms-dtc-to-allow-transactions-for-oracle-e-business-suite-adapter.md)
-   [Développer des applications BizTalk à l’aide de l’adaptateur Oracle eBusiness Suite](develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)
-   [Développer des applications à l’aide du modèle de Service WCF](develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)
-   [Développer des applications à l’aide du modèle de canal WCF](develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)
-   [Utilisez l’adaptateur Oracle eBusiness Suite avec SharePoint](use-the-oracle-e-business-suite-adapter-with-sharepoint.md)
-   [Exemples](samples-for-the-oracle-ebs-adapter.md)
-   [Configurer les propriétés de transaction et le contexte de l’application](configure-transaction-properties-and-application-context-in-oracle-ebs-adapter.md)
  
