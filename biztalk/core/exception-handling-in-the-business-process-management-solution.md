---
title: "Gestion des exceptions dans la Solution gestion des processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, tutorials
- process management solution tutorial, errors
ms.assetid: ac9fcb33-7dac-448e-88b8-04d4d439ea6a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cd3134b8ed4e2fc6fd4a50d9b64397692ea32b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exception-handling-in-the-business-process-management-solution"></a><span data-ttu-id="dc0d1-102">Gestion des exceptions dans la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="dc0d1-102">Exception Handling in the Business Process Management Solution</span></span>
<span data-ttu-id="dc0d1-103">La solution de gestion des processus d'entreprise utilise une orchestration spéciale de gestion des exceptions, ainsi que la gestion des exceptions standard de BizTalk Server. Pour les erreurs d'adaptateur, de pipeline, de mappage et de routage, elle utilise la nouvelle fonctionnalité de création de rapports d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="dc0d1-103">The business process management solution uses a special exception handling orchestration, as well as the standard BizTalk Server exception handling, and for adapter, pipeline, mapping, and routing failures, the new error reporting feature.</span></span> <span data-ttu-id="dc0d1-104">Ce système personnalisé repose sur le **ExceptionHandler** orchestration.</span><span class="sxs-lookup"><span data-stu-id="dc0d1-104">This customized system is built around the **ExceptionHandler** orchestration.</span></span> <span data-ttu-id="dc0d1-105">La solution utilise le **ExceptionHandler** orchestration pour retenter une opération ou un appel susceptible de réussir après un problème temporaire.</span><span class="sxs-lookup"><span data-stu-id="dc0d1-105">The solution uses the **ExceptionHandler** orchestration to retry an operation or to retry a call that might succeed after a transient problem.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc0d1-106">Vous pouvez réutiliser le code à partir d’orchestrations, tel que **activer**, qui utilisent la **ExceptionHandler** orchestration.</span><span class="sxs-lookup"><span data-stu-id="dc0d1-106">You can re-use code from orchestrations, such as **Activate**, that use the **ExceptionHandler** orchestration.</span></span> <span data-ttu-id="dc0d1-107">Toutes ces orchestrations incluent une étendue nommée **CallingCode** avec une **Exception** bloc.</span><span class="sxs-lookup"><span data-stu-id="dc0d1-107">All of these orchestrations include a scope titled **CallingCode** with an attached **Exception** block.</span></span> <span data-ttu-id="dc0d1-108">Remplacez le code dans le **CallingCode** étendue avec votre code.</span><span class="sxs-lookup"><span data-stu-id="dc0d1-108">Replace the code in the **CallingCode** scope with your code.</span></span> <span data-ttu-id="dc0d1-109">Le **Exception** bloc définit toutes les variables qui doivent appeler le **ExceptionHandler** orchestration.</span><span class="sxs-lookup"><span data-stu-id="dc0d1-109">The **Exception** block defines all of the variables need to call the **ExceptionHandler** orchestration.</span></span> <span data-ttu-id="dc0d1-110">Vous devez modifier les valeurs affectées aux variables.</span><span class="sxs-lookup"><span data-stu-id="dc0d1-110">Edit the values assigned to the variables.</span></span>  
  
 <span data-ttu-id="dc0d1-111">La solution utilise des exceptions personnalisées, ainsi que des exceptions BizTalk prédéfinies, pour les situations dans lesquelles l'erreur est irrécupérable (par exemple, message de commande malformé).</span><span class="sxs-lookup"><span data-stu-id="dc0d1-111">The solution uses custom exceptions, and a couple pre-defined BizTalk exceptions, for cases where the error is unrecoverable such as a malformed order message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc0d1-112">La solution utilise un adaptateur personnalisé pour la gestion des erreurs sur certains ports.</span><span class="sxs-lookup"><span data-stu-id="dc0d1-112">The solution uses a custom adapter for handling failures on some ports.</span></span> <span data-ttu-id="dc0d1-113">Pour plus d’informations sur la carte, consultez [l’adaptateur Ops](../core/the-ops-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="dc0d1-113">For more information about the adapter, see [The Ops Adapter](../core/the-ops-adapter.md).</span></span>  
  
 <span data-ttu-id="dc0d1-114">Cette section décrit la **ExceptionHandler** orchestration ainsi que les exceptions personnalisées.</span><span class="sxs-lookup"><span data-stu-id="dc0d1-114">This section describes the **ExceptionHandler** orchestration and the custom exceptions.</span></span> <span data-ttu-id="dc0d1-115">Par ailleurs, elle explique brièvement l'utilisation de la fonctionnalité de création de rapports d'erreurs par la solution.</span><span class="sxs-lookup"><span data-stu-id="dc0d1-115">It also discusses, briefly, how the solution employs the error reporting product feature.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc0d1-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dc0d1-116">In This Section</span></span>  
  
-   [<span data-ttu-id="dc0d1-117">L’Orchestration ExceptionHandler</span><span class="sxs-lookup"><span data-stu-id="dc0d1-117">The ExceptionHandler Orchestration</span></span>](../core/the-exceptionhandler-orchestration.md)  
  
-   [<span data-ttu-id="dc0d1-118">Exceptions personnalisées</span><span class="sxs-lookup"><span data-stu-id="dc0d1-118">Custom Exceptions</span></span>](../core/custom-exceptions.md)