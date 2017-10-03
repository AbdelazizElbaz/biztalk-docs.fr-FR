---
title: "Prise en charge de ExecuteNonQuery, ExecuteReader et les opérations de ExecuteScalar | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afdd1a5b-2a6b-48b8-a659-afd81f43f34b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40bad547627669bb22a6b32f05d96c6c7b2f68c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-executenonquery-executereader-and-executescalar-operations"></a>Prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] expose les opérations suivantes sortantes au niveau racine :  
  
-   **ExecuteNonQuery**: cette opération permet d’exécuter des instructions SQL arbitraires ou des blocs de PL/SQL dans Oracle E-Business Suite, si vous souhaitez retourner plusieurs jeux de résultats. Les paramètres d’entrée de cette fonction incluent un paramètre de chaîne (bloc PL/SQL entière doit être exécuté) et un tableau de chaînes (OutRefCursorNames). Chaque valeur de chaîne spécifiée dans OutRefCursorNames est censé pour être le nom du paramètre d’une sortie REF CURSOR avec le bloc de PL/SQL retournant des REF CURSOR portant le même nom. Cette fonction accepte également un paramètre OUT (OutRefCursors), qui est un tableau de jeux de données. Pour plus d’informations sur le jeu de données, consultez la documentation Oracle à l’adresse [http://go.microsoft.com/fwlink/?LinkId=124538](http://go.microsoft.com/fwlink/?LinkId=124538). La valeur de retour de cette opération est de type de données entier et indique le nombre de lignes affectées.  
  
-   **ExecuteReader**: cette opération permet d’exécuter des instructions SQL arbitraires ou des blocs de PL/SQL dans Oracle E-Business Suite, si vous souhaitez que le jeu de résultats à retourner en tant que jeu de données. Cette opération accepte un paramètre de chaîne en tant qu’entrée et retourne un jeu de données.  
  
-   **ExecuteScalar**: cette opération permet d’exécuter des instructions SQL arbitraires ou des blocs de PL/SQL dans Oracle E-Business Suite, si vous ne souhaitez qu’une seule valeur à retourner. Si la valeur de retour est un jeu de résultats, seule la valeur dans la première colonne de la première ligne est retournée sous forme de chaîne XML.  
  
> [!NOTE]
>  -   Les opérations ExecuteNonQuery, ExecuteReader et ExecuteScalar ne sont pas pris en charge pour le Types de définis par l’utilisateur (UDT).  
> -   Vous pouvez également définir le contexte des applications pour les opérations ExecuteNonQuery, ExecuteReader et ExecuteScalar [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Il est obligatoire de définir le contexte des applications pour les opérations ExecuteNonQuery, ExecuteReader et ExecuteScalar si un de l’opération est ciblée sur un artefact dans Oracle E-Business Suite (table d’interface, vue de l’interface, des programmes simultanés ou la demande définit). Pour plus d’informations sur le contexte des applications et comment le configurer, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)