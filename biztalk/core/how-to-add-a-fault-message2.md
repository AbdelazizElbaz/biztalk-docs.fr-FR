---
title: "L’ajout d’une erreur de 2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fault messages, adding
- messages, fault messages
ms.assetid: 8f1b40af-2c75-4167-8b62-a86b791907c9
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dee8a1fca0e30a96b6a714b5c717c0638bc8144
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-fault-message"></a><span data-ttu-id="d19c9-102">Ajout d'un message d'erreur</span><span class="sxs-lookup"><span data-stu-id="d19c9-102">How to Add a Fault Message</span></span>
<span data-ttu-id="d19c9-103">Lorsque vous créez un port dans le système principal, celui-ci contient une requête et une réponse.</span><span class="sxs-lookup"><span data-stu-id="d19c9-103">When you create a port to the back-end system, it contains a request and a response.</span></span> <span data-ttu-id="d19c9-104">Vous devez ajouter un message afin de pouvoir l'affecter à l'erreur.</span><span class="sxs-lookup"><span data-stu-id="d19c9-104">You must add a message so that you can assign it to the fault.</span></span>  
  
### <a name="to-add-a-fault-message"></a><span data-ttu-id="d19c9-105">Pour ajouter un message d'erreur</span><span class="sxs-lookup"><span data-stu-id="d19c9-105">To add a fault message</span></span>  
  
1.  <span data-ttu-id="d19c9-106">Dans le **Vue Orchestration** fenêtre, avec le bouton droit **Messages**, puis sélectionnez **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="d19c9-106">In the **Orchestration View** window, right-click **Messages**, and select **New Message**.</span></span>  
  
     <span data-ttu-id="d19c9-107">Ceci crée le message Message_3, que vous pouvez affecter spécifiquement à l'erreur.</span><span class="sxs-lookup"><span data-stu-id="d19c9-107">This creates Message_3, which you can assign specifically to the fault.</span></span>  
  
2.  <span data-ttu-id="d19c9-108">Cliquez sur Message_3, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d19c9-108">Right-click Message_3, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="d19c9-109">Dans le **propriétés** boîte de dialogue, définissez la **Type de Message**.</span><span class="sxs-lookup"><span data-stu-id="d19c9-109">In the **Properties** dialog box, set the **Message Type**.</span></span>  
  
     <span data-ttu-id="d19c9-110">Sélectionnez **Classes .NET** , puis sélectionnez **SystemString**.</span><span class="sxs-lookup"><span data-stu-id="d19c9-110">Select **.NET Classes** and then select **SystemString**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d19c9-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d19c9-111">See Also</span></span>  
 [<span data-ttu-id="d19c9-112">À l’aide de la gestion des exceptions de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d19c9-112">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling3.md)