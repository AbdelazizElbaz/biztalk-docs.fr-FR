---
title: "Les opérations sont prises en charge par l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP
- operations, performing
ms.assetid: d78dbeb8-9dab-4a71-982e-f7ada51472e8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 014b0fc6158c151d510152550c0093f6ffa9031b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-operations-are-supported-by-the-oracle-database-adapter"></a>Les opérations sont prises en charge par l’adaptateur de base de données Oracle
Les clients de l’adaptateur peuvent effectuer des opérations sur la base de données Oracle en créant les projets BizTalk, en utilisant le modèle de canal WCF ou en utilisant le modèle de service WCF. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications. Ces opérations sont appelées en envoyant des messages SOAP sur un canal. Si une réponse est requise, il est retourné dans un message SOAP sur le même canal. Pour plus d’informations sur la structure du message et l’action SOAP associée à chaque opération, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).  
  
 Cette section fournit des informations sur les opérations prises en charge sur la base de données Oracle à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Exécution de base Insert, Update, Delete et les opérations Select sur Oracle Tables et vues](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-and-select-operations-on-oracle-tables-and-views.md)  
  
-   [Opérations sur les Tables et vues qui contiennent des données LOB](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md)  
  
-   [Opérations sur les fonctions et procédures stockées dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/operations-on-functions-and-stored-procedures-in-oracle-database.md)  
  
-   [Opérations sur les fonctions et procédures avec des paramètres REF CURSOR dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/ref-cursor-parameters-in-oracle-database-adapter.md)  
  
-   [Opérations sur les fonctions et procédures avec des Types d’enregistrements de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/operations-on-functions-and-procedures-with-record-types-in-oracle-database.md)  
  
-   [Opérations sur les Tables avec des Types de données BFILE](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)  
  
-   [Opérations sur les synonymes dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/operations-on-synonyms-in-oracle-database.md)  
  
-   [Opération SQLEXECUTE dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md)  
  
-   [Effectuer des opérations composites dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md)  
  
-   [Prise en charge pour la réception des Messages de modification de données reposant sur l’interrogation dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md)  
  
-   [Considérations relatives à la réception de base de données modifiées des Notifications à l’aide de l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [Prise en charge pour les Types définis par l’utilisateur Oracle dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/support-for-oracle-user-defined-types-in-oracle-database.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)