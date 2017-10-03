---
title: "Comment configurer la forme décider | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Decide shape [Orchestration Designer]
- Decide shape [Orchestration Designer], configuring
- Decide shape [Orchestration Designer], branching
- configuring [Orchestration Designer], Decide shapes
ms.assetid: 70910861-3834-49e7-ab1e-d62730ea2a95
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a22368134e2c1a0d8deb277e186792158a7c2dd0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-decide-shape"></a>Configuration de la forme Décider
![](../core/media/ebiz-orch-decide.gif "ebiz_orch_decide")  
Forme Décider  
  
 Chaque branche d’un **décider** forme, à l’exception de la **else** créer une branche, est associé à une règle. Vous pouvez utiliser l'Éditeur d'expression BizTalk pour créer une expression booléenne dans la règle évaluée pour l'exécution de cette branche. Étant donné que la **else** branche implique la négation de l’expression booléenne dans la branche précédente, il n’a pas une expression associée.  
  
 Sous la règle ou **else** clause, une branche d’un **décider** forme peut contenir des formes supplémentaires, comme toute autre partie de l’orchestration.  
  
### <a name="to-configure-a-decide-shape"></a>Pour configurer une forme Décider  
  
1.  Si l’éditeur d’Expression BizTalk n’est pas visible, cliquez sur la règle, puis cliquez sur **modifier l’Expression booléenne**, ou dans la fenêtre Propriétés, cliquez sur le **points de suspension** (**...** ) bouton pour le **Expression** propriété.  
  
2.  Dans Éditeur d’Expression BizTalk, créez une expression booléenne pour chaque branche sauf la **Else** branche. Par exemple :  
  
    ```  
    myMessage.Total > 1000  
    myObject.IsValid()  
    myMessage.VIP == true  
    ```  
  
### <a name="to-add-a-branch-to-a-decide-shape"></a>Pour ajouter une branche à une forme Décider  
  
1.  Avec le bouton droit le **décider** mettre en forme, puis cliquez sur **nouvelle branche règles**.  
  
     — Ou :  
  
2.  Faites glisser une nouvelle forme entre deux branches existantes.  
  
    > [!NOTE]
    >  Pour supprimer une branche d’un **décider** mettre en forme, cliquez sur la branche que vous souhaitez supprimer, puis cliquez sur **supprimer**, ou sélectionnez la branche de règle et appuyez sur la **supprimer** clé.