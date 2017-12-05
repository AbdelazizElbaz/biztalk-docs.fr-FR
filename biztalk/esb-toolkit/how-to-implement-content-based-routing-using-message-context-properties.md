---
title: "Comment : implémenter le routage basé sur le contenu à l’aide des propriétés de contexte de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 952af792-5762-4b04-9087-980bb3323568
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be099923fea9d5dbb22559203b297fadf5dd1fdc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-implement-content-based-routing-using-message-context-properties"></a><span data-ttu-id="438f6-102">Comment : implémenter le routage basé sur le contenu à l’aide des propriétés de contexte de Message</span><span class="sxs-lookup"><span data-stu-id="438f6-102">How to: Implement Content-Based Routing Using Message Context Properties</span></span>
## <a name="goal"></a><span data-ttu-id="438f6-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="438f6-103">Goal</span></span>  
 <span data-ttu-id="438f6-104">Cette section montre comment utiliser le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Concepteur de feuille de route pour créer un itinéraire qui sélectionne un destinataire de message en fonction de la propriété de contexte de message, puis achemine un message vers ce destinataire à l’aide de l’itinéraire Service Broker pour les service de messagerie.</span><span class="sxs-lookup"><span data-stu-id="438f6-104">This section demonstrates how to use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Itinerary Designer to create an itinerary that selects a message recipient based on the message context property and then routes a message to that recipient using the Itinerary Broker messaging service.</span></span>  
  
 <span data-ttu-id="438f6-105">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-105">In this topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="438f6-106">Créer un itinéraire avec un broker d’itinéraire et les deux services de routage avec des programmes de résolution statiques.</span><span class="sxs-lookup"><span data-stu-id="438f6-106">Create an itinerary with an itinerary broker and two routing services with static resolvers.</span></span>  
  
-   <span data-ttu-id="438f6-107">Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="438f6-107">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="438f6-108">Aucun service broker basé sur l’orchestration n’est fournie dans l’implémentation actuelle.</span><span class="sxs-lookup"><span data-stu-id="438f6-108">No orchestration-based broker service is provided in the current implementation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="438f6-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="438f6-109">Prerequisites</span></span>  
 <span data-ttu-id="438f6-110">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="438f6-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="438f6-111">Étapes</span><span class="sxs-lookup"><span data-stu-id="438f6-111">Steps</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="438f6-112">Pour créer un modèle ESB itinéraire DSL</span><span class="sxs-lookup"><span data-stu-id="438f6-112">To create an ESB Itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="438f6-113">Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="438f6-113">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="438f6-114">Dans l’Explorateur de solutions, cliquez sur **ItineraryLibrary**, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="438f6-114">In Solution Explorer, right-click **ItineraryLibrary**, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="438f6-115">Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **ItineraryDsl** dans le volet Modèles.</span><span class="sxs-lookup"><span data-stu-id="438f6-115">In the **Add New Item** dialog box, click **ItineraryDsl** in the Templates pane.</span></span>  
  
