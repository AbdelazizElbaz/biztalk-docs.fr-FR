---
title: "Comment : transformer un Message et un itinéraire vers un point de terminaison de Service à l’aide d’un modèle d’échange de Message demande-réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1e656fb-6c5f-4b2b-a1b6-4c812b78ee22
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dfc7c7d572f3370e87df2f03d392a993116b74d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-transform-a-message-and-route-to-a-service-endpoint-using-a-request-response-message-exchange-pattern"></a><span data-ttu-id="af0c4-102">Comment : transformer un Message et un itinéraire vers un point de terminaison de Service à l’aide d’un modèle d’échange de Message demande-réponse</span><span class="sxs-lookup"><span data-stu-id="af0c4-102">How to: Transform a Message and Route to a Service Endpoint Using a Request-Response Message Exchange Pattern</span></span>
## <a name="goal"></a><span data-ttu-id="af0c4-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="af0c4-103">Goal</span></span>  
 <span data-ttu-id="af0c4-104">Cette section montre comment utiliser le langage spécifique à un domaine (DSL), ESB concepteur pour créer un itinéraire de requête-réponse qui peut être utilisé avec un bidirectionnelle rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="af0c4-104">This section demonstrates how to use the ESB Designer domain-specific language (DSL) to create a request-response itinerary that can be used with a two-way on-ramp.</span></span> <span data-ttu-id="af0c4-105">Vous allez créer un bordereau de routage pour recevoir un message, transformer le message, envoyer le message à un service et renvoyer le message de réponse de service à l’émetteur du message d’origine.</span><span class="sxs-lookup"><span data-stu-id="af0c4-105">You will create a routing slip to receive a message, transform the message, submit the message to a service, and return the service response message to the submitter of the original message.</span></span>  
  
 <span data-ttu-id="af0c4-106">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="af0c4-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="af0c4-107">Créer un bordereau d’itinéraire de routage avec un service d’itinéraire de transformation qui implémente un mappage de Microsoft BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="af0c4-107">Create an itinerary routing slip with a transform itinerary service that implements a Microsoft BizTalk Server map.</span></span>  
  
-   <span data-ttu-id="af0c4-108">Configurer la feuille de route pour acheminer le message transformé à un point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="af0c4-108">Configure the itinerary to route the transformed message to a service endpoint.</span></span>  
  
-   <span data-ttu-id="af0c4-109">Configurez l’itinéraire pour renvoyer le message de réponse de service à l’expéditeur d’origine.</span><span class="sxs-lookup"><span data-stu-id="af0c4-109">Configure the itinerary to return the service response message to the original sending party.</span></span>  
  
-   <span data-ttu-id="af0c4-110">Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="af0c4-110">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="af0c4-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="af0c4-111">Prerequisites</span></span>  
 <span data-ttu-id="af0c4-112">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="af0c4-112">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="af0c4-113">Étapes</span><span class="sxs-lookup"><span data-stu-id="af0c4-113">Steps</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="af0c4-114">Pour créer un modèle DSL de la feuille de route ESB</span><span class="sxs-lookup"><span data-stu-id="af0c4-114">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="af0c4-115">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="af0c4-115">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="af0c4-116">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-116">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="af0c4-117">Dans le **ajouter un nouvel élément** boîte de dialogue le **nom** , tapez **requête-réponse**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-117">In the **Add New Item** dialog box, in the **Name** box, type **RequestResponse**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="af0c4-118">Pour configurer les propriétés de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="af0c4-118">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="af0c4-119">Dans Visual Studio, cliquez sur l’aire de conception de **RequestResponse.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-119">In Visual Studio, click the design surface of **RequestResponse.itinerary**.</span></span> <span data-ttu-id="af0c4-120">Dans le **requête-réponse** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="af0c4-120">In the **RequestResponse** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="af0c4-121">Dans le **réponse à la demande est** la liste déroulante, cliquez sur **True**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-121">In the **Is Request Response** drop-down list, click **True**.</span></span>  
  
    2.  <span data-ttu-id="af0c4-122">Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-122">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    3.  <span data-ttu-id="af0c4-123">Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="af0c4-123">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    4.  <span data-ttu-id="af0c4-124">Dans le **sélectionner un fichier XML** boîte de dialogue le **nom de fichier** , tapez **C:\HowTos\Itineraries\RequestResponse**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-124">In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\RequestResponse**, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="af0c4-125">Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local.</span><span class="sxs-lookup"><span data-stu-id="af0c4-125">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="af0c4-126">En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB.</span><span class="sxs-lookup"><span data-stu-id="af0c4-126">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="af0c4-127">Vous pourrez terminer cette procédure plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="af0c4-127">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="af0c4-128">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="af0c4-128">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="af0c4-129">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="af0c4-129">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="af0c4-130">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="af0c4-130">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="af0c4-131">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-131">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="af0c4-132">Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-132">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="af0c4-133">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-133">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="af0c4-134">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary.Response**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-134">In the **Receive Port** drop-down list, click **OnRamp.Itinerary.Response**.</span></span>  
  
