---
title: "Comment : router un Message unique à plusieurs destinataires à l’aide d’un bon d’itinéraire de routage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c30493-4fe1-4fd5-8bc7-af091535b091
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fa96603bc93c9d5d19ef102695a1189a50d00ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip"></a><span data-ttu-id="f5f3a-102">Comment : router un Message unique à plusieurs destinataires à l’aide d’un bon d’itinéraire de routage</span><span class="sxs-lookup"><span data-stu-id="f5f3a-102">How to: Route a Single Message to Multiple Recipients Using an Itinerary Routing Slip</span></span>
## <a name="goal"></a><span data-ttu-id="f5f3a-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="f5f3a-103">Goal</span></span>  
 <span data-ttu-id="f5f3a-104">Cette section montre comment utiliser le langage spécifique à un domaine (DSL), concepteur pour créer un itinéraire qui route un message à trois destinataires distinctes à l’aide d’un programme de résolution statique et [!INCLUDE[prague](../includes/prague-md.md)] adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-104">This section demonstrates how to use the Designer domain-specific language (DSL) to create an itinerary that routes a message to three distinct recipients using a static resolver and the [!INCLUDE[prague](../includes/prague-md.md)] FILE adapter.</span></span>  
  
 <span data-ttu-id="f5f3a-105">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5f3a-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="f5f3a-106">Créer un itinéraire avec trois programmes de résolution statiques pour router les messages à plusieurs destinataires.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-106">Create an itinerary with three static resolvers to route messages to multiple recipients.</span></span>  
  
-   <span data-ttu-id="f5f3a-107">Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-107">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f5f3a-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f5f3a-108">Prerequisites</span></span>  
 <span data-ttu-id="f5f3a-109">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="f5f3a-109">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="f5f3a-110">Étapes</span><span class="sxs-lookup"><span data-stu-id="f5f3a-110">Steps</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="f5f3a-111">Pour créer un modèle DSL de la feuille de route ESB</span><span class="sxs-lookup"><span data-stu-id="f5f3a-111">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="f5f3a-112">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-112">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="f5f3a-113">Dans l’Explorateur de solutions, cliquez sur **ItineraryLibrary**, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-113">In Solution Explorer, right-click **ItineraryLibrary**, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="f5f3a-114">Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **ItineraryDsl** dans le volet Modèles.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-114">In the **Add New Item** dialog box, click **ItineraryDsl** in the Templates pane.</span></span>  
  
4.  <span data-ttu-id="f5f3a-115">Dans le **nom** , tapez **RecipientList**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-115">In the **Name** box, type **RecipientList**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="f5f3a-116">Pour configurer les propriétés de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="f5f3a-116">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="f5f3a-117">Dans Visual Studio, cliquez sur l’aire de conception de RecipientList.itinerary.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-117">In Visual Studio, click the design surface of RecipientList.itinerary.</span></span> <span data-ttu-id="f5f3a-118">Dans la fenêtre Propriétés de RecipientList, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5f3a-118">In the RecipientList Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f5f3a-119">Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-119">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="f5f3a-120">Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="f5f3a-120">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="f5f3a-121">Dans le **sélectionner un fichier XML** boîte de dialogue le **nom de fichier** , tapez **C:\HowTos\Itineraries\RecipientList**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-121">In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\RecipientList**, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f5f3a-122">Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-122">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="f5f3a-123">En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-123">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="f5f3a-124">Vous pourrez terminer cette procédure plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-124">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="f5f3a-125">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="f5f3a-125">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="f5f3a-126">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-126">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="f5f3a-127">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5f3a-127">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f5f3a-128">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-128">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="f5f3a-129">Dans le **extendeur** la liste déroulante, cliquez sur **extendeur de rampe d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-129">In the **Extender** drop-down list, click **On-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="f5f3a-130">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-130">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="f5f3a-131">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-131">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="f5f3a-132">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de la **rampe d’entrée** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-132">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="f5f3a-133">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5f3a-133">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f5f3a-134">Cliquez sur le **nom** propriété, puis tapez **RouteToThreeRecipients**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-134">Click the **Name** property, and then type **RouteToThreeRecipients**.</span></span>  
  
    2.  <span data-ttu-id="f5f3a-135">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-135">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f5f3a-136">Cette propriété définit que le processus a lieu dans un pipeline (messagerie).</span><span class="sxs-lookup"><span data-stu-id="f5f3a-136">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="f5f3a-137">Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-137">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="f5f3a-138">Dans le **conteneur** déroulante liste, développez **ReceiveNaOrderDoc**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-138">In the **Container** drop-down list, expand **ReceiveNaOrderDoc**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="f5f3a-139">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-139">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
