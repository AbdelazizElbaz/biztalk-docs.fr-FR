---
title: "Comment éviter la limitation des Messages corrélés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfe47747-01e7-4e2f-bbd5-d5055cea001a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10cfcf0009cac5a72d71190c1b974ca6d01a2e1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-avoid-throttling-correlated-messages"></a>Élimination des risques de limitation des messages corrélés
Les messages mis en file d'attente dans un serveur BizTalk Server, par exemple via un emplacement de réception ou par des orchestrations, peuvent être traités de l'une des manières suivantes :  
  
-   Ils peuvent activer de nouvelles instances d'abonnés (c'est-à-dire des orchestrations ou des ports d'envoi).  
  
-   Ils peuvent être acheminés vers une instance d'abonné existante via la corrélation. Pour plus d’informations sur la corrélation, consultez [à l’aide de corrélations dans les Orchestrations](../core/using-correlations-in-orchestrations.md).  
  
 Les développeurs sont nombreux à voir les emplacements de réception comme une solution pour recevoir des messages d'activation et corrélés via un même port. Rien d'étonnant à cela puisque le nombre d'adresses dont les expéditeurs des messages doivent garder la trace est ainsi réduit. Mais avec la limitation dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il peut y avoir des avantages à distinguer le flux des messages d'activation et le flux des messages corrélés.  
  
 Lorsque les messages d'activation et les messages de corrélation arrivent via le même emplacement de réception, ils sont soumis au même état de limitation car la limitation est appliquée au niveau de l'hôte. Il en résulte que tous les messages arrivant aux emplacements de réception dans l'hôte sont limités sous la forme d'une unité. Cela ne pose pas de problème dans la plupart des cas mais il peut arriver que la limitation de corrélations avec des activations puisse entraîner des blocages du système.  
  
## <a name="example"></a>Exemple  
 Supposons par exemple que vous ayez une orchestration qui reçoive une activation, qui l'utilise pour initialiser un ensemble de corrélations, puis qui reçoive un convoi de dix messages supplémentaires à la suite de l'ensemble de corrélations. Supposons de plus qu'en conditions de charge, une accumulation se produise au niveau du spooleur lors de l'arrivée du mélange de messages d'activation et de corrélation, et que cette accumulation entraîne une limitation de la quantité des messages pouvant être reçus. Malheureusement, les messages de corrélation étant limités avec les activations, cela ralentit l'exécution des orchestrations et entraîne ainsi une nouvelle accumulation et une limitation supplémentaire. Si ce scénario se poursuivait, on assisterait à la limitation du système jusqu'à un débit proche de zéro.  
  
 En divisant l'emplacement de réception unique en deux, un emplacement pour les activations et un emplacement pour les corrélations, et en configurant les emplacements dans des hôtes distincts, le seuil de limitation de la taille de la base de données correspondant aux activations peut être maintenu à un niveau plus bas que celui correspondant aux corrélations, ce qui permet de réduire le nombre global des blocages et de maintenir la transmission des messages.  
  
 Par conséquent, vous vous demandez peut-être : « Pourquoi ne puis-je pas simplement relever le seuil de taille de base de données de mon seul emplacement de réception à résoudre le problème ? » Ce serait possible mais vous n'obtiendriez pas toujours le comportement souhaité. La limitation sert surtout à protéger le système contre les surcharges. Si vous élevez suffisamment les seuils ou si vous les désactivez complètement, vous ôterez cette protection.  
  
## <a name="recommendation"></a>Recommandation  
 La meilleure chose à faire dans les scénarios similaires à celui décrit ci-dessus est de répartir les emplacements de réception dans des hôtes distincts pouvant être limités de façon indépendante.  
  
 Lorsque des hôtes distincts sont configurés pour des emplacements de réception, définissez le seuil de limitation de la taille de base de données correspondant à l'hôte utilisé par les emplacements de réception sur une valeur inférieure à celle du seuil correspondant aux hôtes utilisés par les orchestrations ou les corrélations.  
  
 Si vous savez que votre charge ne dépassera jamais le débit maximal acceptable du système, ou que les pics de débit sont récupérables entre les événements de pic, élever les seuils de limitation pourra aussi être une solution mais ne permettra sans doute pas un débit aussi élevé que si vous utilisiez des hôtes distincts pour les activations et les corrélations.