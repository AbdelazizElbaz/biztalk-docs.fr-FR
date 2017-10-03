---
title: "Didacticiel 2 : EDI Interface Developer Tutorial | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d10fb650-cbb9-41e5-a80d-06afd0513814
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9cb84454d2570ae6833847b598b55af6cf7777e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-2-edi-interface-developer-tutorial"></a><span data-ttu-id="abe71-102">Didacticiel 2 : EDI Interface Developer Tutorial.</span><span class="sxs-lookup"><span data-stu-id="abe71-102">Tutorial 2: EDI Interface Developer Tutorial</span></span>
<span data-ttu-id="abe71-103">Ce didacticiel décrit l'utilisation de la fonctionnalité EDI dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le cadre d'un scénario pour développeur d'interface.</span><span class="sxs-lookup"><span data-stu-id="abe71-103">This tutorial demonstrates how to use the EDI functionality in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in an Interface Developer scenario.</span></span>  
  
 <span data-ttu-id="abe71-104">**Scénario du didacticiel**</span><span class="sxs-lookup"><span data-stu-id="abe71-104">**Tutorial Scenario**</span></span>  
  
 <span data-ttu-id="abe71-105">Votre partenaire commercial envoie des bons de commande à votre entreprise à l'aide du document informatisé 850 ANSI X12 Version 4010 (message 850).</span><span class="sxs-lookup"><span data-stu-id="abe71-105">In this scenario, your trading partner sends Purchase Orders to your company using the ANSI X12 Version 4010 850 Transaction Set (an 850 message).</span></span> <span data-ttu-id="abe71-106">Votre entreprise utilise une application interne (OrderSystem) pour traiter les bons de commande.</span><span class="sxs-lookup"><span data-stu-id="abe71-106">Your company uses an internal application, the Order System, to process purchase orders.</span></span>  
  
 <span data-ttu-id="abe71-107">Développeur d'interface, vous êtes un responsable de la conception de l'interface entre le message 850 reçu de votre partenaire commercial et le système OrderSystem interne de votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="abe71-107">You are an interface developer responsible for designing the interface between the 850 message you receive from your trading partner and your company’s internal Order System.</span></span> <span data-ttu-id="abe71-108">Votre partenaire commercial requiert un accusé de réception fonctionnel (997) pour chaque message 850 qu'il envoie.</span><span class="sxs-lookup"><span data-stu-id="abe71-108">Your trading partner requires a Functional Acknowledgement (997) for each 850 message it sends.</span></span>  
  
 <span data-ttu-id="abe71-109">Pour faciliter la compréhension des références, les identificateurs suivants sont utilisés :</span><span class="sxs-lookup"><span data-stu-id="abe71-109">For ease of reference, the following identifiers are used:</span></span>  
  
|<span data-ttu-id="abe71-110">Entité</span><span class="sxs-lookup"><span data-stu-id="abe71-110">Entity</span></span>|<span data-ttu-id="abe71-111">Identificateur</span><span class="sxs-lookup"><span data-stu-id="abe71-111">Identifier</span></span>|  
|------------|----------------|  
|<span data-ttu-id="abe71-112">Votre entreprise</span><span class="sxs-lookup"><span data-stu-id="abe71-112">Your company</span></span>|<span data-ttu-id="abe71-113">OrderSystem</span><span class="sxs-lookup"><span data-stu-id="abe71-113">OrderSystem</span></span>|  
|<span data-ttu-id="abe71-114">Votre partenaire commercial</span><span class="sxs-lookup"><span data-stu-id="abe71-114">Your trading partner</span></span>|<span data-ttu-id="abe71-115">Fabrikam</span><span class="sxs-lookup"><span data-stu-id="abe71-115">Fabrikam</span></span>|  
  
 <span data-ttu-id="abe71-116">Le flux de messages de la solution terminée ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="abe71-116">The message flow in the completed solution will be as follows:</span></span>  
  
 <span data-ttu-id="abe71-117">![Flux de messages EDI Interface Developer Tutorial](../core/media/4944352a-dc77-47f1-a324-bf71444670c5.gif "4944352a-dc77-47f1-a324-bf71444670c5")</span><span class="sxs-lookup"><span data-stu-id="abe71-117">![EDI Interface Developer Tutorial message flow](../core/media/4944352a-dc77-47f1-a324-bf71444670c5.gif "4944352a-dc77-47f1-a324-bf71444670c5")</span></span>  
  
 <span data-ttu-id="abe71-118">**Flux de messages**</span><span class="sxs-lookup"><span data-stu-id="abe71-118">**Message Flow**</span></span>  
  
 <span data-ttu-id="abe71-119">La solution de ce didacticiel effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="abe71-119">The solution in this tutorial will do the following:</span></span>  
  
