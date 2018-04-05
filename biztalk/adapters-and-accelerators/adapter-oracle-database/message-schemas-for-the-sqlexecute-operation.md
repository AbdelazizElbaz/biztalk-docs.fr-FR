---
title: Schémas de message pour l’opération SQLEXECUTE | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLEXECUTE operations, message schemas for
ms.assetid: 744645f4-0674-44e0-bf8d-8df70086b0f1
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7c7efc6a59e9dd4c163388803763a7b90a13b31
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-schemas-for-the-sqlexecute-operation"></a>Schémas de message pour l’opération SQLEXECUTE
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]met en évidence fortement typée de métadonnées pour les artefacts présents dans le système métier et expose des opérations standard sur ces artefacts. Toutefois, il existe des scénarios où une application peut nécessiter l’exécution d’une instruction SQL arbitraire piloté par la logique métier de l’application. Par exemple, vous souhaiterez :  
  
-   Effectuer une opération sur les artefacts de base de données qui ne sont pas signalées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; par exemple, obtenir le CURVAL ou NEXTVAL d’une séquence Oracle.  
  
-   Effectuer des opérations de langage de définition de données ; par exemple, créer une table.  
  
-   Effectuer des opérations sur un objet de base de données qui n’était pas présente au moment du design ; par exemple, mettre à jour des enregistrements dans une table temporaire qui est créé par votre logique métier.  
  
-   Effectuer des opérations DML plus complexes sur les tables que les opérations exposées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; pour l’exemple montre comment exécuter une requête qui inclut une clause JOIN.  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] met en évidence une opération spécial appelée l’opération SQLEXECUTE pour prendre en charge ces scénarios. À l’aide de cette opération, vous pouvez spécifier une instruction SQL arbitraire pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à exécuter sur la base de données Oracle. Vous pouvez également spécifier plusieurs blocs de paramètres d’entrée de l’instruction SQL. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exécute l’instruction SQL qu’une seule fois pour chaque jeu de paramètres et retourne toute sortie sous la forme d’un jeu d’enregistrements (faiblement typée) générique.  
  
> [!NOTE]
>  Vous pouvez passer dans et dans les paramètres pour les procédures, fonctions et des packages dans l’opération SQLEXECUTE. L’artefact appelée s’exécute avec les paramètres fournis sur la base de données Oracle ; Toutefois, l’opération SQLEXECUTE ne retourne pas la valeur de sortie et dans les paramètres pour le client. Si vous souhaitez appeler des procédures, fonctions ou des packages, Microsoft vous recommande de faire en appelant les opérations dédiées qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose pour que ces artefacts Oracle.  
  
 Le code XML suivant montre la structure de l’opération SQLEXECUTE :  
  
```  
<SQLEXECUTE xmlns="SQLEXECUTE">  
  <SQLSTATEMENT> [STATEMENT] </SQLSTATEMENT>  
  <PARAMETERSCHEMA>[PARAM_SPEC]</PARAMETERSCHEMA>  
  <PARAMETERSET>  
    <PARAMETERDATA>  
      <PARAMETER xmlns:c="http://schemas.microsoft.com/2003/10/Serialization/Arrays">  
        <c:string>[PARAM_VAL_1]</c:string>  
      </PARAMETER>  
    </PARAMETERDATA>  
    …  
  </PARAMETERSET>  
</SQLEXECUTE>  
```  
  
 [Instruction] = l’instruction SQL à exécuter ; par exemple, « sélectionnez * de la table emp WHERE matemp = : emp_no ».  
  
 [PARAM_SPEC] = la liste des paramètres IN dans l’instruction SQL et leurs types de données ; par exemple, « emp_no nombre ».  
  
 [PARAM_VAL_1] = la valeur du premier paramètre.  
  
 Chaque \<PARAMETERDATA\> section contient un ensemble complet de \<paramètre\> les éléments qui correspondent au schéma dans le \<PARAMETERSCHEMA\> section. Le \<PARAMETERSET\> peut contenir plusieurs \<PARAMETERDATA\> sections. Si c’est le cas, l’instruction SQL est exécutée plusieurs fois, une fois par rapport à chaque jeu de paramètres.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et schémas de message pour l’adaptateur BizTalk pour Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)