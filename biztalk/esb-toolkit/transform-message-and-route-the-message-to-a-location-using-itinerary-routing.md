---
title: "Comment : transformer un Message et router le Message résultant à un emplacement de fichier à l’aide d’une feuille de route bordereau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c27749ba-c228-4cd4-827e-e8009a0c999d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18caef7d7c60fa7aa129baa787c746b3b797c808
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-transform-a-message-and-route-the-resulting-message-to-a-file-location-using-an-itinerary-routing-slip"></a><span data-ttu-id="8a2a6-102">Comment : transformer un Message et router le Message résultant à un emplacement de fichier à l’aide d’un bon d’itinéraire de routage</span><span class="sxs-lookup"><span data-stu-id="8a2a6-102">How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip</span></span>
## <a name="goal"></a><span data-ttu-id="8a2a6-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="8a2a6-103">Goal</span></span>  
 <span data-ttu-id="8a2a6-104">Cette section montre comment utiliser le langage spécifique à un domaine (DSL), ESB concepteur pour créer un itinéraire qui implémente la transformation des messages en appelant un mappage BizTalk, puis il achemine les messages à l’aide de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-104">This section demonstrates how to use the ESB Designer domain-specific language (DSL) to create an itinerary that implements message transformation by invoking a BizTalk map, and then it routes the messages using the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] FILE adapter.</span></span>  
  
 <span data-ttu-id="8a2a6-105">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a2a6-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="8a2a6-106">Créer un bordereau d’itinéraire de routage avec un service d’itinéraire de transformation qui implémente un mappage BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-106">Create an itinerary routing slip with a transform itinerary service that implements a BizTalk map.</span></span>  
  
-   <span data-ttu-id="8a2a6-107">Configurer la feuille de route pour acheminer le message transformé à un emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-107">Configure the itinerary to route the transformed message to a file location.</span></span>  
  
-   <span data-ttu-id="8a2a6-108">Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-108">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8a2a6-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8a2a6-109">Prerequisites</span></span>  
 <span data-ttu-id="8a2a6-110">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="8a2a6-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="8a2a6-111">Étapes</span><span class="sxs-lookup"><span data-stu-id="8a2a6-111">Steps</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="8a2a6-112">Pour créer un modèle DSL de la feuille de route ESB</span><span class="sxs-lookup"><span data-stu-id="8a2a6-112">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="8a2a6-113">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-113">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="8a2a6-114">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-114">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="8a2a6-115">Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **ItineraryDsl** dans le volet Modèles.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-115">In the **Add New Item** dialog box, click **ItineraryDsl** in the Templates pane.</span></span>  
  
4.  <span data-ttu-id="8a2a6-116">Dans le **nom** , tapez **DataModelTransformation**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-116">In the **Name** box, type **DataModelTransformation**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="8a2a6-117">Pour configurer les propriétés de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="8a2a6-117">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="8a2a6-118">Dans Visual Studio, cliquez sur l’aire de conception de **DataModelTransformation.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-118">In Visual Studio, click the design surface of **DataModelTransformation.itinerary**.</span></span> <span data-ttu-id="8a2a6-119">Dans le **DataModelTransformation** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a2a6-119">In the **DataModelTransformation** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8a2a6-120">Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-120">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="8a2a6-121">Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="8a2a6-121">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="8a2a6-122">Dans le **sélectionner un fichier XML** boîte de dialogue le **nom de fichier** , tapez **C:\HowTos\Itineraries\DataModelTransformation**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-122">In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\DataModelTransformation**, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8a2a6-123">Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-123">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="8a2a6-124">En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-124">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="8a2a6-125">Vous pourrez terminer cette procédure plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-125">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="8a2a6-126">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="8a2a6-126">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="8a2a6-127">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-127">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="8a2a6-128">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a2a6-128">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8a2a6-129">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-129">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="8a2a6-130">Dans le **extendeur** la liste déroulante, cliquez sur **Extension du Service ESB rampe d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-130">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="8a2a6-131">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-131">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="8a2a6-132">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-132">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="8a2a6-133">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de la **rampe d’entrée** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-133">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="8a2a6-134">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a2a6-134">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8a2a6-135">Cliquez sur le **nom** propriété, puis tapez **MapNAOrderToCNOrder**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-135">Click the **Name** property, and then type **MapNAOrderToCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="8a2a6-136">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-136">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8a2a6-137">Cette propriété définit que le processus a lieu dans un pipeline (messagerie).</span><span class="sxs-lookup"><span data-stu-id="8a2a6-137">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="8a2a6-138">Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-138">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="8a2a6-139">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-139">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="8a2a6-140">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Transform**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-140">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
3.  <span data-ttu-id="8a2a6-141">Avec le bouton droit le **résolveur** collection de la **MapNAOrderToCNOrder** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-141">Right-click the **Resolver** collection of the **MapNAOrderToCNOrder** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="8a2a6-142">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a2a6-142">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8a2a6-143">Cliquez sur le **nom** propriété, puis tapez **StaticallySpecifyTheMap**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-143">Click the **Name** property, and then type **StaticallySpecifyTheMap**.</span></span>  
  
    2.  <span data-ttu-id="8a2a6-144">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-144">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="8a2a6-145">Dans le **transformer un Type** la liste déroulante, cliquez sur **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-145">In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span></span>  
  
    4.  <span data-ttu-id="8a2a6-146">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-146">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