3.  <span data-ttu-id="f5f3a-140">Avec le bouton droit le **résolveur** collection de la **RouteToThreeRecipients** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-140">Right-click the **Resolver** collection of the **RouteToThreeRecipients** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="f5f3a-141">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5f3a-141">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f5f3a-142">Cliquez sur le **nom** propriété, puis tapez **FirstResolver**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-142">Click the **Name** property, and then type **FirstResolver**.</span></span>  
  
    2.  <span data-ttu-id="f5f3a-143">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-143">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="f5f3a-144">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-144">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="f5f3a-145">Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\First%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-145">Click the **Transport Location** property, and then type **C:\HowTos\Out\First%MessageID%.xml**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f5f3a-146">Vous avez ajouté la première des trois programmes de résolution de ce service d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-146">You have added the first of three resolvers for this itinerary service.</span></span> <span data-ttu-id="f5f3a-147">Vous allez maintenant ajouter les deux programmes de résolution plus pour acheminer le message à des destinataires supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-147">You will now add two more resolvers to route the message to additional recipients.</span></span>  
  
4.  <span data-ttu-id="f5f3a-148">Avec le bouton droit le **résolveur** collection de la **RouteToThreeRecipients** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-148">Right-click the **Resolver** collection of the **RouteToThreeRecipients** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="f5f3a-149">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5f3a-149">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f5f3a-150">Cliquez sur le **nom** propriété, puis tapez **SecondResolver**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-150">Click the **Name** property, and then type **SecondResolver**.</span></span>  
  
    2.  <span data-ttu-id="f5f3a-151">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-151">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="f5f3a-152">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-152">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="f5f3a-153">Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\Second%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-153">Click the **Transport Location** property, and then type **C:\HowTos\Out\Second%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="f5f3a-154">Avec le bouton droit le **résolveur** collection de la **RouteToThreeRecipients** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-154">Right-click the **Resolver** collection of the **RouteToThreeRecipients** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="f5f3a-155">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5f3a-155">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f5f3a-156">Cliquez sur le **nom** propriété, puis tapez **ThirdResolver**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-156">Click the **Name** property, and then type **ThirdResolver**.</span></span>  
  
    2.  <span data-ttu-id="f5f3a-157">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-157">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="f5f3a-158">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-158">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="f5f3a-159">Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\Third%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-159">Click the **Transport Location** property, and then type **C:\HowTos\Out\Third%MessageID%.xml**.</span></span>  
  
6.  <span data-ttu-id="f5f3a-160">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-160">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="f5f3a-161">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteToThreeRecipients** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-161">Drag a connection from the **ReceiveNAOrder** model element to the **RouteToThreeRecipients** model element.</span></span>  
  
7.  <span data-ttu-id="f5f3a-162">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **RouteToThreeRecipients** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-162">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteToThreeRecipients** model element.</span></span> <span data-ttu-id="f5f3a-163">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5f3a-163">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f5f3a-164">Cliquez sur le **nom** propriété, puis tapez **SendThreeMessages**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-164">Click the **Name** property, and then type **SendThreeMessages**.</span></span>  
  
    2.  <span data-ttu-id="f5f3a-165">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-165">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="f5f3a-166">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-166">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="f5f3a-167">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-167">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
8.  <span data-ttu-id="f5f3a-168">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **RouteToThreeRecipients** élément de modèle et la **SendThreeMessages** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-168">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteToThreeRecipients** model element and the **SendThreeMessages** model element.</span></span> <span data-ttu-id="f5f3a-169">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5f3a-169">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f5f3a-170">Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-170">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="f5f3a-171">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-171">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="f5f3a-172">Dans le **rampe** déroulante liste, développez **SendThreeMessages**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-172">In the **Off-Ramp** drop-down list, expand **SendThreeMessages**, and then click **Send Handlers**.</span></span>  
  
