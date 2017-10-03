---
title: "Portée des variables dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: orchestrations, variables
ms.assetid: 5856cdca-0ebd-4e16-8739-7bd50753b9f9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82803cd7f2b0beb8349e978fdd7b9e453dca31ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="variable-scope-in-orchestrations"></a><span data-ttu-id="02100-102">Portée des variables dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="02100-102">Variable Scope in Orchestrations</span></span>
<span data-ttu-id="02100-103">Il y a quelques points importants à bien comprendre à propos de la visibilité et de l'état des variables et des paramètres d'orchestration en plusieurs endroits de votre orchestration et notamment concernant les gestionnaires d'exception et les blocs de compensation.</span><span class="sxs-lookup"><span data-stu-id="02100-103">There are a few important points to understand about the visibility and state of variables and orchestration parameters in various places within your orchestration, including exception handlers and compensation blocks.</span></span>  
  
-   <span data-ttu-id="02100-104">Les paramètres d'orchestration sont visibles dans tout le corps de l'orchestration ainsi que dans son bloc de compensation.</span><span class="sxs-lookup"><span data-stu-id="02100-104">Orchestration parameters are visible throughout the body of the orchestration as well as in its compensation block.</span></span>  
  
-   <span data-ttu-id="02100-105">Les variables de niveau d'étendue sont visibles dans le corps de l'étendue ainsi que dans l'ensemble de ses gestionnaires d'exception et de son bloc de compensation.</span><span class="sxs-lookup"><span data-stu-id="02100-105">Scope-level variables are visible in the body of the scope as well as in all of its exception handlers and compensation block.</span></span> <span data-ttu-id="02100-106">Dans les gestionnaires d'exception, les variables sont considérées comme non initialisées dès lors qu'il n'est pas déterminé si l'exception qui a conduit à un gestionnaire donné a eu lieu avant ou après toute initialisation dans le corps.</span><span class="sxs-lookup"><span data-stu-id="02100-106">Inside exception handlers, the variables are considered un-initialized since it is indeterminate whether the exception that led to a given handler took place before or after any initialization in the body.</span></span> <span data-ttu-id="02100-107">C'est pour cette raison que, si vous déclarez une variable dans une étendue et que vous l'initialisez dans le corps, vous ne pourrez pas la lire dans un gestionnaire d'exceptions ou obtiendrez une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="02100-107">For this reason, if you declare a variable in a scope and initialize it in the body, you cannot read from it in an exception handler, or you will get a compiler error.</span></span> <span data-ttu-id="02100-108">Il est possible de contourner ce problème avec les transactions à long terme.</span><span class="sxs-lookup"><span data-stu-id="02100-108">A workaround for that exists in the case of long running transactions.</span></span> <span data-ttu-id="02100-109">L'exemple suivant illustre comment l'opérateur succeeded() peut être utilisé pour garantir un comportement correct à l'exécution.</span><span class="sxs-lookup"><span data-stu-id="02100-109">The following example shows how the succeeded() operator can be used to ensure proper runtime behavior:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="02100-110">Le code ci-dessous est un pseudo-code qui décrit un processus logique. Il ne peut pas être employé dans une forme Expression d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="02100-110">The code below is pseudo code that describes a logical process; this code cannot be used within an Orchestration Expression shape.</span></span>  
  
    ```  
    scope longrunning transaction L  
    {  
       System.Int32 i;  
       System.Int32 v;  
       body  
       {  
          i = 3;  
          scope longrunning transaction T  
          {  
             body  
             {  
                i = 5;  
             }  
          }  
       }  
       exceptions  
       {  
          catch  
          {  
             if(succeeded(T))  
             {  
                v = i;  // OK to read from it here — no compiler errors!  
             }  
          }  
       }  
    }  
    ```  
  
-   <span data-ttu-id="02100-111">À l'intérieur d'un bloc de compensation, toutes les variables endossent les valeurs qu'elles avaient lorsque le corps de l'étendue a été validé.</span><span class="sxs-lookup"><span data-stu-id="02100-111">Inside a compensation block, all variables assume the values they had when the body of the scope committed.</span></span> <span data-ttu-id="02100-112">Remarquez que le bloc de compensation d'une étendue ne s'exécute jamais immédiatement après la fin de son corps. Il y a toujours un code intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="02100-112">Note that the compensation block of a scope never runs immediately after its body completes; there is always intervening code.</span></span> <span data-ttu-id="02100-113">Si ce code intermédiaire met à jour quelques variables d'étendue externe et que le bloc de compensation s'exécute ensuite, les mises à jour effectuées ne seront pas visibles dans le bloc de compensation.</span><span class="sxs-lookup"><span data-stu-id="02100-113">If any of that intervening code updates some outer-scope variables, and then the compensation block runs, those updates will not be seen inside the compensation block.</span></span> <span data-ttu-id="02100-114">Les variables reprendront temporairement les valeurs qu'elles avaient au moment où l'étendue à laquelle appartient cette compensation avait été validée.</span><span class="sxs-lookup"><span data-stu-id="02100-114">Instead the variables will temporarily revert to the values they had at the time the scope which owns that compensation had committed.</span></span>  
  
-   <span data-ttu-id="02100-115">Si une transaction est imbriquée dans une boucle, elle sera compensée autant de fois que la boucle s'exécutera.</span><span class="sxs-lookup"><span data-stu-id="02100-115">When a transaction is nested inside a loop, the transaction will be compensated as many times as the loop executes.</span></span> <span data-ttu-id="02100-116">Dans le bloc de compensation de chaque itération, les variables d'étendue externe endossent les valeurs qui étaient les leurs lorsque l'itération de la transaction a été validée.</span><span class="sxs-lookup"><span data-stu-id="02100-116">Inside the compensation block for each iteration, outer-scope variables assume the values they had at the time of the iteration of the transaction committed.</span></span>  
  
-   <span data-ttu-id="02100-117">Toutes les mises à jour apportées aux variables d'étendue externe ou aux paramètres d'orchestration figurant dans les blocs de compensation des étendues internes ne seront plus visibles une fois que le bloc de compensation aura terminé.</span><span class="sxs-lookup"><span data-stu-id="02100-117">Any updates made to outer-scope variables or orchestration parameters inside compensation blocks of inner scopes will not be visible after the compensation block completes.</span></span> <span data-ttu-id="02100-118">En d'autres termes, le bloc de compensation ne peut pas être utilisé pour modifier directement les valeurs des variables d'étendue externe.</span><span class="sxs-lookup"><span data-stu-id="02100-118">In other words, the compensation block cannot be used to directly modify the values of outer-scope variables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02100-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02100-119">See Also</span></span>  
 [<span data-ttu-id="02100-120">Types de données XLANG-s</span><span class="sxs-lookup"><span data-stu-id="02100-120">XLANG-s Data Types</span></span>](../core/xlang-s-data-types.md)