4.  <span data-ttu-id="8a2a6-147">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-147">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="8a2a6-148">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **MapNAOrderToCNOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-148">Drag a connection from the **ReceiveNAOrder** model element to the **MapNAOrderToCNOrder** model element.</span></span>  
  
5.  <span data-ttu-id="8a2a6-149">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **MapNAOrderToCNOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-149">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **MapNAOrderToCNOrder** model element.</span></span> <span data-ttu-id="8a2a6-150">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a2a6-150">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8a2a6-151">Cliquez sur le **nom** propriété, puis tapez **SendCNOrder**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-151">Click the **Name** property, and then type **SendCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="8a2a6-152">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-152">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="8a2a6-153">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-153">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="8a2a6-154">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-154">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
6.  <span data-ttu-id="8a2a6-155">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **MapNAOrderToCNOrder** élément de modèle et la **SendCNOrder**élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-155">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **MapNAOrderToCNOrder** model element and the **SendCNOrder** model element.</span></span> <span data-ttu-id="8a2a6-156">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a2a6-156">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8a2a6-157">Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-157">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="8a2a6-158">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-158">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="8a2a6-159">Dans le **rampe** déroulante liste, développez **SendCNOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-159">In the **Off-Ramp** drop-down list, expand **SendCNOrder**, and then click **Send Handlers**.</span></span>  
  
7.  <span data-ttu-id="8a2a6-160">Avec le bouton droit le **résolveur** collection de la **SendPortFilter** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-160">Right-click the **Resolver** collection of the **SendPortFilter** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="8a2a6-161">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a2a6-161">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8a2a6-162">Cliquez sur le **nom** propriété, puis tapez **ConfigureFolderSettings**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-162">Click the **Name** property, and then type **ConfigureFolderSettings**.</span></span>  
  
    2.  <span data-ttu-id="8a2a6-163">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-163">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    3.  <span data-ttu-id="8a2a6-164">Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\\%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-164">Click the **Transport Location** property, and then type **C:\HowTos\Out\\%MessageID%.xml**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8a2a6-165">Chaque rampe aura un Service de l’itinéraire associé ; la combinaison des propriétés du Service de l’itinéraire et les propriétés de la rampe définir l’abonnement du port d’envoi dynamique.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-165">Each off-ramp will have an Itinerary Service associated with it; the combination of the Itinerary Service properties and the properties of the off-ramp define the subscription of the dynamic send port.</span></span>  
  
8.  <span data-ttu-id="8a2a6-166">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-166">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="8a2a6-167">Faites glisser une connexion à partir de la **MapNAOrderToCNOrder** élément de modèle à la **SendPortFilter** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-167">Drag a connection from the **MapNAOrderToCNOrder** model element to the **SendPortFilter** model element.</span></span>  
  
9. <span data-ttu-id="8a2a6-168">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-168">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="8a2a6-169">Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendCNOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-169">Drag a connection from the **SendPortFilter** model element to the **SendCNOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="8a2a6-170">Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="8a2a6-170">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="8a2a6-171">Dans Visual Studio, cliquez sur l’aire de conception de la **DataModelTransformation** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-171">In Visual Studio, right-click the design surface of the **DataModelTransformation** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8a2a6-172">La version XML de l’itinéraire s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-172">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="8a2a6-173">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-173">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="8a2a6-174">Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (DataModelTransformation.xml).</span><span class="sxs-lookup"><span data-stu-id="8a2a6-174">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (DataModelTransformation.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="8a2a6-175">Pour tester la feuille de route</span><span class="sxs-lookup"><span data-stu-id="8a2a6-175">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="8a2a6-176">Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).</span><span class="sxs-lookup"><span data-stu-id="8a2a6-176">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="8a2a6-177">Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-177">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="8a2a6-178">Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-178">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="8a2a6-179">Sélectionnez **DataModelTransformation.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-179">Select **DataModelTransformation.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="8a2a6-180">Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-180">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="8a2a6-181">Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-181">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="8a2a6-182">Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-182">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="8a2a6-183">Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-183">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="8a2a6-184">Cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-184">Click the **Submit Request** button.</span></span> <span data-ttu-id="8a2a6-185">Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-185">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="8a2a6-186">Dans l’Explorateur Windows, accédez à C:\HowTos\Out. Vérifiez que le **%MessageID%.xml** message a été écrit dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="8a2a6-186">In Windows Explorer, browse to C:\HowTos\Out. Verify that the **%MessageID%.xml** message has been written to the directory.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="8a2a6-187">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="8a2a6-187">Additional Resources</span></span>  
 <span data-ttu-id="8a2a6-188">Pour plus d’informations, consultez que ces rubriques connexes :</span><span class="sxs-lookup"><span data-stu-id="8a2a6-188">For more information, see these related topics:</span></span>  
  
1.  [<span data-ttu-id="8a2a6-189">Comment : fractionner un échange et de router les Messages résultants vers plusieurs emplacements de fichier à l’aide d’itinéraires distinctes</span><span class="sxs-lookup"><span data-stu-id="8a2a6-189">How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries</span></span>](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)  
  
2.  [<span data-ttu-id="8a2a6-190">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="8a2a6-190">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
3.  [<span data-ttu-id="8a2a6-191">Modèles de Transformation de messages</span><span class="sxs-lookup"><span data-stu-id="8a2a6-191">Message Transformation Patterns</span></span>](../esb-toolkit/message-transformation-patterns.md)