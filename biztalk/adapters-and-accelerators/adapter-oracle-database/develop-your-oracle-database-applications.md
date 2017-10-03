---
title: "Développer vos applications de base de données Oracle dans BizTalk Server | Documents Microsoft"
description: "Créer des applications de base de données Oracle à l’aide de WCF, ou BizTalk Server avec le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4a685b2-ac17-4949-bc77-001f56450847
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b0da5ae6691e3cca4a844d037e4714bd09ec146
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-your-oracle-database-applications"></a>Développer vos applications de base de données Oracle

## <a name="overview"></a>Vue d'ensemble
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée. Les applications clientes peuvent consommer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour appeler des opérations sur les objets de base de données Oracle. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] peuvent être utilisés :  
  
-   Via une liaison de port physique dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   En appelant des méthodes sur une instance d’un [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] proxy client.  
  
-   En tant que hébergé [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service.  
  
-   En envoyant des messages SOAP via une instance de canal dans le code qui utilise le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal.  

## <a name="biztalk-vs-wcf-service-vs-wcf-channel"></a>Canal WCF vs du service WCF BizTalk vs  
 Le tableau suivant :  
  
-   Répertorie les différentes opérations qui peuvent être effectuées sur une base de données Oracle à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
-   Fournit des liens vers les rubriques contenant des informations sur l’exécution de la tâche à l’aide de l’approche choisie ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], modèle ou modèle de canal WCF du service WCF).  
  
|Tâche|BizTalk Server|Modèle de Service WCF|Modèle de canal WCF|  
|----------|--------------------|-----------------------|-----------------------|  
|Base Insert, Update, Delete et les opérations Select sur les tables et vues|[Insérer, mettre à jour, supprimer ou sélectionner des opérations à l’aide de BizTalk Server avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-using-biztalk-server-with-oracle-db.md)|[Insérer, mettre à jour, supprimer ou sélectionner des opérations dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md)|[Exécuter une opération d’insertion dans la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md)|  
|Opérations sur les tables et les vues contenant des données LOB|[Exécuter des opérations sur les tables avec des types de données dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-large-object-data-types-in-oracle-database.md)|[Effectuer des opérations sur les tables avec des types de données de grande taille dans la base de données Oracle à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-large-data-types-in-oracle-db-using-a-wcf-service.md)||  
|Opérations sur les fonctions et procédures stockées|[Appeler des fonctions et les procédures de base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md)|[Appeler des fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)|[Appeler une fonction dans la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)|  
|Appel de fonctions surchargées et procédures|[Appeler des fonctions surchargées et les procédures de base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server.md)|[Appeler des fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)||  
|Opérations sur les paramètres avec des REF CURSOR fonctions et procédures|[Appeler des fonctions et procédures avec des REF CURSOR dans la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-ref-cursors-in-oracle-db-using-biztalk-server.md)|[Exécuter des opérations à l’aide de REF CURSOR dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md)||  
|Opérations sur les fonctions et procédures avec des types d’enregistrements|[Appeler des fonctions et procédures avec des Types d’enregistrements dans la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-record-types-in-oracle-db-with-biztalk-server.md)|[Exécuter des opérations à l’aide des Types d’enregistrements dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)||  
|Opérations sur les tables et les vues avec les types de données BFILE|[Exécuter des opérations sur les Tables avec des Types de données BFILE dans la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md)|||  
|Opération SQLEXECUTE|[Exécuter l’opération SQLEXECUTE dans la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-biztalk-server.md)|[Exécuter l’opération SQLEXECUTE dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)|[Exécuter une opération SQLEXECUTE dans la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)|  
|Réception de messages de modification de données reposant sur l’interrogation|[Base de données Oracle interrogation à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-biztalk-server.md)|[Recevoir des Messages d’interrogation de données modifiées dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-service.md)|[Recevoir des Messages d’interrogation de données modifiées dans la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-channel.md)|  
|Effectuer des opérations composites sur la base de données Oracle|[Exécuter des opérations composites sur la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)|||  
|Réception des Notifications de modification de base de données|[Recevoir des Notifications de modification de base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)|[Recevoir des Notifications de modification de base de données Oracle à l’aide de la Modèle1 de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-the-wcf-service-model1.md)||  
  

  
## <a name="next-steps"></a>Étapes suivantes
 Les rubriques de cette section fournissent des informations, des procédures et des exemples pour vous aider à développer des applications qui consomment le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] dans les deux [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] programmation de solutions. 
  
-   [Créer une connexion à la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)
  
-   [Obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) 
  
-   [Configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)
  
-   [Diffusion en continu des types de données dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md)
  
-   [Recevoir des messages d’interrogation de données modifiées dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)
  
-   [Développement d’Applications de BizTalk Server](../../core/developing-biztalk-server-applications.md)
  
-   [Développer des applications de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)  
  
-   [Développer des applications de base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)  
  
-   [Obtenir les métadonnées par programme à partir de la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)  
  
-   [Utilisez l’adaptateur de base de données Oracle avec SharePoint](../../adapters-and-accelerators/adapter-oracle-database/use-the-oracle-database-adapter-with-sharepoint.md)
  
-   [Exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)  
  
-   [Configurer le niveau d’isolation de transaction et le délai d’attente de transaction avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)

- [Utiliser svcutil.exe](use-the-servicemodel-metadata-utility-with-the-oracle-db-adapter-in-biztalk.md)