---
title: "Gestion des modèles de service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fea915c-0074-472e-909b-fbbd88d7359c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a48639fb2a540b5b2597b34ad95ee390b4382c34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="service-management-patterns"></a><span data-ttu-id="4e09d-102">Modèles de service de gestion</span><span class="sxs-lookup"><span data-stu-id="4e09d-102">Service Management Patterns</span></span>
## <a name="repair-and-resubmit"></a><span data-ttu-id="4e09d-103">Réparer et soumettez à nouveau</span><span class="sxs-lookup"><span data-stu-id="4e09d-103">Repair and Resubmit</span></span>  
 <span data-ttu-id="4e09d-104">Le modèle de réparation et soumettez à nouveau définit une solution dans laquelle un service ne peut pas traiter un message et doit normalement externaliser son état dans le formulaire du message ayant échoué, le contenu du message soit disponible pour l’activation de réparer et puis soumettez à nouveau à un service Pour continuer le traitement du message.</span><span class="sxs-lookup"><span data-stu-id="4e09d-104">The Repair and Resubmit pattern defines a solution in which a service is unable to process a message and needs to gracefully externalize its state in the form of the failed message, enabling the message content to be available for repair and then resubmit it to a service to continue processing the message.</span></span>  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]<span data-ttu-id="4e09d-105">inclut des mécanismes par le Microsoft BizTalk les exceptions de messagerie et d’orchestration peuvent être normalisées et exposées pour une action supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="4e09d-105"> includes mechanisms by which Microsoft BizTalk messaging and orchestration exceptions can be normalized and exposed for additional action.</span></span> <span data-ttu-id="4e09d-106">Lorsque vous concevez une solution ESB, il est important de compte de gestion des exceptions de.</span><span class="sxs-lookup"><span data-stu-id="4e09d-106">When designing an ESB solution, it is important to account for how exceptions will be handled.</span></span> <span data-ttu-id="4e09d-107">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] comprend un exemple d’application de portail de gestion ESB qui montre comment les exceptions peuvent être affichées et gérées.</span><span class="sxs-lookup"><span data-stu-id="4e09d-107">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes a sample ESB Management Portal application that demonstrates how exceptions can be viewed and managed.</span></span> <span data-ttu-id="4e09d-108">Pour plus d’informations sur la réparation et la soumettre à nouveau les exceptions à l’aide de l’exemple d’application de portail de gestion ESB, consultez [réparation et soumettre à nouveau les Messages](../esb-toolkit/repairing-and-resubmitting-messages.md).</span><span class="sxs-lookup"><span data-stu-id="4e09d-108">For detailed information about repairing and resubmitting exceptions using the ESB Management Portal sample application, see [Repairing and Resubmitting Messages](../esb-toolkit/repairing-and-resubmitting-messages.md).</span></span>