4.  <span data-ttu-id="438f6-116">Dans le **nom** , tapez **ChoiceRouter**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="438f6-116">In the **Name** box, type **ChoiceRouter**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="438f6-117">Pour configurer les propriétés de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="438f6-117">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="438f6-118">Dans Visual Studio, cliquez sur l’aire de conception de la **ChoiceRouter** itinéraire.</span><span class="sxs-lookup"><span data-stu-id="438f6-118">In Visual Studio, click the design surface of the **ChoiceRouter** itinerary.</span></span> <span data-ttu-id="438f6-119">Dans le **ChoiceRouter** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-119">In the **ChoiceRouter** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-120">Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-120">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="438f6-121">Dans le **extendeur paramètres** , cliquez sur le bouton de sélection (...) à côté du **fichier XML de la feuille de route** propriété.</span><span class="sxs-lookup"><span data-stu-id="438f6-121">In the **Extender Settings** section, click the ellipsis button (...) next to the **Itinerary XML file** property.</span></span>  
  
    3.  <span data-ttu-id="438f6-122">Dans le **exporter un Mode** liste de propriétés de liste déroulante, cliquez sur **Strict**.</span><span class="sxs-lookup"><span data-stu-id="438f6-122">In the **Export Mode** property drop-down list, click **Strict**.</span></span>  
  
    4.  <span data-ttu-id="438f6-123">Dans le **sélectionner un fichier XML** boîte de dialogue, tapez **C:\HowTos\Itineraries\ChoiceRouter** dans les **nom de fichier** zone, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="438f6-123">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\ChoiceRouter** in the **File name** box, and then click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="438f6-124">Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local.</span><span class="sxs-lookup"><span data-stu-id="438f6-124">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="438f6-125">En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, vous pouvez tester l’itinéraire à l’aide de l’application cliente de Test ESB.</span><span class="sxs-lookup"><span data-stu-id="438f6-125">By exporting an itinerary to a local file location, instead of to the itinerary database, you can test the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="438f6-126">Vous pourrez terminer cette procédure plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="438f6-126">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="438f6-127">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="438f6-127">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="438f6-128">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="438f6-128">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="438f6-129">Dans la fenêtre Propriétés de OnRamp1, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-129">In the OnRamp1 Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-130">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="438f6-130">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="438f6-131">Dans le **extendeur** la liste déroulante, cliquez sur **extendeur de rampe d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="438f6-131">In the **Extender** drop-down list, click **On-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="438f6-132">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="438f6-132">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="438f6-133">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="438f6-133">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="438f6-134">Dans la boîte à outils, faites glisser un **itinéraire Service Broker Service** élément à l’aire du Concepteur de modèle, puis placez-le à droite de la **rampe d’entrée** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-134">From the Toolbox, drag an **Itinerary Broker Service** model element to the designer surface, and then place it to the right side of the **On-Ramp** model element.</span></span> <span data-ttu-id="438f6-135">Dans le **ItineraryBrokerService1**, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-135">In the **ItineraryBrokerService1**, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-136">Cliquez sur le **nom** propriété, puis tapez **RouteBrokerService**.</span><span class="sxs-lookup"><span data-stu-id="438f6-136">Click the **Name** property, and then type **RouteBrokerService**.</span></span>  
  
    2.  <span data-ttu-id="438f6-137">Dans le **extendeur** la liste déroulante, cliquez sur **extendeur de service Broker de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="438f6-137">In the **Extender** drop-down list, click **Messaging Broker Extender**.</span></span>  
  
    3.  <span data-ttu-id="438f6-138">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="438f6-138">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="438f6-139">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Itinerary.Services.Broker.MessagingBroker**.</span><span class="sxs-lookup"><span data-stu-id="438f6-139">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Itinerary.Services.Broker.MessagingBroker**.</span></span>  
  
3.  <span data-ttu-id="438f6-140">Cliquez sur le **filtre** collection, puis cliquez sur **ajouter un nouveau filtre**.</span><span class="sxs-lookup"><span data-stu-id="438f6-140">Right-click the **Filter** collection, and then click **Add new Filter**.</span></span> <span data-ttu-id="438f6-141">Dans le **Filter1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-141">In the **Filter1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-142">Cliquez sur le **nom** propriété, puis tapez **ASMXFilter**.</span><span class="sxs-lookup"><span data-stu-id="438f6-142">Click the **Name** property, and then type **ASMXFilter**.</span></span>  
  
    2.  <span data-ttu-id="438f6-143">Cliquez sur le **filtre** implémentation d’un menu déroulant, puis cliquez sur **filtre XPath**.</span><span class="sxs-lookup"><span data-stu-id="438f6-143">Click the **Filter** Implementation drop-down list, and then click **XPath Filter**.</span></span>  
  
    3.  <span data-ttu-id="438f6-144">Cliquez sur le **Expression** propriété, puis tapez **count (ContextProperties/propriété [@name= 'InboundTransportLocation'] [contient (., 'ProcessItinerary.asmx')]) > 0**.</span><span class="sxs-lookup"><span data-stu-id="438f6-144">Click the **Expression** property, and then type **count(/ContextProperties/Property[@name='InboundTransportLocation'][contains(., 'ProcessItinerary.asmx')]) > 0**.</span></span>  
  
