---
title: "Comment ajouter un Shape1 étendue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scope shapes, adding
- Scope shapes, Catch Exception blocks
- Catch Exception blocks, Scope shapes
- adding, Scope shapes
ms.assetid: dfe039d1-4c4a-4e21-ae03-7ca534aafec3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 094f744f7d4d6d1c405ea50d222beb8c0a67920e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-scope-shape"></a><span data-ttu-id="3cef2-102">Ajout d'une forme Étendue</span><span class="sxs-lookup"><span data-stu-id="3cef2-102">How to Add a Scope Shape</span></span>
<span data-ttu-id="3cef2-103">Pour ajouter une forme Étendue, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="3cef2-103">Follow these steps to add a Scope shape.</span></span>  
  
### <a name="to-add-a-scope-shape"></a><span data-ttu-id="3cef2-104">Pour ajouter une forme Étendue</span><span class="sxs-lookup"><span data-stu-id="3cef2-104">To add a Scope Shape</span></span>  
  
1.  <span data-ttu-id="3cef2-105">Cliquez sur la flèche située sous le **ReceiveFromIn** de port, pointez sur **insérer une forme**, puis cliquez sur **étendue**.</span><span class="sxs-lookup"><span data-stu-id="3cef2-105">Right-click the arrow below the **ReceiveFromIn** port, point to **Insert Shape**, and then click **Scope**.</span></span>  
  
     ![](../core/media/siebeladapter-18-exceptionhandling-insertscope.gif "SiebelAdapter_18_ExceptionHandling_InsertScope")  
  
     <span data-ttu-id="3cef2-106">Dans la forme Étendue, définissez les opérations susceptibles de rencontrer une erreur.</span><span class="sxs-lookup"><span data-stu-id="3cef2-106">In the Scope shape, you set operations that might have a fault.</span></span>  
  
     <span data-ttu-id="3cef2-107">Par exemple, ajoutez un port d'envoi et de réception dans une orchestration SQLExecute.</span><span class="sxs-lookup"><span data-stu-id="3cef2-107">For example, add a send, a receive, and a send port in an SQLExecute orchestration.</span></span> <span data-ttu-id="3cef2-108">Dans cet exemple, vous envoyez un message vers DB2.</span><span class="sxs-lookup"><span data-stu-id="3cef2-108">In this example, we are sending a message to DB2.</span></span> <span data-ttu-id="3cef2-109">DB2 renvoie une réponse.</span><span class="sxs-lookup"><span data-stu-id="3cef2-109">DB2 gives a response.</span></span> <span data-ttu-id="3cef2-110">Il exécute le reste de l’orchestration et retourne des informations sur le port OutFile.</span><span class="sxs-lookup"><span data-stu-id="3cef2-110">It runs the rest of the orchestration and returns information back to the OutFile port.</span></span>  
  
2.  <span data-ttu-id="3cef2-111">Dans la forme étendue, définissez la **Transaction** à **aucun**.</span><span class="sxs-lookup"><span data-stu-id="3cef2-111">In the Scope shape, set the **Transaction** to **None**.</span></span>  
  
3.  <span data-ttu-id="3cef2-112">Avec le bouton droit à l’intérieur de la forme étendue, puis sélectionnez **nouveau gestionnaire d’exceptions**.</span><span class="sxs-lookup"><span data-stu-id="3cef2-112">Right-click inside the Scope shape, and select **New Exception Handler**.</span></span>  
  
     ![](../core/media/siebeladapter-19-exceptionhandling-newexception.gif "SiebelAdapter_19_ExceptionHandling_NewException")  
  
     <span data-ttu-id="3cef2-113">Cette opération permet de créer le bloc Intercepter l'exception.</span><span class="sxs-lookup"><span data-stu-id="3cef2-113">This creates the Catch Exception block.</span></span> <span data-ttu-id="3cef2-114">Si une exception se produit dans le serveur principal, elle est interceptée dans le bloc intercepter l’Exception.</span><span class="sxs-lookup"><span data-stu-id="3cef2-114">If an exception occurs from the back-end, it is caught inside the Catch Exception block.</span></span>  
  
4.  <span data-ttu-id="3cef2-115">Vous devez ajouter la logique au bloc Intercepter l'exception.</span><span class="sxs-lookup"><span data-stu-id="3cef2-115">In the Catch Exception block, you must add the logic.</span></span>  
  
     <span data-ttu-id="3cef2-116">La logique la plus importante à définir est le type de message d'erreur que vous pensez recevoir.</span><span class="sxs-lookup"><span data-stu-id="3cef2-116">The most important logic you must set is the type of error message you are expecting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cef2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cef2-117">See Also</span></span>  
 [<span data-ttu-id="3cef2-118">À l’aide de la gestion des exceptions de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="3cef2-118">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling2.md)