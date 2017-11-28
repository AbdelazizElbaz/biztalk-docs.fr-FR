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
# <a name="how-to-configure-the-suspend-shape"></a><span data-ttu-id="79969-102">Configuration de la forme Interrompre</span><span class="sxs-lookup"><span data-stu-id="79969-102">How to Configure the Suspend Shape</span></span>
![](../core/media/ebiz-orch-suspend.gif "ebiz_orch_suspend")  
<span data-ttu-id="79969-103">Forme Interrompre</span><span class="sxs-lookup"><span data-stu-id="79969-103">Suspend shape</span></span>  
  
 <span data-ttu-id="79969-104">Lorsqu’une instance d’orchestration est suspendue, une erreur est consignée.</span><span class="sxs-lookup"><span data-stu-id="79969-104">When an orchestration instance is suspended, an error is logged.</span></span> <span data-ttu-id="79969-105">Vous pouvez spécifier une chaîne de message accompagnant l'erreur, afin d'aider l'administrateur à diagnostiquer le problème.</span><span class="sxs-lookup"><span data-stu-id="79969-105">You can specify a message string to accompany the error to help the administrator diagnose the situation.</span></span>  
  
 <span data-ttu-id="79969-106">Toutes les informations sur l'état de l'instance de l'orchestration sont enregistrées. Elles sont réintégrées lorsque l'administrateur reprend l'instance de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="79969-106">All of the state information for the orchestration instance is saved, and is reinstated if and when the administrator resumes the orchestration instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79969-107">Si un **Suspend** forme existe dans une orchestration qui a été appelée de façon synchrone (comme avec la **appeler** forme) par une autre orchestration, l’instance imbriquée et toutes les instances d’orchestration englobant seront être suspendu.</span><span class="sxs-lookup"><span data-stu-id="79969-107">If a **Suspend** shape exists in an orchestration that has been called synchronously (as with the **Call** shape) by another orchestration, the nested instance and all enclosing orchestration instances will be suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79969-108">Vous ne pouvez pas placer un **Suspend** forme dans une transaction atomique.</span><span class="sxs-lookup"><span data-stu-id="79969-108">You cannot place a **Suspend** shape inside an atomic transaction.</span></span>  
  
### <a name="to-configure-a-suspend-shape"></a><span data-ttu-id="79969-109">Pour configurer une forme Interrompre</span><span class="sxs-lookup"><span data-stu-id="79969-109">To configure a Suspend shape</span></span>  
  
-   <span data-ttu-id="79969-110">Vous pouvez utiliser le **Message d’erreur** propriété pour spécifier le texte que vous souhaitez être consignés quand un **Suspend** forme est rencontrée.</span><span class="sxs-lookup"><span data-stu-id="79969-110">You can use the **Error Message** property to specify text that you want to be logged when a **Suspend** shape is encountered.</span></span> <span data-ttu-id="79969-111">Ce texte peut être une chaîne littérale ou une expression qui correspond à un **System.String**.</span><span class="sxs-lookup"><span data-stu-id="79969-111">This text may be a literal string, or an expression that evaluates to a **System.String**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="79969-112">Si vous entrez une chaîne littérale, vous devez la placer entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="79969-112">If you enter a literal string, you must enclose it in quotation marks.</span></span>