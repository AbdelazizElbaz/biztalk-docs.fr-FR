---
title: "Interrogation SQL Server à l’aide de l’adaptateur SQL avec le modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eef2e868-bd51-4393-b091-f67299b4759d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20d0ab576e5feddb0b5f3e867ca549a45bb2af97
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="poll-sql-server-using-the-sql-adapter-with-wcf-service-model"></a>Interrogation SQL Server à l’aide de l’adaptateur SQL avec le modèle de Service WCF
Vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages d’interrogation de données modifiées à partir de SQL Server. Vous pouvez spécifier une instruction d’interrogation de l’adaptateur s’exécute pour interroger la base de données. L’instruction d’interrogation peut être une instruction SELECT ou une procédure stockée qui retourne un jeu de résultats. Selon le type de message d’interrogation reçue, l’adaptateur expose des opérations d’interrogation différente :  
  
-   **L’interrogation**. Cette opération retourne un jeu de données en tant que partie du message d’interrogation.  
  
-   **TypedPolling**. Cette opération renvoie un message d’interrogation fortement typée.  
  
-   **XmlPolling**. Cette opération renvoie le message d’interrogation en tant qu’un message XML. Vous devez utiliser cette opération si vous souhaitez utiliser des instructions SELECT ou des procédures stockées qui utilisent la clause FOR XML pour retourner des données en tant que messages XML. [Clause FOR XML](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server) fournit plus d’informations. 
  
 Pour plus d’informations sur ces opérations d’interrogation, consultez [d’interrogation dans SQL Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md).  
  
> [!NOTE]
>  Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet aux clients de carte avoir une application unique avec plusieurs d’interrogation ou TypedPolling des opérations pour la même base de données ou une table. Pour prendre en charge un tel scénario, l’adaptateur inclut un ID unique : **InboundID**: dans l’URI de connexion. Cet ID, lors de l’ajout à la connexion URI, rend unique, ce qui permet à plusieurs opérations d’interrogation dans une application unique.  
  
 Les rubriques de cette section fournissent des instructions sur l’utilisation des opérations d’interrogation et TypedPolling dans une application .NET.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server en utilisant le modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-service.md)  
  
-   [Recevoir des fortement typée d’interrogation de modification de données de Messages à partir de SQL Server à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-sql-messages-with-wcf-service.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)