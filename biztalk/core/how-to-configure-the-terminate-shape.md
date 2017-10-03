---
title: Comment configurer la forme terminer | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Terminate shape [Orchestration Designer], about Terminate shape
- Terminate shape [Orchestration Designer], literal strings
- configuring [Orchestration Designer], Terminate shapes
- Terminate shape [Orchestration Designer], configuring
- Terminate shape [Orchestration Designer]
ms.assetid: 2c4f2c94-2bab-4af3-8954-7275696ca147
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a5eb4867970c6acafc8903eb474b67541d22764
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-terminate-shape"></a>Configuration de la forme Terminer
![](../core/media/ebiz-orch-terminate.gif "ebiz_orch_terminate")  
Forme Terminer  
  
 La forme Terminer sert à mettre fin à une instance de l'orchestration. Vous pouvez spécifier une chaîne de message accompagnant la forme lors de son affichage dans le résultat de la page Hub du groupe.  
  
> [!CAUTION]
>  Si vous placez un **Terminate** mettre en forme à l’intérieur d’un **Actions parallèles** forme et la branche avec la **Terminate** son exécution, l’instance se termine immédiatement, indépendamment du Indique si des autres branches en cours d’exécution. En fonction de votre conception, les résultats peuvent être imprévisibles.  
  
> [!CAUTION]
>  Si un **Terminate** forme est rencontrée dans une orchestration qui a été appelée de façon synchrone (comme avec la **appeler** forme) par une autre orchestration, l’instance imbriquée et toutes les orchestration associée instances va être interrompues.  
  
### <a name="to-configure-a-terminate-shape"></a>Pour configurer une forme Terminer  
  
-   Vous pouvez utiliser la **Message d’erreur** propriété pour spécifier le texte que vous souhaitez associer à la forme lorsqu’ils sont affichés dans la sortie de la requête sur la page Hub du groupe. Ce texte peut être une chaîne littérale ou une expression qui correspond à un **System.String**.  
  
    > [!CAUTION]
    >  Si vous entrez une chaîne littérale, vous devez la placer entre guillemets.