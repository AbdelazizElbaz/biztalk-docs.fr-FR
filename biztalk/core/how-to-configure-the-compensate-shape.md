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
# <a name="how-to-configure-the-compensate-shape"></a><span data-ttu-id="4ad65-102">Configuration de la forme Compenser</span><span class="sxs-lookup"><span data-stu-id="4ad65-102">How to Configure the Compensate Shape</span></span>
<span data-ttu-id="4ad65-103">Si vous utilisez des transactions imbriquées dans votre orchestration, vous pouvez ajouter un **compenser** forme dans le bloc de compensation ou un bloc d’exception d’une étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="4ad65-103">If you are using nested transactions in your orchestration, you can add a **Compensate** shape in the compensation block or an exception block of a transaction scope.</span></span> <span data-ttu-id="4ad65-104">De cette manière, votre orchestration pourra effectuer, de manière explicite, une compensation sur la transaction imbriquée.</span><span class="sxs-lookup"><span data-stu-id="4ad65-104">This enables your orchestration to explicitly perform compensation on a nested transaction.</span></span> <span data-ttu-id="4ad65-105">Vous spécifiez la transaction dans laquelle vous souhaitez être compensée dans le **compenser** forme, ainsi que tout code de compensation dans la transaction imbriquée seront exécuté, fourni la transaction validée avec succès.</span><span class="sxs-lookup"><span data-stu-id="4ad65-105">You specify which transaction you would like to be compensated in the **Compensate** shape, and any compensation code in the nested transaction will be run, provided the transaction committed successfully.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ad65-106">Le **Compensation** propriété fait référence à l’identificateur unique de l’étendue de transaction ; il ne fait pas référence au nom de l’étendue.</span><span class="sxs-lookup"><span data-stu-id="4ad65-106">The **Compensation** property refers to the unique identifier of the transaction scope; it does not refer to the name of the scope.</span></span>  
  
 <span data-ttu-id="4ad65-107">Si vous souhaitez compenser plusieurs transactions imbriquées, vous ajoutez un autre **compenser** forme pour chaque transaction.</span><span class="sxs-lookup"><span data-stu-id="4ad65-107">If you want to compensate more than one nested transaction, you add an additional **Compensate** shape for each transaction.</span></span>  
  
 <span data-ttu-id="4ad65-108">Ne **compenser** forme est nécessaire s’il n’existe aucun autre code de compensation dans une transaction externe ; le code de compensation des transactions imbriquées s’exécute automatiquement.</span><span class="sxs-lookup"><span data-stu-id="4ad65-108">No **Compensate** shape is necessary if there is no other compensation code in an outer transaction; the compensation code of any nested transactions will be run automatically.</span></span> <span data-ttu-id="4ad65-109">Le **compenser** forme vous permet de contrôler le processus en vous permettant de décider si vous souhaitez utiliser une transaction imbriquée soit compensée.</span><span class="sxs-lookup"><span data-stu-id="4ad65-109">The **Compensate** shape gives you control over the process by allowing you to decide whether or not you want a nested transaction to be compensated.</span></span>  
  
### <a name="to-configure-a-compensate-shape"></a><span data-ttu-id="4ad65-110">Pour configurer une forme Compenser</span><span class="sxs-lookup"><span data-stu-id="4ad65-110">To configure a Compensate shape</span></span>  
  
-   <span data-ttu-id="4ad65-111">Dans la fenêtre Propriétés, sélectionnez le bloc de compensation à appeler à partir de la **Compensation** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="4ad65-111">In the Properties window, select the compensation block to call from the **Compensation** drop-down list.</span></span>  
  
     <span data-ttu-id="4ad65-112">Cette liste déroulante affiche l'ensemble des transactions qui peuvent être compensées, et notamment la transaction actuelle et ses transactions enfants immédiates.</span><span class="sxs-lookup"><span data-stu-id="4ad65-112">The drop-down list will display all of the transactions which can be compensated, which includes the current transaction and any immediate child transactions of the current transaction.</span></span> <span data-ttu-id="4ad65-113">Si vous ne parvenez pas à afficher une transaction souhaitée, cela peut être dû aux relations des transactions.</span><span class="sxs-lookup"><span data-stu-id="4ad65-113">If you cannot see a transaction that you expect, it might be due to the relationship of the transactions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ad65-114">Vous ne pouvez pas compenser la transaction actuelle à partir du corps de la transaction.</span><span class="sxs-lookup"><span data-stu-id="4ad65-114">You cannot compensate the current transaction from within the body of the transaction.</span></span>  <span data-ttu-id="4ad65-115">Vous pouvez la compenser à partir du bloc de compensation ou d'un bloc d'exception de la transaction.</span><span class="sxs-lookup"><span data-stu-id="4ad65-115">You can compensate it from the compensation block or an exception block of the transaction.</span></span>  
  
     <span data-ttu-id="4ad65-116">Si vous choisissez de compenser la transaction actuelle, le gestionnaire par défaut sera appelé, et non pas un bloc de compensation explicite (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="4ad65-116">If you choose to compensate the current transaction, that means that the default handler will be invoked, and not an explicit compensation block (if there is one).</span></span> <span data-ttu-id="4ad65-117">Il s'agit d'un mécanisme permettant de compenser automatiquement les transactions directement imbriquées qui ont été correctement exécutées.</span><span class="sxs-lookup"><span data-stu-id="4ad65-117">This is a mechanism for automatically compensating directly nested transactions that have completed successfully.</span></span>