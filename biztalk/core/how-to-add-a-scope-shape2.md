---
title: "Comment ajouter un Shape2 étendue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scope shapes, adding
- adding, Scope shapes
ms.assetid: 9449210f-1f29-4b86-a14b-148caa06ac6b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ef67618c553702ae32cd0a88f6d2f77eb1ff053
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-scope-shape"></a><span data-ttu-id="62511-102">Ajout d'une forme Étendue</span><span class="sxs-lookup"><span data-stu-id="62511-102">How to Add a Scope Shape</span></span>
<span data-ttu-id="62511-103">Utilisez la procédure suivante pour ajouter un **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="62511-103">Use the following procedure to add a **Scope** shape.</span></span>  
  
### <a name="to-add-a-scope-shape"></a><span data-ttu-id="62511-104">Pour ajouter une forme étendue</span><span class="sxs-lookup"><span data-stu-id="62511-104">To add a scope shape</span></span>  
  
1.  <span data-ttu-id="62511-105">Cliquez sur la flèche située sous le **ReceiveFromIn** de port, pointez sur **insérer une forme**, puis sélectionnez **étendue**.</span><span class="sxs-lookup"><span data-stu-id="62511-105">Right-click the arrow below the **ReceiveFromIn** port, point to **Insert Shape**, and select **Scope**.</span></span>  
  
     <span data-ttu-id="62511-106">Dans le **étendue** forme, vous définissez les opérations pouvant rencontrer une erreur.</span><span class="sxs-lookup"><span data-stu-id="62511-106">In the **Scope** shape, you set operations that might have a fault.</span></span>  
  
     <span data-ttu-id="62511-107">Par exemple, ajouter un envoi, réception et un port d’envoi dans une orchestration SQLExecute.</span><span class="sxs-lookup"><span data-stu-id="62511-107">For example, add a send, a receive and a send port in an SQLExecute orchestration.</span></span> <span data-ttu-id="62511-108">Dans cet exemple, envoyez un message vers SERVER.</span><span class="sxs-lookup"><span data-stu-id="62511-108">In this example, you send a message to SERVER.</span></span> <span data-ttu-id="62511-109">SERVER renvoie une réponse.</span><span class="sxs-lookup"><span data-stu-id="62511-109">SERVER gives a response.</span></span> <span data-ttu-id="62511-110">Il exécute le reste de l’orchestration et retourne des informations sur le port OutFile.</span><span class="sxs-lookup"><span data-stu-id="62511-110">It runs the rest of the orchestration and returns information back to the OutFile port.</span></span>  
  
2.  <span data-ttu-id="62511-111">Dans le **étendue** mettre en forme, définissez le **Type de Transaction** à **aucun**.</span><span class="sxs-lookup"><span data-stu-id="62511-111">In the **Scope** shape, set the **Transaction Type** to **None**.</span></span>  
  
3.  <span data-ttu-id="62511-112">Avec le bouton droit à l’intérieur de la **étendue** mettre en forme et sélectionnez **nouveau gestionnaire d’exceptions**.</span><span class="sxs-lookup"><span data-stu-id="62511-112">Right-click inside the **Scope** shape and select **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="62511-113">Cette opération crée le **intercepter l’Exception** bloc.</span><span class="sxs-lookup"><span data-stu-id="62511-113">This creates the **Catch Exception** block.</span></span> <span data-ttu-id="62511-114">Si une exception se produit dans le système principal, elle est interceptée le **intercepter l’Exception** bloc.</span><span class="sxs-lookup"><span data-stu-id="62511-114">If an exception occurs from the back-end system, it is caught inside the **Catch Exception** block.</span></span>  
  
4.  <span data-ttu-id="62511-115">Dans le **intercepter l’Exception** bloc, vous devez ajouter la logique.</span><span class="sxs-lookup"><span data-stu-id="62511-115">In the **Catch Exception** block, you must add the logic.</span></span>  
  
     <span data-ttu-id="62511-116">La logique la plus importante que vous devez définir est le type de message d’erreur que vous attendez à recevoir.</span><span class="sxs-lookup"><span data-stu-id="62511-116">The most important logic that you must set is the type of error message that you expect to receive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62511-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62511-117">See Also</span></span>  
 [<span data-ttu-id="62511-118">À l’aide de la gestion des exceptions de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="62511-118">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling3.md)