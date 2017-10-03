---
title: Comment ajouter des formes aux Orchestrations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes, orchestrations
- orchestrations, shapes
- Construct Message shape [Orchestration Designer]
- Message Assignment shape [Orchestration Designer]
- Scope shape [Orchestration Designer]
ms.assetid: d39eb12c-cdc6-4918-93d9-536db1dfb889
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9fa6634adb20ffcf927da0af6f58e9daa2800ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-shapes-to-orchestrations"></a>Comment ajouter des formes aux Orchestrations
Cette section décrit les procédures d'ajout et de suppression de formes dans une orchestration. Pour plus d’informations sur les formes disponibles, consultez [formes d’Orchestration](../core/orchestration-shapes.md).  
  
### <a name="to-add-a-shape-to-an-orchestration"></a>Pour ajouter une forme à une orchestration  
  
1.  Dans la boîte à outils, sur le **Orchestrations BizTalk** onglet, faites glisser la forme vers une ligne de connexion sur l’aire de conception d’Orchestration.  
  
     — Ou :  
  
2.  Avec le bouton droit de la ligne de connexion ou l’espace réservé où vous souhaitez ajouter la forme, pointez sur **insérer une forme**, puis cliquez sur le nom de la forme à ajouter.  
  
    > [!NOTE]
    >  Une balise active apparaît sur les formes dont la configuration n'est pas terminée.  
  
> [!NOTE]
>  **Transformer** formes et **assignation du Message** ne peuvent exister dans un **construire un Message** forme. Si vous ajoutez une de ces formes à votre orchestration en dehors d’un **construire un Message** forme, il est placé automatiquement dans une nouvelle **construire un Message** forme.  
  
> [!NOTE]
>  **Intercepter Exception** et **Compensation** blocs peuvent exister uniquement après un **étendue** forme.  
  
### <a name="to-remove-a-shape-from-an-orchestration"></a>Pour supprimer une forme d'une orchestration  
  
1.  Avec le bouton droit de la forme sur l’aire de conception, puis cliquez sur **supprimer**.  
  
     — Ou :  
  
2.  Sélectionnez la forme et appuyez sur la **supprimer** clé.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’Orchestrations](../core/creating-orchestrations.md)