2.  <span data-ttu-id="af0c4-135">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de la **rampe d’entrée** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="af0c4-135">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="af0c4-136">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="af0c4-136">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="af0c4-137">Cliquez sur le **nom** propriété, puis tapez **MapNAOrderToCNOrder**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-137">Click the **Name** property, and then type **MapNAOrderToCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="af0c4-138">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-138">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="af0c4-139">Cette propriété définit que le processus a lieu dans un pipeline (messagerie).</span><span class="sxs-lookup"><span data-stu-id="af0c4-139">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="af0c4-140">Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-140">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="af0c4-141">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-141">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="af0c4-142">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Transform**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-142">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
3.  <span data-ttu-id="af0c4-143">Avec le bouton droit le **résolveur** collection de la **MapNAOrderToCNOrder** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-143">Right-click the **Resolver** collection of the **MapNAOrderToCNOrder** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="af0c4-144">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="af0c4-144">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="af0c4-145">Cliquez sur le **nom** propriété, puis tapez **StaticallySpecifyTheMap**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-145">Click the **Name** property, and then type **StaticallySpecifyTheMap**.</span></span>  
  
    2.  <span data-ttu-id="af0c4-146">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-146">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="af0c4-147">Dans le **transformer un Type** la liste déroulante, cliquez sur **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-147">In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span></span>  
  
4.  <span data-ttu-id="af0c4-148">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-148">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="af0c4-149">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **MapNAOrderToCNOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="af0c4-149">Drag a connection from the **ReceiveNAOrder** model element to the **MapNAOrderToCNOrder** model element.</span></span>  
  
5.  <span data-ttu-id="af0c4-150">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de la **MapNAOrderToCNOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="af0c4-150">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **MapNAOrderToCNOrder** model element.</span></span> <span data-ttu-id="af0c4-151">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="af0c4-151">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="af0c4-152">Cliquez sur le **nom** propriété, puis tapez **RouteToCNService**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-152">Click the **Name** property, and then type **RouteToCNService**.</span></span>  
  
    2.  <span data-ttu-id="af0c4-153">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-153">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="af0c4-154">Cette propriété définit que le processus a lieu dans un pipeline (messagerie).</span><span class="sxs-lookup"><span data-stu-id="af0c4-154">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="af0c4-155">Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-155">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="af0c4-156">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-156">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="af0c4-157">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-157">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
