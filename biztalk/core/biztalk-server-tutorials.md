---
title: Didacticiels de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorials, getting started
- getting started, tutorials
ms.assetid: 58019f98-e91a-4705-b689-c269174d6bae
caps.latest.revision: "42"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f13a5d74d0957a208600653823e7604680296f4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-tutorials"></a><span data-ttu-id="e63ce-102">Didacticiels de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e63ce-102">BizTalk Server Tutorials</span></span>
<span data-ttu-id="e63ce-103">Didacticiels pour apprendre à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e63ce-103">Tutorials to learn how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>

<span data-ttu-id="e63ce-104">Il s'agit de scénarios simples permettant aux nouveaux utilisateurs de prendre en main divers outils que propose BizTalk dans le cadre de la création de solutions d'intégration compilées pouvant être testées.</span><span class="sxs-lookup"><span data-stu-id="e63ce-104">The BizTalk Server tutorials contain simple scenarios to give new users an experience of using a variety of BizTalk tools while creating compiled, testable integration solutions.</span></span> <span data-ttu-id="e63ce-105">Pour les utilisateurs plus expérimentés, ou les utilisateurs concevez des solutions BizTalk, consultez [scénarios pour les Solutions](../core/scenarios-for-business-solutions.md).</span><span class="sxs-lookup"><span data-stu-id="e63ce-105">For more advanced users, or users who are designing BizTalk solutions, see [Scenarios for Business Solutions](../core/scenarios-for-business-solutions.md).</span></span>  
  
## <a name="enterprise-application-integration"></a><span data-ttu-id="e63ce-106">IAE (Intégration des applications de l'entreprise)</span><span class="sxs-lookup"><span data-stu-id="e63ce-106">Enterprise Application Integration</span></span>
  
[<span data-ttu-id="e63ce-107">Didacticiel : Intégration d’Application d’entreprise</span><span class="sxs-lookup"><span data-stu-id="e63ce-107">Tutorial: Enterprise Application Integration</span></span>](../core/tutorial-1-enterprise-application-integration.md) 

<span data-ttu-id="e63ce-108">Implémenter une solution BizTalk qui reçoit les messages de demande de réapprovisionnement de stock d’un entrepôt et évalue les messages de demande.</span><span class="sxs-lookup"><span data-stu-id="e63ce-108">Implement a BizTalk solution that receives inventory replenishment request messages from a warehouse, and evaluates the request messages.</span></span> <span data-ttu-id="e63ce-109">Si la solution refuse une requête, il envoie un message de refus à l’entrepôt.</span><span class="sxs-lookup"><span data-stu-id="e63ce-109">If the solution denies a request, then it sends a decline message to the warehouse.</span></span> <span data-ttu-id="e63ce-110">Si la demande est acceptée par la solution, puis il transmet le message à un système de planification ERP (Enterprise Resource).</span><span class="sxs-lookup"><span data-stu-id="e63ce-110">If the solution approves a request, then it forwards the message to an Enterprise Resource Planning (ERP) system.</span></span>  