9. <span data-ttu-id="f5f3a-173">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-173">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="f5f3a-174">Faites glisser une connexion à partir de la **RouteToThreeRecipients** élément de modèle à la **SendPortFilter** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-174">Drag a connection from the **RouteToThreeRecipients** model element to the **SendPortFilter** model element.</span></span>  
  
10. <span data-ttu-id="f5f3a-175">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-175">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="f5f3a-176">Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendThreeMessages** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-176">Drag a connection from the **SendPortFilter** model element to the **SendThreeMessages** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="f5f3a-177">Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="f5f3a-177">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="f5f3a-178">Dans Visual Studio, cliquez sur l’aire de conception de la **RecipientList** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-178">In Visual Studio, right-click the design surface of the **RecipientList** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f5f3a-179">La version XML de l’itinéraire s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-179">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f5f3a-180">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-180">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="f5f3a-181">Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (RecipientList.xml).</span><span class="sxs-lookup"><span data-stu-id="f5f3a-181">In Windows Explorer, browse to C:\HowTos\Itineraries, and then notice the creation of your itinerary XML (RecipientList.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="f5f3a-182">Pour tester la feuille de route</span><span class="sxs-lookup"><span data-stu-id="f5f3a-182">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="f5f3a-183">Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).</span><span class="sxs-lookup"><span data-stu-id="f5f3a-183">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="f5f3a-184">Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-184">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="f5f3a-185">Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-185">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="f5f3a-186">Sélectionnez **RecipientList.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-186">Select **RecipientList.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="f5f3a-187">Cliquez sur **OK** pour effacer le « itinéraire a été chargé avec succès : message.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-187">Click **OK** to clear the "Itinerary Loaded Successfully: message.</span></span>  
  
5.  <span data-ttu-id="f5f3a-188">Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-188">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="f5f3a-189">Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\Patterns.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-189">In the **Select XML Document to load** dialog box, browse to C:\Patterns.</span></span> <span data-ttu-id="f5f3a-190">Sélectionnez NAOrderDoc.xml, puis cliquez sur **ouvrir** pour le message de test de charge.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-190">Select NAOrderDoc.xml, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="f5f3a-191">Cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-191">Click the **Submit Request** button.</span></span> <span data-ttu-id="f5f3a-192">Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-192">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="f5f3a-193">Dans l’Explorateur Windows, accédez à C:\HowTos\Out\\.</span><span class="sxs-lookup"><span data-stu-id="f5f3a-193">In Windows Explorer, browse to C:\HowTos\Out\\.</span></span> <span data-ttu-id="f5f3a-194">Vérifiez que les messages suivants ont été écrits dans le répertoire :</span><span class="sxs-lookup"><span data-stu-id="f5f3a-194">Verify that the following messages have been written to the directory:</span></span>  
  
    -   <span data-ttu-id="f5f3a-195">First%MessageID%.Xml</span><span class="sxs-lookup"><span data-stu-id="f5f3a-195">First%MessageID%.xml</span></span>  
  
    -   <span data-ttu-id="f5f3a-196">Second%MessageID%.Xml</span><span class="sxs-lookup"><span data-stu-id="f5f3a-196">Second%MessageID%.xml</span></span>  
  
    -   <span data-ttu-id="f5f3a-197">Third%MessageID%.Xml</span><span class="sxs-lookup"><span data-stu-id="f5f3a-197">Third%MessageID%.xml</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="f5f3a-198">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f5f3a-198">Additional Resources</span></span>  
 <span data-ttu-id="f5f3a-199">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5f3a-199">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="f5f3a-200">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="f5f3a-200">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="f5f3a-201">Modèles de routage de messages</span><span class="sxs-lookup"><span data-stu-id="f5f3a-201">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)  
  
-   [<span data-ttu-id="f5f3a-202">À l’aide de la résolution dynamique et le routage</span><span class="sxs-lookup"><span data-stu-id="f5f3a-202">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)