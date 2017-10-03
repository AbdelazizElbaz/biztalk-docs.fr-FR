---
title: Causes des Exceptions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, errors
- errors, orchestrations
- errors, causes
ms.assetid: b0422382-d034-4c58-87c6-fc269dbbfe43
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9006234d71751078269e5a88559839fdadd91e91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="causes-of-exceptions"></a><span data-ttu-id="d280e-102">Causes des exceptions </span><span class="sxs-lookup"><span data-stu-id="d280e-102">Causes of Exceptions</span></span>
<span data-ttu-id="d280e-103">Les exceptions peuvent être générées dans une orchestration de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="d280e-103">Exceptions can be generated within an orchestration in the following ways:</span></span>  
  
-   <span data-ttu-id="d280e-104">Par un **lever Exception** forme, qui lève une exception immédiatement et sans condition.</span><span class="sxs-lookup"><span data-stu-id="d280e-104">By a **Throw Exception** shape, which throws an exception immediately and unconditionally.</span></span> <span data-ttu-id="d280e-105">Le contrôle passe à partir de la **lever Exception** forme directement au gestionnaire d’exceptions approprié.</span><span class="sxs-lookup"><span data-stu-id="d280e-105">Control passes from the **Throw Exception** shape directly to the appropriate exception handler.</span></span>  
  
-   <span data-ttu-id="d280e-106">Par expiration du délai d'attente dans une transaction longue.</span><span class="sxs-lookup"><span data-stu-id="d280e-106">By a time-out expiring in a long-running transaction.</span></span> <span data-ttu-id="d280e-107">Une exception système prédéfinies :**Microsoft.XLANG.BaseTypes.TimeOutException**— est levée dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="d280e-107">A predefined system exception—**Microsoft.XLANG.BaseTypes.TimeOutException**—is thrown in this case.</span></span>  
  
-   <span data-ttu-id="d280e-108">Par d'autres échecs de transaction.</span><span class="sxs-lookup"><span data-stu-id="d280e-108">By some other transaction failure.</span></span> <span data-ttu-id="d280e-109">Pour ces échecs, le moteur d'exécution lève un message défini par le système du type Microsoft.XLANG.BaseTypes.PersistenceException.</span><span class="sxs-lookup"><span data-stu-id="d280e-109">The runtime engine throws a system-defined message such as Microsoft.XLANG.BaseTypes.PersistenceException for these failures.</span></span>  
  
-   <span data-ttu-id="d280e-110">Par une exception de code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d280e-110">By a user code exception.</span></span> <span data-ttu-id="d280e-111">Lorsque des appels vers le code utilisateur externe sont effectués dans une orchestration, les classes du Common Language Runtime appelées peuvent lever des exceptions.</span><span class="sxs-lookup"><span data-stu-id="d280e-111">When calls to external user code are made within an orchestration, common language runtime classes that are called can throw exceptions.</span></span> <span data-ttu-id="d280e-112">Si ces exceptions ne sont pas gérées dans le code utilisateur, elles se propagent finalement dans l'étendue dans laquelle l'appel vers le code utilisateur est effectué.</span><span class="sxs-lookup"><span data-stu-id="d280e-112">If these exceptions are not handled in the user code, they eventually propagate up into the scope in which the call to the user code is made.</span></span>  
  
-   <span data-ttu-id="d280e-113">Par d'autres exceptions système (par exemple, un échec de persistance, une autre exception système ou .NET telle qu'une exception de chargeur de type, ou une erreur de conversion des données).</span><span class="sxs-lookup"><span data-stu-id="d280e-113">By some other system exception (for example, a persistence failure, another .NET or system exception such as type loader exception, or a data conversion error).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d280e-114">Lorsqu’une exception de chargeur de type est levée, l’exception ne peut pas être interceptée dans le **intercepter l’Exception** bloquer dans la même **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="d280e-114">When a type loader exception is thrown, the exception may not be caught in the **Catch Exception** block in the same **Scope** shape.</span></span> <span data-ttu-id="d280e-115">Cela est dû au fait que l'exception provient du chargeur de type, et non pas du processus d'orchestration  BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d280e-115">This is because of that the exception is from the type loader, not from the BizTalk orchestration process.</span></span> <span data-ttu-id="d280e-116">En conséquence, elle ne suit pas les règles BizTalk de flux de contrôle.</span><span class="sxs-lookup"><span data-stu-id="d280e-116">Therefore, it does not follow the BizTalk rules of control flow.</span></span>  
  
-   <span data-ttu-id="d280e-117">Par une branche frère dans une étendue voisine interrompant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="d280e-117">By a sibling branch in a surrounding scope halting execution.</span></span> <span data-ttu-id="d280e-118">Dans ce cas, l'exception Microsoft.XLANG.BaseTypes.ForcedTerminationException est levée pour chaque branche, et vous pouvez ajouter un gestionnaire d'exceptions à chacune d'elles.</span><span class="sxs-lookup"><span data-stu-id="d280e-118">Microsoft.XLANG.BaseTypes.ForcedTerminationException is thrown to each branch in this case, and you might want to add an exception handler to each.</span></span> <span data-ttu-id="d280e-119">Un gestionnaire d'exceptions de ce type ne peut ni lever à nouveau son exception, ni lever d'autres types d'exception.</span><span class="sxs-lookup"><span data-stu-id="d280e-119">Such an exception handler cannot re-throw its exception, nor should it attempt to throw any other type of exception.</span></span>  
  
-   <span data-ttu-id="d280e-120">Par réception d'un message externe indiquant une erreur.</span><span class="sxs-lookup"><span data-stu-id="d280e-120">By receipt of an external message that indicates a fault.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d280e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d280e-121">See Also</span></span>  
 <span data-ttu-id="d280e-122">[Messages d’erreur](../core/fault-messages.md) </span><span class="sxs-lookup"><span data-stu-id="d280e-122">[Fault Messages](../core/fault-messages.md) </span></span>  
 [<span data-ttu-id="d280e-123">Exceptions</span><span class="sxs-lookup"><span data-stu-id="d280e-123">Exceptions</span></span>](../core/exceptions.md)