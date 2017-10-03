---
title: Fonctoids en cascade | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoid types, Cascading
- Cascading functoids
ms.assetid: 03c46e7b-be1c-475e-b68b-f9d1d7732fce
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d5e9cfcad2432eb83c8a251147bac76b20db0bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cascading-functoids"></a>Fonctoids en cascade
On dit que les fonctoids sont en cascade lorsqu'un fonctoid est lié à un autre fonctoid avant d’être lié à un enregistrement ou à un champ dans le schéma de destination. Par exemple, vous pouvez créer des fonctoids en cascade dans lesquels deux chaînes concaténées produisent une troisième chaîne alimentée dans un champ du schéma de destination.  
  
 Lorsque vous placez des fonctoids en cascade, vous pouvez créer des transformations consécutives et multiples dans la page de grille. Il n'existe pas de limite au nombre de fonctoids que vous pouvez mettre en cascade dans une page, veillez toutefois à utiliser la mise en cascade judicieusement. La mise en cascade complexe allonge le temps de transformation d'un message d'instance d'entrée en message d'instance de sortie, ce qui réduit considérablement les performances d'exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctoids dans les mappages](../core/functoids-in-maps.md)   
 [À l’aide des fonctoids pour créer des mappages plus complexes](../core/using-functoids-to-create-more-complex-mappings.md)