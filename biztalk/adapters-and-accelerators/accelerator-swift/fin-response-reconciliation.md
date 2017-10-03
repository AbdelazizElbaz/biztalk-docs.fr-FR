---
title: "Rapprochement de réponse FIN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ACKs
- FRR
- FIN Response Reconciliation
- SAA
- NAKs
- FRR, about FRR
- acknowledgements
- FIN Response Reconciliation, about FIN Response Reconciliation
- FIN Response Reconciliation, acknowledgements
ms.assetid: 987b932b-e487-4ca8-acd0-410d71df8e6d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5452dbacb8a9a20c8d2e62d62f6043aaea2d18da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fin-response-reconciliation"></a><span data-ttu-id="47cad-102">Rapprochement de réponse FIN</span><span class="sxs-lookup"><span data-stu-id="47cad-102">FIN Response Reconciliation</span></span>
<span data-ttu-id="47cad-103">La fonctionnalité de rapprochement de réponse de FIN (FRR) de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] rapproche d’une réponse FIN avec le message d’origine correspondant envoyé par [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="47cad-103">The FIN Response Reconciliation (FRR) feature of [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] reconciles a FIN response with the corresponding original message sent by [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="47cad-104">Cela établit l’état du message d’origine et permet [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] prendre des mesures en fonction de cet état.</span><span class="sxs-lookup"><span data-stu-id="47cad-104">This establishes the status of the original message, and enables [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to take steps based upon that status.</span></span> <span data-ttu-id="47cad-105">Sans le rapprochement, cela ne serait pas possible.</span><span class="sxs-lookup"><span data-stu-id="47cad-105">Without reconciliation, this would not be possible.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="47cad-106">sait qu’il (avec ou sans succès) envoyé le message d’origine à l’autorité d’homologation et il aurait la réponse reçue à partir de l’autorité d’homologation indiquant l’état de la transmission, mais il ne serait pas en mesure d’établir la connexion entre les deux.</span><span class="sxs-lookup"><span data-stu-id="47cad-106"> would know that it successfully (or unsuccessfully) sent the original message to SAA, and it would have the response that it received from SAA, indicating the status of the transmission, but it would not be able to make the connection between the two.</span></span> <span data-ttu-id="47cad-107">FRR établit la connexion.</span><span class="sxs-lookup"><span data-stu-id="47cad-107">FRR establishes that connection.</span></span>  
  
 <span data-ttu-id="47cad-108">Réponses FIN sont des accusés de réception (ACK) ou négatifs (NAKs) d’accusés de réception envoyés par SAA à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], ou envoyé par le réseau SWIFT à SAA et ensuite transmis par SAA à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="47cad-108">FIN responses are acknowledgments (ACKs) or negative acknowledgments (NAKs) sent by SAA to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], or sent by the SWIFT network to SAA and then forwarded by SAA to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="47cad-109">La présence ou l’absence de ces accusés de réception définit l’état de l’entreprise du message.</span><span class="sxs-lookup"><span data-stu-id="47cad-109">The presence or absence of these acknowledgments defines the business status of the message.</span></span> <span data-ttu-id="47cad-110">Vous pouvez surveiller cet état au moyen de rapports d’analyse BAM (Business Activity).</span><span class="sxs-lookup"><span data-stu-id="47cad-110">You can monitor this status through Business Activity Monitoring (BAM) reporting.</span></span>  
  
 <span data-ttu-id="47cad-111">Vous pouvez également implémenter le comportement de l’application personnalisée autour de FRR.</span><span class="sxs-lookup"><span data-stu-id="47cad-111">You can also implement custom application behavior around FRR.</span></span> <span data-ttu-id="47cad-112">Un gestionnaire personnalisé peut implémenter votre propre logique pour la gestion de jeux rapprochée des réponses FIN.</span><span class="sxs-lookup"><span data-stu-id="47cad-112">A custom handler can implement your own logic for handling reconciled sets of FIN responses.</span></span> <span data-ttu-id="47cad-113">Pour obtenir un exemple d’un gestionnaire personnalisé qui traite les messages FRR a mis en corrélation avec un message MTS21_FIN_ACKNAK NAK, consultez [FRR NAK Gestionnaire exemple](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md).</span><span class="sxs-lookup"><span data-stu-id="47cad-113">For an example of a custom handler that processes messages that FRR has correlated with a MTS21_FIN_ACKNAK NAK message, see [FRR NAK Handler Sample](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md).</span></span>  
  
 <span data-ttu-id="47cad-114">L’orchestration FRR est installée par défaut par le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="47cad-114">The FRR orchestration is installed by default by the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] setup program.</span></span> <span data-ttu-id="47cad-115">Vous devez configurer le système FRR en créant un pipeline de réception, emplacements de réception et ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="47cad-115">You need to configure the FRR system by creating a receive pipeline, receive locations, and send ports.</span></span> <span data-ttu-id="47cad-116">Vous devez également configurer FRR pour spécifier la durée pendant laquelle il doit attendre pour NAKs retardées et pour les réponses en général.</span><span class="sxs-lookup"><span data-stu-id="47cad-116">You also need to configure FRR to specify how long it should wait for delayed NAKs, and for responses in general.</span></span> <span data-ttu-id="47cad-117">Pour plus d’informations sur la configuration de FRR et d’administration, consultez [rapprochement de réponse de FIN configuration](../../adapters-and-accelerators/accelerator-swift/configuring-fin-response-reconciliation.md) et [rapprochement de réponse de FIN administration](../../adapters-and-accelerators/accelerator-swift/administering-fin-response-reconciliation.md).</span><span class="sxs-lookup"><span data-stu-id="47cad-117">For more information about FRR configuration and administration, see [Configuring FIN Response Reconciliation](../../adapters-and-accelerators/accelerator-swift/configuring-fin-response-reconciliation.md) and [Administering FIN Response Reconciliation](../../adapters-and-accelerators/accelerator-swift/administering-fin-response-reconciliation.md).</span></span>  
  
 <span data-ttu-id="47cad-118">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="47cad-118">This section contains:</span></span>  
  
