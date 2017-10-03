---
title: "L’utilisation de Ports dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, receiving
- ports, configuring manually
- send ports, messages
- ports, creating
- ports, messages
- creating, ports
- send ports, sending
- ports, operations
- configuring, ports
- ports, deleting
- deleting, ports
- orchestrations, ports
- Port Configuration Wizard [Orchestration Designer]
- ports
- ports, about ports
- ports, configuring
ms.assetid: 968b2d1b-e233-4eb0-8254-9ec6b7642cdf
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7f48c1c070e3a3a3e7ebe7e86618a4fd9ebc90d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-ports-in-orchestrations"></a><span data-ttu-id="ddc6d-102">Utilisation des ports dans des orchestrations</span><span class="sxs-lookup"><span data-stu-id="ddc6d-102">Using Ports in Orchestrations</span></span>
<span data-ttu-id="ddc6d-103">Les ports indiquent comment votre orchestration enverra et recevra des messages vers et à partir d'autres processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="ddc6d-103">Ports specify how your orchestration will send messages to and receive messages from other business processes.</span></span> <span data-ttu-id="ddc6d-104">Chaque port possède un type, une direction et une liaison qui déterminent ensemble la direction de communication, le modèle de communication, l'emplacement vers et à partir duquel le message est envoyé ou reçu, et comment la communication a lieu.</span><span class="sxs-lookup"><span data-stu-id="ddc6d-104">Each port has a type, a direction, and a binding, which together determine the direction of communication, the pattern of communication, the location to or from which the message is sent or received, and how the communication takes place.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddc6d-105">Il faut faire la distinction entre port et type de port.</span><span class="sxs-lookup"><span data-stu-id="ddc6d-105">There is a distinction between a port and a port type.</span></span> <span data-ttu-id="ddc6d-106">Un port est une instance d'un type de port. Plusieurs ports peuvent avoir le même type de port.</span><span class="sxs-lookup"><span data-stu-id="ddc6d-106">A port is an instance of a port type; several different ports may have the same port type.</span></span>  
  
 <span data-ttu-id="ddc6d-107">En fonction de ces facteurs, un port peut être associé à un URI (emplacement physique), un transport (FILE, HTTP, SOAP, SMTP ou Message Queuing BizTalk), un pipeline d'envoi pour préparer un message pour l'envoi (par exemple en l'assemblant, le chiffrant ou le compressant) et un pipeline de réception pour préparer un message reçu au traitement (par exemple en le désassemblant, le déchiffrant ou le décompressant).</span><span class="sxs-lookup"><span data-stu-id="ddc6d-107">Depending on these factors, a port may have associated with it a URI (a physical location), a transport (either FILE, HTTP, SOAP, SMTP or BizTalk Message Queuing), a send pipeline to prepare a message for sending (for example, by assembling, encrypting, compressing, or performing some other action on it), and a receive pipeline to prepare a received message for processing (for example, by disassembling, decrypting, or decompressing it).</span></span>  
  
 <span data-ttu-id="ddc6d-108">Pour ajouter des ports à une orchestration, on procède sensiblement de la même façon que pour ajouter des contrôles à un formulaire Web ou Windows.</span><span class="sxs-lookup"><span data-stu-id="ddc6d-108">You add ports to an orchestration in much the same way that you add controls to a Web Form or Windows Form.</span></span> <span data-ttu-id="ddc6d-109">Vous pouvez également ajouter des ports en utilisant la fenêtre Vue Orchestration.</span><span class="sxs-lookup"><span data-stu-id="ddc6d-109">You can also add ports by using the Orchestration View window.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ddc6d-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ddc6d-110">In This Section</span></span>  
  
-   [<span data-ttu-id="ddc6d-111">Modèle de communication</span><span class="sxs-lookup"><span data-stu-id="ddc6d-111">Communication Pattern</span></span>](../core/communication-pattern.md)  
  
-   [<span data-ttu-id="ddc6d-112">Direction de communication</span><span class="sxs-lookup"><span data-stu-id="ddc6d-112">Communication Direction</span></span>](../core/communication-direction.md)  
  
-   [<span data-ttu-id="ddc6d-113">Liaisons de port</span><span class="sxs-lookup"><span data-stu-id="ddc6d-113">Port Bindings</span></span>](../core/port-bindings.md)  
  
-   [<span data-ttu-id="ddc6d-114">L’utilisation de Ports dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="ddc6d-114">How to Use Ports in Orchestrations</span></span>](../core/how-to-use-ports-in-orchestrations.md)  
  
-   [<span data-ttu-id="ddc6d-115">L’utilisation des Types de ports</span><span class="sxs-lookup"><span data-stu-id="ddc6d-115">How to Work with Port Types</span></span>](../core/how-to-work-with-port-types.md)  
  
-   [<span data-ttu-id="ddc6d-116">Comment exécuter l’Assistant Configuration du Port</span><span class="sxs-lookup"><span data-stu-id="ddc6d-116">How to Run the Port Configuration Wizard</span></span>](../core/how-to-run-the-port-configuration-wizard.md)  
  
-   [<span data-ttu-id="ddc6d-117">Utilisation de Ports à liaison directe dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="ddc6d-117">Working with Direct Bound Ports in Orchestrations</span></span>](../core/working-with-direct-bound-ports-in-orchestrations.md)  
  
## <a name="see-also"></a><span data-ttu-id="ddc6d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddc6d-118">See Also</span></span>  
 <span data-ttu-id="ddc6d-119">[Comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="ddc6d-119">[How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md) </span></span>  
 [<span data-ttu-id="ddc6d-120">À l’aide de liens de rôle dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="ddc6d-120">Using Role Links in Orchestrations</span></span>](../core/using-role-links-in-orchestrations.md)