4.  <span data-ttu-id="438f6-145">Cliquez sur le **filtre** collection, puis cliquez sur **ajouter un nouveau filtre**.</span><span class="sxs-lookup"><span data-stu-id="438f6-145">Right-click the **Filter** collection, and then click **Add new Filter**.</span></span> <span data-ttu-id="438f6-146">Dans le **Filter1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-146">In the **Filter1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-147">Cliquez sur le **nom** propriété, puis tapez **WCFFilter**.</span><span class="sxs-lookup"><span data-stu-id="438f6-147">Click the **Name** property, and then type **WCFFilter**.</span></span>  
  
    2.  <span data-ttu-id="438f6-148">Cliquez sur le **implémentation de filtre** liste déroulante, puis cliquez sur **filtre XPath**.</span><span class="sxs-lookup"><span data-stu-id="438f6-148">Click the **Filter Implementation** drop-down list, and click **XPath Filter**.</span></span>  
  
    3.  <span data-ttu-id="438f6-149">Cliquez sur le **Expression** propriété, puis tapez **count (ContextProperties/propriété [@name= 'InboundTransportLocation'] [contient (., ' ESB. ItineraryServices.WCF')]) > 0**.</span><span class="sxs-lookup"><span data-stu-id="438f6-149">Click the **Expression** property, and then type **count(/ContextProperties/Property[@name='InboundTransportLocation'][contains(., 'ESB.ItineraryServices.WCF')]) > 0**.</span></span>  
  
5.  <span data-ttu-id="438f6-150">Avec le bouton droit le **résolveur** collection de la **RouteBrokerService** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="438f6-150">Right-click the **Resolver** collection of the **RouteBrokerService** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="438f6-151">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-151">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-152">Cliquez sur le **nom** propriété, puis tapez **ResolverBrokerRoute**.</span><span class="sxs-lookup"><span data-stu-id="438f6-152">Click the **Name** property, and then type **ResolverBrokerRoute**.</span></span>  
  
    2.  <span data-ttu-id="438f6-153">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **MessageContext programme de résolution d’Extension**.</span><span class="sxs-lookup"><span data-stu-id="438f6-153">In the **Resolver Implementation** drop-down list, click **MessageContext Resolver Extension**.</span></span>  
  
6.  <span data-ttu-id="438f6-154">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-154">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="438f6-155">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteBrokerService** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-155">Drag a connection from the **ReceiveNAOrder** model element to the **RouteBrokerService** model element.</span></span>  
  
7.  <span data-ttu-id="438f6-156">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle et placez-le sous le **RouteBrokerService** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-156">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it under the **RouteBrokerService** model element.</span></span> <span data-ttu-id="438f6-157">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-157">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-158">Cliquez sur le **nom** propriété, puis tapez **RouteToFileFromASMX**.</span><span class="sxs-lookup"><span data-stu-id="438f6-158">Click the **Name** property, and then type **RouteToFileFromASMX**.</span></span>  
  
    2.  <span data-ttu-id="438f6-159">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="438f6-159">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="438f6-160">Cette propriété définit que le processus a lieu dans un pipeline (messagerie).</span><span class="sxs-lookup"><span data-stu-id="438f6-160">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="438f6-161">Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-161">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="438f6-162">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="438f6-162">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="438f6-163">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.</span><span class="sxs-lookup"><span data-stu-id="438f6-163">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
