---
title: "Opérations sur les Tables avec des Types de données BFILE dans la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operations, on tables with BFILE data types
- BFILE data type
- BFILE
ms.assetid: 7937564e-4423-459f-9824-6a27113ebfb3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c236651e6c44248ea8f6cf0f73f0c9bc17e46ac5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-tables-with-bfile-data-types-in-oracle-database"></a>Opérations sur les Tables avec des Types de données BFILE dans la base de données Oracle
Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge le type de données BFILE dans les tables et procédures stockées. Le tableau suivant résume le type de données BFILE exposées par la carte en fonction de l’opération effectuée et l’objet LOB (table ou de la procédure) accédé :  
  
|Artefact|Opération|Type de données exposée pour BFILE col/param|Commentaires|  
|--------------|---------------|--------------------------------------------|--------------|  
|TABLE|INSERT|Chaîne|Représente le chemin d’accès de répertoire Oracle logique du fichier à insérer dans la colonne BFILE<br /><br /> Par ex. MYDIR/screen.jpg où MYDIR est un répertoire logique dans Oracle|  
|TABLE|UPDATE|Chaîne|Représente le chemin d’accès de répertoire logique Oracle pour le fichier de mise à jour dans la colonne BFILE|  
|TABLE|SELECT|byte[]|Représente les données binaires constituant BFILE|  
|PROCÉDURE STOCKÉE|DANS PARAM|Chaîne|Représente le chemin d’accès de répertoire Oracle logique du fichier à insérer dans la colonne BFILE<br /><br /> Par ex. MYDIR/screen.jpg où MYDIR est un répertoire logique dans Oracle|  
|PROCÉDURE STOCKÉE|OUT PARAM|Chaîne|Représente le chemin d’accès de répertoire Oracle logique du fichier à insérer dans la colonne BFILE<br /><br /> Par ex. MYDIR/screen.jpg où MYDIR est un répertoire logique dans Oracle|  
|PROCÉDURE STOCKÉE|INOUT PARAM|Non pris en charge|-|  
  
 L’opération spéciale ReadLOB est également pris en charge sur les tables avec le type de données BFILE. L’opération UpdateLOB n’est pas pris en charge. Les clients de l’adaptateur peuvent également utiliser l’opération de mise à jour.  
  
 Pour plus d’informations sur :  
  
-   Opérations sur les tables qui contiennent des types de données BFILE à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [exécuter des opérations sur les Tables avec des Types de données BFILE dans la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)