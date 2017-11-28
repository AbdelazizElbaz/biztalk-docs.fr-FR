---
title: "Comment ajouter un Block3 d’Exception Catch | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scope shape [Orchestration Designer], Catch Exception block [Orchestration Designer]
- Catch Exception block [Orchestration Designer]
- Catch Exception block [Orchestration Designer], creating
- Catch Exception block [Orchestration Designer], exception handler
- Catch Exception block [Orchestration Designer], about Catch Exception blocks
- Orchestration Designer, errors
ms.assetid: 63ca4a60-b657-452a-86fd-78968ccf2933
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1040a27a5e1273d2ad80a722deb421878de36c12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a><span data-ttu-id="b2944-102">Ajout d'un bloc Intercepter l'exception</span><span class="sxs-lookup"><span data-stu-id="b2944-102">How to Add a Catch Exception Block</span></span>
<span data-ttu-id="b2944-103">Le **intercepter l’Exception** bloc représente un gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="b2944-103">The **Catch Exception** block represents an exception handler.</span></span> <span data-ttu-id="b2944-104">**Intercepter Exception** blocs sont attachés à la fin d’un **étendue** forme dans le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="b2944-104">**Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer.</span></span> <span data-ttu-id="b2944-105">Vous pouvez joindre autant **intercepter l’Exception** bloque dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="b2944-105">You can attach as many **Catch Exception** blocks as you need.</span></span>  
  
 <span data-ttu-id="b2944-106">Vous pouvez configurer les gestionnaires d'exceptions afin qu'ils gèrent différents types d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="b2944-106">You can set up exception handlers to handle different kinds of exceptions.</span></span> <span data-ttu-id="b2944-107">Sur chaque gestionnaire d’exceptions, vous spécifiez un type d’exception, qui doit être un message d’erreur ou d’un objet dérivé de la classe **System.Exception**.</span><span class="sxs-lookup"><span data-stu-id="b2944-107">On each exception handler, you specify an exception type, which must be either a fault message or an object derived from the class **System.Exception**.</span></span> <span data-ttu-id="b2944-108">Si vous ne spécifiez pas un type d’exception, le bloc d’exception sera traité comme un gestionnaire d’exceptions général et pourra intercepter des exceptions qui ne dérivent pas de **System.Exception**.</span><span class="sxs-lookup"><span data-stu-id="b2944-108">If you do not specify an exception type, the exception block will be treated as a general exception handler, and can catch exceptions that do not derive from **System.Exception**.</span></span>  
  
 <span data-ttu-id="b2944-109">Si une exception est levée qui correspond au type spécifié dans un gestionnaire d’exceptions, ce gestionnaire d’exceptions sera appelé.</span><span class="sxs-lookup"><span data-stu-id="b2944-109">If an exception is thrown that matches the specified type in an exception handler, that exception handler will be called.</span></span> <span data-ttu-id="b2944-110">Lorsqu'elle ne correspond pas, elle est gérée par le gestionnaire d'exceptions par défaut.</span><span class="sxs-lookup"><span data-stu-id="b2944-110">If some other exception is thrown, it will be handled by the default exception handler.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2944-111">Pour ajouter un **intercepter l’Exception** bloquer à un **étendue** mettre en forme le **Type de Transaction** propriété de la **étendue** forme doit être définie sur **Aucun** ou **longue**.</span><span class="sxs-lookup"><span data-stu-id="b2944-111">To add a **Catch Exception** block to a **Scope** shape, the **Transaction Type** property of the **Scope** shape must be set to **None** or **Long Running**.</span></span>  
  
### <a name="to-add-a-catch-exception-block"></a><span data-ttu-id="b2944-112">Pour ajouter un bloc Intercepter l'exception</span><span class="sxs-lookup"><span data-stu-id="b2944-112">To add a Catch Exception block</span></span>  
  
1.  <span data-ttu-id="b2944-113">Avec le bouton droit le **étendue** forme à laquelle vous souhaitez ajouter un **intercepter l’Exception** bloquer, puis cliquez sur **nouveau gestionnaire d’exceptions**.</span><span class="sxs-lookup"><span data-stu-id="b2944-113">Right-click the **Scope** shape to which you want to add a **Catch Exception** block, and then click **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="b2944-114">A **intercepter l’Exception** bloc est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="b2944-114">A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.</span></span>  
  
2.  <span data-ttu-id="b2944-115">Dans la fenêtre Propriétés, définissez les propriétés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b2944-115">In the Properties window, specify the following properties:</span></span>  
  
    |<span data-ttu-id="b2944-116">Propriété</span><span class="sxs-lookup"><span data-stu-id="b2944-116">Property</span></span>|<span data-ttu-id="b2944-117"> Description</span><span class="sxs-lookup"><span data-stu-id="b2944-117">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="b2944-118">Nom d'objet d'exception</span><span class="sxs-lookup"><span data-stu-id="b2944-118">Exception Object Name</span></span>|<span data-ttu-id="b2944-119">Affecte un nom à l'objet d'exception intercepté par le gestionnaire d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="b2944-119">Assigns a name to the exception object caught by the exception handler.</span></span>|  
    |<span data-ttu-id="b2944-120">Type d'objet d'exception</span><span class="sxs-lookup"><span data-stu-id="b2944-120">Exception Object Type</span></span>|<span data-ttu-id="b2944-121">Détermine le type d'objet (issu de la classe System.Exception) que ce gestionnaire interceptera.</span><span class="sxs-lookup"><span data-stu-id="b2944-121">Determines the object type (derived from System.Exception) that this exception handler will catch.</span></span>|  
  
3.  <span data-ttu-id="b2944-122">À l’intérieur de la **intercepter l’Exception** bloquer, ajouter des formes pour créer le processus de gestion de l’exception.</span><span class="sxs-lookup"><span data-stu-id="b2944-122">Inside the **Catch Exception** block, add shapes to create the process for handling the exception.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2944-123">Si vous spécifiez l’Exception générale en tant que le **Exception** l’objet de type, le **intercepter l’Exception** bloc intercepte une exception, y compris ceux qui ne sont pas dérivés de **System.Exception** .</span><span class="sxs-lookup"><span data-stu-id="b2944-123">If you specify General Exception as the **Exception** object type, the **Catch Exception** block will intercept any exception, including those that are not derived from **System.Exception**.</span></span> <span data-ttu-id="b2944-124">Dans ce cas, vous n'aurez pas accès à l'objet d'exception.</span><span class="sxs-lookup"><span data-stu-id="b2944-124">In such a case, you will not have access to an exception object.</span></span> <span data-ttu-id="b2944-125">Dans ce bloc, si vous utilisez un **lever Exception** forme avec le type d’Exception générale, vous relèverez l’exception interceptée.</span><span class="sxs-lookup"><span data-stu-id="b2944-125">Within this block, if you use a **Throw Exception** shape with the General Exception type, you will be effectively rethrowing the caught exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2944-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2944-126">See Also</span></span>  
 [<span data-ttu-id="b2944-127">Exceptions</span><span class="sxs-lookup"><span data-stu-id="b2944-127">Exceptions</span></span>](../core/exceptions.md)