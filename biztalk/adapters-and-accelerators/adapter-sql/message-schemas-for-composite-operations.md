---
title: "Schémas de message pour des opérations composites | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d80c023b-1912-43d4-be29-eb9e1b323593
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b89c354baea2ddb46abf549752dc09699b9c9695
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-composite-operations"></a>Schémas de message pour des opérations composites
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] vous permet d’exécuter des opérations composites sur la base de données SQL Server. Une opération composite peut contenir plusieurs opérations, y compris l’insertion, mise à jour et supprimer des opérations sur les tables et les vues et les opérations sur les procédures stockées. Une opération composite peut inclure ces opérations dans n’importe quel ordre.  
  
 Pour plus d’informations sur :  
  
-   Des opérations composites, consultez [prise en charge des opérations composites](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md).  
  
-   Comment effectuer des opérations composites à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [exécuter des opérations composites dans SQL Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md).  
  
## <a name="message-structure-for-the-composite-operation"></a>Structure de message pour l’opération Composite  
 Dans la mesure où une opération composite contient plusieurs opérations individuelles ; la structure d’une opération composite contient des structures de message des opérations individuelles. Une opération composite contient des opérations sur les tables, vues et procédures stockées, le message d’opération composite suit un modèle d’échange de message demande-réponse.  
  
 Le tableau suivant montre la structure des messages de demande et de réponse d’une opération composite qui contient une opération d’insertion, une procédure stockée qui n’accepte pas les paramètres d’entrée et une opération de suppression.  
  
|Opération|Message XML|  
|---------------|-----------------|  
|Demande d’opération composite|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <Rows>       <[TABLE_NAME]>         <[FIELD1_NAME]>[Value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[Value1]</[FIELD2_NAME]>         …       </[TABLE_NAME]>     </Rows>   </Insert>   <[SP_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]" />   <Delete xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <Rows>       <[TABLE_NAME]>         <[FIELD1_NAME]>[Value1]</[FIELD1_NAME]>       </[TABLE_NAME]>     </Rows>   </Delete> </Request>`|  
|Réponse de l’opération composite|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <InsertResult>       <long>[value]</long>      </InsertResult>   </InsertResponse>   <[SP_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]">     <[SP_NAME]Result>       <DataSet>         <any>[Value]</any>          <any>[Value]</any>          …       </DataSet>     </[SP_NAME]Result>     <ReturnValue>[value]</ReturnValue>    </[SP_NAME]Response>   <DeleteResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 [PROJECT_NAME] = nom du projet BizTalk qui contient le schéma de l’opération composite.  
  
 [COMPOSITE_SCHEMA_NAME] = nom du schéma d’opération composite donné par l’utilisateur.  
  
 [Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.  
  
 [Nom_table] = nom de la table ; par exemple, les employés.  
  
 [FIELD1_NAME] = nom du champ de Table ; par exemple, un nom.  
  
 [SP_NAME] = la procédure stockée à exécuter ; par exemple, ADD_EMP_DETAILS.  
  
## <a name="message-action-for-the-composite-operation"></a>Action de message pour l’opération Composite  
 L’action du message pour l’opération composite est « CompositeOperation ».  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)