-   [<span data-ttu-id="47cad-119">Types de réponse FIN</span><span class="sxs-lookup"><span data-stu-id="47cad-119">FIN Response Types</span></span>](../../adapters-and-accelerators/accelerator-swift/fin-response-types.md)  
  
-   [<span data-ttu-id="47cad-120">Traitement de FRR</span><span class="sxs-lookup"><span data-stu-id="47cad-120">FRR Processing</span></span>](../../adapters-and-accelerators/accelerator-swift/frr-processing.md)  
  
-   [<span data-ttu-id="47cad-121">Orchestration de FRR</span><span class="sxs-lookup"><span data-stu-id="47cad-121">FRR Orchestration</span></span>](../../adapters-and-accelerators/accelerator-swift/frr-orchestration.md)  
  
-   [<span data-ttu-id="47cad-122">FRR emplacement de réception pour les Messages à partir de l’Application Back-End.</span><span class="sxs-lookup"><span data-stu-id="47cad-122">FRR Receive Location for Messages from the Back-End Application</span></span>](../../adapters-and-accelerators/accelerator-swift/frr-receive-location-for-messages-from-the-back-end-application.md)  
  
-   [<span data-ttu-id="47cad-123">FRR Port d’envoi de Messages SWIFT</span><span class="sxs-lookup"><span data-stu-id="47cad-123">FRR Send Port for Messages to SWIFT</span></span>](../../adapters-and-accelerators/accelerator-swift/frr-send-port-for-messages-to-swift.md)  
  
-   [<span data-ttu-id="47cad-124">FRR emplacement de réception pour les Messages à partir de SWIFT</span><span class="sxs-lookup"><span data-stu-id="47cad-124">FRR Receive Location for Messages from SWIFT</span></span>](../../adapters-and-accelerators/accelerator-swift/frr-receive-location-for-messages-from-swift.md)  
  
-   [<span data-ttu-id="47cad-125">FRR des Ports d’envoi des Messages aux gestionnaires personnalisés</span><span class="sxs-lookup"><span data-stu-id="47cad-125">FRR Send Ports for Messages to the Custom Handlers</span></span>](../../adapters-and-accelerators/accelerator-swift/frr-send-ports-for-messages-to-the-custom-handlers.md)  
  
-   [<span data-ttu-id="47cad-126">Gestion des ensembles de messages de rapprochement</span><span class="sxs-lookup"><span data-stu-id="47cad-126">Handling Reconciled Message Sets</span></span>](../../adapters-and-accelerators/accelerator-swift/handling-reconciled-message-sets.md)