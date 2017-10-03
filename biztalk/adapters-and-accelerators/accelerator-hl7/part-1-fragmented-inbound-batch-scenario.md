---
title: "Partie 1 : Par lot entrant fragmentés scénario | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, fragmenting messages
- batching tutorial, fragmenting messages
- fragmenting messages
ms.assetid: 8adf2c17-5f66-408d-b30b-51b22d8e71fa
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8891bd09c803c77e1878b304f5db5b71a26ab9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="part-1-fragmented-inbound-batch-scenario"></a><span data-ttu-id="7b69f-102">Partie 1 : Scénario de lot entrant fragmenté</span><span class="sxs-lookup"><span data-stu-id="7b69f-102">Part 1: Fragmented Inbound Batch Scenario</span></span>
<span data-ttu-id="7b69f-103">Dans cette partie du didacticiel, recevoir un lot HL7 encodé, il fragment en messages individuels et envoyer les messages individuels vers une destination.</span><span class="sxs-lookup"><span data-stu-id="7b69f-103">In this part of the tutorial, you receive an HL7-encoded batch, fragment it into individual messages, and send the individual messages to a destination.</span></span> <span data-ttu-id="7b69f-104">La figure suivante illustre le flux de ce processus.</span><span class="sxs-lookup"><span data-stu-id="7b69f-104">The following figure shows the flow of this process.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-fragmented-inbound-batching-scenario.gif "hl7_fragmented_inbound_batching_scenario")  
  
 <span data-ttu-id="7b69f-105">Ce scénario inclut le workflow suivant :</span><span class="sxs-lookup"><span data-stu-id="7b69f-105">This scenario includes the following workflow:</span></span>  
  
1.  <span data-ttu-id="7b69f-106">Le flux de travail commence quand une application métier-envoie un lot de messages à la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] moteur d’intégration à l’aide du protocole de protocole de couche inférieure minimale (MLLP).</span><span class="sxs-lookup"><span data-stu-id="7b69f-106">The workflow begins when a line-of-business application sends a message batch to the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Integration Engine using the Minimal Lower Layer Protocol (MLLP) protocol.</span></span> <span data-ttu-id="7b69f-107">Le lot contient deux versions d’un ADT ^ A03 message.</span><span class="sxs-lookup"><span data-stu-id="7b69f-107">The batch contains two versions of an ADT^A03 message.</span></span> <span data-ttu-id="7b69f-108">L’application source appartient au tiers Tutorial_BatchSource.</span><span class="sxs-lookup"><span data-stu-id="7b69f-108">The source application belongs to the Tutorial_BatchSource party.</span></span>  
  
2.  <span data-ttu-id="7b69f-109">Le moteur de l’Interface reçoit le lot sur un MLLP port de réception et valide le lot de messages.</span><span class="sxs-lookup"><span data-stu-id="7b69f-109">The Interface Engine receives the batch on an MLLP receive port, and validates the message batch.</span></span> <span data-ttu-id="7b69f-110">(Le niveau de validation dépend des paramètres sélectionnés pour la partie de la source dans l’Explorateur de Configuration BTAHL7.)</span><span class="sxs-lookup"><span data-stu-id="7b69f-110">(The level of validation depends on settings selected for the source party in BTAHL7 Configuration Explorer.)</span></span>  
  
3.  <span data-ttu-id="7b69f-111">Basé sur un paramètre dans l’Explorateur de Configuration BTAHL7 qui permet la fragmentation du lot, le moteur d’Interface analyse le lot dans deux ADT individuels ^ A03 messages.</span><span class="sxs-lookup"><span data-stu-id="7b69f-111">Based on a setting in BTAHL7 Configuration Explorer that enables batch fragmentation, the Interface Engine parses the batch into two individual ADT^A03 messages.</span></span> <span data-ttu-id="7b69f-112">Il valide les messages individuels, en fonction de paramètres sélectionnés pour le tiers source dans l’Explorateur de Configuration BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="7b69f-112">It validates the individual messages, again based on settings selected for the source party in BTAHL7 Configuration Explorer.</span></span>  
  
4.  <span data-ttu-id="7b69f-113">Le moteur de l’Interface génère un accusé de réception pour chaque message, selon les paramètres de la définition d’accusé de réception dans l’Explorateur de Configuration BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="7b69f-113">The Interface Engine generates an acknowledgment for each message, based on the acknowledgment definition settings in BTAHL7 Configuration Explorer.</span></span> <span data-ttu-id="7b69f-114">Dans ce didacticiel, vous allez sélectionner le mode d’accusé de réception d’origine, afin du moteur de l’Interface génère une seule Application accepte d’accusé de réception pour chaque message après la validation de l’en-tête de message et le corps.</span><span class="sxs-lookup"><span data-stu-id="7b69f-114">In this tutorial, you will select Original Acknowledgment mode, so the Interface Engine generates a single Application Accept acknowledgment for each message after validating both the message header and body.</span></span> <span data-ttu-id="7b69f-115">Le moteur génère l’accusé de réception en fonction du schéma ACK_024_GLO_DEF, passe à « AA » dans le champ MSA2 de l’accusé de réception, passe à des tiers de destination dans MSH3 et passe à la partie source dans MSH5.</span><span class="sxs-lookup"><span data-stu-id="7b69f-115">The engine builds the acknowledgment based on the ACK_024_GLO_DEF schema, enters "AA" in field MSA2 of the acknowledgment, enters the destination party in MSH3, and enters the source party in MSH5.</span></span>  
  
