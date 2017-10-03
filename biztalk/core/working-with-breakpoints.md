---
title: "Utilisation des points d’arrêt | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Orchestration Debugger, breakpoints
- Orchestration Debugger, suspended orchestrations
- Orchestration Debugger, Message Flow view
- Orchestration Debugger, service options
- Message Flow view [Orchestration Debugger]
ms.assetid: aad1a2b0-d705-49cd-85f7-b0ab2e473bcc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60e9cee77f105b132438e621651ee90c0090c1be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-breakpoints"></a>Utilisation de points d'arrêt
Vous pouvez définir des points d'arrêt en joignant une orchestration suspendue ou en définissant un point d'arrêt sur une classe.  
  
> [!NOTE]
>  Lorsque vous annulez le déploiement d’un assembly, la base de données conserve les options de suivi et les informations de point d’arrêt pour cet assembly. Si, par la suite, vous redéployez le même assembly, ces informations sont restaurées.  
  
### <a name="to-attach-to-a-suspended-orchestration"></a>Pour joindre une orchestration suspendue  
  
1.  Sélectionnez une orchestration suspendue automatiquement à l'aide d'une forme de suspension, puis passez à l'étape 3.  
  
2.  Actualisez la vue pour vérifier que l'instance apparaît maintenant avec l'état Suspendu.  
  
3.  Cliquez sur **reprendre en mode de débogage**.  
  
     L'orchestration reprend à un état Point d'arrêt. Vous pouvez procéder au débogage de façon interactive.  
  
### <a name="to-switch-to-the-message-flow-view"></a>Pour basculer vers l'affichage Flux message  
  
-   Cliquez sur une cellule dans la liste des résultats et sélectionnez **flux Message** dans le menu contextuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de la vue débogueur Orchestration](../core/working-with-the-orchestration-debugger-view.md)