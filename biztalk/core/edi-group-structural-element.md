---
title: "Élément structurel d’un groupe EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 100a7118-9c02-474e-8685-9e4bb6f52e81
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 555d7b86e069adda4f7761b698793fd4ec2af721
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-group-structural-element"></a>Élément structurel d'un groupe EDI
Ce groupe contient un ou plusieurs documents informatisés. Un groupe EDIFACT doit contenir des documents informatisés du même type. Un groupe X12 peut contenir des documents informatisés de type semblable (basés sur le document informatisé : groupe (GS01-ST01) mappage) ou de même type. Le tableau ci-dessous répertorie similaire X12 documents informatisés (ST01), qui peuvent être regroupés dans un seul groupe (GS01).  
  
|GS01|ST01|  
|----------|----------|  
|CF|844|  
|CF|849|  
|DX|894|  
|DX|895|  
|FR|821|  
|FR|827|  
|GC|920|  
|GC|924|  
|GC|925|  
|GC|926|  
|HC|837|  
|HC|837_D|  
|HC|837_I|  
|HC|837_P|  
|IA|110|  
|IA|980|  
|E/S|310|  
|E/S|312|  
|ME|198|  
|ME|200|  
|ME|201|  
|ME|245|  
|ME|261|  
|ME|262|  
|ME|263|  
|ME|833|  
|ME|872|  
|MG|203|  
|MG|206|  
|MG|259|  
|MG|260|  
|MG|264|  
|MG|266|  
|OG|875|  
|OG|876|  
|PK|196|  
|PK|839|  
|QG|878|  
|QG|879|  
|QG|888|  
|QG|889|  
|QG|896|  
|QO|313|  
|QO|315|  
|RO|300|  
|RO|301|  
|RO|303|  
|RQ|836|  
|RQ|840|  
|RS|869|  
|RS|870|  
|SL|135|  
|SL|139|  
|SO|302|  
|SO|311|  
|SO|317|  
|SO|319|  
|SO|322|  
|SO|323|  
|SO|324|  
|SO|325|  
|SO|326|  
|SO|361|  
|TO|197|  
|TO|199|  
|TO|265|  
|TO|485|  
|TO|486|  
|TP|460|  
|TP|463|  
|TP|466|  
|TP|468|  
|TP|490|  
|TP|492|  
|TP|494|  
|WA|140|  
|WA|141|  
|WA|142|  
|WA|143|  
  
> [!NOTE]
>  Un groupe HIPAA 5010 autorise également le regroupement de documents informatisés de versions différentes dans un même groupe.  
  
 Si une exception est rencontrée lors du traitement d'un document informatisé, les propriétés de tiers EDI permettent de déterminer si l'échange entier ou seulement le document informatisé est interrompu.  
  
 Un groupe doit commencer par un en-tête de groupe fonctionnel (GS dans X12 ou UNG dans EDIFACT) et doit se terminer par un code de fin de groupe fonctionnel (GE dans X12 ou UNE dans EDIFACT). L'en-tête du groupe contient les codes de l'expéditeur et du destinataire, une date/heure, un numéro de contrôle correspondant à l'en-tête et au code de fin, un identificateur de groupe définissant les documents informatisés pouvant être inclus dans le groupe fonctionnel, et d'autres informations. Le code de fin du groupe est associé à un élément qui indique le nombre de documents informatisés au sein du groupe.  
  
 Un groupe est facultatif dans un échange EDIFACT. Un échange EDIFACT peut contenir plusieurs documents informatisés même si aucun groupe n'est présent (segment UNG absent). Dans ce cas, les documents informatisés doivent être du même type, tout comme les documents informatisés d'un groupe doivent être du même type. Par exemple, les documents informatisés APERAK et ORDERS ne peuvent pas être réunis dans un même groupe ou dans un échange n'incluant pas plusieurs groupes.  
  
 Un groupe est requis dans un échange X12.