---
title: "À l’aide de corrélations dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, orchestrations
- messages, correlation sets
- correlation sets
- orchestrations, messages
- messages, validating
ms.assetid: d919afa9-bada-406a-bf4b-7b46c831c6d5
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3be56c2171205bb49d2ff1f589c77ac309ea188
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-correlations-in-orchestrations"></a><span data-ttu-id="7dc6f-102">Utilisation des corrélations dans les orchestrations</span><span class="sxs-lookup"><span data-stu-id="7dc6f-102">Using Correlations in Orchestrations</span></span>
<span data-ttu-id="7dc6f-103">La corrélation est le processus de mise en correspondance d'un message entrant et de l'instance appropriée d'une orchestration.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-103">Correlation is the process of matching an incoming message with the appropriate instance of an orchestration.</span></span> <span data-ttu-id="7dc6f-104">Par exemple, une orchestration envoie un message et reçoit une ou plusieurs réponses.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-104">For example, orchestration sends out of a message and receives the response or responses back into the same orchestration.</span></span> <span data-ttu-id="7dc6f-105">Il existe trois modèles d'échange de messages corrélés :</span><span class="sxs-lookup"><span data-stu-id="7dc6f-105">There are three correlated messages exchange patterns:</span></span>  
  
-   <span data-ttu-id="7dc6f-106">établissement de liaison traditionnel ;</span><span class="sxs-lookup"><span data-stu-id="7dc6f-106">Traditional handshake</span></span>  
  
-   <span data-ttu-id="7dc6f-107">convoi séquentiel ;</span><span class="sxs-lookup"><span data-stu-id="7dc6f-107">Sequential convoy</span></span>  
  
-   <span data-ttu-id="7dc6f-108">convoi parallèle.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-108">Parallel convoy</span></span>  
  
 <span data-ttu-id="7dc6f-109">Dans le modèle d'établissement de liaison traditionnel, les établissements de liaison existent entre les échanges de messages entre orchestrations ou processus d'entreprise. De plus, vous pouvez établir des liaisons en définissant des ensembles de corrélations dans les orchestrations, les ensembles de corrélations étant des listes de propriétés promues dotées de valeurs spécifiques que vous utilisez pour acheminer les messages vers une instance d'orchestration spécifique.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-109">In the traditional handshake pattern, handshakes exist between the exchanges of the messages among the orchestrations or business processes, and you can achieve the handshakes by defining correlation sets in the orchestrations where a correlation set is a list of promoted properties with specific values that you use to route messages to a specific orchestration instance.</span></span>  
  
 <span data-ttu-id="7dc6f-110">Si, par exemple, votre orchestration est conçue pour émettre un bon de commande, recevoir une facture et envoyer le paiement, vous devez être certain que le message lié à la facture est reçu par l'instance d'orchestration qui a envoyé le bon de commande, car les numéros de bons de commande risquent d'être traités en même temps.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-110">If, for example, your orchestration is designed to issue a purchase order, receive an invoice, and send out the payment, you need to be sure that the invoice message is received by the same orchestration instance that the corresponding purchase order was sent from since numbers of purchase orders may be processed at the time.</span></span> <span data-ttu-id="7dc6f-111">Dans cet exemple, le numéro d'identification du bon de commande peut être utilisé en tant que paramètre dans l'ensemble de corrélations pour corréler le message du bon de commande et le message de la facture.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-111">In this example, the purchase order identification number can be used as a parameter in the correlation set for correlating the purchase order message and the invoice message.</span></span> <span data-ttu-id="7dc6f-112">Voici une illustration de cet exemple :</span><span class="sxs-lookup"><span data-stu-id="7dc6f-112">The following is the scenario flow for this example,</span></span>  
  
1.  <span data-ttu-id="7dc6f-113">L'Orchestration A envoie le message de bon de commande à l'Orchestration B. Avant l'envoi de ce message, l'ensemble de corrélations est initialisé.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-113">The Orchestration A sends out the purchase order message to the Orchestration B. Before sending out the purchase order message, the correlation set is initialized.</span></span>  
  
2.  <span data-ttu-id="7dc6f-114">Dans l'Orchestration B, qui traite le bon de commande, génère, puis envoie la facture, la première forme Réception suit le même ensemble de corrélations pour recevoir le message de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-114">In the Orchestration B, in which processes the purchase order, generates and sends back the invoice, the first Receive shape follows the same correlation set to receive the purchase order message.</span></span>  
  
3.  <span data-ttu-id="7dc6f-115">Après traitement du message de bon de commande, lors de l'envoi du message de facture à l'Orchestration A, le même ensemble de corrélations est à nouveau suivi.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-115">After processing the purchase order message, when sending back the invoice message to the Orchestration A, the same correlation set is also followed.</span></span>  
  
