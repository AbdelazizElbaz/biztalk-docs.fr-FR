---
title: "Opérations sur les fonctions et procédures avec enregistrement Types1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afc1c84f-2e36-493c-9ea8-4bc2248331db
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43974d1c392a357b9781ff7f6fae5286e282513a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-functions-and-procedures-with-record-types"></a>Opérations sur les fonctions et procédures avec des Types d’enregistrements
Types d’enregistrements Oracle sont utilisés pour représenter des informations hiérarchiques dans les paramètres passés aux procédures et fonctions de PL/SQL. Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence des types d’enregistrement en tant que types XML complexes. 

## <a name="supported-record-types"></a>Prise en charge des types d’enregistrements
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] prend en charge les types de types d’enregistrements suivants :  
  
-   Types d’enregistrements qui sont déclarés en tant que TABLE % ROWTYPE paramètres dans les procédures stockées et fonctions.  
  
-   Types d’enregistrements qui sont déclarés en tant que paramètres de TYPE d’enregistrement dans les packages de PL/SQL. Par exemple, tapez rec_type1 est RECORD(name varchar2(100), age number(3));  
  
-   Types d’enregistrements qui contiennent des enregistrements imbriqués.  
  
-   Types d’enregistrements qui s’affichent, OUT ou paramètres dans des procédures ou des fonctions.  
  
-   Types d’enregistrements qui sont des valeurs de retour des fonctions.  
  
    > [!NOTE]
    >  Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les types BFILE en tant que membres de l’enregistrement.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)