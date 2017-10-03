---
title: "Développer vos applications SQL dans BizTalk Server | Documents Microsoft"
description: "Créer des applications de l’adaptateur SQL à l’aide de WCF, ou BizTalk Server avec le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fac4b5b0-2980-4784-a081-e795654292ed
caps.latest.revision: "39"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e5be1f01a9d8180dea60f508cba1c4ff7c0964f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-your-sql-applications"></a>Développer vos applications SQL

## <a name="overview"></a>Vue d'ensemble
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison. Les applications clientes peuvent consommer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour appeler des opérations sur les objets de SQL Server. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peuvent être utilisés :  
  
-   Via une liaison de port physique dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   En appelant des méthodes sur une instance d’un proxy client.  
  
-   Un service WCF hébergé.  
  
-   En envoyant des messages SOAP via une instance de canal dans le code qui utilise le modèle de canal WCF.  

## <a name="biztalk-vs-wcf-service-vs-wcf-channel"></a>Canal WCF vs du service WCF BizTalk vs    
 Le tableau suivant :  
  
-   Répertorie les différentes opérations qui peuvent être effectuées sur SQL Server à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
-   Fournit des liens vers les rubriques contenant des informations sur l’exécution de la tâche à l’aide de l’approche choisie ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], modèle de service WCF, modèle de canal WCF).  
  
|Tâche|BizTalk Server|Modèle de Service WCF|Modèle de canal WCF|  
|----------|--------------------|-----------------------|-----------------------|  
|Exécution de base Insert, Update, Delete et les opérations Select sur les tables et vues|[Insérer, mettre à jour, supprimer ou sélectionner des opérations à l’aide de BizTalk Server avec l’adaptateur SQL](insert-update-delete-or-select-using-the-sql-adapter-in-biztalk-server.md)|[Insérer, mettre à jour, supprimer ou sélectionner des opérations sur les tables d’interface et les vues à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)|[Exécuter une opération Insert sur une Table dans SQL à l’aide du modèle de canal WCF](run-an-insert-operation-on-a-table-in-sql-using-the-wcf-channel-model.md)|  
|Colonnes de type de l’exécution d’opérations sur les tables et vues avec des données volumineuses<br /><br /> (Inclut également des informations sur les opérations FILESTREAM à l’aide de l’adaptateur)|[Opérations sur les tables et vues qui contiennent des types de données de grande taille à l’aide de l’adaptateur SQL](supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md)|[Exécuter des opérations sur les Tables et vues avec des Types de données volumineux dans SQL à l’aide du modèle de Service WCF](read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md)|-|  
|Exécution de procédures stockées|[Exécuter des procédures stockées dans SQL Server à l’aide de BizTalk Server](execute-stored-procedures-in-sql-server-using-biztalk-server.md)|[Appeler les procédures stockées de SQL à l’aide du modèle de Service WCF](invoke-stored-procedures-in-sql-using-the-wcf-service-model.md)|-|  
|L’exécution de procédures stockées avec paramètres uniques sans l’aide d’une orchestration BizTalk|[Exécuter des procédures stockées avec un seul paramètre XML dans SQL Server à l’aide de BizTalk Server](execute-stored-procedures-with-a-single-xml-parameter-in-sql-using-biztalk.md)|-|-|  
|Exécution de procédures stockées qui contiennent une clause FOR XML dans la définition|[Exécuter des procédures stockées ayant une clause FOR XML dans SQL Server à l’aide de BizTalk Server](execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md)|-|-|  
|Effectuer des opérations composites sur SQL Server|[Exécuter des opérations composites sur SQL Server à l’aide de BizTalk Server](run-composite-operations-on-sql-server-using-biztalk-server.md)|-|-|  
|Appel de fonctions scalaires dans SQL Server|[Appeler des fonctions scalaires dans SQL Server à l’aide de BizTalk Server](invoke-scalar-functions-in-sql-server-using-biztalk-server.md)|[Appeler des fonctions scalaires dans SQL Server à l’aide du modèle de Service WCF](invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model.md)|-|  
|Appel de fonctions table dans SQL Server|[Appeler des fonctions table dans SQL Server à l’aide de BizTalk Server](invoke-table-valued-functions-in-sql-server-using-biztalk-server.md)|[Appeler des fonctions table dans SQL Server à l’aide du modèle de Service WCF](invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model.md)|-|  
|Exécution **ExecuteReader**, **ExecuteScalar**, ou **ExecuteNonQuery** opérations|[ExecuteReader, ExecuteScalar ou opérations ExecuteNonQuery dans SQL à l’aide de BizTalk Server](executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)|[Opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans SQL à l’aide du modèle de Service WCF](executereader-executescalar-executenonquery-in-sql-using-wcf-service-model.md)|-|  
|Réception de messages de modification de données reposant sur l’interrogation|[Interrogation SQL Server à l’aide de l’adaptateur SQL avec BizTalk Server](poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)|[Interrogation SQL Server à l’aide de l’adaptateur SQL avec le modèle de Service WCF](poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)|[Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server à l’aide du modèle de canal WCF](receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md)|  
|Recevoir des notifications de SQL Server|[Recevoir des Notifications de requête SQL à l’aide de BizTalk Server](receive-sql-query-notifications-using-biztalk-server.md)|[Recevoir des Notifications de requête SQL à l’aide du modèle de Service WCF](receive-query-notifications-from-sql-using-the-wcf-service-model.md)|-|  

## <a name="next-steps"></a>Étapes suivantes  
 Les rubriques de cette section fournissent des informations, des procédures et des exemples pour vous aider à développer des applications qui consomment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] dans les deux [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et solutions de programmation .NET. 

- [Créer une connexion à SQL Server](create-a-connection-to-sql-server.md)
- [Obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio](get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)
- [ID de nœud de métadonnées](metadata-node-ids2.md)
- [Utilisez les propriétés de liaison](read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)
- [Condition préalable : Configurer MSDTC](configure-msdtc-on-sql-server-and-adapter-client.md)
- [Développer des applications BizTalk à l’aide de l’adaptateur SQL](develop-biztalk-applications-using-the-sql-adapter.md)
- [Développer des applications à l’aide du modèle de Service WCF](develop-sql-applications-using-the-wcf-service-model.md)
- [Développer des applications à l’aide du modèle de canal WCF](develop-sql-applications-using-the-wcf-channel-model.md)
- [Exemples](samples-for-the-sql-adapter.md)
- [Configurer le niveau d’Isolation de Transaction et le délai d’attente de Transaction](configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)
  
