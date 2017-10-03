---
title: "Schémas de message pour le Composite Operation1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 768473ef-da8d-4e58-86cb-597c28ded49c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b22861d36693ab3ef487e5e3d0b86544f048e95
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-composite-operation"></a>Schémas de message pour l’opération Composite
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] vous permet d’exécuter des opérations composites dans Oracle E-Business Suite. Une opération composite peut contenir plusieurs opérations et dans n’importe quel ordre. Pour plus d’informations sur les opérations peuvent être incluses dans une opération composite, consultez [prise en charge des opérations composites](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md).  
  
 Pour plus d’informations sur la façon d’effectuer des opérations composites à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [exécuter des opérations composites sur la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).  
  
## <a name="message-structure-for-the-composite-operation"></a>Structure de message pour l’opération Composite  
 Dans la mesure où une opération composite contient plusieurs opérations individuelles ; la structure d’une opération composite contient des structures de message des opérations individuelles. Le message d’opération composite suit un modèle d’échange de message demande-réponse.  
  
 Le tableau suivant montre la structure des messages de demande et de réponse d’une opération composite qui contient une opération d’insertion, une procédure stockée empaquetée qui n’accepte pas les paramètres d’entrée et une opération de suppression.  
  
> [!NOTE]
>  Consultez les descriptions de l’entité après le tableau.  
  
|Opération|Message XML|  
|---------------|-----------------|  
|Demande d’opération composite|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/[SCHEMA]/[TABLE_NAME]">     <Recordset>       <InsertRecord>         <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>           <InLineValue>[value]</InlineValue>         <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>           <InLineValue>[value]</InlineValue>         …       <InsertRecord>    </RECORDSET>   </Insert>   <[SP_NAME] xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/[SCHEMA]/[APP_NAME]" />   <Delete xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/[SCHEMA]/[TABLE_NAME]">     <FILTER>[WHERE_clause]</FILTER>   </Delete> </Request>`|  
|Réponse de l’opération composite|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/[SCHEMA]/[TABLE_NAME]">     <InsertResult>[value]</InsertResult>    </InsertResponse>   <[SP_NAME]Response xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Procedures/[SCHEMA]">     <[PRM1_NAME]>value1<[PRM1_NAME]>     <[PRM2_NAME]>value2</[PRM2_NAME]>     …   </[SP_NAME]Response>    <DeleteResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 Descriptions de l’entité :  
  
 [PROJECT_NAME] = nom du projet BizTalk qui contient le schéma de l’opération composite.  
  
 [COMPOSITE_SCHEMA_NAME] = nom du schéma d’opération composite donné par l’utilisateur.  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_table] = nom de la table ; par exemple, les employés.  
  
 [FIELD1_NAME] = nom du champ de Table ; par exemple, un nom.  
  
 [SP_NAME] = la procédure stockée empaquetée à être exécutés ; par exemple, ADD_EMP_DETAILS.  
  
 [Nom_application] = nom de l’Application Oracle qui contient la procédure stockée empaquetée.  
  
 [PRM1_NAME] = le nom du paramètre dans la procédure stockée package Oracle.  
  
## <a name="message-action-for-the-composite-operation"></a>Action de message pour l’opération Composite  
 L’action du message pour l’opération composite est « CompositeOperation ».  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)