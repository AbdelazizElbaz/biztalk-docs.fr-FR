---
title: "Appel des règles d’entreprise dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Rules shape [Orchestration Designer], business rules
- business rules, orchestrations
- Call Rules shape [Orchestration Designer], policies
- policies, Call Rules shape [Orchestration Designer]
- orchestrations, business rules
ms.assetid: ac3a3277-e9ea-4f40-9326-c63076c6b90e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77ecbb9738089dfa2d885f9aa45ac12e92ed27aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoking-business-rules-in-orchestrations"></a><span data-ttu-id="00b13-102">Appel des règles d’entreprise dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="00b13-102">Invoking Business Rules in Orchestrations</span></span>
<span data-ttu-id="00b13-103">Vous pouvez appeler une stratégie (ou un ensemble de règles) à partir d’une orchestration à l’aide de la **appeler règles** forme.</span><span class="sxs-lookup"><span data-stu-id="00b13-103">You can invoke a policy (or rule set) from an orchestration by using the **Call Rules** shape.</span></span> <span data-ttu-id="00b13-104">La stratégie appelle le moteur des règles, qui agit sur les règles de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="00b13-104">The policy invokes the rule engine, which operates on the rules in the policy.</span></span>  
  
 <span data-ttu-id="00b13-105">En plus des règles d’appel, les règles de moteur peut être appelé par programme à partir de l’expression de code, par exemple, dans un **Expression** ou **assignation du Message** forme.</span><span class="sxs-lookup"><span data-stu-id="00b13-105">In addition to using Call Rules, the rules engine can be programmatically called from expression code, for example, in an **Expression** or **Message Assignment** shape.</span></span> <span data-ttu-id="00b13-106">Pour plus d’informations sur l’exécution de stratégies par programme, consultez [comment exécuter les stratégies](../core/how-to-execute-policies.md).</span><span class="sxs-lookup"><span data-stu-id="00b13-106">For information about programmatically executing policies, see [How to Execute Policies](../core/how-to-execute-policies.md).</span></span>  
  
 <span data-ttu-id="00b13-107">Cette section décrit les informations de configuration et les procédures requises pour appeler et exécuter une stratégie commerciale à partir d'une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="00b13-107">This section describes configuration information and the procedures required to call and execute a business policy from a BizTalk orchestration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00b13-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="00b13-108">In This Section</span></span>  
  
-   [<span data-ttu-id="00b13-109">Informations de configuration</span><span class="sxs-lookup"><span data-stu-id="00b13-109">Configuration Information</span></span>](../core/configuration-information.md)  
  
-   [<span data-ttu-id="00b13-110">L’utilisation de la forme Appeler règles</span><span class="sxs-lookup"><span data-stu-id="00b13-110">How to Use the Call Rules Shape</span></span>](../core/how-to-use-the-call-rules-shape.md)