## <a name="create-a-hybrid-application"></a><span data-ttu-id="e63ce-111">Créer une Application hybride</span><span class="sxs-lookup"><span data-stu-id="e63ce-111">Create a Hybrid Application</span></span>
[<span data-ttu-id="e63ce-112">Didacticiel : Création d’une Application hybride à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e63ce-112">Tutorial: Creating a Hybrid Application Using BizTalk Server</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)  

<span data-ttu-id="e63ce-113">Configurer une application de bout en bout qui utilise l’EDI pour générer des accusés de réception, Service Bus pour recevoir des messages, et puis insérez des données dans SQL.</span><span class="sxs-lookup"><span data-stu-id="e63ce-113">Set up an end-to-end application that uses EDI to generate acknowledgements, Service Bus to receive messages, and then insert data into SQL.</span></span> 

## <a name="invoke-a-rest-interface"></a><span data-ttu-id="e63ce-114">Appeler une Interface REST</span><span class="sxs-lookup"><span data-stu-id="e63ce-114">Invoke a REST Interface</span></span>
[<span data-ttu-id="e63ce-115">Didacticiel : Appel d’une Interface REST à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e63ce-115">Tutorial: Invoking a REST Interface Using BizTalk Server</span></span>](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)  

<span data-ttu-id="e63ce-116">Utilise l’adaptateur WCF-WebHttp pour utiliser une URL de REST, puis envoyer un message de réponse.</span><span class="sxs-lookup"><span data-stu-id="e63ce-116">Uses the WCF-WebHttp adapter to use a REST URL, and then send a response message.</span></span> 

## <a name="integrate-biztalk-with-salesforce"></a><span data-ttu-id="e63ce-117">Intégration de BizTalk avec Salesforce</span><span class="sxs-lookup"><span data-stu-id="e63ce-117">Integrate BizTalk with Salesforce</span></span>
[<span data-ttu-id="e63ce-118">Didacticiel : Intégration de BizTalk Server auprès de Salesforce</span><span class="sxs-lookup"><span data-stu-id="e63ce-118">Tutorial: Integrating BizTalk Server with Salesforce</span></span>](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)  

<span data-ttu-id="e63ce-119">Chaque fois qu’une opportunité de vente est créée dans le système Salesforce, Northwind veut que ses systèmes sur site, tels que BizTalk Server, pour être averti afin que les autres systèmes en aval puissent collecter les données et démarrer d’autres processus pertinents.</span><span class="sxs-lookup"><span data-stu-id="e63ce-119">Every time a sales opportunity is created in the Salesforce system, Northwind wants its on-premise systems, such as BizTalk Server, to be notified so that other downstream systems can pick up that data and start other relevant processes.</span></span> 

## <a name="process-json-messages"></a><span data-ttu-id="e63ce-120">Traiter les messages JSON</span><span class="sxs-lookup"><span data-stu-id="e63ce-120">Process JSON messages</span></span>
[<span data-ttu-id="e63ce-121">Traitement des messages JSON à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e63ce-121">Processing JSON messages using BizTalk Server</span></span>](../core/processing-json-messages-using-biztalk-server.md)  

<span data-ttu-id="e63ce-122">Configurer une application BizTalk qui reçoit un bon de commande JSON.</span><span class="sxs-lookup"><span data-stu-id="e63ce-122">Set up a BizTalk application that receives a JSON purchase order.</span></span> <span data-ttu-id="e63ce-123">Dans le pipeline de réception, un composant du décodeur JSON transforme le message JSON en message XML.</span><span class="sxs-lookup"><span data-stu-id="e63ce-123">In the receive pipeline, a JSON decoder component transforms the JSON message to XML message.</span></span> <span data-ttu-id="e63ce-124">Puis, utilise un mappage pour transformer le bon de commande XML en facture XML.</span><span class="sxs-lookup"><span data-stu-id="e63ce-124">Then, uses a map to transform the XML purchase order into an XML invoice.</span></span> <span data-ttu-id="e63ce-125">Le pipeline d’envoi utilise un encodeur JSON pour transformer la facture XML en une facture JSON, puis envoie le message.</span><span class="sxs-lookup"><span data-stu-id="e63ce-125">The send pipeline uses a JSON encoder to transform the XML invoice into a JSON invoice, and then sends the message.</span></span>

## <a name="edi-interface-developer"></a><span data-ttu-id="e63ce-126">Développeur d’Interface EDI</span><span class="sxs-lookup"><span data-stu-id="e63ce-126">EDI Interface Developer</span></span>
  [<span data-ttu-id="e63ce-127">Didacticiel : EDI Interface Developer Tutorial.</span><span class="sxs-lookup"><span data-stu-id="e63ce-127">Tutorial: EDI Interface Developer Tutorial</span></span>](../core/tutorial-2-edi-interface-developer-tutorial.md)
  
<span data-ttu-id="e63ce-128">Un partenaire commercial envoie des bons de commande à l’aide de l’ANSI X12 4010 850 du document informatisé (message 850).</span><span class="sxs-lookup"><span data-stu-id="e63ce-128">A trading partner sends purchase orders using the ANSI X12 4010 850 transaction set (an 850 message).</span></span> <span data-ttu-id="e63ce-129">Un processus de système de commande interne bons de commande.</span><span class="sxs-lookup"><span data-stu-id="e63ce-129">An internal order system processes purchase orders.</span></span>

<span data-ttu-id="e63ce-130">En tant que développeur d’interface chargé de concevoir l’interface entre le message 850, vous recevez de votre partenaire commercial et système de commande interne de votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="e63ce-130">As an interface developer responsible for designing the interface between the 850 message, you receive from your trading partner and your company’s internal Order System.</span></span> <span data-ttu-id="e63ce-131">Votre partenaire commercial requiert un accusé de réception fonctionnel (997) pour chaque message 850 qu'il envoie.</span><span class="sxs-lookup"><span data-stu-id="e63ce-131">Your trading partner requires a Functional Acknowledgement (997) for each 850 message it sends.</span></span>


## <a name="as2"></a><span data-ttu-id="e63ce-132">AS2</span><span class="sxs-lookup"><span data-stu-id="e63ce-132">AS2</span></span>  
[<span data-ttu-id="e63ce-133">Didacticiel : Didacticiel AS2</span><span class="sxs-lookup"><span data-stu-id="e63ce-133">Tutorial: AS2 Tutorial</span></span>](../core/tutorial-3-as2-tutorial.md)

<span data-ttu-id="e63ce-134">Configurer une solution qui reçoit et envoie les messages codés EDIINT/AS2 via un transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="e63ce-134">Set up a solution that receives and sends EDIINT/AS2-encoded messages over an HTTP transport.</span></span>    


## <a name="do-more"></a><span data-ttu-id="e63ce-135">Faire plus</span><span class="sxs-lookup"><span data-stu-id="e63ce-135">Do more</span></span>  
 <span data-ttu-id="e63ce-136">Pour plus d’informations sur l’architecture et les concepts de BizTalk Server, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e63ce-136">To learn more about BizTalk Server concepts and architecture, consider the following:</span></span>  
  
[<span data-ttu-id="e63ce-137">Prise en main</span><span class="sxs-lookup"><span data-stu-id="e63ce-137">Get started</span></span>](../core/getting-started-with-biztalk-server.md)
  
[<span data-ttu-id="e63ce-138">Planifier et concevoir votre solution BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e63ce-138">Plan and architect your BizTalk Server solution</span></span>](../core/plan-and-architect-your-biztalk-server-solution.md)