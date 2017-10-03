---
title: "Opérations sur les API PL-SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d47b894d-1047-48ed-8f8c-865c343a12db
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5462bc4b4d6ee6a55e0e14d3ca9fccabc4dc2daf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-plsql-apis"></a>Opérations sur les API PL/SQL
Oracle E-Business Suite fournit un ensemble d’API PL/SQL sous forme de fonctions empaquetées et les procédures stockées. Ces empaquetées des fonctions et procédures sont signalées en tant qu’opérations dans [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]. 

## <a name="plsql-apis-are-grouped-by-schema-names"></a>Les API PL/SQL sont regroupées par noms de schéma 
Les API PL/SQL sont regroupées par noms de schéma sous la **vue basée sur un artefact** et **basée sur un schéma de vue** lorsque vous vous connectez à Oracle E-Business Suite à l’aide de nœuds [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Pour plus d’informations sur l’exploration de l’API PL/SQL dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [Parcourir, rechercher et d’obtenir des métadonnées pour des opérations Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] affiche les API PL/SQL associé à la base de données Oracle, ainsi que les applications d’Oracle E-Business Suite sous la **vue basée sur un artefact** et **basée sur un schéma de vue** nœuds.  
  
## <a name="important-info"></a>Informations importantes
  -   Avant de pouvoir effectuer des opérations sur les API PL/SQL associés aux applications dans Oracle E-Business Suite, vous devez définir le contexte des applications. Il s’agit, car le contexte des applications paramètre facilite la sécurité des transactions dans Oracle E-Business Suite en définissant des préférences de l’utilisateur (telles que les paramètres de gestion, d’organisation et langage) et de contrôle d’accès pour un artefact. Toutefois, il est facultatif définir le contexte des applications pour les API PL/SQL liées à la base de données Oracle. Consultez [définir le contexte de l’Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  

-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne peut pas déterminer si une valeur par défaut est attribuée pour un paramètre dans une API PL/SQL dans Oracle.  En outre, l’adaptateur également ne peut pas déterminer si un paramètre est défini comme étant obligatoires ou facultatifs dans une API PL/SQL dans Oracle. L’adaptateur traite chaque paramètre comme un paramètre facultatif, et si aucune valeur n’est spécifiée pour un paramètre qui :  

    -   A une valeur par défaut de valeur spécifié dans Oracle, la valeur par défaut est utilisée.  
    -   Est défini comme un paramètre obligatoire dans Oracle, puis une exception est levé.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)