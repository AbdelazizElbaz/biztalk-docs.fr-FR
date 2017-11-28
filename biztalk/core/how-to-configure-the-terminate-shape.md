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
# <a name="how-to-configure-the-terminate-shape"></a><span data-ttu-id="791e7-102">Configuration de la forme Terminer</span><span class="sxs-lookup"><span data-stu-id="791e7-102">How to Configure the Terminate Shape</span></span>
![](../core/media/ebiz-orch-terminate.gif "ebiz_orch_terminate")  
<span data-ttu-id="791e7-103">Forme Terminer</span><span class="sxs-lookup"><span data-stu-id="791e7-103">Terminate shape</span></span>  
  
 <span data-ttu-id="791e7-104">La forme Terminer sert à mettre fin à une instance de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="791e7-104">The Terminate shape is used to end an orchestration instance.</span></span> <span data-ttu-id="791e7-105">Vous pouvez spécifier une chaîne de message accompagnant la forme lors de son affichage dans le résultat de la page Hub du groupe.</span><span class="sxs-lookup"><span data-stu-id="791e7-105">You can specify a message string to accompany the shape when viewed in the output from the Group Hub page.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="791e7-106">Si vous placez un **Terminate** mettre en forme à l’intérieur d’un **Actions parallèles** forme et la branche avec la **Terminate** son exécution, l’instance se termine immédiatement, indépendamment du Indique si des autres branches en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="791e7-106">If you place a **Terminate** shape inside a **Parallel Actions** shape, and the branch with the **Terminate** on it is run, the instance completes immediately, regardless of whether other branches have finished running.</span></span> <span data-ttu-id="791e7-107">En fonction de votre conception, les résultats peuvent être imprévisibles.</span><span class="sxs-lookup"><span data-stu-id="791e7-107">Depending on your design, results might be unpredictable in this case.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="791e7-108">Si un **Terminate** forme est rencontrée dans une orchestration qui a été appelée de façon synchrone (comme avec la **appeler** forme) par une autre orchestration, l’instance imbriquée et toutes les orchestration associée instances va être interrompues.</span><span class="sxs-lookup"><span data-stu-id="791e7-108">If a **Terminate** shape is encountered in an orchestration that has been called synchronously (as with the **Call** shape) by another orchestration, the nested instance and all enclosing orchestration instances will be terminated.</span></span>  
  
### <a name="to-configure-a-terminate-shape"></a><span data-ttu-id="791e7-109">Pour configurer une forme Terminer</span><span class="sxs-lookup"><span data-stu-id="791e7-109">To configure a Terminate shape</span></span>  
  
-   <span data-ttu-id="791e7-110">Vous pouvez utiliser la **Message d’erreur** propriété pour spécifier le texte que vous souhaitez associer à la forme lorsqu’ils sont affichés dans la sortie de la requête sur la page Hub du groupe.</span><span class="sxs-lookup"><span data-stu-id="791e7-110">You can use the **Error Message** property to specify text that you want to associate with the shape when viewed in the query output on the Group Hub page.</span></span> <span data-ttu-id="791e7-111">Ce texte peut être une chaîne littérale ou une expression qui correspond à un **System.String**.</span><span class="sxs-lookup"><span data-stu-id="791e7-111">This text may be a literal string, or an expression that evaluates to a **System.String**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="791e7-112">Si vous entrez une chaîne littérale, vous devez la placer entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="791e7-112">If you enter a literal string, you must enclose it in quotation marks.</span></span>