---
title: "Développer vos applications Siebel dans BizTalk Server | Documents Microsoft"
description: "Créer des applications Siebel à l’aide de WCF, ou BizTalk Server avec le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bc04906-6d64-433c-b357-797ec5883279
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c1535a3aa7861effdad998d4d997fbcdfced02c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-your-siebel-applications"></a>Développer vos applications Siebel

## <a name="overview"></a>Vue d'ensemble
Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée. Les applications clientes peuvent consommer le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] pour appeler des opérations sur les artefacts Siebel. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] peuvent être utilisés :  
  
-   Via une liaison de port physique dans une solution BizTalk Server.  
  
-   En appelant des méthodes sur une instance d’un proxy client.  
  
-   Un service WCF hébergé.  
  
-   En envoyant des messages SOAP via une instance de canal dans le code qui utilise le modèle de canal WCF.  
  
-   Via l’interface ADO.NET.  
  
## <a name="biztalk-vs-wcf-service-vs-wcf-channel-vs-adonet"></a>Vs pour le service WCF BizTalk vs WCF de canal et ADO.NET
 Le tableau suivant :  
  
-   Répertorie les différentes opérations qui peuvent être effectuées sur un système Siebel à l’aide du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
-   Indique laquelle des approches ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], WCF service model, modèle de canal WCF ou interface ADO.NET) peut être utilisé pour effectuer les opérations.  
  
-   Fournit des liens vers plus d’informations sur l’exécution de la tâche à l’aide de l’approche choisie.  
  
|Tâche|BizTalk Server|Modèle de Service WCF|Modèle de canal WCF|Interface ADO.NET|  
|----------|--------------------|-----------------------|-----------------------|-----------------------|  
|Opérations de base Insert, Update, Delete et requête sur des composants d’entreprise|[Exécuter des opérations sur les composants de métier à l’aide de BizTalk Server et de l’adaptateur Siebel](run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)|[Exécuter des opérations sur les composants d’entreprise avec l’adaptateur Siebel à l’aide du modèle de Service WCF](run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)|[Exécuter des opérations sur les composants d’entreprise avec l’adaptateur Siebel à l’aide du modèle de canal WCF](run-tasks-on-business-components-with-the-siebel-adapter-using-a-wcf-channel.md)|[Exécuter une requête SELECT sur les composants d’entreprise Siebel](run-a-select-query-on-business-components-with-siebel.md) **Remarque :** vous ne pouvez effectuer une opération SELECT à l’aide du [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].|  
|Opérations sur les composants d’entreprise avec des champs de groupe à valeurs multiples|[Exécuter des opérations sur les composants d’entreprise avec des champs de groupe à valeurs multiples à l’aide de BizTalk Server et de l’adaptateur Siebel](run-operations-on-business-components-with-mvg-fields-using-the-siebel-adapter.md)|[Exécuter des opérations sur les composants d’entreprise avec des champs de groupe à valeurs multiples avec l’adaptateur Siebel à l’aide du modèle de Service WCF](work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md)|||  
|Opérations sur les composants d’entreprise avec des champs de la liste de choix|[Exécuter des opérations sur les composants d’entreprise avec les champs de liste de choix à l’aide de BizTalk Server et de l’adaptateur Siebel](run-tasks-on-business-components-with-picklist-fields-using-the-siebel-adapter.md)||||  
|Appel de services d’entreprise|[Appeler des méthodes de Service Business à l’aide de BizTalk Server et l’adaptateur Siebel](invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md)|||[Exécuter une opération d’exécution sur les Services avec Siebel](run-an-execute-operation-on-business-services-with-siebel.md)|  
|Appel de services d’entreprise avec des objets d’intégration|[Appeler des méthodes de Service d’entreprise avec des objets d’intégration à l’aide de l’adaptateur Siebel](run-business-service-methods-with-integration-objects-using-the-siebel-adapter.md)||||  

## <a name="next-steps"></a>Étapes suivantes  
 Les rubriques de cette section fournissent des informations, des procédures et des exemples pour vous aider à développer des applications qui consomment le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] dans les deux [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] programmation de solutions. 

- [Créer une connexion au système Siebel](create-a-connection-to-the-siebel-system.md)
- [Obtenir les métadonnées pour les opérations Siebel dans Visual Studio](get-metadata-for-siebel-operations-in-visual-studio.md)
- [ID de nœud de métadonnées](metadata-node-ids1.md)
- [Utilisez les propriétés de liaison](read-about-biztalk-adapter-for-siebel-binding-properties.md)
- [Développer des applications BizTalk à l’aide de l’adaptateur Siebel](develop-biztalk-applications-using-the-siebel-adapter.md)
- [Développer des applications à l’aide du modèle de Service WCF](develop-siebel-applications-using-the-wcf-service-model.md)
- [Développer des applications à l’aide du modèle de canal WCF](develop-siebel-applications-using-the-wcf-channel-model3.md)
- [Utiliser le fournisseur de données .NET Framework pour Siebel eBusiness Applications](use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)
- [Utilisez l’adaptateur Siebel avec SharePoint](use-the-siebel-adapter-with-sharepoint.md)
- [Exemples](samples-for-the-siebel-adapter.md)
- [À l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour Siebel eBusiness Applications](use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md)