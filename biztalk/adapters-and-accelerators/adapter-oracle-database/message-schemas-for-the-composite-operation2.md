---
title: "Schémas de message pour l’OP2 Composite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0164ea07-a373-430b-b569-3e29df1d081b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1014ea162e9fab33aa6630d0cdb4eb774f91031
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-composite-operation"></a>Schémas de message pour l’opération Composite
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] vous permet d’exécuter des opérations composites sur la base de données Oracle. Une opération composite peut contenir plusieurs opérations et dans n’importe quel ordre. Pour plus d’informations sur les opérations peuvent être incluses dans une opération composite, consultez [exécuter des opérations composites dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md).  
  
 Pour plus d’informations sur la façon d’effectuer des opérations composites à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [exécuter des opérations composites sur la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).  
  
## <a name="message-structure-for-the-composite-operation"></a>Structure de message pour l’opération Composite  
 Parce qu’une opération composite contient plusieurs opérations individuelles ; la structure d’une opération composite contient des structures de message des opérations individuelles. Le message d’opération composite suit un modèle d’échange de message demande-réponse.  
  
 Le tableau suivant montre la structure des messages de demande et de réponse d’une opération composite qui contient une opération d’insertion, une procédure stockée empaquetée qui n’accepte pas les paramètres d’entrée et une opération de suppression.  
  
|Opération|Message XML|  
|---------------|-----------------|  
|Demande d’opération composite|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <RECORDSET>       <[TABLE_NAME]RECORDINSERT>         <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>         …       </[TABLE_NAME]RECORDINSERT>    </RECORDSET>   </Insert>   <[SP_NAME] xmlns="[VERSION]/[SCHEMA]/Procedure" />   <Delete xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <FILTER>[WHERE_clause]</FILTER>   </Delete> </Request>`|  
|Réponse de l’opération composite|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <InsertResult>[value]</InsertResult>    </InsertResponse>   <[SP_NAME]Response xmlns="[VERSION]/[SCHEMA]/Procedure">     <[PRM1_NAME]>value1<[PRM1_NAME]>     <[PRM2_NAME]>value2</[PRM2_NAME]>     …   </[SP_NAME]Response>    <DeleteResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 [VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.OracleDB/2007/03  
  
 [PROJECT_NAME] = nom du projet BizTalk qui contient le schéma de l’opération composite.  
  
 [COMPOSITE_SCHEMA_NAME] = nom du schéma d’opération composite donné par l’utilisateur.  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_table] = nom de la table ; par exemple, les employés.  
  
 [FIELD1_NAME] = nom du champ de Table ; par exemple, un nom.  
  
 [SP_NAME] = la procédure stockée empaquetée à être exécutés ; par exemple, ADD_EMP_DETAILS.  
  
 [PRM1_NAME] = le nom du paramètre Oracle dans la procédure stockée.  
  
## <a name="message-action-for-the-composite-operation"></a>Action de message pour l’opération Composite  
 L’action du message pour l’opération composite est « http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation ».  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)