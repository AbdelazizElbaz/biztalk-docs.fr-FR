---
title: "Comment ajouter un Shape4 étendue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding, Scope shapes
- Scope shape, adding
ms.assetid: 4ed56ada-a656-40b1-b34a-0c0803c01216
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a81bb85412784616d185b64ee39f1e777d19fea3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-scope-shape"></a><span data-ttu-id="12c95-102">Ajout d'une forme Étendue</span><span class="sxs-lookup"><span data-stu-id="12c95-102">How to Add a Scope Shape</span></span>
<span data-ttu-id="12c95-103">Procédez comme suit pour ajouter un **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="12c95-103">Follow these steps to add a **Scope** shape.</span></span>  
  
### <a name="to-add-a-scope-shape"></a><span data-ttu-id="12c95-104">Pour ajouter une forme étendue</span><span class="sxs-lookup"><span data-stu-id="12c95-104">To add a scope shape</span></span>  
  
1.  <span data-ttu-id="12c95-105">Cliquez sur la flèche située sous le **ReceiveFromIn** de port, pointez sur **insérer une forme**, puis cliquez sur **étendue**.</span><span class="sxs-lookup"><span data-stu-id="12c95-105">Right-click the arrow below the **ReceiveFromIn** port, point to **Insert Shape**, and then click **Scope**.</span></span>  
  
     <span data-ttu-id="12c95-106">Dans la forme Étendue, définissez les opérations susceptibles de rencontrer une erreur.</span><span class="sxs-lookup"><span data-stu-id="12c95-106">In the Scope shape, you set operations that might have a fault.</span></span>  
  
     <span data-ttu-id="12c95-107">Par exemple, ajouter un envoi, réception et un port d’envoi dans une orchestration SQLExecute.</span><span class="sxs-lookup"><span data-stu-id="12c95-107">For example, add a send, a receive and a send port in an SQLExecute orchestration.</span></span> <span data-ttu-id="12c95-108">Dans cet exemple, envoyez un message vers SERVER.</span><span class="sxs-lookup"><span data-stu-id="12c95-108">In this example, you send a message to SERVER.</span></span> <span data-ttu-id="12c95-109">SERVER renvoie une réponse.</span><span class="sxs-lookup"><span data-stu-id="12c95-109">SERVER gives a response.</span></span> <span data-ttu-id="12c95-110">Il exécute le reste de l’orchestration et retourne des informations sur le port OutFile.</span><span class="sxs-lookup"><span data-stu-id="12c95-110">It runs the rest of the orchestration and returns information back to the OutFile port.</span></span>  
  
2.  <span data-ttu-id="12c95-111">Dans la forme étendue, définissez la **Transaction** à **aucun**.</span><span class="sxs-lookup"><span data-stu-id="12c95-111">In the Scope shape, set the **Transaction** to **None**.</span></span>  
  
3.  <span data-ttu-id="12c95-112">Avec le bouton droit à l’intérieur de la forme étendue, puis sélectionnez **nouveau gestionnaire d’exceptions**.</span><span class="sxs-lookup"><span data-stu-id="12c95-112">Right-click inside the Scope shape and select **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="12c95-113">Cette opération crée le **intercepter l’Exception** bloc.</span><span class="sxs-lookup"><span data-stu-id="12c95-113">This creates the **Catch Exception** block.</span></span> <span data-ttu-id="12c95-114">Si une exception se produit dans le serveur principal, elle est interceptée le **intercepter l’Exception** bloc.</span><span class="sxs-lookup"><span data-stu-id="12c95-114">If an exception occurs from the back-end, it is caught inside the **Catch Exception** block.</span></span>  
  
4.  <span data-ttu-id="12c95-115">Dans le **intercepter l’Exception** bloc, vous devez ajouter la logique.</span><span class="sxs-lookup"><span data-stu-id="12c95-115">In the **Catch Exception** block, you must add the logic.</span></span>  
    <span data-ttu-id="12c95-116">La logique la plus importante que vous devez définir est le type de message d’erreur que vous attendez à recevoir.</span><span class="sxs-lookup"><span data-stu-id="12c95-116">The most important logic that you must set is the type of error message that you expect to receive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c95-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12c95-117">See Also</span></span>  
 [<span data-ttu-id="12c95-118">À l’aide de la gestion des exceptions de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="12c95-118">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling4.md)