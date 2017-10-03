---
title: "Comment configurer la forme écouter | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Listen shape [Orchestration Designer], about Listen shape
- Listen shape [Orchestration Designer], configuring
- Listen shape [Orchestration Designer]
- Listen shape [Orchestration Designer], branching
- configuring [Orchestration Designer], Listen shapes
ms.assetid: 4765dc0a-a30e-4515-83bc-72b4f37268cf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bd8f8bbcc08d41430b95a9d177aeb06a5288be4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-listen-shape"></a>Configuration de la forme Écouter
Les tâches d'écoute permettent aux applications d'attendre un ou plusieurs messages sur un ou plusieurs ports, ou de mettre un terme à l'écoute après un délai donné, et de créer une branche en fonction des résultats.  
  
 ![](../core/media/ebiz-orch-listen.gif "ebiz_orch_listen")  
Forme Écouter  
  
 Vous pouvez ajouter autant de branches que vous le souhaitez, Vous pouvez placer n’importe quel autre forme sous initial **réception** ou **délai** forme.  
  
 Il est possible d’utiliser une activation de réception dans un **écouter** forme. Si une branche de la **écouter** forme contient une activation de réception, toutes les autres branches doivent également contenir l’activation reçoit et aucun délai d’expiration ne peut être utilisé. La réception avec activation doit être la première action de chaque branche.  
  
 Vous pouvez utiliser la **écouter** forme au flux d’orchestration de branche en fonction de l’occurrence d’un ou plusieurs événements. La première forme dans chaque branche doit être un **délai** ou un **réception** forme. La première branche remplissant la condition, l’occurrence d’un délai d’attente pour un **délai** forme ou la réception d’un message pour un **réception** forme — s’exécute. Vous avez la possibilité d'ajouter de nouvelles branches, si besoin est.  
  
### <a name="to-configure-a-listen-shape"></a>Pour configurer une forme Écouter  
  
1.  Sélectionnez une branche.  
  
2.  Dans la fenêtre Propriétés, définissez la **Type de branche** propriété.  
  
     — Ou :  
  
     Faites glisser un **délai** ou **réception** forme sur la branche.  
  
### <a name="to-add-a-branch-to-a-listen-shape"></a>Pour ajouter une branche à une forme Écouter  
  
-   Cliquez sur le **écouter** mettre en forme, puis cliquez sur **nouvelle branche écouter**.  
  
    > [!NOTE]
    >  Pour supprimer une branche d’un **écouter** mettre en forme, cliquez sur la branche que vous souhaitez supprimer, puis cliquez sur **supprimer**.