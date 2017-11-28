---
title: Exemple de gestionnaire FRR NAK | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, NAKs
- examples, FRR
- NAKs
- acknowledgements
- FRR, examples
- examples, FRR NAK handler
ms.assetid: be992507-ba8c-461f-a563-f1d7b2ab221d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a3881b8bcf4b62af7653ef6214b4fccdf8402d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-nak-handler-sample"></a><span data-ttu-id="1590a-102">Exemple de gestionnaire FRR NAK</span><span class="sxs-lookup"><span data-stu-id="1590a-102">FRR NAK Handler Sample</span></span>
<span data-ttu-id="1590a-103">L’exemple de gestionnaire de NAK FRR montre comment créer un gestionnaire personnalisé pour traiter les messages rapprochement de réponse de FIN (FRR) a mis en corrélation avec les réponses SWIFT.</span><span class="sxs-lookup"><span data-stu-id="1590a-103">The FRR NAK Handler sample demonstrates how to create a custom handler to process messages that FIN Response Reconciliation (FRR) has correlated with SWIFT responses.</span></span> <span data-ttu-id="1590a-104">Ce gestionnaire personnalisé traite les messages qui FRR a mis en corrélation avec un message MTS21_FIN_ACKNAK-accusé de réception négatif, ce qui indique que SWIFT n’a pas été reçu le message d’A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="1590a-104">This custom handler processes messages that FRR has correlated with a MTS21_FIN_ACKNAK negative-acknowledgment message, which indicates that SWIFT did not successfully receive the message from A4SWIFT.</span></span> <span data-ttu-id="1590a-105">Le gestionnaire personnalisé ajoute un objet d’erreur pour le message, en rendant un message en deux parties, un message et promeut les propriétés qui provoquent l’orchestration de réparation de message récupérer le message.</span><span class="sxs-lookup"><span data-stu-id="1590a-105">The custom handler adds an error object to the message, making the message a two-part message, and promotes the properties that cause the message-repair orchestration to pick up the message.</span></span> <span data-ttu-id="1590a-106">Par conséquent, un réparateur peut résoudre le message et le renvoyer à l’accès de Alliance SWIFT (SAA).</span><span class="sxs-lookup"><span data-stu-id="1590a-106">As a result, a repairer can fix the message and resend it to SWIFT Alliance Access (SAA).</span></span>  
  
 <span data-ttu-id="1590a-107">**Exemples de composants**</span><span class="sxs-lookup"><span data-stu-id="1590a-107">**Sample Components**</span></span>  
  
 <span data-ttu-id="1590a-108">L’exemple de gestionnaire de NAK FRR inclut les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="1590a-108">The FRR NAK Handler sample includes the following components:</span></span>  
  
-   <span data-ttu-id="1590a-109">**RepairSWIFTRejectedMessage.odx.**</span><span class="sxs-lookup"><span data-stu-id="1590a-109">**RepairSWIFTRejectedMessage.odx.**</span></span> <span data-ttu-id="1590a-110">Cette orchestration est le gestionnaire personnalisé qui traite un message SWIFT n'a pas reçu, routage à l’orchestration de réparation de message pour un réparateur peut corriger et renvoyer le message.</span><span class="sxs-lookup"><span data-stu-id="1590a-110">This orchestration is the custom handler that processes a message that SWIFT could not successfully receive, routing it to the message-repair orchestration so a repairer can fix and resend the message.</span></span>  
  
-   <span data-ttu-id="1590a-111">**RepairSWIFTRejectedMessage.btproj.**</span><span class="sxs-lookup"><span data-stu-id="1590a-111">**RepairSWIFTRejectedMessage.btproj.**</span></span> <span data-ttu-id="1590a-112">Ce projet comprend RepairSWIFTRejectedMessage.odx et les références requises pour le projet pour générer et déployer.</span><span class="sxs-lookup"><span data-stu-id="1590a-112">This project includes RepairSWIFTRejectedMessage.odx and the references required for the project to build and deploy.</span></span>  
  
-   <span data-ttu-id="1590a-113">**RepairSWIFTRejectedMessage.sln.**</span><span class="sxs-lookup"><span data-stu-id="1590a-113">**RepairSWIFTRejectedMessage.sln.**</span></span> <span data-ttu-id="1590a-114">Cette solution inclut le projet RepairSWIFTRejectedMessage.btproj.</span><span class="sxs-lookup"><span data-stu-id="1590a-114">This solution includes the RepairSWIFTRejectedMessage.btproj project.</span></span>  
  
 <span data-ttu-id="1590a-115">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="1590a-115">This section contains:</span></span>  
  
-   [<span data-ttu-id="1590a-116">Implémentation de l’exemple de gestionnaire FRR NAK</span><span class="sxs-lookup"><span data-stu-id="1590a-116">Implementing the FRR NAK Handler Sample</span></span>](../../adapters-and-accelerators/accelerator-swift/implementing-the-frr-nak-handler-sample.md)  
  
-   [<span data-ttu-id="1590a-117">Fonctionne de l’exemple de gestionnaire FRR NAK</span><span class="sxs-lookup"><span data-stu-id="1590a-117">How the FRR NAK Handler Sample Works</span></span>](../../adapters-and-accelerators/accelerator-swift/how-the-frr-nak-handler-sample-works.md)  
  
