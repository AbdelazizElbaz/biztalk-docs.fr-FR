---
title: "À l’aide de commandes multiples éléments | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, multiple calls
- JD Edwards OneWorld adapters, multi-order numbers
- multiple edit line calls [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], multi-order numbers
- multi-order numbers [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], multiple calls
ms.assetid: 207ea92c-03f7-4117-8414-eb174e659d26
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 389e73ede2d1062c9907bd8640f38ce74ad6f316
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-multi-order-items"></a>L’utilisation des éléments de commandes multiples
En raison de la structure de l'API JD Edwards OneWorld, si vous souhaitez utiliser plusieurs numéros de commande avec BizTalk Server, vous devez effectuer plusieurs appels de modification d'article dans votre orchestration pour ajouter ces articles dans une orchestration. Par exemple, un article appartenant à plusieurs commandes inclut un en-tête avec un seul numéro de commande, et des détails comprenant plusieurs commandes d'articles (par exemple, Jouet 1pc, Gants 2pcs).  
  
 Avant de pouvoir utiliser plusieurs appels de modification d'article, le développeur BizTalk Server doit les structurer. Il doit créer une boucle interne pour que l'orchestration puisse effectuer ces appels.  
  
 Contrairement au système JD Edwards OneWorld, l'API ne prend pas en charge plusieurs appels de modification d'article. La structure de la méthode de modification d'article est une structure plate, et non une séquence. C'est pourquoi, vous devez appeler la fonction à chaque fois que vous souhaitez insérer un article.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification et Architecture](../core/planning-and-architecture17.md)