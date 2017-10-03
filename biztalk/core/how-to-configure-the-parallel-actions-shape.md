---
title: "Comment configurer la forme Actions parallèles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Parallel Actions shape [Orchestration Designer], Terminate shape [Orchestration Designer]
- Parallel Actions shape [Orchestration Designer], synchronizing data access
- Parallel Actions shape [Orchestration Designer]
- configuring [Orchestration Designer], Parallel Actions shapes
- Parallel Actions shape [Orchestration Designer], branching
- Parallel Actions shape [Orchestration Designer], about Parallel Actions shape
- Terminate shape [Orchestration Designer], Parallel Actions shape [Orchestration Designer]
- Parallel Actions shape [Orchestration Designer], configuring
ms.assetid: 396d6182-f5dd-4aab-9edc-92efe236fd3e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 125d479a09eefb6771a884d2cddbfa98f34aeb36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-parallel-actions-shape"></a>Configuration de la forme Actions parallèles
![](../core/media/ebiz-orch-paralactions.gif "ebiz_orch_paralactions")  
Forme Actions parallèle  
  
> [!CAUTION]
>  Si vous placez un **Terminate** mettre en forme à l’intérieur d’un **Actions parallèles** forme et la branche avec la **Terminate** son exécution, l’instance se termine immédiatement, indépendamment du Indique si des autres branches en cours d’exécution. En fonction de votre conception, les résultats peuvent être imprévisibles.  
  
## <a name="synchronization-of-data-access"></a>Synchronisation de l'accès aux données  
 Il est possible que plusieurs branches d’un **Actions parallèles** forme va tenter d’accéder aux mêmes données. Pour éviter la génération d'erreurs, placez toutes les formes accédant aux données dans des étendues synchronisées. Vous pouvez spécifier dans les propriétés d’un **étendue** forme qu’elle est synchronisée ou pas. Pour plus d’informations, consultez [étendues](../core/scopes.md).  
  
#### <a name="to-add-a-branch-to-a-parallel-actions-shape"></a>Pour ajouter une branche à une forme Actions parallèles  
  
1.  Cliquez sur le **Actions parallèles** mettre en forme, puis cliquez sur **nouvelle branche parallèle**.  
  
     — Ou :  
  
2.  Faites glisser une nouvelle forme entre deux branches existantes.  
  
> [!NOTE]
>  Pour supprimer une branche d’un **Actions parallèles** mettre en forme, cliquez sur la branche que vous souhaitez supprimer, puis cliquez sur **supprimer**.