---
title: Comment configurer la forme interrompre | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Orchestration Designer], Suspend shapes
- Suspend shape [Orchestration Designer], literal strings
- Suspend shape [Orchestration Designer], configuring
- Suspend shape [Orchestration Designer]
- atomic transactions, Suspend shape [Orchestration Designer]
- Suspend shape [Orchestration Designer], atomic transactions
- Suspend shape [Orchestration Designer], about Suspend shape
ms.assetid: 62fbb6d4-78d2-4671-84bb-909cbf6b0ec3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c846001b5a2b39a4e23e0d06ed56fb91c8863832
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-suspend-shape"></a>Configuration de la forme Interrompre
![](../core/media/ebiz-orch-suspend.gif "ebiz_orch_suspend")  
Forme Interrompre  
  
 Lorsqu’une instance d’orchestration est suspendue, une erreur est consignée. Vous pouvez spécifier une chaîne de message accompagnant l'erreur, afin d'aider l'administrateur à diagnostiquer le problème.  
  
 Toutes les informations sur l'état de l'instance de l'orchestration sont enregistrées. Elles sont réintégrées lorsque l'administrateur reprend l'instance de l'orchestration.  
  
> [!NOTE]
>  Si un **Suspend** forme existe dans une orchestration qui a été appelée de façon synchrone (comme avec la **appeler** forme) par une autre orchestration, l’instance imbriquée et toutes les instances d’orchestration englobant seront être suspendu.  
  
> [!NOTE]
>  Vous ne pouvez pas placer un **Suspend** forme dans une transaction atomique.  
  
### <a name="to-configure-a-suspend-shape"></a>Pour configurer une forme Interrompre  
  
-   Vous pouvez utiliser le **Message d’erreur** propriété pour spécifier le texte que vous souhaitez être consignés quand un **Suspend** forme est rencontrée. Ce texte peut être une chaîne littérale ou une expression qui correspond à un **System.String**.  
  
    > [!CAUTION]
    >  Si vous entrez une chaîne littérale, vous devez la placer entre guillemets.