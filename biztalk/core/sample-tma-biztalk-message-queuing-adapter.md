---
title: "Exemple TMA : Adaptateur de file d’attente de Message BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security examples [TMA], MSMQ adapters
- architecture, examples
- MSMQ adapters, TMA
- DFD, MSMQ adapters
- MSMQ adapters, data flow
ms.assetid: 15b4a540-2fcd-4668-b4b4-757f23ebd83e
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91f37c57c24bdd37c0f2cc0399a797050228aa54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-tma-biztalk-message-queuing-adapter"></a><span data-ttu-id="e8a65-102">Exemple de menaces : Adaptateur Message Queuing BizTalk</span><span class="sxs-lookup"><span data-stu-id="e8a65-102">Sample TMA: BizTalk Message Queuing Adapter</span></span>
<span data-ttu-id="e8a65-103">Cette rubrique présente l'analyse du modèle des menaces pour le scénario de l'adaptateur de Message Queuing BizTalk dans un exemple d'architecture.</span><span class="sxs-lookup"><span data-stu-id="e8a65-103">This topic presents the threat model analysis (TMA) for the BizTalk Message Queuing adapter scenario for the sample architecture.</span></span>  
  
## <a name="step-1-collect-background-information-biztalk-message-queuing-adapter-scenario"></a><span data-ttu-id="e8a65-104">Étape 1.</span><span class="sxs-lookup"><span data-stu-id="e8a65-104">Step 1.</span></span> <span data-ttu-id="e8a65-105">Collecter des informations générales (scénario Message Queuing BizTalk adaptateur)</span><span class="sxs-lookup"><span data-stu-id="e8a65-105">Collect Background Information (BizTalk Message Queuing Adapter Scenario)</span></span>  
 <span data-ttu-id="e8a65-106">Cette section présente le diagramme de flux de données pour le scénario de l'adaptateur de Message Queuing BizTalk dans un exemple d'architecture.</span><span class="sxs-lookup"><span data-stu-id="e8a65-106">This section provides the data flow diagram (DFD) for the BizTalk Message Queuing adapter scenario for the sample architecture.</span></span> <span data-ttu-id="e8a65-107">La figure suivante illustre l'exemple d'architecture pour le scénario des adaptateurs HTTP et SOAP.</span><span class="sxs-lookup"><span data-stu-id="e8a65-107">The following figure shows the sample architecture for the HTTP and SOAP adapters scenario.</span></span>  
  
 <span data-ttu-id="e8a65-108">**Figure 1 exemple d’architecture pour le scénario de l’adaptateur BizTalk Message Queuing**</span><span class="sxs-lookup"><span data-stu-id="e8a65-108">**Figure 1 Sample architecture for the BizTalk Message Queuing adapter scenario**</span></span>  
  
 <span data-ttu-id="e8a65-109">![Exemple d’architecture pour Message Queuing BizTalk](../core/media/tdi-sec-refarch-msmq.gif "TDI_Sec_RefArch_MSMQ")</span><span class="sxs-lookup"><span data-stu-id="e8a65-109">![Sample architecture for BizTalk Message Queuing](../core/media/tdi-sec-refarch-msmq.gif "TDI_Sec_RefArch_MSMQ")</span></span>  
  
 <span data-ttu-id="e8a65-110">Toutes les autres informations d’arrière-plan est le même pour tous nos scénarios d’utilisation et est décrite précédemment dans [informations générales relatives aux exemples de scénarios](../core/background-information-for-sample-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="e8a65-110">All the other background information is the same for all our usage scenarios, and is described previously in [Background Information for Sample Scenarios](../core/background-information-for-sample-scenarios.md).</span></span>  
  
### <a name="data-flow-diagram"></a><span data-ttu-id="e8a65-111">Diagramme de flux de données</span><span class="sxs-lookup"><span data-stu-id="e8a65-111">Data Flow Diagram</span></span>  
 <span data-ttu-id="e8a65-112">La figure suivante illustre le diagramme de flux de données pour l'exemple d'architecture lors de l'utilisation de l'adaptateur de Message Queuing BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e8a65-112">The following figure shows the DFD for the sample architecture when you use the BizTalk Message Queuing adapter.</span></span>  
  
 <span data-ttu-id="e8a65-113">**Figure 2 DFD pour l’exemple d’architecture du scénario de l’adaptateur de Message Queuing BizTalk**</span><span class="sxs-lookup"><span data-stu-id="e8a65-113">**Figure 2 DFD for the sample architecture of the BizTalk Message Queuing adapter scenario**</span></span>  
  
 <span data-ttu-id="e8a65-114">![Exemple d’architecture pour Message Queuing BizTalk](../core/media/tdi-sec-refarch-dfd-msmq.gif "TDI_Sec_RefArch_DFD_MSMQ")</span><span class="sxs-lookup"><span data-stu-id="e8a65-114">![Sample architecture for BizTalk Message Queuing](../core/media/tdi-sec-refarch-dfd-msmq.gif "TDI_Sec_RefArch_DFD_MSMQ")</span></span>  
  
 <span data-ttu-id="e8a65-115">Le flux de données est le suivant :</span><span class="sxs-lookup"><span data-stu-id="e8a65-115">The data flow is as follows:</span></span>  
  
1.  <span data-ttu-id="e8a65-116">Un partenaire envoie un message à l'aide de Message Queuing ou de Message Queuing BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e8a65-116">A partner sends a message using Message Queuing or BizTalk Message Queuing.</span></span> <span data-ttu-id="e8a65-117">Le message est converti au format approprié et envoyé sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="e8a65-117">The message is packed in the appropriate format and sent on the network.</span></span> <span data-ttu-id="e8a65-118">Si vous utilisez Active Directory, le message passe par une série de routeurs Message Queuing jusqu'à atteindre la bonne destination (le serveur BizTalk qui exécute une instance de l'hôte de l'adaptateur de réception Message Queuing BizTalk).</span><span class="sxs-lookup"><span data-stu-id="e8a65-118">If you use Active Directory, the message goes through a series of Message Queuing routers until it reaches the right destination (the BizTalk Server that runs a host instance of the BizTalk Message Queuing receive adapter).</span></span>  
  
2.  <span data-ttu-id="e8a65-119">Une instance d'un hôte In-process pour l'adaptateur de réception Message Queuing BizTalk reçoit régulièrement le message d'un routeur Message Queuing (à travers le pare-feu 2), effectue un traitement initial, envoie les réponses correctes du réseau, comme défini par le protocole réseau, puis place le message dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="e8a65-119">An instance of an in-process host for the BizTalk Message Queuing receive adapter regularly receives the message from a Message Queuing router (through Firewall 2), does any initial processing, sends the correct network responses as defined by the network protocol, and puts the message in the MessageBox database.</span></span>  
  
3.  <span data-ttu-id="e8a65-120">Une instance de l'hôte de traitement, qui a un abonnement au message, le récupère dans la base de données MessageBox, effectue un traitement supplémentaire, puis replace le message dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="e8a65-120">An instance of the processing host that has a subscription to the message picks it up from the MessageBox database, does any additional processing, and puts the message back in the MessageBox database.</span></span>  
  
4.  <span data-ttu-id="e8a65-121">Une instance de l'hôte In-process, qui a un adaptateur d'envoi Message Queuing BizTalk, récupère le message dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="e8a65-121">An instance of the in-process host that has a BizTalk Message Queuing send adapter picks up the message from the MessageBox database.</span></span> <span data-ttu-id="e8a65-122">Le message passe par un traitement final dans le pipeline d'envoi, puis est envoyé, à travers le pare-feu 2, sur le réseau au partenaire ou à l'application.</span><span class="sxs-lookup"><span data-stu-id="e8a65-122">The message goes through any final processing in the send pipeline, and is then sent through Firewall 2 over the network to the partner or application.</span></span>  
  
## <a name="step-2-create-and-analyze-the-threat-model-biztalk-message-queuing-adapter-scenario"></a><span data-ttu-id="e8a65-123">Étape 2.</span><span class="sxs-lookup"><span data-stu-id="e8a65-123">Step 2.</span></span> <span data-ttu-id="e8a65-124">Créer et analyser le modèle des menaces (scénario Message Queuing BizTalk adaptateur)</span><span class="sxs-lookup"><span data-stu-id="e8a65-124">Create and Analyze the Threat Model (BizTalk Message Queuing Adapter Scenario)</span></span>  
 <span data-ttu-id="e8a65-125">Cette section présente les résultats de l'analyse du modèle des menaces pour le scénario de l'adaptateur de Message Queuing BizTalk dans un exemple d'architecture.</span><span class="sxs-lookup"><span data-stu-id="e8a65-125">This section provides the results of the TMA we did for the BizTalk Message Queuing adapter scenario for the sample architecture.</span></span>  
  
-   <span data-ttu-id="e8a65-126">**Identifier les Points d’entrée, les limites de confiance et les flux de données -** consultez les informations générales décrites précédemment à l’étape 1 et dans [informations générales relatives aux exemples de scénarios](../core/background-information-for-sample-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="e8a65-126">**Identify Entry Points, Trust Boundaries, and Flow of Data -** See background information described earlier in step 1 and in [Background Information for Sample Scenarios](../core/background-information-for-sample-scenarios.md).</span></span>  
  
-   <span data-ttu-id="e8a65-127">**Créer une liste des menaces identifiées -** nous avons utilisé la catégorisation suivante pour toutes les entrées du diagramme pour identifier les menaces potentielles pour le scénario : **S**urpation identifier, **T** ion des données, **R**épudiation, **I**la divulgation d’informations, **D**éni de service, et **E**lévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="e8a65-127">**Create a List of the Identified Threats -** We used the following categorization for all entries in the DFD to identify potential threats to the scenario: **S**poofing identify, **T**ampering with data, **R**epudiation, **I**nformation disclosure, **D**enial of service, and **E**levation of privileges.</span></span> <span data-ttu-id="e8a65-128">Le tableau suivant répertorie les menaces que nous avons identifiées lorsque vous utilisez l'adaptateur de Message Queuing BizTalk pour envoyer et recevoir des messages à et de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e8a65-128">The following table lists the threats we identified when you use the BizTalk Message Queuing adapter to send and receive messages to and from BizTalk Server.</span></span>  
  
 <span data-ttu-id="e8a65-129">**Tableau 1 liste des menaces identifiées**</span><span class="sxs-lookup"><span data-stu-id="e8a65-129">**Table 1 List of identified threats**</span></span>  
  
|<span data-ttu-id="e8a65-130">Menace</span><span class="sxs-lookup"><span data-stu-id="e8a65-130">Threat</span></span>|<span data-ttu-id="e8a65-131"> Description</span><span class="sxs-lookup"><span data-stu-id="e8a65-131">Description</span></span>|<span data-ttu-id="e8a65-132">Actif</span><span class="sxs-lookup"><span data-stu-id="e8a65-132">Asset</span></span>|<span data-ttu-id="e8a65-133">Impact</span><span class="sxs-lookup"><span data-stu-id="e8a65-133">Impact</span></span>|  
|------------|-----------------|-----------|------------|  
|<span data-ttu-id="e8a65-134">Envoi d'un grand nombre de messages à l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="e8a65-134">Send lots of messages to receive location</span></span>|<span data-ttu-id="e8a65-135">Un utilisateur malveillant peut envoyer un grand nombre de messages valides ou non valides et inonder l'application.</span><span class="sxs-lookup"><span data-stu-id="e8a65-135">A malicious user can send a large number of valid or invalid messages and flood the application.</span></span>|<span data-ttu-id="e8a65-136">Environnement BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e8a65-136">BizTalk Server environment</span></span>|<span data-ttu-id="e8a65-137">Déni de service</span><span class="sxs-lookup"><span data-stu-id="e8a65-137">Denial of service</span></span>|  
|<span data-ttu-id="e8a65-138">L'en-tête du message transite en texte clair.</span><span class="sxs-lookup"><span data-stu-id="e8a65-138">Message header travels in the clear on the wire</span></span>|<span data-ttu-id="e8a65-139">Comme le message transite de la file d'attente à l'adaptateur de réception Message Queuing BizTalk, l'en-tête du message est en texte clair et un utilisateur malveillant peut lire et falsifier l'en-tête.</span><span class="sxs-lookup"><span data-stu-id="e8a65-139">As the message travels from the queue to the BizTalk Message Queuing receive adapter, the message header is in the clear, and a malicious user can potentially read and tamper with the header.</span></span>|<span data-ttu-id="e8a65-140">En-tête du message</span><span class="sxs-lookup"><span data-stu-id="e8a65-140">Message header</span></span>|<span data-ttu-id="e8a65-141">Falsification de données</span><span class="sxs-lookup"><span data-stu-id="e8a65-141">Tampering with data</span></span><br /><br /> <span data-ttu-id="e8a65-142">Divulgation d'informations</span><span class="sxs-lookup"><span data-stu-id="e8a65-142">Information disclosure</span></span>|  
|<span data-ttu-id="e8a65-143">Un utilisateur non autorisé peut établir une connexion réseau au serveur BizTalk qui exécute l'hôte Message Queuing BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e8a65-143">An unauthorized user can make a network connection to the BizTalk Server that runs the BizTalk Message Queuing host</span></span>|<span data-ttu-id="e8a65-144">Vous ne pouvez pas utiliser de liste de contrôle d'accès discrétionnaire pour limiter l'accès à l'emplacement de réception Message Queuing BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e8a65-144">You cannot use a discretionary access list (DACL) to restrict access to the BizTalk Message Queuing receive location.</span></span> <span data-ttu-id="e8a65-145">Par conséquent, toute personne pouvant établir une connexion réseau au serveur BizTalk qui exécute une instance de l'hôte de l'adaptateur de réception Message Queuing BizTalk et au port 1801 peut envoyer des messages à l'emplacement de réception Message Queuing BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e8a65-145">Therefore, anyone that can make a network connection to the BizTalk Server that runs a host instance of the BizTalk Message Queuing receive adapter and to port 1801 can send messages to the BizTalk Message Queuing receive location.</span></span>|<span data-ttu-id="e8a65-146">Environnement BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e8a65-146">BizTalk Server environment</span></span>|<span data-ttu-id="e8a65-147">Répudiation</span><span class="sxs-lookup"><span data-stu-id="e8a65-147">Repudiation</span></span><br /><br /> <span data-ttu-id="e8a65-148">Falsification de données</span><span class="sxs-lookup"><span data-stu-id="e8a65-148">Tampering with data</span></span><br /><br /> <span data-ttu-id="e8a65-149">Divulgation d'informations</span><span class="sxs-lookup"><span data-stu-id="e8a65-149">Information disclosure</span></span><br /><br /> <span data-ttu-id="e8a65-150">Déni de service</span><span class="sxs-lookup"><span data-stu-id="e8a65-150">Denial of service</span></span><br /><br /> <span data-ttu-id="e8a65-151">Élévation de privilèges</span><span class="sxs-lookup"><span data-stu-id="e8a65-151">Elevation of privileges</span></span>|  
|<span data-ttu-id="e8a65-152">Un utilisateur malveillant peut falsifier le message avant que BizTalk Server ne le reçoive.</span><span class="sxs-lookup"><span data-stu-id="e8a65-152">A malicious user can tamper with the message before BizTalk Server receives it</span></span>|<span data-ttu-id="e8a65-153">Un utilisateur malveillant peut intercepter le message lorsqu'il transite et le modifier.</span><span class="sxs-lookup"><span data-stu-id="e8a65-153">A malicious user can intercept the message while it is in transit and modify it.</span></span>|<span data-ttu-id="e8a65-154">Corps du message</span><span class="sxs-lookup"><span data-stu-id="e8a65-154">Message body</span></span>|<span data-ttu-id="e8a65-155">Falsification de données</span><span class="sxs-lookup"><span data-stu-id="e8a65-155">Tampering with data</span></span><br /><br /> <span data-ttu-id="e8a65-156">Divulgation d'informations</span><span class="sxs-lookup"><span data-stu-id="e8a65-156">Information disclosure</span></span>|  
  
## <a name="step-3-review-threats-biztalk-message-queuing-adapter-scenario"></a><span data-ttu-id="e8a65-157">Étape 3.</span><span class="sxs-lookup"><span data-stu-id="e8a65-157">Step 3.</span></span> <span data-ttu-id="e8a65-158">Examen des menaces (scénario Message Queuing BizTalk adaptateur)</span><span class="sxs-lookup"><span data-stu-id="e8a65-158">Review Threats (BizTalk Message Queuing Adapter Scenario)</span></span>  
 <span data-ttu-id="e8a65-159">Cette section présente les résultats de l'analyse des risques réalisée sur les menaces identifiées pour le scénario de l'adaptateur de Message Queuing BizTalk dans un exemple d'architecture.</span><span class="sxs-lookup"><span data-stu-id="e8a65-159">This section provides the results of the risk analysis we did for threats we identified for the BizTalk Message Queuing adapter scenario for the sample architecture.</span></span> <span data-ttu-id="e8a65-160">Après la principale menace réunion sur le modèle, nous avons passé en revue les menaces et les catégories d’impact suivants permettent d’identifier les risques pour chaque menace : **D**égâts potentiels, **R**eproductibilité, **E**xploitabilité, **A**tteinte des utilisateurs et **D**étectabilité.</span><span class="sxs-lookup"><span data-stu-id="e8a65-160">After the main threat model meeting, we reviewed the threats and used the following impact categories to identify the risk for each threat: **D**amage potential, **R**eproducibility, **E**xploitability, **A**ffected users, and **D**iscoverability.</span></span>  
  
 <span data-ttu-id="e8a65-161">Le tableau suivant répertorie les degrés de risque pour les menaces que nous avons identifiées lorsque vous utilisez l'adaptateur de Message Queuing BizTalk pour envoyer et recevoir des messages à et de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e8a65-161">The following table lists the risk ratings for the threats we identified when you use the BizTalk Message Queuing adapter to send and receive messages to and from BizTalk Server.</span></span>  
  
 <span data-ttu-id="e8a65-162">**Tableau 2 degrés de risque pour les menaces identifiées**</span><span class="sxs-lookup"><span data-stu-id="e8a65-162">**Table 2 Risk ratings for identified threats**</span></span>  
  
|<span data-ttu-id="e8a65-163">Menace</span><span class="sxs-lookup"><span data-stu-id="e8a65-163">Threat</span></span>|<span data-ttu-id="e8a65-164">Impact</span><span class="sxs-lookup"><span data-stu-id="e8a65-164">Impact</span></span>|<span data-ttu-id="e8a65-165">Dégâts potentiels</span><span class="sxs-lookup"><span data-stu-id="e8a65-165">Damage potential</span></span>|<span data-ttu-id="e8a65-166">Reproductibilité</span><span class="sxs-lookup"><span data-stu-id="e8a65-166">Reproducibility</span></span>|<span data-ttu-id="e8a65-167">Exploitabilité</span><span class="sxs-lookup"><span data-stu-id="e8a65-167">Exploitability</span></span>|<span data-ttu-id="e8a65-168">Atteinte des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="e8a65-168">Affected users</span></span>|<span data-ttu-id="e8a65-169">Détectabilité</span><span class="sxs-lookup"><span data-stu-id="e8a65-169">Discoverability</span></span>|<span data-ttu-id="e8a65-170">Exposition au risque</span><span class="sxs-lookup"><span data-stu-id="e8a65-170">Risk exposure</span></span>|  
|------------|------------|----------------------|---------------------|--------------------|--------------------|---------------------|-------------------|  
|<span data-ttu-id="e8a65-171">Envoi d'un grand nombre de messages à l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="e8a65-171">Send lots of messages to receive location</span></span>|<span data-ttu-id="e8a65-172">Déni de service</span><span class="sxs-lookup"><span data-stu-id="e8a65-172">Denial of service</span></span>|<span data-ttu-id="e8a65-173">8</span><span class="sxs-lookup"><span data-stu-id="e8a65-173">8</span></span>|<span data-ttu-id="e8a65-174">7</span><span class="sxs-lookup"><span data-stu-id="e8a65-174">7</span></span>|<span data-ttu-id="e8a65-175">7</span><span class="sxs-lookup"><span data-stu-id="e8a65-175">7</span></span>|<span data-ttu-id="e8a65-176">7</span><span class="sxs-lookup"><span data-stu-id="e8a65-176">7</span></span>|<span data-ttu-id="e8a65-177">5</span><span class="sxs-lookup"><span data-stu-id="e8a65-177">5</span></span>|<span data-ttu-id="e8a65-178">6.8</span><span class="sxs-lookup"><span data-stu-id="e8a65-178">6.8</span></span>|  
|<span data-ttu-id="e8a65-179">L'en-tête du message transite en texte clair.</span><span class="sxs-lookup"><span data-stu-id="e8a65-179">Message header travels in the clear on the wire</span></span>|<span data-ttu-id="e8a65-180">Falsification de données</span><span class="sxs-lookup"><span data-stu-id="e8a65-180">Tampering with data</span></span><br /><br /> <span data-ttu-id="e8a65-181">Divulgation d'informations</span><span class="sxs-lookup"><span data-stu-id="e8a65-181">Information disclosure</span></span>|<span data-ttu-id="e8a65-182">8</span><span class="sxs-lookup"><span data-stu-id="e8a65-182">8</span></span>|<span data-ttu-id="e8a65-183">10</span><span class="sxs-lookup"><span data-stu-id="e8a65-183">10</span></span>|<span data-ttu-id="e8a65-184">8</span><span class="sxs-lookup"><span data-stu-id="e8a65-184">8</span></span>|<span data-ttu-id="e8a65-185">3</span><span class="sxs-lookup"><span data-stu-id="e8a65-185">3</span></span>|<span data-ttu-id="e8a65-186">5</span><span class="sxs-lookup"><span data-stu-id="e8a65-186">5</span></span>|<span data-ttu-id="e8a65-187">6.8</span><span class="sxs-lookup"><span data-stu-id="e8a65-187">6.8</span></span>|  
|<span data-ttu-id="e8a65-188">Un utilisateur non autorisé peut établir une connexion réseau au serveur BizTalk qui exécute l'hôte Message Queuing BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e8a65-188">An unauthorized user can make a network connection to the BizTalk Server that runs the BizTalk Message Queuing host</span></span>|<span data-ttu-id="e8a65-189">Répudiation</span><span class="sxs-lookup"><span data-stu-id="e8a65-189">Repudiation</span></span><br /><br /> <span data-ttu-id="e8a65-190">Falsification de données</span><span class="sxs-lookup"><span data-stu-id="e8a65-190">Tampering with data</span></span><br /><br /> <span data-ttu-id="e8a65-191">Divulgation d'informations</span><span class="sxs-lookup"><span data-stu-id="e8a65-191">Information disclosure</span></span><br /><br /> <span data-ttu-id="e8a65-192">Déni de service</span><span class="sxs-lookup"><span data-stu-id="e8a65-192">Denial of service</span></span><br /><br /> <span data-ttu-id="e8a65-193">Élévation de privilèges</span><span class="sxs-lookup"><span data-stu-id="e8a65-193">Elevation of privileges</span></span>|<span data-ttu-id="e8a65-194">8</span><span class="sxs-lookup"><span data-stu-id="e8a65-194">8</span></span>|<span data-ttu-id="e8a65-195">10</span><span class="sxs-lookup"><span data-stu-id="e8a65-195">10</span></span>|<span data-ttu-id="e8a65-196">9</span><span class="sxs-lookup"><span data-stu-id="e8a65-196">9</span></span>|<span data-ttu-id="e8a65-197">9</span><span class="sxs-lookup"><span data-stu-id="e8a65-197">9</span></span>|<span data-ttu-id="e8a65-198">9</span><span class="sxs-lookup"><span data-stu-id="e8a65-198">9</span></span>|<span data-ttu-id="e8a65-199">9</span><span class="sxs-lookup"><span data-stu-id="e8a65-199">9</span></span>|  
|<span data-ttu-id="e8a65-200">Un utilisateur malveillant peut falsifier le message avant que BizTalk Server ne le reçoive.</span><span class="sxs-lookup"><span data-stu-id="e8a65-200">A malicious user can tamper with the message before BizTalk Server receives it</span></span>|<span data-ttu-id="e8a65-201">Falsification de données</span><span class="sxs-lookup"><span data-stu-id="e8a65-201">Tampering with data</span></span><br /><br /> <span data-ttu-id="e8a65-202">Divulgation d'informations</span><span class="sxs-lookup"><span data-stu-id="e8a65-202">Information disclosure</span></span>|<span data-ttu-id="e8a65-203">5</span><span class="sxs-lookup"><span data-stu-id="e8a65-203">5</span></span>|<span data-ttu-id="e8a65-204">7</span><span class="sxs-lookup"><span data-stu-id="e8a65-204">7</span></span>|<span data-ttu-id="e8a65-205">6</span><span class="sxs-lookup"><span data-stu-id="e8a65-205">6</span></span>|<span data-ttu-id="e8a65-206">5</span><span class="sxs-lookup"><span data-stu-id="e8a65-206">5</span></span>|<span data-ttu-id="e8a65-207">7</span><span class="sxs-lookup"><span data-stu-id="e8a65-207">7</span></span>|<span data-ttu-id="e8a65-208">6</span><span class="sxs-lookup"><span data-stu-id="e8a65-208">6</span></span>|  
  
## <a name="step-4-identify-mitigation-techniques-biztalk-message-queuing-adapter-scenario"></a><span data-ttu-id="e8a65-209">Étape 4.</span><span class="sxs-lookup"><span data-stu-id="e8a65-209">Step 4.</span></span> <span data-ttu-id="e8a65-210">Identifier les Techniques de prévention (scénario Message Queuing BizTalk adaptateur)</span><span class="sxs-lookup"><span data-stu-id="e8a65-210">Identify Mitigation Techniques (BizTalk Message Queuing Adapter Scenario)</span></span>  
 <span data-ttu-id="e8a65-211">Cette section présente certaines techniques de prévention des menaces identifiées pour le scénario de l'adaptateur de Message Queuing BizTalk dans un exemple d'architecture.</span><span class="sxs-lookup"><span data-stu-id="e8a65-211">This section presents some mitigation techniques for the threats we identified for the BizTalk Message Queuing adapter scenario for the sample architecture.</span></span>  
  
 <span data-ttu-id="e8a65-212">Le tableau suivant répertorie les techniques et technologies de prévention des menaces que nous avons identifiées lorsque vous utilisez l'adaptateur de Message Queuing BizTalk pour envoyer et recevoir des messages à et de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e8a65-212">The following table lists mitigation techniques and technologies for the threats we identified when you use the BizTalk Message Queuing adapter to send and receive messages to and from BizTalk Server.</span></span>  
  
 <span data-ttu-id="e8a65-213">**Tableau 3 techniques de prévention et technologies**</span><span class="sxs-lookup"><span data-stu-id="e8a65-213">**Table 3 Mitigation techniques and technologies**</span></span>  
  
|<span data-ttu-id="e8a65-214">Menace</span><span class="sxs-lookup"><span data-stu-id="e8a65-214">Threat</span></span>|<span data-ttu-id="e8a65-215">Impact</span><span class="sxs-lookup"><span data-stu-id="e8a65-215">Impact</span></span>|<span data-ttu-id="e8a65-216">Exposition au risque</span><span class="sxs-lookup"><span data-stu-id="e8a65-216">Risk exposure</span></span>|<span data-ttu-id="e8a65-217">Techniques et technologies de prévention</span><span class="sxs-lookup"><span data-stu-id="e8a65-217">Mitigation techniques and technologies</span></span>|  
|------------|------------|-------------------|--------------------------------------------|  
|<span data-ttu-id="e8a65-218">Envoi d'un grand nombre de messages à l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="e8a65-218">Send lots of messages to receive location</span></span>|<span data-ttu-id="e8a65-219">Déni de service</span><span class="sxs-lookup"><span data-stu-id="e8a65-219">Denial of service</span></span>|<span data-ttu-id="e8a65-220">6.8</span><span class="sxs-lookup"><span data-stu-id="e8a65-220">6.8</span></span>|<span data-ttu-id="e8a65-221">Utilisez l'adaptateur de Message Queuing BizTalk en mode à authentification requise.</span><span class="sxs-lookup"><span data-stu-id="e8a65-221">Use the BizTalk Message Queuing adapter in authentication-required mode.</span></span> <span data-ttu-id="e8a65-222">Définir le **authentification MSMQ requise** indicateur sur l’emplacement de réception et **authentification requis (abandonner les messages)** sur le port de réception.</span><span class="sxs-lookup"><span data-stu-id="e8a65-222">Set the **Requires MSMQ authentication** flag on the receive location and **Authentication Required (Drop messages)** on the receive port.</span></span><br /><br /> <span data-ttu-id="e8a65-223">Configurez Message Queuing BizTalk pour qu'il exige une authentification basée sur un certificat.</span><span class="sxs-lookup"><span data-stu-id="e8a65-223">Configure BizTalk Message Queuing to require certificate-based authentication.</span></span> <span data-ttu-id="e8a65-224">Ce comportement se produit au niveau de l'adaptateur et est différent du composant Résolution du tiers d'un pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e8a65-224">This behavior occurs at the adapter level, and is different from the Party Resolution component of a BizTalk pipeline.</span></span> <span data-ttu-id="e8a65-225">Si configuré, le certificat public est inclus avec le message entrant.</span><span class="sxs-lookup"><span data-stu-id="e8a65-225">If configured, the public certificate is included with the incoming message.</span></span> <span data-ttu-id="e8a65-226">C'est le seul mode d'authentification client disponible pour Message Queuing BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e8a65-226">This is the only client authentication mode available for BizTalk Message Queuing.</span></span> <span data-ttu-id="e8a65-227">Pour l'utiliser, vous devez installer Message Queuing BizTalk en mode d'intégration Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e8a65-227">To use this client authentication mode, you must install BizTalk Message Queuing with Active Directory Integration Mode.</span></span> <span data-ttu-id="e8a65-228">Lorsque vous utilisez cette fonctionnalité, n’oubliez pas de sélectionner le **exiger une authentification** emplacement de réception de case à cocher dans la boîte de dialogue Propriétés de Message Queuing BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e8a65-228">When you use this feature, remember to select the **Require Authentication** check box on the property dialog box for the BizTalk Message Queuing receive location.</span></span>|  
|<span data-ttu-id="e8a65-229">L'en-tête du message transite en texte clair.</span><span class="sxs-lookup"><span data-stu-id="e8a65-229">Message header travels in the clear on the wire</span></span>|<span data-ttu-id="e8a65-230">Falsification de données</span><span class="sxs-lookup"><span data-stu-id="e8a65-230">Tampering with data</span></span><br /><br /> <span data-ttu-id="e8a65-231">Divulgation d'informations</span><span class="sxs-lookup"><span data-stu-id="e8a65-231">Information disclosure</span></span>|<span data-ttu-id="e8a65-232">6.8</span><span class="sxs-lookup"><span data-stu-id="e8a65-232">6.8</span></span>|<span data-ttu-id="e8a65-233">Utilisez la sécurité du protocole Internet (IPSec) pour protéger le corps et l'en-tête du message lorsqu'il transite d'un serveur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="e8a65-233">Use Internet Protocol security (IPsec) to help protect the message body and the message header as it travels from one server to another.</span></span>|  
|<span data-ttu-id="e8a65-234">Un utilisateur non autorisé peut établir une connexion réseau au serveur BizTalk qui exécute l'hôte Message Queuing BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e8a65-234">An unauthorized user can make a network connection to the BizTalk Server that runs the BizTalk Message Queuing host</span></span>|<span data-ttu-id="e8a65-235">Répudiation</span><span class="sxs-lookup"><span data-stu-id="e8a65-235">Repudiation</span></span><br /><br /> <span data-ttu-id="e8a65-236">Falsification de données</span><span class="sxs-lookup"><span data-stu-id="e8a65-236">Tampering with data</span></span><br /><br /> <span data-ttu-id="e8a65-237">Divulgation d'informations</span><span class="sxs-lookup"><span data-stu-id="e8a65-237">Information disclosure</span></span><br /><br /> <span data-ttu-id="e8a65-238">Déni de service</span><span class="sxs-lookup"><span data-stu-id="e8a65-238">Denial of service</span></span><br /><br /> <span data-ttu-id="e8a65-239">Élévation de privilèges</span><span class="sxs-lookup"><span data-stu-id="e8a65-239">Elevation of privileges</span></span>|<span data-ttu-id="e8a65-240">9</span><span class="sxs-lookup"><span data-stu-id="e8a65-240">9</span></span>|<span data-ttu-id="e8a65-241">Créez un pipeline personnalisé avec un composant de pipeline Résolution de tiers, puis configurez ce dernier pour utiliser l'ID de l'expéditeur (SID) afin de résoudre le tiers.</span><span class="sxs-lookup"><span data-stu-id="e8a65-241">Create a custom pipeline with a Party Resolution pipeline component, and then configure the Party Resolution component to use the Sender ID (SID) to resolve the party.</span></span> <span data-ttu-id="e8a65-242">Définir le **résoudre le tiers par certificat** propriété **False**et le **résoudre le tiers par SID** propriété **True**.</span><span class="sxs-lookup"><span data-stu-id="e8a65-242">Set the **Resolve Party By Certificate** property to **False**, and the **Resolve Party By SID** property to **True**.</span></span> <span data-ttu-id="e8a65-243">Pour plus d’informations, consultez [composant de Pipeline résolution tiers](../core/party-resolution-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="e8a65-243">For more information, see [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).</span></span><br /><br /> <span data-ttu-id="e8a65-244">Sur le port de réception, définissez la **authentification** propriété **requis (abandonner les Messages)**.</span><span class="sxs-lookup"><span data-stu-id="e8a65-244">On the receive port, set the **Authentication** property to **Required (Drop Messages)**.</span></span>|  
|<span data-ttu-id="e8a65-245">Un utilisateur malveillant peut falsifier le message avant que BizTalk Server ne le reçoive.</span><span class="sxs-lookup"><span data-stu-id="e8a65-245">A malicious user can tamper with the message before BizTalk Server receives it</span></span>|<span data-ttu-id="e8a65-246">Falsification de données</span><span class="sxs-lookup"><span data-stu-id="e8a65-246">Tampering with data</span></span><br /><br /> <span data-ttu-id="e8a65-247">Divulgation d'informations</span><span class="sxs-lookup"><span data-stu-id="e8a65-247">Information disclosure</span></span>|<span data-ttu-id="e8a65-248">6</span><span class="sxs-lookup"><span data-stu-id="e8a65-248">6</span></span>|<span data-ttu-id="e8a65-249">Utilisez l'authentification par protocole pour vous assurer que le message n'a pas été falsifié lors de son transit.</span><span class="sxs-lookup"><span data-stu-id="e8a65-249">Use protocol-level authentication to make sure the message was not tampered with while in transit.</span></span> <span data-ttu-id="e8a65-250">Pour l'utiliser, vous devez disposer d'un routeur Message Queuing dans le domaine E-Business.</span><span class="sxs-lookup"><span data-stu-id="e8a65-250">To use protocol-level authentication, you must have a Message Queuing router in the E-Business domain.</span></span> <span data-ttu-id="e8a65-251">Configurer BizTalk Server comme suit :</span><span class="sxs-lookup"><span data-stu-id="e8a65-251">Configure BizTalk Server as follows:</span></span><br /><br /> <span data-ttu-id="e8a65-252">-Sur le **messagerie BizTalk** page du Gestionnaire de Configuration, indiquez le nom du routeur.</span><span class="sxs-lookup"><span data-stu-id="e8a65-252">-   On the **BizTalk Messaging** page of the Configuration Manager, provide the name of the router.</span></span><br /><span data-ttu-id="e8a65-253">-Pour le port de réception, définissez la **authentification** propriété **requis (abandonner les Messages)** ou **requis (conserver les Messages)**.</span><span class="sxs-lookup"><span data-stu-id="e8a65-253">-   For the receive port, set the **Authentication** property to **Required (Drop Messages)** or **Required (Keep Messages)**.</span></span><br /><span data-ttu-id="e8a65-254">-Pour le Gestionnaire d’envoi sur le **général** sous l’onglet du **routeur MSMQ** zone Nom, tapez le nom du routeur Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="e8a65-254">-   For the send handler, on the **General** tab, in the **MSMQ Router** name box, type the name of the Message Queuing router.</span></span><br /><span data-ttu-id="e8a65-255">-Pour le port d’envoi, sélectionnez **utiliser l’authentification MSMQ**.</span><span class="sxs-lookup"><span data-stu-id="e8a65-255">-   For the send port, select **Use MSMQ Authentication**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8a65-256">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8a65-256">See Also</span></span>  
 <span data-ttu-id="e8a65-257">[Analyse du modèle](../core/threat-model-analysis.md) </span><span class="sxs-lookup"><span data-stu-id="e8a65-257">[Threat Model Analysis](../core/threat-model-analysis.md) </span></span>  
 <span data-ttu-id="e8a65-258">[Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md) </span><span class="sxs-lookup"><span data-stu-id="e8a65-258">[Sample Scenarios for Threat Model Analysis](../core/sample-scenarios-for-threat-model-analysis.md) </span></span>  
 [<span data-ttu-id="e8a65-259">Exemples d’architecture pour les petites et moyennes entreprises</span><span class="sxs-lookup"><span data-stu-id="e8a65-259">Sample Architectures for Small & Medium-Sized Companies</span></span>](../core/sample-architectures-for-small-medium-sized-companies.md)