1.  <span data-ttu-id="abe71-120">réception d'un échange de fichier plat de la part du partenaire commercial Fabrikam ;</span><span class="sxs-lookup"><span data-stu-id="abe71-120">Receive a flat-file interchange from the trading partner Fabrikam.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="abe71-121">Les événements dans cette liste peuvent se produire dans un ordre différent de celui indiqué.</span><span class="sxs-lookup"><span data-stu-id="abe71-121">The events in this list may not occur in the order shown.</span></span>  
  
2.  <span data-ttu-id="abe71-122">validation de l'échange EDI selon son schéma, désassemblage du message en XML, puis déplacement du message XML dans la base de données MessageBox ;</span><span class="sxs-lookup"><span data-stu-id="abe71-122">Validate the EDI interchange against its schema, disassemble the message into XML, and drop the message XML into the MessageBox.</span></span>  
  
3.  <span data-ttu-id="abe71-123">génération d'un accusé de réception 997 vers l'échange EDI reçu, puis déplacement dans la base de données MessageBox ;</span><span class="sxs-lookup"><span data-stu-id="abe71-123">Generate a 997 acknowledgment to the received EDI interchange, and drop it in the MessageBox.</span></span>  
  
4.  <span data-ttu-id="abe71-124">récupération du message 997 XML par un port d'envoi unidirectionnel, puis assemblage de l'échange du message 997 EDI ;</span><span class="sxs-lookup"><span data-stu-id="abe71-124">Pick up the 997 XML by a one-way send port, and assemble the 997 EDI interchange.</span></span>  
  
5.  <span data-ttu-id="abe71-125">envoi de l'échange 997 à Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="abe71-125">Send the 997 interchange to Fabrikam.</span></span>  
  
6.  <span data-ttu-id="abe71-126">Récupération du XML de message par un port d’envoi unidirectionnel, puis assemblage de l’échange du message EDI.</span><span class="sxs-lookup"><span data-stu-id="abe71-126">Pick up the Msg XML by a one-way send port, and assemble the message EDI interchange.</span></span>  
  
7.  <span data-ttu-id="abe71-127">envoi de l'échange EDI à OrderSystem.</span><span class="sxs-lookup"><span data-stu-id="abe71-127">Send the EDI interchange to OrderSystem.</span></span>  
  
 <span data-ttu-id="abe71-128">**Configuration**</span><span class="sxs-lookup"><span data-stu-id="abe71-128">**Configuration**</span></span>  
  
 <span data-ttu-id="abe71-129">Dans ce didacticiel, vous allez effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="abe71-129">In this tutorial, you will do the following:</span></span>  
  
-   <span data-ttu-id="abe71-130">configuration de BizTalk pour attendre le message 850 de votre partenaire commercial et renvoyer un accusé de réception 997 ;</span><span class="sxs-lookup"><span data-stu-id="abe71-130">Configure BizTalk to expect the 850 message from your trading partner and to send back a 997 acknowledgment</span></span>  
  
-   <span data-ttu-id="abe71-131">utilisation d'un mappage BizTalk pour convertir les données du message 850 au format requis par le système de commande (OrderSystem).</span><span class="sxs-lookup"><span data-stu-id="abe71-131">Use a BizTalk map to convert the 850 message data into the format required by the Order System.</span></span> <span data-ttu-id="abe71-132">Ce mappage est inclus dans les fichiers de didacticiel dans le Kit de développement logiciel (SDK) de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;</span><span class="sxs-lookup"><span data-stu-id="abe71-132">This map is provided in the tutorial files in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK.</span></span>  
  
