---
title: "Comment construire une partie de Message Web à partir d’un Type .NET primitif | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, Web messages
- Web messages, Message Assignment shape [Orchestration Designer]
- Web messages, creating
- Message Assignment shape [Orchestration Designer], Web messages
- Web messages, parts
- Web messages, .NET types
ms.assetid: 1fe52412-d2bc-484c-8925-c7ff3ca7704b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 991970d5b0d40da1ec00b54919d2742cfd48353c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-construct-a-web-message-part-from-a-primitive-net-type"></a><span data-ttu-id="16ac1-102">Développement d'une partie de message web à partir d'un type .NET primitif</span><span class="sxs-lookup"><span data-stu-id="16ac1-102">How to Construct a Web Message Part from a Primitive .NET Type</span></span>
<span data-ttu-id="16ac1-103">Vous créez une partie de message Web à partir d’un type .NET primitif à l’aide un **assignation du Message** forme.</span><span class="sxs-lookup"><span data-stu-id="16ac1-103">You create a Web message part from a primitive .NET type by using a **Message Assignment** shape.</span></span> <span data-ttu-id="16ac1-104">ou à l'aide d'une classe d'assistance .NET pour définir les parties.</span><span class="sxs-lookup"><span data-stu-id="16ac1-104">Alternatively, you can create a Web message part from a primitive .NET type by using a .NET helper class to set the parts.</span></span> <span data-ttu-id="16ac1-105">Pour plus d’informations sur la création de types de messages à l’aide d’une classe .NET, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).</span><span class="sxs-lookup"><span data-stu-id="16ac1-105">For more information on creating message types by using a .NET class, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
### <a name="to-construct-a-web-message-part-from-a-primitive-net-type"></a><span data-ttu-id="16ac1-106">Pour créer une partie de message Web à partir d'un type .NET primitif</span><span class="sxs-lookup"><span data-stu-id="16ac1-106">To construct a Web message part from a primitive .NET type</span></span>  
  
1.  <span data-ttu-id="16ac1-107">Ouvrez une orchestration, ouvrez le **boîte à outils** et cliquez sur le **Orchestrations BizTalk** onglet.</span><span class="sxs-lookup"><span data-stu-id="16ac1-107">With an orchestration open, open the **Toolbox** and click the **BizTalk Orchestrations** tab.</span></span>  
  
2.  <span data-ttu-id="16ac1-108">Faites glisser un **construire un Message** forme à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="16ac1-108">Drag a **Construct Message** shape to the orchestration.</span></span>  
  
3.  <span data-ttu-id="16ac1-109">Modifier la **Message construit** propriété à inclure l’instance de message que vous avez créé pour le type de message Web.</span><span class="sxs-lookup"><span data-stu-id="16ac1-109">Edit the **Message Constructed** property to include the message instance that you created for the Web message type.</span></span>  
  
4.  <span data-ttu-id="16ac1-110">Faites glisser un **assignation du Message** forme sur le **construire un Message** forme.</span><span class="sxs-lookup"><span data-stu-id="16ac1-110">Drag a **Message Assignment** shape onto the **Construct Message** shape.</span></span>  
  
5.  <span data-ttu-id="16ac1-111">Double-cliquez sur le **assignation du Message** forme pour ouvrir l’éditeur d’Expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="16ac1-111">Double-click the **Message Assignment** shape to open the BizTalk Expression Editor.</span></span>  
  
6.  <span data-ttu-id="16ac1-112">Définissez les parties du type de message Web sur les valeurs requises dans la zone Éditeur d'expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="16ac1-112">Set the parts of the Web message type to their required values in the BizTalk Expression Editor box.</span></span>  
  
     <span data-ttu-id="16ac1-113">Par exemple, le code suivant définit l'expression sur une chaîne :</span><span class="sxs-lookup"><span data-stu-id="16ac1-113">For example, the following code sets the expression to a string:</span></span>  
  
    ```  
    ItemAvailRequestInstance.Item_ID = "This is Item_ID.";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="16ac1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16ac1-114">See Also</span></span>  
 [<span data-ttu-id="16ac1-115">Construction de Messages Web</span><span class="sxs-lookup"><span data-stu-id="16ac1-115">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)