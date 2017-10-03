---
title: "Résolution des erreurs de base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases
- errors, databases
ms.assetid: d7b1cc9f-3f3e-464a-8249-1fd03b2b4d76
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47a22877cf06f03f875138208281420e56963da9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="resolving-database-errors"></a>Résolution des erreurs de base de données
Dans la base de données HL7 accès que l’organisation HL7 publie, DataItems et TableValues sont deux tables liées par table_id et hl7_version. La requête de base de données par entre suivante montre que certains éléments de données font référence à un table_id, ce qui n’a aucune valeur répertoriés dans le tableau :  
  
```  
select distinct d.table_id, d.hl7_version, t.table_item from DataElements as d left join TableValues as t on   
   d.table_id = t.table_id and d.hl7_version = t.hl7_version where d.table_id <>0 order by d.table_id  
```  
  
 Si la base de données HL7 accès manque les valeurs d’énumération, vous devez Cross-Vérifiez les valeurs manuellement avec les spécifications HL7 et utiliser ces valeurs dans votre schéma. Une pour gérer cette situation consiste à ajouter une liste d’énumération pour le schéma. Pour ce faire, consultez [énumérations d’extension](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)