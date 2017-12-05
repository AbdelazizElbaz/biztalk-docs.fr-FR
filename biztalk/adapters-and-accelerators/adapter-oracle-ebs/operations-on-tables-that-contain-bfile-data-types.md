---
title: "Opérations sur les Tables qui contiennent des Types de données BFILE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d7ebeb9-c2d6-4024-a169-263b947eeeb1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5096539b86512e51756d3a872ff566872ff520f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="operations-on-tables-that-contain-bfile-data-types"></a>Opérations sur les Tables qui contiennent des Types de données BFILE
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] prend en charge le type de données BFILE dans les tables et procédures stockées. 

## <a name="bfile-data-types"></a>Types de données BFILE
Le tableau suivant résume le type de données BFILE exposées par la carte en fonction de l’opération effectuée et l’objet LOB (table ou de la procédure) accédé :  
  
|Artefact|Opération|Type de données exposée pour BFILE col/param|Commentaires|  
|--------------|---------------|--------------------------------------------|--------------|  
|TABLE|INSERT|Chaîne|Représente le chemin d’accès de répertoire Oracle logique du fichier à insérer dans la colonne BFILE<br /><br /> Par ex. MYDIR/screen.jpg où MYDIR est un répertoire logique dans Oracle|  
|TABLE|UPDATE|Chaîne|Représente le chemin d’accès de répertoire logique Oracle pour le fichier de mise à jour dans la colonne BFILE|  
|TABLE|SELECT|byte[]|Représente les données binaires constituant BFILE|  
|PROCÉDURE STOCKÉE|DANS PARAM|Chaîne|Représente le chemin d’accès de répertoire Oracle logique du fichier à insérer dans la colonne BFILE<br /><br /> Par ex. MYDIR/screen.jpg où MYDIR est un répertoire logique dans Oracle|  
|PROCÉDURE STOCKÉE|OUT PARAM|Chaîne|Représente le chemin d’accès de répertoire Oracle logique du fichier à insérer dans la colonne BFILE<br /><br /> Par ex. MYDIR/screen.jpg où MYDIR est un répertoire logique dans Oracle|  
|PROCÉDURE STOCKÉE|INOUT PARAM|Non pris en charge|-|  
  
 L’opération spéciale `Read_<LOBColName>` est également pris en charge sur les tables avec le type de données BFILE, où \<LOBColName\> est le nom de la colonne LOB de la table. Le `Update_<LOBColName>` opération n’est pas prise en charge pour le type de données BFILE. Les clients de l’adaptateur peuvent également utiliser l’opération de mise à jour.  
  
## <a name="more-good-info"></a>Plus d’informations correct  
  
-   Le `Read_<LOBColName>` et `Update_<LOBColName>` opérations, consultez [opérations sur les Tables d’Interface, les vues de l’Interface, les Tables et les vues que contiennent LOB des données](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)