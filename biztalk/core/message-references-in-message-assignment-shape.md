---
title: "Références dans la forme assignation du Message du message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, code samples
- code samples, messages
- messages, objects
ms.assetid: 428f7eb8-001e-4147-b1c8-f9bb6f3a80f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b834eefa991b6cad89a04a836f63d1b9af73fc04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-references-in-message-assignment-shape"></a><span data-ttu-id="035c6-102">Références de message dans la forme assignation du Message</span><span class="sxs-lookup"><span data-stu-id="035c6-102">Message References in Message Assignment Shape</span></span>
<span data-ttu-id="035c6-103">Lorsque vous assignez un objet .NET à un message ou à une partie de message pour la première fois, ce message conserve une référence de l'objet.</span><span class="sxs-lookup"><span data-stu-id="035c6-103">When you first assign a .NET-based object to a message or message part, that message holds and maintains a reference to the object.</span></span>  
  
 <span data-ttu-id="035c6-104">Pour une efficacité et l’évolutivité, le moteur d’orchestration n’effectue une copie « complète » de l’objet : autrement dit, elle ne copie pas tout le contenu de l’objet pour le message.</span><span class="sxs-lookup"><span data-stu-id="035c6-104">For efficiency and scalability, the orchestration engine does not do a "deep copy" of the object: that is, it does not copy the entire contents of the object to the message.</span></span>  
  
 <span data-ttu-id="035c6-105">Si vous attribuez ensuite l'objet à un autre message ou à une autre partie de message, toute modification apportée à l'original entraîne la modification du second message ou partie de message.</span><span class="sxs-lookup"><span data-stu-id="035c6-105">If you subsequently assign the object to another message or message part, any modifications to the original results in modifications to the second message or message part.</span></span> <span data-ttu-id="035c6-106">Les résultats devenant alors imprévisibles, il est recommandé d'éviter cette pratique.</span><span class="sxs-lookup"><span data-stu-id="035c6-106">You should avoid this practice, because results are unpredictable.</span></span>  
  
 <span data-ttu-id="035c6-107">Si votre second message doit disposer d'une copie distincte de l'objet, vous devez attribuer le premier message (ou partie de message) au second message (ou partie de message). </span><span class="sxs-lookup"><span data-stu-id="035c6-107">If you need your second message to have a distinct copy of the object, you should assign the first message or message part to the second message or message part.</span></span>  
  
 <span data-ttu-id="035c6-108">Prenons l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="035c6-108">Consider the following example:</span></span>  
  
 <span data-ttu-id="035c6-109">Mauvaise méthode :</span><span class="sxs-lookup"><span data-stu-id="035c6-109">Wrong way:</span></span>  
  
```  
myMsg1 = myObj; // assign the first message  
myMsg2 = myObj; // assign the second message (wrong!)  
myMsg2.myInt = 100; // modify the second  
myMsg1.myInt = 5;  
```  
  
 <span data-ttu-id="035c6-110">Ici, myMsg2.myInt a été modifié et affiche maintenant la valeur 5.</span><span class="sxs-lookup"><span data-stu-id="035c6-110">In this case, myMsg2.myInt has been overwritten, and now has the value 5.</span></span>  
  
 <span data-ttu-id="035c6-111">Bonne méthode :</span><span class="sxs-lookup"><span data-stu-id="035c6-111">Right way:</span></span>  
  
```  
myMsg1 = myObj; // assign the first message  
myMsg2 = myMsg1; // assign the second message (right!)  
myMsg2.myInt = 100; // modify the second  
myMsg1.myInt = 5;  
```  
  
 <span data-ttu-id="035c6-112">Ici, myMsg2.myInt affiche toujours la valeur 100, comme escompté.</span><span class="sxs-lookup"><span data-stu-id="035c6-112">In this case, myMsg2.myInt still has the value 100, as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="035c6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="035c6-113">See Also</span></span>  
 [<span data-ttu-id="035c6-114">Construction de Messages</span><span class="sxs-lookup"><span data-stu-id="035c6-114">Constructing Messages</span></span>](../core/constructing-messages.md)