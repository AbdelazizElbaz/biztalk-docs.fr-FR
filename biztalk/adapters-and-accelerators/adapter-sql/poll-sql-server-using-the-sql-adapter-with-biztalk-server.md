---
title: "Interrogation SQL Server à l’aide de l’adaptateur SQL avec BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eef9a4b4-552d-4552-b318-1deab506bad9
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31e631a966ffee632e6c866a962c4fe47b2f1025
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="poll-sql-server-using-the-sql-adapter-with-biztalk-server"></a>Interrogation SQL Server à l’aide de l’adaptateur SQL avec BizTalk Server
Vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages d’interrogation de données modifiées à partir de SQL Server. Vous pouvez spécifier une instruction d’interrogation de l’adaptateur s’exécute pour interroger la base de données. L’instruction d’interrogation peut être une instruction SELECT ou une procédure stockée qui retourne un jeu de résultats. Selon le type de message d’interrogation reçue, l’adaptateur expose trois façons différentes d’interrogation :  
  
-   **L’interrogation**. Cette opération retourne un jeu de données en tant que partie du message d’interrogation. Au moment du design, le schéma de l’objet de base de données interrogé n’est pas disponible. Au lieu de cela, le schéma est disponible en tant que partie du message d’interrogation pendant l’exécution.  
  
-   **TypedPolling**. Cette opération renvoie un message d’interrogation fortement typée. Au moment du design, le schéma de l’objet de base de données est également disponible. Vous devez utiliser cette opération pour l’interrogation si vous souhaitez mapper certains éléments à partir du message d’interrogation à un autre schéma, ce qui pourrait être pour une autre opération.  
  
-   **XmlPolling**. Cette opération renvoie le message d’interrogation en tant qu’un message XML. Vous devez utiliser cette opération si vous souhaitez utiliser des instructions SELECT ou des procédures stockées qui utilisent la clause FOR XML pour retourner des données en tant que messages XML. Pour plus d’informations sur la clause FOR XML, consultez [FOR XML (SQL Server)](https://msdn.microsoft.com/library/ms178107.aspx). 
  
 Pour plus d’informations sur ces opérations d’interrogation, consultez [prise en charge pour l’interrogation](https://msdn.microsoft.com/library/dd788416.aspx).  
  
> [!NOTE]
>  Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet aux clients d’adaptateur pour qu’une application BizTalk unique avec plusieurs d’interrogation ou TypedPolling des opérations pour la même base de données ou une table. Pour prendre en charge un tel scénario, l’adaptateur inclut un ID unique : **InboundID**: dans l’URI de connexion. Cet ID, lors de l’ajout à la connexion URI, rend unique, ce qui permet à plusieurs opérations d’interrogation dans une même application BizTalk.  
  
 Les rubriques de cette section fournissent des instructions sur l’utilisation de l’interrogation, TypedPolling et XmlPolling dans une application BizTalk. Cette section fournit des informations sur l’utilisation de la **InboundID** propriété de connexion.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md)  
  
-   [Recevoir des fortement typée d’interrogation de modification de données de Messages à partir de SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md)  
  
-   [Réception d’interrogation de Messages à l’aide d’instructions SELECT avec la Clause FOR XML à partir de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md)  
  
-   [Réception d’interrogation de Messages entre plusieurs Ports de réception à partir de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)