6.  <span data-ttu-id="af0c4-158">Avec le bouton droit le **résolveur** collection de la **RouteToCNService** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-158">Right-click the **Resolver** collection of the **RouteToCNService** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="af0c4-159">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="af0c4-159">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="af0c4-160">Cliquez sur le **nom** propriété, puis tapez **StaticallySpecifyTheService**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-160">Click the **Name** property, and then type **StaticallySpecifyTheService**.</span></span>  
  
    2.  <span data-ttu-id="af0c4-161">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-161">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="af0c4-162">Dans le **nom Transport** la liste déroulante, cliquez sur **WCF-BasicHttp**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-162">In the **Transport Name** drop-down list, click **WCF-BasicHttp**.</span></span>  
  
    4.  <span data-ttu-id="af0c4-163">Cliquez sur le **Transport emplacement** propriété, puis tapez **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-163">Click the **Transport Location** property, and then type **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.</span></span>  
  
    5.  <span data-ttu-id="af0c4-164">Cliquez sur le **cible Namespace** propriété, puis tapez **http://globalbank.esb.dynamicresolution.com/canadianservices**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-164">Click the **Target Namespace** property, and then type **http://globalbank.esb.dynamicresolution.com/canadianservices**.</span></span>  
  
    6.  <span data-ttu-id="af0c4-165">Cliquez sur le **Action** propriété, puis tapez **submitOrder**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-165">Click the **Action** property, and then type **submitOrder**.</span></span>  
  
7.  <span data-ttu-id="af0c4-166">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-166">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="af0c4-167">Faites glisser une connexion à partir de la **MapNAOrderToCNOrder** élément de modèle à la **RouteToCNService** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="af0c4-167">Drag a connection from the **MapNAOrderToCNOrder** model element to the **RouteToCNService** model element.</span></span>  
  
8.  <span data-ttu-id="af0c4-168">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **RouteToCNService** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="af0c4-168">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteToCNService** model element.</span></span> <span data-ttu-id="af0c4-169">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="af0c4-169">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="af0c4-170">Cliquez sur le **nom** propriété, puis tapez **InvokeCNService**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-170">Click the **Name** property, and then type **InvokeCNService**.</span></span>  
  
    2.  <span data-ttu-id="af0c4-171">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-171">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="af0c4-172">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-172">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="af0c4-173">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionSolicitResp**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-173">In the **Send Port** drop-down list, click **DynamicResolutionSolicitResp**.</span></span>  
  
9. <span data-ttu-id="af0c4-174">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **RouteToCNService** élément de modèle et la **InvokeCNService**élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="af0c4-174">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteToCNService** model element and the **InvokeCNService** model element.</span></span> <span data-ttu-id="af0c4-175">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="af0c4-175">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="af0c4-176">Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-176">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="af0c4-177">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-177">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="af0c4-178">Dans le **rampe** déroulante liste, développez **InvokeCNService**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-178">In the **Off-Ramp** drop-down list, expand **InvokeCNService**, and then click **Send Handlers**.</span></span>  
  
10. <span data-ttu-id="af0c4-179">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-179">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="af0c4-180">Faites glisser une connexion à partir de la **RouteToCNService** élément de modèle à la **SendPortFilter** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="af0c4-180">Drag a connection from the **RouteToCNService** model element to the **SendPortFilter** model element.</span></span>  
  
11. <span data-ttu-id="af0c4-181">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-181">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="af0c4-182">Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **InvokeCNService** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="af0c4-182">Drag a connection from the **SendPortFilter** model element to the **InvokeCNService** model element.</span></span>  
  
12. <span data-ttu-id="af0c4-183">Cliquez sur l’aire de conception, puis cliquez sur **Validate**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-183">Right-click the design surface, and then click **Validate**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="af0c4-184">L’itinéraire est valide ; Il n’est pas nécessaire de se connecter la rampe à la bande afin d’envoyer le message de réponse au demandeur tiers.</span><span class="sxs-lookup"><span data-stu-id="af0c4-184">The itinerary validates; it is not necessary to connect the off-ramp back to the on-ramp in order to send the response message back to the requesting party.</span></span> <span data-ttu-id="af0c4-185">En utilisant un bidirectionnelle rampe d’entrée, le message final est automatiquement renvoyé à la partie.</span><span class="sxs-lookup"><span data-stu-id="af0c4-185">By using a two-way on-ramp, the final message is automatically returned to the requesting party.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="af0c4-186">Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="af0c4-186">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="af0c4-187">Dans Visual Studio, cliquez sur l’aire de conception de la **requête-réponse** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-187">In Visual Studio, right-click the design surface of the **RequestResponse** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="af0c4-188">La version XML de l’itinéraire s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="af0c4-188">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="af0c4-189">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="af0c4-189">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="af0c4-190">Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="af0c4-190">In Windows Explorer, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="af0c4-191">Notez que la création de votre feuille de route XML (RequestResponse.xml).</span><span class="sxs-lookup"><span data-stu-id="af0c4-191">Notice the creation of your itinerary XML (RequestResponse.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="af0c4-192">Pour tester la feuille de route</span><span class="sxs-lookup"><span data-stu-id="af0c4-192">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="af0c4-193">Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).</span><span class="sxs-lookup"><span data-stu-id="af0c4-193">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="af0c4-194">Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="af0c4-194">In the Itinerary Test Client, clear the **Use WCF Service** check box.</span></span>  
  
