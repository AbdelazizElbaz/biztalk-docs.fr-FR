---
title: "Comment configurer les propriétés transactionnelles sur une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- atomic transactions
- orchestrations, transactions
- transactions, long-running
- orchestrations, configuring
- transactions, atomic
ms.assetid: 8eec6019-4d96-4ed6-8a90-9403738d8af4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9164a9f5670a996a62450a19d802c97b89d8e242
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-transactional-properties-on-an-orchestration"></a><span data-ttu-id="06357-102">Comment configurer les propriétés transactionnelles sur une Orchestration</span><span class="sxs-lookup"><span data-stu-id="06357-102">How to Configure Transactional Properties on an Orchestration</span></span>
<span data-ttu-id="06357-103">Une orchestration peut être traitée comme une transaction atomique, une transaction à long terme, ou aucune des deux.</span><span class="sxs-lookup"><span data-stu-id="06357-103">An orchestration can be treated as an atomic transaction, a long-running transaction, or neither.</span></span>  
  
### <a name="to-make-your-orchestration-an-atomic-transaction"></a><span data-ttu-id="06357-104">Pour traiter votre orchestration comme une transaction atomique</span><span class="sxs-lookup"><span data-stu-id="06357-104">To make your orchestration an atomic transaction</span></span>  
  
1.  <span data-ttu-id="06357-105">Dans la fenêtre Vue Orchestration, sélectionnez **propriétés d’Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="06357-105">In the Orchestration View window, select **Orchestration Properties**.</span></span>  
  
2.  <span data-ttu-id="06357-106">Dans la fenêtre Propriétés, sélectionnez **atomique** dans la liste déroulante pour le **Type de Transaction** propriété.</span><span class="sxs-lookup"><span data-stu-id="06357-106">In the Properties window, select **Atomic** in the drop-down for the **Transaction Type** property.</span></span>  
  
     <span data-ttu-id="06357-107">**Lot**, **Compensation**, **niveau d’Isolation**, **réessayer**, **délai d’attente**, et **Transaction Identificateur** apparaissent en tant que propriétés dans la fenêtre Propriétés, exactement comme pour n’importe quelle étendue.</span><span class="sxs-lookup"><span data-stu-id="06357-107">**Batch**, **Compensation**, **Isolation Level**, **Retry**, **Timeout**, and **Transaction Identifier** appear as properties in the Properties window, just as they do for any scope.</span></span> <span data-ttu-id="06357-108">Pour plus d’informations sur ces propriétés, consultez [comment configurer la forme étendue](../core/how-to-configure-the-scope-shape.md).</span><span class="sxs-lookup"><span data-stu-id="06357-108">For more information on these properties, see [How to Configure the Scope Shape](../core/how-to-configure-the-scope-shape.md).</span></span>  
  
### <a name="to-make-your-orchestration-a-long-running-transaction"></a><span data-ttu-id="06357-109">Pour traiter votre orchestration comme une transaction à long terme</span><span class="sxs-lookup"><span data-stu-id="06357-109">To make your orchestration a long-running transaction</span></span>  
  
1.  <span data-ttu-id="06357-110">Dans la fenêtre Vue Orchestration, sélectionnez **propriétés d’Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="06357-110">In the Orchestration View window, select **Orchestration Properties**.</span></span>  
  
2.  <span data-ttu-id="06357-111">Dans la fenêtre Propriétés, sélectionnez **Long terme** dans la liste déroulante pour le **Type de Transaction** propriété.</span><span class="sxs-lookup"><span data-stu-id="06357-111">In the Properties window, select **Long Running** in the drop-down for the **Transaction Type** property.</span></span>  
  
     <span data-ttu-id="06357-112">**Compensation**, **délai d’attente**, et **identificateur de Transaction** apparaissent en tant que propriétés dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="06357-112">**Compensation**, **Timeout**, and **Transaction Identifier** appear as properties in the Properties window.</span></span> <span data-ttu-id="06357-113">Pour plus d’informations sur ces propriétés, comme pour n’importe quelle étendue.</span><span class="sxs-lookup"><span data-stu-id="06357-113">For more information on these properties, just as they do for any scope.</span></span> <span data-ttu-id="06357-114">Pour plus d’informations sur ces propriétés, consultez [comment configurer la forme étendue](../core/how-to-configure-the-scope-shape.md).</span><span class="sxs-lookup"><span data-stu-id="06357-114">For more information on these properties, see [How to Configure the Scope Shape](../core/how-to-configure-the-scope-shape.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06357-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06357-115">See Also</span></span>  
 [<span data-ttu-id="06357-116">Rendre les Orchestrations transactionnelles</span><span class="sxs-lookup"><span data-stu-id="06357-116">Making Orchestrations Transactional</span></span>](../core/making-orchestrations-transactional.md)