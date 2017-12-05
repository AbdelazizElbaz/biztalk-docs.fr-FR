---
title: "Schémas de message pour les procédures stockées, fonctions et API PL-SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d707f10-470d-4390-bb5b-0301c326f375
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 029c48c1e6066d09d43da51b2bb1f6786a516f54
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-schemas-for-stored-procedures-functions-and-plsql-apis"></a>Schémas de message pour les procédures stockées, fonctions et API PL/SQL
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]surfaces Oracle sous-jacentes de base de données des procédures stockées, des fonctions et des API PL/SQL (procédures stockées et fonctions dans un package) en tant qu’opérations. Cette section décrit la structure des messages et les actions utilisées pour appeler des procédures stockées, fonctions et les API PL/SQL.  
  
## <a name="message-structure-of-stored-procedures-functions-and-plsql-apis"></a>Structure des messages de procédures stockées, fonctions et API PL/SQL  
 Les opérations signalées pour les fonctions et procédures stockées utilisent un modèle d’échange de message demande-réponse. Le tableau suivant illustre la structure de ces messages de demande et de réponse.  
  
> [!NOTE]
>  Consultez les descriptions de l’entité après le tableau.  
  
|Opération|Message XML| Description|  
|---------------|-----------------|-----------------|  
|Demande de procédure stockée|`<[SP_NAME] xmlns="[VERSION]/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|Prend en charge les paramètres Oracle et IN OUT dans le corps du message|  
|Réponse de la procédure stockée|`<[SP_NAME]Response xmlns="[VERSION]/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|Prend en charge Oracle OUT et dans les paramètres dans le corps du message|  
|Demande de la fonction|`<[FN_NAME] xmlns="[VERSION]/Functions/[SCHEMA] ">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[FN_NAME]>`|Prend en charge les paramètres Oracle et IN OUT dans le corps du message|  
|Réponse de la fonction|`<[FN_NAME]Response xmlns="[VERSION]/Functions/[SCHEMA]">   <[FN_NAME]Result>return_value</[FN_NAME]Result>   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   …    </[FN_NAME]Response>`|Prend en charge Oracle OUT et dans les paramètres dans le corps du message<br /><br /> La valeur de retour de fonction est retournée dans le \<[FN_NAME] résultat\> élément. Il s’agit du premier élément dans le message de réponse. Il se situe avant tous les paramètres.|  
|Demande d’API PL/SQL|`<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME/[SP_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|Même en tant que fonction ou procédure stockée|  
|Procédure empaquetée ou une réponse de la fonction|`<[SP_NAME]Response xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|Même en tant que fonction ou procédure stockée|  
  
 Descriptions de l’entité :  
  
 [VERSION] = http://schemas.microsoft.com/OracleEBS/2008/05.  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [SP_NAME] = la procédure stockée à exécuter ; par exemple, SP_INSERT.  
  
 [FN_NAME] = la fonction à exécuter ; par exemple, FN_GETID.  
  
 [PRM1_NAME] = le nom du paramètre Oracle. Consultez la colonne de Description pour les directions de paramètre pris en charge pour chaque message.  
  
 [PACKAGE_NAME] = le nom du package qui contient la fonction ou procédure ciblé.  
  
 La base de données Oracle prend en charge la surcharge des fonctions et procédures stockées. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge cette fonctionnalité en ajoutant une chaîne de la surcharge de l’espace de noms cible pour chaque artefact surchargé. La valeur de cette chaîne est « overload1 » pour la première surcharge, « overload2 » pour la seconde surcharge et ainsi de suite. L’exemple suivant montre la structure du message pour les deux procédures stockées surchargés.  
  
```  
Stored Procedure Overload 1:  
<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]/overload1">    
  <[PRM1_NAME]>value1</[PRM1_NAME]>  
  <[PRM2_NAME]>value1</[PRM2_NAME]>  
  …  
</[SP_NAME]>  
  
Stored Procedure Overload 2:  
<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]/overload2">    
  <[PRM1_NAME]>value1</I_[PRM1_NAME]>  
  <[PRM2_NAME]>value1</I_[PRM2_NAME]>  
  …  
</[SP_NAME]>  
```  
  
## <a name="message-actions-of-stored-procedures-functions-and-plsql-apis"></a>Actions de message de procédures stockées, fonctions et API PL/SQL  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise les actions de message suivant de procédure stockée, fonction et les opérations d’API de PL/SQL.  
  
> [!NOTE]
>  Consultez les descriptions de l’entité après le tableau.  
  
|Message|Action|Exemple|  
|-------------|------------|-------------|  
|Demande de procédure stockée|Procédures / [schéma] / [SP_NAME]|Procédures/SCOTT/SP_INSERT|  
|Réponse de la procédure stockée|Procédures / [schéma] / [SP_NAME] / réponse|Procédures/SCOTT/SP_INSERT/réponse|  
|Demande de la fonction|Fonctions / [schéma] / [FN_NAME]|SCOTT/fonctions/FN_GETID|  
|Réponse de la fonction|Fonctions / [schéma] / [FN_NAME] / réponse|Fonctions/SCOTT/FN_GETID/réponse|  
|Demande d’API PL/SQL|[Schéma] /Package/ [PACKAGE_NAME] / [SP_NAME]|SCOTT/Package/CUSTOMER/SP_INSERT|  
|Empaqueté de réponse de la procédure stockée|[Schéma] /Package/ [PACKAGE_NAME] / [SP_NAME] / réponse|SCOTT/Package/CUSTOMER/SP_INSERT/réponse.|  
|Fonction packagée demande|[Schéma] /Package/ [PACKAGE_NAME] / [FN_NAME]|SCOTT/Package/CUSTOMER/FN_GETID|  
|Réponse de la fonction packagée|[Schéma] /Package/ [PACKAGE_NAME] / [FN_NAME] / réponse|SCOTT/Package/CUSTOMER/FN_GETID/réponse.|  
|Demande de la procédure stockée surchargée|[Schéma] /Procedure/ [SP_NAME] / [surcharge]|SCOTT/procédure/SP_INSERT/overload1|  
|Surchargée de réponse de la procédure stockée|[Schéma] /Procedure/ [SP_NAME] / [surcharge] / réponse|SCOTT/procédure/SP_INSERT/overload1/réponse.|  
  
 Descriptions de l’entité :  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [SP_NAME] = la procédure stockée à exécuter ; par exemple, SP_INSERT.  
  
 [FN_NAME] = la fonction à exécuter ; par exemple, FN_GETID.  
  
 [PACKAGE_NAME] = le nom du package qui contient la fonction ou procédure ciblé.  
  
 [Surcharge] = le paramètre de surcharger le. Les valeurs possibles sont overload1, overload2 et ainsi de suite.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et schémas de message pour l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)