4.  <span data-ttu-id="7dc6f-116">Dans l'Orchestration A, au niveau de la forme Réception qui reçoit le message de facture de la part de l'Orchestration B, le même ensemble de corrélations est également suivi, afin de garantir une réception du message de facture corrélé basée sur l'ensemble de corrélations prédéfini.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-116">In the Orchestration A, at the Receive shape which receives the invoice message back from the orchestration B, the same correlation set is also followed to ensure that receiving the correlated invoice message based on the predefined correlation set.</span></span>  
  
 <span data-ttu-id="7dc6f-117">Les modèles de convoi séquentiel et de convoi parallèle sont utilisés chaque fois que plusieurs éléments uniques doivent être reliés de façon à obtenir une chose qu'un élément individuel ne peut pas accomplir seul.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-117">The sequential convoy and parallel convoy patterns exist in the world any time multiple single items must be related together in order to achieve something that the individual item cannot accomplish by itself.</span></span> <span data-ttu-id="7dc6f-118">Pour plus d’informations, consultez [utilisation des convois](../core/working-with-convoy-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="7dc6f-118">For more information, see [Working with Convoy Scenarios](../core/working-with-convoy-scenarios.md).</span></span>  
  
 <span data-ttu-id="7dc6f-119">Outre les modèles d'échange de messages corrélés, il existe deux types de corrélations dans les orchestrations :</span><span class="sxs-lookup"><span data-stu-id="7dc6f-119">In addition to the correlated message exchange patterns, there are two types of correlations in orchestration:</span></span>  
  
-   <span data-ttu-id="7dc6f-120">corrélation manuelle ;</span><span class="sxs-lookup"><span data-stu-id="7dc6f-120">Manual correlation</span></span>  
  
-   <span data-ttu-id="7dc6f-121">corrélation automatique.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-121">Automatic correlation</span></span>  
  
 <span data-ttu-id="7dc6f-122">Dans le cas d'une corrélation manuelle, vous configurez manuellement les orchestrations à initialiser et suivez l'ensemble de corrélations pour associer les messages aux instances appropriées.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-122">In the manual correlation scenario, you manually configure the orchestrations to initialize and follow the correlation set to associate the messages with proper instances.</span></span> <span data-ttu-id="7dc6f-123">Lorsque la corrélation est automatique, le moteur de messagerie corrèle les messages avec les instances à votre place, par exemple, lorsque vous configurez le port Requête-Réponse ou le port Autocorrélation dans vos orchestrations.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-123">In the automatic correlation scenario, the messaging engine will correlate the messages with the instances for you, for example, when you set up Request-Response port or Self-Correlating port in your orchestrations.</span></span>  
  
 <span data-ttu-id="7dc6f-124">Vous devez utiliser la corrélation chaque fois qu'une orchestration ne dispose pas d'une façon explicite d'associer un message à une instance, telle qu'une réception avec activation, une requête-réponse ou un port d'autocorrélation.</span><span class="sxs-lookup"><span data-stu-id="7dc6f-124">You must use correlation whenever your orchestration does not have an explicit way of associating a message with an instance, such as an activate receive, a request-response, or a self-correlating port.</span></span>  
  
## <a name="examples-of-using-correlations"></a><span data-ttu-id="7dc6f-125">Exemples d'utilisation de corrélations</span><span class="sxs-lookup"><span data-stu-id="7dc6f-125">Examples of Using Correlations</span></span>  
  
-   [<span data-ttu-id="7dc6f-126">PartyResolution (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="7dc6f-126">PartyResolution (BizTalk Server Sample)</span></span>](../core/partyresolution-biztalk-server-sample.md)  
  
-   <span data-ttu-id="7dc6f-127">Téléchargez l’exemple du Kit de développement logiciel « Corrélation des Messages avec des Instances d’Orchestration » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="7dc6f-127">Download the SDK sample "Correlating Messages with Orchestration Instances" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="7dc6f-128">Téléchargez l’exemple du Kit de développement logiciel « Convoi parallèle » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="7dc6f-128">Download the SDK sample "Parallel Convoy" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7dc6f-129">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7dc6f-129">In This Section</span></span>  
  
-   [<span data-ttu-id="7dc6f-130">Ensembles de corrélations</span><span class="sxs-lookup"><span data-stu-id="7dc6f-130">Correlation Sets</span></span>](../core/correlation-sets.md) 
  
-   [<span data-ttu-id="7dc6f-131">Types de corrélations</span><span class="sxs-lookup"><span data-stu-id="7dc6f-131">Correlation Types</span></span>](../core/correlation-types.md) 
  
-   [<span data-ttu-id="7dc6f-132">Comment ajouter et supprimer des ensembles de corrélations</span><span class="sxs-lookup"><span data-stu-id="7dc6f-132">How to Add and Remove Correlation Sets</span></span>](../core/how-to-add-and-remove-correlation-sets.md) 
  
-   [<span data-ttu-id="7dc6f-133">Comment configurer des ensembles de corrélations</span><span class="sxs-lookup"><span data-stu-id="7dc6f-133">How to Configure Correlation Sets</span></span>](../core/how-to-configure-correlation-sets.md)  
  
-   [<span data-ttu-id="7dc6f-134">Comment configurer les Types de corrélations</span><span class="sxs-lookup"><span data-stu-id="7dc6f-134">How to Configure Correlation Types</span></span>](../core/how-to-configure-correlation-types.md)  
  
-   [<span data-ttu-id="7dc6f-135">Utilisation des convois</span><span class="sxs-lookup"><span data-stu-id="7dc6f-135">Working with Convoy Scenarios</span></span>](../core/working-with-convoy-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="7dc6f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7dc6f-136">See Also</span></span>  
 [<span data-ttu-id="7dc6f-137">Ports de liaison de l’utilisation directe d’autocorrélation</span><span class="sxs-lookup"><span data-stu-id="7dc6f-137">How to Use Self-Correlating Direct Bound Ports</span></span>](../core/how-to-use-self-correlating-direct-bound-ports.md)