8.  <span data-ttu-id="438f6-164">Avec le bouton droit le **résolveur** collection de la **RouteToFileFromASMX** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="438f6-164">Right-click the **Resolver** collection of the **RouteToFileFromASMX** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="438f6-165">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-165">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-166">Cliquez sur le **nom** propriété, puis tapez **ResolverFromAsmx**.</span><span class="sxs-lookup"><span data-stu-id="438f6-166">Click the **Name** property, and then type **ResolverFromAsmx**.</span></span>  
  
    2.  <span data-ttu-id="438f6-167">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="438f6-167">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="438f6-168">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="438f6-168">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="438f6-169">Cliquez sur le **Transport emplacement** propriété, puis tapez **c:\howtos\out\asmx%MessageId%.xml**.</span><span class="sxs-lookup"><span data-stu-id="438f6-169">Click the **Transport Location** property, and then type **c:\howtos\out\asmx%MessageId%.xml**.</span></span>  
  
9. <span data-ttu-id="438f6-170">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **RouteToFileFromASMX** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-170">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteToFileFromASMX** model element.</span></span> <span data-ttu-id="438f6-171">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-171">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-172">Cliquez sur le **nom** propriété, puis tapez **SendASMXOrder**.</span><span class="sxs-lookup"><span data-stu-id="438f6-172">Click the **Name** property, and then type **SendASMXOrder**.</span></span>  
  
    2.  <span data-ttu-id="438f6-173">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-173">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="438f6-174">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="438f6-174">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="438f6-175">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="438f6-175">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
10. <span data-ttu-id="438f6-176">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **RouteToFileFromASMX** élément de modèle et la **SendASMXOrder**élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-176">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteToFileFromASMX** model element and the **SendASMXOrder** model element.</span></span> <span data-ttu-id="438f6-177">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-177">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-178">Cliquez sur le **nom** propriété, puis tapez **SendPortFilterASMX**.</span><span class="sxs-lookup"><span data-stu-id="438f6-178">Click the **Name** property, and then type **SendPortFilterASMX**.</span></span>  
  
    2.  <span data-ttu-id="438f6-179">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-179">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="438f6-180">Dans le **rampe** déroulante liste, développez **SendASMXOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="438f6-180">In the **Off-Ramp** drop-down list, expand **SendASMXOrder**, and then click **Send Handlers**.</span></span>  
  
11. <span data-ttu-id="438f6-181">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-181">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="438f6-182">Faites glisser une connexion à partir de la **RouteToFileFromASMX** élément de modèle à la **SendPortFilterASMX** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-182">Drag a connection from the **RouteToFileFromASMX** model element to the **SendPortFilterASMX** model element.</span></span>  
  
12. <span data-ttu-id="438f6-183">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-183">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="438f6-184">Faites glisser une connexion à partir de la **SendPortFilterASMX** élément de modèle à la **SendASMXOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-184">Drag a connection from the **SendPortFilterASMX** model element to the **SendASMXOrder** model element.</span></span>  
  
13. <span data-ttu-id="438f6-185">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de **RouteBrokerService** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-185">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of **RouteBrokerService** model element.</span></span> <span data-ttu-id="438f6-186">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-186">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-187">Cliquez sur le **nom** propriété, puis tapez **RouteToFileFromWCF**.</span><span class="sxs-lookup"><span data-stu-id="438f6-187">Click the **Name** property, and then type **RouteToFileFromWCF**.</span></span>  
  
    2.  <span data-ttu-id="438f6-188">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="438f6-188">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="438f6-189">Cette propriété définit que le processus a lieu dans un pipeline (messagerie).</span><span class="sxs-lookup"><span data-stu-id="438f6-189">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="438f6-190">Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-190">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="438f6-191">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="438f6-191">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="438f6-192">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.</span><span class="sxs-lookup"><span data-stu-id="438f6-192">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
14. <span data-ttu-id="438f6-193">Avec le bouton droit le **résolveur** collection de la **RouteToFileFromWCF** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="438f6-193">Right-click the **Resolver** collection of the **RouteToFileFromWCF** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="438f6-194">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-194">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-195">Cliquez sur le **nom** propriété, puis tapez **ResolverFromWCF**.</span><span class="sxs-lookup"><span data-stu-id="438f6-195">Click the **Name** property, and then type **ResolverFromWCF**.</span></span>  
  
    2.  <span data-ttu-id="438f6-196">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="438f6-196">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="438f6-197">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="438f6-197">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="438f6-198">Cliquez sur le **Transport emplacement** propriété, puis tapez **c:\howtos\out\wcf%MessageId%.xml**.</span><span class="sxs-lookup"><span data-stu-id="438f6-198">Click the **Transport Location** property, and then type **c:\howtos\out\wcf%MessageId%.xml**.</span></span>  
  