3.  <span data-ttu-id="af0c4-195">Dans le **Options du Service Web** section, sélectionnez le **deux manière Service** case à cocher, puis cliquez sur **charge itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-195">In the **Web Service Options** section, select the **Two Way Service** check box, and then click **Load Itinerary**.</span></span>  
  
4.  <span data-ttu-id="af0c4-196">Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="af0c4-196">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="af0c4-197">Sélectionnez **RequestResponse.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="af0c4-197">Select **RequestResponse.xml**, and then click **Open** to load the itinerary.</span></span>  
  
5.  <span data-ttu-id="af0c4-198">Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.</span><span class="sxs-lookup"><span data-stu-id="af0c4-198">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
6.  <span data-ttu-id="af0c4-199">Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="af0c4-199">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
7.  <span data-ttu-id="af0c4-200">Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="af0c4-200">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="af0c4-201">Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.</span><span class="sxs-lookup"><span data-stu-id="af0c4-201">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
8.  <span data-ttu-id="af0c4-202">Cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="af0c4-202">Click the **Submit Request** button.</span></span> <span data-ttu-id="af0c4-203">Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="af0c4-203">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
9. <span data-ttu-id="af0c4-204">Dans le **résultats** zone, notez le nœud racine du message est **submitOrderResponse** et l’espace de noms par défaut est en cours... **canadianservices**.</span><span class="sxs-lookup"><span data-stu-id="af0c4-204">In the **Results** box, notice the message's root node is **submitOrderResponse** and the default namespace is ... **canadianservices**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="af0c4-205">Si le message de réponse nécessite une transformation supplémentaire avant que la réponse est envoyée au demandeur tiers, vous devez utiliser un pipeline qui contient le composant redirecteur d’ESB.</span><span class="sxs-lookup"><span data-stu-id="af0c4-205">If the response message requires additional transformation before the response is sent to the requesting party, you must use a pipeline that contains the ESB Forwarder component.</span></span> <span data-ttu-id="af0c4-206">Pour obtenir un exemple de cette fonctionnalité, consultez le [installer et exécuter l’exemple de Services Web plusieurs](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md).</span><span class="sxs-lookup"><span data-stu-id="af0c4-206">For an example of this functionality, see the [Installing and Running the Multiple Web Services Sample](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md).</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="af0c4-207">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="af0c4-207">Additional Resources</span></span>  
 <span data-ttu-id="af0c4-208">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="af0c4-208">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="af0c4-209">Comment : transformer un Message et router le Message résultant à un emplacement de fichier à l’aide d’un bon d’itinéraire de routage</span><span class="sxs-lookup"><span data-stu-id="af0c4-209">How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip</span></span>](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [<span data-ttu-id="af0c4-210">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="af0c4-210">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="af0c4-211">Modèles de routage de messages</span><span class="sxs-lookup"><span data-stu-id="af0c4-211">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)  
  
-   [<span data-ttu-id="af0c4-212">Installer et exécuter l’exemple de Services Web multiples</span><span class="sxs-lookup"><span data-stu-id="af0c4-212">Installing and Running the Multiple Web Services Sample</span></span>](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)