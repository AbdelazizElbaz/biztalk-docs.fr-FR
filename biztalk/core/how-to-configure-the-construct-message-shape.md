---
title: Comment configurer la forme construire un Message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Construct Message shape [Orchestration Designer], configuring
- Construct Message shape [Orchestration Designer]
- configuring [Orchestration Designer], Construct Message shapes
- Construct Message shape [Orchestration Designer], about Construct Message shape
ms.assetid: 8d052b4e-0873-4102-9462-6604423d0524
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07b73e7fe62463767894808d7e95f12cf963e4dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-construct-message-shape"></a><span data-ttu-id="ad979-102">Configuration de la forme Construire un message</span><span class="sxs-lookup"><span data-stu-id="ad979-102">How to Configure the Construct Message Shape</span></span>
![](../core/media/ebiz-orch-constructmsg.gif "ebiz_orch_constructmsg")  
<span data-ttu-id="ad979-103">Forme Construire un message</span><span class="sxs-lookup"><span data-stu-id="ad979-103">Construct Message shape</span></span>  
  
 <span data-ttu-id="ad979-104">Vous devez indiquer la variable de message que vous souhaitez créer et réaliser des assignations pour ce message ou ses différentes parties.</span><span class="sxs-lookup"><span data-stu-id="ad979-104">You specify the message variable that you want to construct, and make assignments to the message or its parts.</span></span> <span data-ttu-id="ad979-105">Toutes les assignations effectuées pour un message donné doivent avoir lieu dans la même forme Construire un message.</span><span class="sxs-lookup"><span data-stu-id="ad979-105">All assignments to any given message must take place within the same Construct Message shape.</span></span>  
  
 <span data-ttu-id="ad979-106">Si vous souhaitez modifier une propriété d'un message déjà construit, tel qu'un message reçu, vous devez créer une nouvelle instance de message en affectant l'instance du message déjà construit à la nouvelle instance, puis en modifiant la propriété dans la nouvelle instance. La construction et la modification surviennent dans la même forme Construire un message.</span><span class="sxs-lookup"><span data-stu-id="ad979-106">If you want to modify a property on a message that has already been constructed—such as a message that has been received—you must construct a new message instance by assigning the first to the second and then modifying the property on the new message instance; both the construction and modification occur within the same Construct Message shape.</span></span>  
  
### <a name="to-configure-a-construct-message-shape"></a><span data-ttu-id="ad979-107">Pour configurer une forme construire un Message</span><span class="sxs-lookup"><span data-stu-id="ad979-107">To configure a Construct Message shape</span></span>  
  
1.  <span data-ttu-id="ad979-108">Dans la fenêtre Propriétés, utilisez le **Messages construits** propriété pour spécifier les messages à cette forme construira.</span><span class="sxs-lookup"><span data-stu-id="ad979-108">In the Properties window, use the **Messages Constructed** property to specify which messages this shape will construct.</span></span>  
  
2.  <span data-ttu-id="ad979-109">Ajouter et configurer un ou plusieurs **transformer** ou **assignation du Message** des formes à l’intérieur de la **forme construire un Message**.</span><span class="sxs-lookup"><span data-stu-id="ad979-109">Add and configure one or more **Transform** or **Message Assignment** shapes inside the **Construct Message shape**.</span></span>