15. <span data-ttu-id="438f6-199">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **RouteToFileFromWCF** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-199">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteToFileFromWCF** model element.</span></span> <span data-ttu-id="438f6-200">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-200">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-201">Cliquez sur le **nom** propriété, puis tapez **SendWCFOrder**.</span><span class="sxs-lookup"><span data-stu-id="438f6-201">Click the **Name** property, and then type **SendWCFOrder**.</span></span>  
  
    2.  <span data-ttu-id="438f6-202">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-202">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="438f6-203">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="438f6-203">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="438f6-204">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="438f6-204">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
16. <span data-ttu-id="438f6-205">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **RouteToFileFromWCF** élément de modèle et la **SendWCFOrder**élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-205">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteToFileFromWCF** model element and the **SendWCFOrder** model element.</span></span> <span data-ttu-id="438f6-206">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-206">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-207">Cliquez sur le **nom** propriété, puis tapez **SendPortFilterWCF**.</span><span class="sxs-lookup"><span data-stu-id="438f6-207">Click the **Name** property, and then type **SendPortFilterWCF**.</span></span>  
  
    2.  <span data-ttu-id="438f6-208">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-208">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="438f6-209">Dans le **rampe** déroulante liste, développez **SendWCFOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="438f6-209">In the **Off-Ramp** drop-down list, expand **SendWCFOrder**, and then click **Send Handlers**.</span></span>  
  
17. <span data-ttu-id="438f6-210">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-210">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="438f6-211">Faites glisser une connexion à partir de la **RouteToFileFromWCF** élément de modèle à la **SendPortFilterWCF** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-211">Drag a connection from the **RouteToFileFromWCF** model element to the **SendPortFilterWCF** model element.</span></span>  
  
18. <span data-ttu-id="438f6-212">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-212">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="438f6-213">Faites glisser une connexion à partir de la **SendPortFilterWCF** élément de modèle à la **SendWCFOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-213">Drag a connection from the **SendPortFilterWCF** model element to the **SendWCFOrder** model element.</span></span>  
  
19. <span data-ttu-id="438f6-214">Dans la boîte à outils, faites glisser un **itinéraire Outport** élément de modèle à la bordure droite de **RouteBrokerService**.</span><span class="sxs-lookup"><span data-stu-id="438f6-214">From the Toolbox, drag an **Itinerary Outport** model element to right border of **RouteBrokerService**.</span></span> <span data-ttu-id="438f6-215">Dans le **ItineraryBrokerOutPort1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-215">In the **ItineraryBrokerOutPort1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-216">Cliquez sur le **nom** propriété, puis tapez **Port WCF**.</span><span class="sxs-lookup"><span data-stu-id="438f6-216">Click the **Name** property, and then type **WCF Port**.</span></span>  
  
    2.  <span data-ttu-id="438f6-217">Dans le **filtre** la liste déroulante, cliquez sur **WCFFilter**.</span><span class="sxs-lookup"><span data-stu-id="438f6-217">In the **Filter** drop-down list, click **WCFFilter**.</span></span>  
  
    3.  <span data-ttu-id="438f6-218">Dans le **résolveur** la liste déroulante, cliquez sur **ResolverBrokerRoute**.</span><span class="sxs-lookup"><span data-stu-id="438f6-218">In the **Resolver** drop-down list, click **ResolverBrokerRoute**.</span></span>  
  