5.  <span data-ttu-id="7b69f-116">Le moteur d’Interface place wrappers MLLP autour de chaque accusé de réception, et les itinéraires les accusés de réception à la source de tiers via un adaptateur d’envoi MLLP configurée pour traiter les accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="7b69f-116">The Interface Engine places MLLP wrappers around each acknowledgment, and routes the acknowledgments to the source party through an MLLP send adapter set up to process acknowledgments.</span></span>  
  
6.  <span data-ttu-id="7b69f-117">Le moteur de l’Interface place des wrappers autour de chaque message et les itinéraires configurée pour traiter les messages d’accusé de réception non de port d’envoi de chaque message individuellement pour un MLLP MLLP.</span><span class="sxs-lookup"><span data-stu-id="7b69f-117">The Interface Engine places MLLP wrappers around each message, and routes each message individually to an MLLP send port set up to process non-acknowledgment messages.</span></span>  
  
7.  <span data-ttu-id="7b69f-118">BTAHL7 envoie chaque message via un autre port d’envoi MLLP à la destination spécifiée dans son champ MSH5.</span><span class="sxs-lookup"><span data-stu-id="7b69f-118">BTAHL7 sends each message through another MLLP send port to the destination specified in its MSH5 field.</span></span>  
  
8.  <span data-ttu-id="7b69f-119">Le tiers de destination envoie à BTAHL7 une acceptation d’accusé de réception pour chaque message qu’il a reçu d’application.</span><span class="sxs-lookup"><span data-stu-id="7b69f-119">The destination party sends to BTAHL7 an application-accept acknowledgment for each message that it received.</span></span>  
  
9. <span data-ttu-id="7b69f-120">Le moteur de l’Interface reçoit chaque accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="7b69f-120">The Interface Engine receives each acknowledgment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b69f-121">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7b69f-121">In This Section</span></span>  
  
-   [<span data-ttu-id="7b69f-122">Étape 1 : Ajouter des schémas d’en-tête et d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="7b69f-122">Step 1: Add Header and Acknowledgment Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-add-header-and-acknowledgment-schemas.md)  
  
-   [<span data-ttu-id="7b69f-123">Étape 2 : Ajouter des schémas courants pour v2.3.1</span><span class="sxs-lookup"><span data-stu-id="7b69f-123">Step 2: Add Common Schemas for v2.3.1</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-add-common-schemas-for-v2-3-1.md)  
  
-   [<span data-ttu-id="7b69f-124">Étape 3 : Ajouter un schéma d’événement (Message) de déclencheur</span><span class="sxs-lookup"><span data-stu-id="7b69f-124">Step 3: Add a Trigger Event (Message) Schema</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md)  
  
-   [<span data-ttu-id="7b69f-125">Étape 4 : Créer un Port de réception pour accepter le Message du lot</span><span class="sxs-lookup"><span data-stu-id="7b69f-125">Step 4: Create a Receive Port for Accepting the Batch Message</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md)  
  
-   [<span data-ttu-id="7b69f-126">Étape 5 : Créer un Port d’envoi pour remettre des Messages</span><span class="sxs-lookup"><span data-stu-id="7b69f-126">Step 5: Create a Send Port to Deliver Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-create-a-send-port-to-deliver-messages.md)  
  
-   [<span data-ttu-id="7b69f-127">Étape 6 : Créer un Port d’envoi pour remettre les accusés de réception</span><span class="sxs-lookup"><span data-stu-id="7b69f-127">Step 6: Create a Send Port to Deliver Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-acknowledgments.md)  
  
-   [<span data-ttu-id="7b69f-128">Étape 7 : Créer et configurer une partie de la Source</span><span class="sxs-lookup"><span data-stu-id="7b69f-128">Step 7: Create and Configure a Source Party</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md)  
  
-   [<span data-ttu-id="7b69f-129">Étape 8 : Redémarrer BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7b69f-129">Step 8: Restart BizTalk Server</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-8-restart-biztalk-server.md)  
  
-   [<span data-ttu-id="7b69f-130">Étape 9 : Vérifier que le scénario par lot entrant fragmentés</span><span class="sxs-lookup"><span data-stu-id="7b69f-130">Step 9: Verify the Fragmented Inbound Batch Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-9-verify-the-fragmented-inbound-batch-scenario.md)