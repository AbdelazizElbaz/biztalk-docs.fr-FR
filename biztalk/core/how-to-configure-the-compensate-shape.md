---
title: Comment configurer la forme compenser | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Compensate shape [Orchestration Designer], about Compensate shape
- Compensate shape [Orchestration Designer]
- compensations, Compensate shape [Orchestration Designer]
- configuring [Orchestration Designer], Compensate shape
- Compensate shape [Orchestration Designer], configuring
ms.assetid: 9f06289e-4d11-4864-9851-c210276865a7
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 059ac58d95d33234737033c00c4a6a2a36e256f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-compensate-shape"></a>Configuration de la forme Compenser
Si vous utilisez des transactions imbriquées dans votre orchestration, vous pouvez ajouter un **compenser** forme dans le bloc de compensation ou un bloc d’exception d’une étendue de transaction. De cette manière, votre orchestration pourra effectuer, de manière explicite, une compensation sur la transaction imbriquée. Vous spécifiez la transaction dans laquelle vous souhaitez être compensée dans le **compenser** forme, ainsi que tout code de compensation dans la transaction imbriquée seront exécuté, fourni la transaction validée avec succès.  
  
> [!NOTE]
>  Le **Compensation** propriété fait référence à l’identificateur unique de l’étendue de transaction ; il ne fait pas référence au nom de l’étendue.  
  
 Si vous souhaitez compenser plusieurs transactions imbriquées, vous ajoutez un autre **compenser** forme pour chaque transaction.  
  
 Ne **compenser** forme est nécessaire s’il n’existe aucun autre code de compensation dans une transaction externe ; le code de compensation des transactions imbriquées s’exécute automatiquement. Le **compenser** forme vous permet de contrôler le processus en vous permettant de décider si vous souhaitez utiliser une transaction imbriquée soit compensée.  
  
### <a name="to-configure-a-compensate-shape"></a>Pour configurer une forme Compenser  
  
-   Dans la fenêtre Propriétés, sélectionnez le bloc de compensation à appeler à partir de la **Compensation** liste déroulante.  
  
     Cette liste déroulante affiche l'ensemble des transactions qui peuvent être compensées, et notamment la transaction actuelle et ses transactions enfants immédiates. Si vous ne parvenez pas à afficher une transaction souhaitée, cela peut être dû aux relations des transactions.  
  
    > [!NOTE]
    >  Vous ne pouvez pas compenser la transaction actuelle à partir du corps de la transaction.  Vous pouvez la compenser à partir du bloc de compensation ou d'un bloc d'exception de la transaction.  
  
     Si vous choisissez de compenser la transaction actuelle, le gestionnaire par défaut sera appelé, et non pas un bloc de compensation explicite (le cas échéant). Il s'agit d'un mécanisme permettant de compenser automatiquement les transactions directement imbriquées qui ont été correctement exécutées.