20. <span data-ttu-id="438f6-219">Dans la boîte à outils, faites glisser un **itinéraire Outport** élément de modèle à la bordure inférieure de **RouteBrokerService**.</span><span class="sxs-lookup"><span data-stu-id="438f6-219">From the Toolbox, drag an **Itinerary Outport** model element to the bottom border of **RouteBrokerService**.</span></span> <span data-ttu-id="438f6-220">Dans le **ItineraryBrokerOutPort1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-220">In the **ItineraryBrokerOutPort1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="438f6-221">Cliquez sur le **nom** propriété, puis tapez **ASMX Port**.</span><span class="sxs-lookup"><span data-stu-id="438f6-221">Click the **Name** property, and then type **ASMX Port**.</span></span>  
  
    2.  <span data-ttu-id="438f6-222">Dans le **filtre** la liste déroulante, cliquez sur **ASMXFilter**.</span><span class="sxs-lookup"><span data-stu-id="438f6-222">In the **Filter** drop-down list, click **ASMXFilter**.</span></span>  
  
    3.  <span data-ttu-id="438f6-223">Dans le **résolveur** la liste déroulante, cliquez sur **ResolverBrokerRoute**.</span><span class="sxs-lookup"><span data-stu-id="438f6-223">In the **Resolver** drop-down list, click **ResolverBrokerRoute**.</span></span>  
  
21. <span data-ttu-id="438f6-224">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-224">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="438f6-225">Faites glisser une connexion à partir de la **Port WCF** élément de modèle à la **RouteToFileFromWCF** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-225">Drag a connection from the **WCF Port** model element to the **RouteToFileFromWCF** model element.</span></span>  
  
22. <span data-ttu-id="438f6-226">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="438f6-226">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="438f6-227">Faites glisser une connexion à partir de la **ASMX Port** élément de modèle à la **RouteToFileFromASMX** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="438f6-227">Drag a connection from the **ASMX Port** model element to the **RouteToFileFromASMX** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="438f6-228">Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="438f6-228">To export the model for use with the Itinerary Test Client</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="438f6-229">Vous devez exporter la feuille de route à deux reprises : une fois au format XML et une heure à la base de données pour tester le routage via le service broker.</span><span class="sxs-lookup"><span data-stu-id="438f6-229">You will need to export the itinerary twice: one time in XML and one time to the database to test the routing through the broker.</span></span>  
  
1.  <span data-ttu-id="438f6-230">Dans Visual Studio, cliquez sur l’aire de conception de la **ChoiceRouter** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="438f6-230">In Visual Studio, right-click the design surface of the **ChoiceRouter** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="438f6-231">La version XML de l’itinéraire s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="438f6-231">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="438f6-232">Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (ChoiceRouter.xml).</span><span class="sxs-lookup"><span data-stu-id="438f6-232">In Windows Explorer, browse to C:\HowTos\Itineraries, and then notice the creation of your itinerary XML (ChoiceRouter.xml).</span></span>  
  
3.  <span data-ttu-id="438f6-233">Dans Visual Studio, cliquez sur l’aire de conception de la **ChoiceRouter** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="438f6-233">In Visual Studio, right-click the design surface of the **ChoiceRouter** itinerary, and then click **Export Model**.</span></span>  
  
4.  <span data-ttu-id="438f6-234">Dans la fenêtre Propriétés, cliquez sur **exportateur de feuille de route de base de données** dans les **modèle exportateur** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="438f6-234">In the Properties window, click **Database Itinerary Exporter** in the **Model Exporter** drop-down list.</span></span>  
  
5.  <span data-ttu-id="438f6-235">Dans la fenêtre Propriétés, définissez la **base de données de la feuille de route** chaîne de connexion de propriété pour pointer vers la base de données d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="438f6-235">In the Properties window, set the **Itinerary Database** property connection string to point to the itinerary database.</span></span>  
  
6.  <span data-ttu-id="438f6-236">Dans le **état de la feuille de route** propriété liste déroulante, sélectionnez **déployées**.</span><span class="sxs-lookup"><span data-stu-id="438f6-236">In the **Itinerary Status** property drop-down list select **Deployed**.</span></span>  
  
