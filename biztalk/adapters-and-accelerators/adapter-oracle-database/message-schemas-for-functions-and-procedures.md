---
title: "Schémas de message pour les fonctions et procédures | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions and procedures, message structure of
- functions and procedures, message actions of
ms.assetid: 90b77b15-a4c6-487d-a09e-a078ceddfd1e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85585945ae6376e11ddc39e7a1280f69d024c439
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-functions-and-procedures"></a>Schémas de message pour les fonctions et procédures
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces Oracle de la base de données des fonctions et procédures stockées en tant qu’opérations. Cette section décrit la structure des messages et les actions utilisées pour appeler des fonctions et des procédures.  
  
## <a name="message-structure-of-functions-and-procedures"></a>Structure des messages des fonctions et procédures  
 Les opérations signalées pour les fonctions et procédures stockées utilisent un modèle d’échange de message demande-réponse. Le tableau suivant illustre la structure de ces messages de demande et de réponse.  
  
|Opération|Message XML| Description|  
|---------------|-----------------|-----------------|  
|Demande de procédure stockée|`<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|Prend en charge les paramètres Oracle et IN OUT dans le corps du message|  
|Réponse de la procédure stockée|`<[SP_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|Prend en charge Oracle OUT et dans les paramètres dans le corps du message|  
|Demande de la fonction|`<[FN_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[FN_NAME]>`|Prend en charge les paramètres Oracle et IN OUT dans le corps du message|  
|Réponse de la fonction|`<[FN_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function">   <[FN_NAME]Result>return_value</[FN_NAME]Result>   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   …    </[FN_NAME]Response>`|Prend en charge Oracle OUT et dans les paramètres dans le corps du message<br /><br /> -La valeur de retour de fonction est retournée dans le \<[FN_NAME] résultat > élément. Il s’agit du premier élément dans le message de réponse. Il se situe avant tous les paramètres.|  
|Procédure empaquetée ou demande de la fonction|`<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|Même en tant que fonction ou procédure stockée|  
|Procédure empaquetée ou une réponse de la fonction|`<[SP_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|Même en tant que fonction ou procédure stockée|  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [SP_NAME] = la procédure stockée à exécuter ; par exemple, SP_INSERT.  
  
 [FN_NAME] = la fonction à exécuter ; par exemple, FN_GETID.  
  
 [PRM1_NAME] = le nom du paramètre Oracle. Consultez la colonne de Description pour les directions de paramètre pris en charge pour chaque message.  
  
 [PACKAGE_NAME] = le nom du package qui contient la fonction ou procédure ciblé.  
  
 La base de données Oracle prend en charge la surcharge des fonctions et procédures stockées. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge cette fonctionnalité en ajoutant une chaîne de la surcharge de l’espace de noms cible pour chaque artefact surchargé. La valeur de cette chaîne est « overload1 » pour la première surcharge, « overload2 » pour la seconde surcharge et ainsi de suite. L’exemple suivant montre la structure du message pour les deux procédures stockées surchargés.  
  
```  
Stored Procedure Overload 1:  
<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/overload1">    
  <[PRM1_NAME]>value1</[PRM1_NAME]>  
  <[PRM2_NAME]>value1</[PRM2_NAME]>  
  …  
</[SP_NAME]>  
  
Stored Procedure Overload 2:  
<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/overload2">    
  <[PRM1_NAME]>value1</I_[PRM1_NAME]>  
  <[PRM2_NAME]>value1</I_[PRM2_NAME]>  
  …  
</[SP_NAME]>  
```  
  
## <a name="message-actions-of-functions-and-procedures"></a>Actions de message des fonctions et procédures  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise les actions de message suivantes pour les opérations de fonction et de procédure stockées.  
  
|Message|Action|Exemple|  
|-------------|------------|-------------|  
|Demande de procédure stockée|http://Microsoft.LobServices.OracleDB/2007/03/ [schéma] /Procedure/ [SP_NAME]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/Procedure/SP_INSERT|  
|Réponse de la procédure stockée|http://Microsoft.LobServices.OracleDB/2007/03/ [schéma] /Procedure/ [SP_NAME] / réponse|http://Microsoft.LobServices.OracleDB/2007/03/Scott/Procedure/SP_INSERT/Response|  
|Demande de la fonction|http://Microsoft.LobServices.OracleDB/2007/03/ [schéma] /Function/ [FN_NAME]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/Function/FN_GETID|  
|Réponse de la fonction|http://Microsoft.LobServices.OracleDB/2007/03/ [schéma] /Function/ [FN_NAME] / réponse|http://Microsoft.LobServices.OracleDB/2007/03/Scott/Function/FN_GETID/Response|  
|Demande de la procédure stockée empaquetées|http://Microsoft.LobServices.OracleDB/2007/03/ [schéma] /Package/ [PACKAGE_NAME] / [SP_NAME]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/package/Customer/SP_INSERT|  
|Empaqueté de réponse de la procédure stockée|http://Microsoft.LobServices.OracleDB/2007/03/ [schéma] /Package/ [PACKAGE_NAME] / [SP_NAME] / réponse|http://Microsoft.LobServices.OracleDB/2007/03/Scott/package/Customer/SP_INSERT/Response|  
|Fonction packagée demande|http://Microsoft.LobServices.OracleDB/2007/03/ [schéma] /Package/ [PACKAGE_NAME] / [FN_NAME]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/package/Customer/FN_GETID|  
|Réponse de la fonction packagée|http://Microsoft.LobServices.OracleDB/2007/03/ [schéma] /Package/ [PACKAGE_NAME] / [FN_NAME] / réponse|http://Microsoft.LobServices.OracleDB/2007/03/Scott/package/Customer/FN_GETID/Response|  
|Demande de la procédure stockée surchargée|http://Microsoft.LobServices.OracleDB/2007/03/ [schéma] /Procedure/ [SP_NAME] / [surcharge]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/Procedure/SP_INSERT/overload1|  
|Surchargée de réponse de la procédure stockée|http://Microsoft.LobServices.OracleDB/2007/03/ [schéma] /Procedure/ [SP_NAME] / [surcharge] / réponse|http://Microsoft.LobServices.OracleDB/2007/03/Scott/Procedure/SP_INSERT/overload1/Response|  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [SP_NAME] = la procédure stockée à exécuter ; par exemple, SP_INSERT.  
  
 [FN_NAME] = la fonction à exécuter ; par exemple, FN_GETID.  
  
 [PACKAGE_NAME] = le nom du package qui contient la fonction ou procédure ciblé.  
  
 [Surcharge] = le paramètre de surcharger le. Les valeurs possibles sont overload1, overload2 et ainsi de suite.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)