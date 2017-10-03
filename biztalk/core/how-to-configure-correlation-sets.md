---
title: "Comment configurer des ensembles de corrélations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- correlation sets, send activities
- correlation sets, assigning correlation types
- correlation types, correlation sets
- correlation sets, receive activities
- configuring, correlation sets
- correlation sets, configuring
- correlation types, assigning
ms.assetid: 060bf2ba-c173-4dca-a8c4-4c5341e5ceaa
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52bcb0216fc24e14107c7632df97671b64f2ac1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-correlation-sets"></a>Comment configurer des ensembles de corrélations
Pour configurer votre ensemble de corrélations, vous pouvez sélectionner un type de corrélation existant, en créer un ou en modifier un.  
  
### <a name="to-assign-a-correlation-type-to-a-correlation-set"></a>Pour affecter un type de corrélation à un ensemble de corrélations  
  
-   Sélectionnez un type de corrélation existant.  
  
     \-Ou -  
  
     Cliquez sur le nouveau type de corrélation et sélectionnez **configurer les propriétés de corrélation**.  
  
     \-Ou -  
  
     Cliquez sur le bouton de sélection (**...** ) bouton **corrélation** propriétés dans le **propriétés** fenêtre.  
  
     Le **propriétés de corrélation** boîte de dialogue s’affiche. Ajoutez les propriétés à inclure dans votre ensemble de corrélations. Si aucun type n'est affecté à votre ensemble de corrélations, un nouveau type est créé.  
  
 Si un type de corrélation existe déjà pour l’ensemble de corrélations, et que vous ajoutez ou supprimez les propriétés avec la **propriétés de corrélation** boîte de dialogue, la corrélation existante type sera modifié.  
  
#### <a name="to-associate-send-and-receive-activities-with-a-correlation-set"></a>Pour associer des activités d'envoi et de réception à un ensemble de corrélations  
  
1.  Développez le **ensemble de corrélations** nœud.  
  
2.  Sélectionnez une activité d'envoi ou de réception dans la liste déroulante  
  
     \-Ou -  
  
     Sélectionnez l’ensemble de corrélations dans la **l’initialisation des ensembles de corrélations** propriété ou le **ensembles de corrélations suivants** propriété dans le **propriétés** fenêtre pour chaque **Envoyer** ou **réception** forme que vous souhaitez associer à l’ensemble de corrélations.  
  
#### <a name="to-disassociate-send-and-receive-activities-from-a-correlation-set"></a>Pour dissocier des activités d'envoi et de réception d'un ensemble de corrélations  
  
-   Dans le **Vue Orchestration** fenêtre, développez le nœud de jeu de corrélations, si nécessaire, cliquez sur l’activité que vous souhaitez supprimer, puis cliquez sur **supprimer**.  
  
     \-Ou -  
  
     Effacer l’ensemble de corrélations dans la **l’initialisation des ensembles de corrélations** propriété ou le **ensembles de corrélations suivants** propriété dans le **propriétés** fenêtre pour chaque  **Envoyer** ou **réception** forme que vous souhaitez dissocier de l’ensemble de corrélations.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des filtres avec la forme d’un Message de réception](../core/using-filters-with-the-receive-message-shape.md)   
 [À l’aide de corrélations dans les Orchestrations](../core/using-correlations-in-orchestrations.md)