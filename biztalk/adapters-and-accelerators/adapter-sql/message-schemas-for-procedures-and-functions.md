---
title: "Schémas de message pour les procédures et fonctions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4acfb29e-8774-4eb7-ba10-2dcb93d2b41a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 374b4d3365ec3aaac86fb5004969cd4cc189271d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-procedures-and-functions"></a>Schémas de message pour les procédures et fonctions
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces SQL Server de base de données des procédures stockées et scalaires et fonctions table en tant qu’opérations. Cette section décrit la structure des messages et les actions utilisées pour appeler des procédures et des fonctions.  
  
## <a name="message-structure-of-procedures-and-functions"></a>Structure des messages de procédures et fonctions  
 Les opérations signalées pour les procédures et fonctions suivent un modèle d’échange de message demande-réponse. Le tableau suivant illustre la structure de ces messages de demande et de réponse.  
  
|Opération|Message XML| Description|  
|---------------|-----------------|-----------------|  
|Demande de procédure stockée|`<[SP_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|-|  
|Réponse de la procédure stockée|`<[SP_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]">   <[SP_NAME]Result>      <DataSet>        <any>[Value]</any>       <any>[Value]</any>       …     </DataSet>   </[SP_NAME]Result>   <ReturnValue>[Value]</ReturnValue> </[SP_NAME]Response>`|La valeur de retour d’une procédure stockée est un tableau du jeu de données.|  
|Fortement typée demande de procédure stockée|`<[STRNG_SP_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/[SCHEMA]">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[STRNG_SP_NAME]>`|-|  
|Réponse de fortement typée de procédure stockée|`<[STRNG_SP_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/[SCHEMA]">     <StoredProcedureResultSet0>          <StoredProcedureResultSet0 xmlns:ns1="http://schemas.microsoft.com/Sql/2008/05/ProcedureResultSets/[SCHEMA]/[STRNG_SP_NAME]">               <[PRM1_NAME]>value1<[PRM1_NAME]>               <[PRM2_NAME]>value2</[PRM2_NAME]>               …         </StoredProcedureResultSet0>     </StoredProcedureResultSet0>    <ReturnValue>[Value]</ReturnValue> </[STRNG_SP_NAME]Response>`|La valeur de retour d’une procédure stockée fortement typé est un tableau de données fortement typées.|  
|Demande de la fonction scalaire|`<[SCLR_FN_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/ScalarFunctions/[SCHEMA]">   <[PRM_NAME]>value</[PRM_NAME]> </[SCLR_FN_NAME]>`|-|  
|Réponse de la fonction scalaire|`<[SCLR_FN_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/ScalarFunctions/[SCHEMA]">   <[SCLR_FN_NAME]Result>return_value</[SCLR_FN_NAME]Result>   <[PRM_NAME]>value</[PRM_NAME]>   </[SCLR_FN_NAME]Response>`|-|  
|Demande de fonction table|`<[TBL_FN_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/[SCHEMA]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[TBL_FN_NAME]>`|-|  
|Réponse de la fonction de table|`<[TBL_FN_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/[SCHEMA]">   <[TBL_FN_NAME]Result>      <[TBL_FN_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/[SCHEMA]">         <[PRM1_NAME]>value1</[PRM1_NAME]>         <[PRM2_NAME]>value2</[PRM2_NAME]>         ...      </[TBL_FN_NAME]">        ...      </[TBL_FN_NAME]Result> </[TBL_FN_NAME]Response>`||  
  
 [Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.  
  
 [SP_NAME] = la procédure stockée à exécuter ; par exemple, ADD_EMP_DETAILS.  
  
 [STRNG_SP_NAME] = la procédure stockée fortement typée pour être exécutés ; par exemple, GET_EMP_DETAILS.  
  
 [SCLR_FN_NAME] = la fonction scalaire doit être exécuté ; par exemple, GET_EMP_ID.  
  
 [TBL_FN_NAME] = la fonction table doit être exécuté ; par exemple, TVF_EMPLOYEE.  
  
 [PRM_NAME] = le nom du paramètre de SQL Server.  
  
## <a name="message-actions-of-functions-and-procedures"></a>Actions de message des fonctions et procédures  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise les actions de message suivantes pour les opérations de fonction et de procédure stockées.  
  
|Message|Action|Exemple|  
|-------------|------------|-------------|  
|Demande de procédure stockée|Procédure / [schéma] / [SP_NAME]|Procédure/dbo/ADD_EMP_DETAILS|  
|Réponse de la procédure stockée|Procédure / [schéma] / [SP_NAME] / réponse|Procédure/dbo/ADD_EMP_DETAILS/réponse|  
|Fortement typée demande de procédure stockée|TypedProcedure / [schéma] / [STRNG_SP_NAME]|TypedProcedure/dbo/GET_EMP_DETAILS|  
|Réponse de fortement typée de procédure stockée|TypedProcedure / [schéma] / [STRNG_SP_NAME] / réponse|TypedProcedure/dbo/GET_EMP_DETAILS/réponse|  
|POUR XML stocké demande de procédure|XmlProcedure / [schéma] / [SP_NAME]|XmlProcedure/dbo/GET_EMP_DETAILS_FOR_XML|  
|POUR XML stocké réponse de procédure|XmlProcedure / [schéma] / [SP_NAME] / réponse|XmlProcedure/dbo/GET_EMP_DETAILS_FOR_XML/réponse|  
|Demande de la fonction scalaire|ScalarFunction / [schéma] / [SCLR_FN_NAME]|ScalarFunction/dbo/GET_EMP_ID|  
|Réponse de la fonction scalaire|ScalarFunction / [schéma] / [SCLR_FN_NAME] / réponse|ScalarFunction/dbo/GET_EMP_ID/réponse|  
|Demande de fonction table|TableFunction / [schéma] / [TBL_FN_NAME]|TableFunction/dbo/TVF_EMPLOYEE|  
|Réponse de la fonction de table|TableFunction / [schéma] / [TBL_FN_NAME] / réponse|TableFunction/dbo/TVF_EMPLOYEE/réponse|  
  
 [SP_NAME] = la procédure stockée à exécuter ; par exemple, ADD_EMP_DETAILS.  
  
 [STRNG_SP_NAME] = la procédure stockée fortement typée pour être exécutés ; par exemple, GET_EMP_DETAILS.  
  
 [SCLR_FN_NAME] = la fonction scalaire doit être exécuté ; par exemple, GET_EMP_ID.  
  
 [TBL_FN_NAME] = le nom de la fonction table doit être exécuté ; par exemple, TVF_EMPLOYEE.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)