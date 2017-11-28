---
title: "Ajout d’un Message pour un Exception2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, adding messages
- messages, exceptions
- exception handling, adding messages
- fault messages, adding
ms.assetid: 9d8a3801-78cd-4c18-8deb-3fbe4a49a2f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b2c314684094e73cb6d663bcf2183ffc3eccae5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-message-for-an-exception"></a><span data-ttu-id="2f640-102">L’ajout d’un Message pour une Exception</span><span class="sxs-lookup"><span data-stu-id="2f640-102">How to Add a Message for an Exception</span></span>
<span data-ttu-id="2f640-103">Lorsque vous commencez par créer un port menant au système principal, il contient une demande et une réponse.</span><span class="sxs-lookup"><span data-stu-id="2f640-103">When you first create a port to the back-end system, it contains a request and a response.</span></span> <span data-ttu-id="2f640-104">Vous devez ajouter un message afin de pouvoir l'affecter à l'erreur.</span><span class="sxs-lookup"><span data-stu-id="2f640-104">You must add a message so that you can assign it to the fault.</span></span>  
  
### <a name="to-add-a-fault-message"></a><span data-ttu-id="2f640-105">Pour ajouter un message d'erreur</span><span class="sxs-lookup"><span data-stu-id="2f640-105">To add a fault message</span></span>  
  
1.  <span data-ttu-id="2f640-106">Dans le **Vue Orchestration** fenêtre, avec le bouton droit **Messages**, puis sélectionnez **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="2f640-106">In the **Orchestration View** window, right-click **Messages**, and then select **New Message**.</span></span>  
  
     <span data-ttu-id="2f640-107">Ceci crée le message Message_3, que vous pouvez affecter spécifiquement à l'erreur.</span><span class="sxs-lookup"><span data-stu-id="2f640-107">This creates Message_3, which you can assign specifically to the fault.</span></span>  
  
2.  <span data-ttu-id="2f640-108">Avec le bouton droit **Message_3**, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2f640-108">Right-click **Message_3**, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="2f640-109">Définir le **Type de Message** comme suit : sélectionnez **Classes .NET**, puis sélectionnez **System, String**</span><span class="sxs-lookup"><span data-stu-id="2f640-109">Set the **Message Type** as follows: select **.NET Classes**, and then select **System,String**</span></span>  
  
 ![](../core/media/jdeoneworld-03-addscope.gif "JdeOneWorld_03_addscope")  
  
## <a name="see-also"></a><span data-ttu-id="2f640-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f640-110">See Also</span></span>  
 [<span data-ttu-id="2f640-111">À l’aide de la gestion des exceptions de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2f640-111">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling1.md)