7.  <span data-ttu-id="438f6-237">Dans Visual Studio, cliquez sur l’aire de conception de la **ChoiceRouter** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="438f6-237">In Visual Studio, right-click the design surface of the **ChoiceRouter** itinerary, and then click **Export Model**.</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="438f6-238">Pour tester la feuille de route</span><span class="sxs-lookup"><span data-stu-id="438f6-238">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="438f6-239">Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).</span><span class="sxs-lookup"><span data-stu-id="438f6-239">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="438f6-240">Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="438f6-240">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="438f6-241">Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="438f6-241">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="438f6-242">Sélectionnez **ChoiceRouter.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="438f6-242">Select **ChoiceRouter.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="438f6-243">Cliquez sur **OK** pour fermer le message « Itinéraire chargé avec succès ».</span><span class="sxs-lookup"><span data-stu-id="438f6-243">Click **OK** to close the "Itinerary Loaded Successfully" message.</span></span>  
  
5.  <span data-ttu-id="438f6-244">Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="438f6-244">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="438f6-245">Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\Patterns\HowTos.</span><span class="sxs-lookup"><span data-stu-id="438f6-245">In the **Select XML Document to load** dialog box, browse to C:\Patterns\HowTos.</span></span> <span data-ttu-id="438f6-246">Sélectionnez NAOrderDoc.xml, puis cliquez sur **ouvrir** pour le message de test de charge.</span><span class="sxs-lookup"><span data-stu-id="438f6-246">Select NAOrderDoc.xml, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="438f6-247">Cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="438f6-247">Click the **Submit Request** button.</span></span> <span data-ttu-id="438f6-248">Une fois le test terminé, cliquez sur **OK** pour fermer le message de confirmation qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="438f6-248">When the test completes, click **OK** to close the confirmation message that appears.</span></span>  
  
8.  <span data-ttu-id="438f6-249">Dans l’Explorateur Windows, accédez à C:\HowTos\Out. Vérifiez que les messages ASMX%MessageID%.xml ont été écrits dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="438f6-249">In Windows Explorer, browse to C:\HowTos\Out. Verify that the ASMX%MessageID%.xml messages have been written to this directory.</span></span>  
  
9. <span data-ttu-id="438f6-250">Cliquez sur le client de Test de la feuille de route **utiliser le Service WCF** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="438f6-250">Click the Itinerary Test client **Use WCF Service** check box.</span></span> <span data-ttu-id="438f6-251">Dans le **nom d’itinéraire** , tapez **ChoiceRouter**, puis cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="438f6-251">In the **Itinerary Name** box, type **ChoiceRouter**, and then click the **Submit Request** button.</span></span> <span data-ttu-id="438f6-252">Une fois le test terminé, cliquez sur **OK** pour fermer le message de confirmation.</span><span class="sxs-lookup"><span data-stu-id="438f6-252">When the test completes, click **OK** to close the confirmation message.</span></span>  
  
10. <span data-ttu-id="438f6-253">Dans l’Explorateur Windows, accédez à C:\HowTos\Out. Vérifiez que les messages WCF%MessageID%.xml ont été écrits dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="438f6-253">In Windows Explorer, browse to C:\HowTos\Out. Verify that the WCF%MessageID%.xml messages have been written to this directory.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="438f6-254">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="438f6-254">Additional Resources</span></span>  
 <span data-ttu-id="438f6-255">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="438f6-255">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="438f6-256">Guide pratique pour sélectionner un itinéraire à l’aide d’une stratégie de règles métier</span><span class="sxs-lookup"><span data-stu-id="438f6-256">How to: Select an Itinerary Using a Business Rules Policy</span></span>](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [<span data-ttu-id="438f6-257">Guide pratique pour router un message en fonction de son contexte à l’aide d’une stratégie de règles métier</span><span class="sxs-lookup"><span data-stu-id="438f6-257">How to: Dynamically Route a Message Based on Message Context Using a Business Rules Policy</span></span>](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
-   [<span data-ttu-id="438f6-258">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="438f6-258">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="438f6-259">Modèles de routage des messages</span><span class="sxs-lookup"><span data-stu-id="438f6-259">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)