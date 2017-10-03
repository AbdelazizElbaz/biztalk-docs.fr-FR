---
title: "Comment ajouter un Shape3 étendue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Scope shapes, adding
ms.assetid: 8068ce97-4409-4c88-89e8-6505b56cefc5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8231dfed1ea84ba5c11e0352f789b92cc38d0f83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-scope-shape"></a><span data-ttu-id="d4f0d-102">Ajout d'une forme Étendue</span><span class="sxs-lookup"><span data-stu-id="d4f0d-102">How to Add a Scope Shape</span></span>
<span data-ttu-id="d4f0d-103">La procédure suivante permet d'ajouter une forme Étendue.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-103">Use the following procedure to add a Scope shape.</span></span>  
  
### <a name="to-add-a-scope-shape"></a><span data-ttu-id="d4f0d-104">Pour ajouter une forme Étendue</span><span class="sxs-lookup"><span data-stu-id="d4f0d-104">To add a Scope Shape</span></span>  
  
1.  <span data-ttu-id="d4f0d-105">Cliquez sur la flèche située sous le **réception** de port, pointez sur **insérer une forme**, puis sélectionnez **étendue**.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-105">Right-click the arrow below the **Receive** port, point to **Insert Shape**, and then select **Scope**.</span></span>  
  
     ![](../core/media/siebeladapter-18-exceptionhandling-insertscope.gif "SiebelAdapter_18_ExceptionHandling_InsertScope")  
  
     <span data-ttu-id="d4f0d-106">Dans le **étendue** forme, vous définissez les opérations pouvant rencontrer une erreur.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-106">In the **Scope** shape, you set operations that might have a fault.</span></span>  
  
     <span data-ttu-id="d4f0d-107">Par exemple, ajoutez un port d'envoi et de réception dans une orchestration SQLExecute.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-107">For example, add a send, a receive, and a send port in an SQLExecute orchestration.</span></span> <span data-ttu-id="d4f0d-108">Dans cet exemple, envoyez un message vers SERVER.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-108">In this example, you send a message to SERVER.</span></span> <span data-ttu-id="d4f0d-109">SERVER renvoie une réponse.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-109">SERVER gives a response.</span></span> <span data-ttu-id="d4f0d-110">Il exécute le reste de l'orchestration et renvoie des informations vers le port OutFile.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-110">It runs the rest of the orchestration and returns information back to the outFile port.</span></span>  
  
2.  <span data-ttu-id="d4f0d-111">Dans le **étendue** mettre en forme, définissez le **Transaction** à **aucun**.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-111">In the **Scope** shape, set the **Transaction** to **None**.</span></span>  
  
3.  <span data-ttu-id="d4f0d-112">Avec le bouton droit à l’intérieur de la **étendue** mettre en forme, puis sélectionnez **nouveau gestionnaire d’exceptions**.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-112">Right-click inside the **Scope** shape, and select **New Exception Handler**.</span></span>  
  
     ![](../core/media/siebeladapter-19-exceptionhandling-newexception.gif "SiebelAdapter_19_ExceptionHandling_NewException")  
  
     <span data-ttu-id="d4f0d-113">Cette opération crée le **intercepter l’Exception** bloc.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-113">This creates the **Catch Exception** block.</span></span> <span data-ttu-id="d4f0d-114">Si une exception se produit dans le système principal, elle est interceptée le **intercepter l’Exception** bloc.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-114">If an exception occurs from the back-end system, it is caught inside the **Catch Exception** block.</span></span>  
  
4.  <span data-ttu-id="d4f0d-115">Dans le **intercepter l’Exception** bloc, vous devez ajouter la logique.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-115">In the **Catch Exception** block, you must add the logic.</span></span>  
  
     <span data-ttu-id="d4f0d-116">La logique la plus importante que vous devez définir est le type de message d’erreur que vous attendez à recevoir.</span><span class="sxs-lookup"><span data-stu-id="d4f0d-116">The most important logic that you must set is the type of error message that you expect to receive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f0d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4f0d-117">See Also</span></span>  
 [<span data-ttu-id="d4f0d-118">À l’aide de la gestion des exceptions de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d4f0d-118">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling1.md)