-   <span data-ttu-id="abe71-133">configuration d'un port de réception pour la réception du message 850 ;</span><span class="sxs-lookup"><span data-stu-id="abe71-133">Configure a receive port for receiving the 850 message.</span></span>  
  
-   <span data-ttu-id="abe71-134">configuration d'un port d'envoi pour l'envoi du message 850 à OrderSystem au format approprié ;</span><span class="sxs-lookup"><span data-stu-id="abe71-134">Configure a send port to send the 850 message to OrderSystem in the correct format.</span></span>  
  
-   <span data-ttu-id="abe71-135">configuration d'un port d'envoi pour l'abonnement à l'accusé de réception 997 généré par BizTalk et acheminé en réponse au partenaire commercial, Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="abe71-135">Configure a send port to subscribe to the BizTalk-generated 997 acknowledgment for routing back to the trading partner, Fabrikam.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="abe71-136">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="abe71-136">In This Section</span></span>  
  
-   [<span data-ttu-id="abe71-137">Étape 1 : Préparer le didacticiel pour développeur d’Interface EDI</span><span class="sxs-lookup"><span data-stu-id="abe71-137">Step 1: Prepare for the EDI Interface Developer Tutorial</span></span>](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)  
  
-   [<span data-ttu-id="abe71-138">Étape 2 : Mettre à jour et déployer la Solution du didacticiel</span><span class="sxs-lookup"><span data-stu-id="abe71-138">Step 2: Update and Deploy the Tutorial Solution</span></span>](../core/step-2-update-and-deploy-the-tutorial-solution.md)  
  
-   [<span data-ttu-id="abe71-139">Étape 3 : Configurer un tiers et un profil d’entreprise pour votre organisation</span><span class="sxs-lookup"><span data-stu-id="abe71-139">Step 3: Configure a Party and Business Profile for Your Organization</span></span>](../core/step-3-configure-a-party-and-business-profile-for-your-organization1.md)  
  
-   [<span data-ttu-id="abe71-140">Étape 4 : Configurer un tiers et un profil d’entreprise pour votre partenaire commercial</span><span class="sxs-lookup"><span data-stu-id="abe71-140">Step 4: Configure a Party and Business Profile for Your Trading Partner</span></span>](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner1.md)  
  
-   [<span data-ttu-id="abe71-141">Étape 5 : Configurer un Port de réception et l’emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="abe71-141">Step 5: Configure a Receive Port and Receive Location</span></span>](../core/step-5-configure-a-receive-port-and-receive-location.md)  
  
-   [<span data-ttu-id="abe71-142">Étape 6 : Configurer un Port d’envoi pour envoyer des données à votre organisation</span><span class="sxs-lookup"><span data-stu-id="abe71-142">Step 6: Configure a Send Port to Send Data to Your Organization</span></span>](../core/step-6-configure-a-send-port-to-send-data-to-your-organization.md)  
  
-   [<span data-ttu-id="abe71-143">Étape 7 : Configurer un Port d’envoi pour envoyer l’accusé de réception à votre partenaire commercial</span><span class="sxs-lookup"><span data-stu-id="abe71-143">Step 7: Configure a Send Port to Send the Acknowledgment to Your Trading Partner</span></span>](../core/step-7-configure-a-send-port-to-send-the-acknowledgment-to-trading-partner.md)  
  
-   [<span data-ttu-id="abe71-144">Étape 8 : Configurer l’accord de partenariat commercial entre les Parties</span><span class="sxs-lookup"><span data-stu-id="abe71-144">Step 8: Configure the Trading Partner Agreement between the Parties</span></span>](../core/step-8-configure-the-trading-partner-agreement-between-the-parties.md)  
  
-   [<span data-ttu-id="abe71-145">Étape 9 : Tester la Solution EDI</span><span class="sxs-lookup"><span data-stu-id="abe71-145">Step 9: Test the EDI Solution</span></span>](../core/step-9-test-the-edi-solution.md)  
  
## <a name="see-also"></a><span data-ttu-id="abe71-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abe71-146">See Also</span></span>  
 [<span data-ttu-id="abe71-147">Didacticiels de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="abe71-147">BizTalk Server Tutorials</span></span>](../core/biztalk-server-tutorials.md)