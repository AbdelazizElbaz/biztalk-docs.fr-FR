---
title: "Les opérations sont prises en charge par l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64cd124a-5e7f-4ee8-85d3-f9540b25d766
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7236c21f1e298f2ccd4cbb97db481cbd3626d186
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-operations-are-supported-by-the-oracle-e-business-suite-adapter"></a>Les opérations sont prises en charge par l’adaptateur Oracle E-Business Suite
## <a name="overview"></a>Vue d'ensemble
Les clients de carte peuvent effectuer des opérations dans Oracle E-Business Suite par :  
  
-   Création de projets BizTalk  
  
-   À l’aide du modèle de canal WCF  
  
-   À l’aide du modèle de service WCF  
  
 Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications. Ces opérations sont appelées en envoyant des messages SOAP sur un canal. Si une réponse est requise, il est retourné dans un message SOAP sur le même canal. Pour plus d’informations sur la structure du message et l’action SOAP associée à chaque opération, consultez [messages et des schémas de message pour l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).  
  
 Cette section fournit des informations sur les opérations prises en charge dans Oracle E-Business Suite à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
-   [Définir le contexte de l’Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)  
  
-   [Opérations sur les Tables d’Interface et les vues de l’Interface](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)  
  
-   [Opérations sur les API PL/SQL](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-pl-sql-apis.md)  
  
-   [Opérations sur les programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)  
  
-   [Opérations sur des ensembles de demande](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md)  
  
-   [Opérations sur les Tables d’Interface, les vues de l’Interface, les Tables et les vues qui contiennent des données LOB](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)  
  
-   [Opérations sur les Tables qui contiennent des Types de données BFILE](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)  
  
-   [Opérations sur les fonctions et procédures stockées](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-stored-procedures1.md)  
  
-   [Opérations sur les fonctions et procédures avec des paramètres REF CURSOR](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md)  
  
-   [Opérations sur les fonctions et procédures avec des Types d’enregistrements](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
-   [Opérations sur les synonymes](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-synonyms2.md)  
  
-   [Considération pour recevoir des Notifications de modification de base de données](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [Prise en charge pour les appels entrants à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)  
  
-   [Prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)  
  
-   [Prise en charge des opérations composites](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md)  
  
-   [Prise en charge pour les Types définis par l’utilisateur Oracle](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-oracle-user-defined-types2.md)  
  
## <a name="see-also"></a>Voir aussi  
[Comprendre l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)