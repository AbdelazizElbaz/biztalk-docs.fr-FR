---
title: "Comment configurer un extracteur de faits pour une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, policies
- Business Rule Composer, facts
- policies, facts
ms.assetid: a7bcf3e5-3f28-4f0e-b112-8c97dee072a1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18572af1323de817b3c934866af917d2601332f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-fact-retriever-for-a-policy"></a>Comment configurer un extracteur de faits pour une stratégie
Vous pouvez stocker les faits qui changent rarement puis, avant le premier cycle d'exécution de votre application hôte, les extraire, les présenter une fois au moteur des règles pour qu'il les mette en mémoire cache et les réutiliser pour d'autres cycles d'exécution.  
  
 Vous avez le choix entre deux méthodes pour associer un extracteur de faits à une stratégie : Faire cela à l’aide de l’éditeur des règles d’entreprise ou par programmation à l’aide de la **RuleSetExecutionConfiguration** objet.  
  
> [!NOTE]
>  Une seule implémentation d'extracteur de faits peut être associée à une version de stratégie.  
  
### <a name="to-associate-a-fact-retriever-with-a-policy-in-the-business-rule-composer"></a>Pour associer un extracteur de faits à une stratégie dans l'Éditeur des règles d'entreprise  
  
1.  Dans la fenêtre Explorateur de stratégies, cliquez sur la version de stratégie à laquelle vous voulez associer l'extracteur de faits.  
  
2.  Dans la fenêtre Propriétés, cliquez sur le **points de suspension** bouton (...) dans le **extracteur de faits** propriété à rechercher dans le global assembly cache pour un objet extracteur de faits.  
  
    > [!IMPORTANT]
    >  Le **points de suspension** bouton (...) n’apparaît que si vous cliquez sur le **extracteur de faits** ligne dans la fenêtre Propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer un extracteur de faits](../core/how-to-create-a-fact-retriever.md)