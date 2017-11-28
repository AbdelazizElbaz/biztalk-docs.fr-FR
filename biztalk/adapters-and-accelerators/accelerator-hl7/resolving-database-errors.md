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
# <a name="resolving-database-errors"></a><span data-ttu-id="b297a-102">Résolution des erreurs de base de données</span><span class="sxs-lookup"><span data-stu-id="b297a-102">Resolving Database Errors</span></span>
<span data-ttu-id="b297a-103">Dans la base de données HL7 accès que l’organisation HL7 publie, DataItems et TableValues sont deux tables liées par table_id et hl7_version.</span><span class="sxs-lookup"><span data-stu-id="b297a-103">In the HL7 Access database that the HL7 organization publishes, DataItems and TableValues are two tables linked by table_id and hl7_version.</span></span> <span data-ttu-id="b297a-104">La requête de base de données par entre suivante montre que certains éléments de données font référence à un table_id, ce qui n’a aucune valeur répertoriés dans le tableau :</span><span class="sxs-lookup"><span data-stu-id="b297a-104">The following database cross-query shows that some data items refer to a table_id, which has no values listed in the table:</span></span>  
  
```  
select distinct d.table_id, d.hl7_version, t.table_item from DataElements as d left join TableValues as t on   
   d.table_id = t.table_id and d.hl7_version = t.hl7_version where d.table_id <>0 order by d.table_id  
```  
  
 <span data-ttu-id="b297a-105">Si la base de données HL7 accès manque les valeurs d’énumération, vous devez Cross-Vérifiez les valeurs manuellement avec les spécifications HL7 et utiliser ces valeurs dans votre schéma.</span><span class="sxs-lookup"><span data-stu-id="b297a-105">If the HL7 Access database has missing enumeration values, you must cross check the values manually with the HL7 specifications and use those values in your schema.</span></span> <span data-ttu-id="b297a-106">Une pour gérer cette situation consiste à ajouter une liste d’énumération pour le schéma.</span><span class="sxs-lookup"><span data-stu-id="b297a-106">One way to deal with this situation is to add an enumeration list to the schema.</span></span> <span data-ttu-id="b297a-107">Pour ce faire, consultez [énumérations d’extension](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="b297a-107">To do so, see [Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b297a-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b297a-108">See Also</span></span>  
 <span data-ttu-id="b297a-109">[L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="b297a-109">[Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span></span>  
 [<span data-ttu-id="b297a-110">Extension des schémas 2.X HL7 avec des objets Z</span><span class="sxs-lookup"><span data-stu-id="b297a-110">Extending HL7 2.X Schemas with Z Objects</span></span>](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)