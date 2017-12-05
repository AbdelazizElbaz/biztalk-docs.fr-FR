---
title: "Comment : résoudre un point de terminaison de Service à l’aide d’une recherche de catégorie UDDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ac5d37-5529-4509-a948-415453944e01
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 207c50c8f2dc61c0e7e86f865fec470dae4d2e84
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-resolve-a-service-endpoint-using-a-uddi-category-search"></a><span data-ttu-id="78a77-102">Comment : résoudre un point de terminaison de Service à l’aide d’une recherche de catégorie UDDI</span><span class="sxs-lookup"><span data-stu-id="78a77-102">How to: Resolve a Service Endpoint Using a UDDI Category Search</span></span>
## <a name="goal"></a><span data-ttu-id="78a77-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="78a77-103">Goal</span></span>  
 <span data-ttu-id="78a77-104">Cette section montre comment utiliser le langage spécifique à un domaine (DSL), ESB concepteur pour créer une basée sur un itinéraire de routage qui utilise le Universal Description, Discovery, et le programme de résolution d’intégration (UDDI) 3 pour localiser un point de terminaison de service à l’aide d’une catégorie de recherche.</span><span class="sxs-lookup"><span data-stu-id="78a77-104">This section demonstrates how to use the ESB Designer domain-specific language (DSL) to create an itinerary-based routing slip that uses the Universal Description, Discovery, and Integration (UDDI) 3 resolver to locate a service endpoint using a category search.</span></span> <span data-ttu-id="78a77-105">Dans ce scénario, le point de terminaison de service sera un point de terminaison de fichiers publié dans UDDI.</span><span class="sxs-lookup"><span data-stu-id="78a77-105">In this scenario, the service endpoint will be a file endpoint published in UDDI.</span></span>  
  
 <span data-ttu-id="78a77-106">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="78a77-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="78a77-107">Créer un bordereau d’itinéraire de routage pour résoudre un point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="78a77-107">Create an itinerary routing slip to resolve a service endpoint.</span></span>  
  
-   <span data-ttu-id="78a77-108">Configurer la feuille de route pour acheminer le message vers un point de terminaison de service à l’aide d’un programme de résolution UDDI 3.</span><span class="sxs-lookup"><span data-stu-id="78a77-108">Configure the itinerary to route the message to a service endpoint using a UDDI 3 resolver.</span></span>  
  
-   <span data-ttu-id="78a77-109">Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="78a77-109">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="78a77-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="78a77-110">Prerequisites</span></span>  
 <span data-ttu-id="78a77-111">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="78a77-111">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="78a77-112">Étapes</span><span class="sxs-lookup"><span data-stu-id="78a77-112">Steps</span></span>  
  
#### <a name="to-create-an-itinerary-model"></a><span data-ttu-id="78a77-113">Pour créer un modèle d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="78a77-113">To create an itinerary model</span></span>  
  
1.  <span data-ttu-id="78a77-114">Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="78a77-114">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="78a77-115">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="78a77-115">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="78a77-116">Dans le **ajouter un nouvel élément** boîte de dialogue, tapez **UDDI3CategorySearch** dans les **nom** zone, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="78a77-116">In the **Add New Item** dialog box, type **UDDI3CategorySearch** in the **Name** box, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="78a77-117">Pour configurer les propriétés de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="78a77-117">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="78a77-118">Dans Visual Studio, cliquez sur l’aire de conception de **UDDI3CategorySearch.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="78a77-118">In Visual Studio, click the design surface of **UDDI3CategorySearch.itinerary**.</span></span> <span data-ttu-id="78a77-119">Dans le **UDDI3CategorySearch** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="78a77-119">In the **UDDI3CategorySearch** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="78a77-120">Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.</span><span class="sxs-lookup"><span data-stu-id="78a77-120">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="78a77-121">Sous le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="78a77-121">Under the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="78a77-122">Dans le **sélectionner un fichier XML** boîte de dialogue, tapez **C:\HowTos\Itineraries\UDDI3CategorySearch** dans les **nom de fichier** zone, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="78a77-122">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\UDDI3CategorySearch** in the **File name** box, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="78a77-123">Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local.</span><span class="sxs-lookup"><span data-stu-id="78a77-123">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="78a77-124">En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB.</span><span class="sxs-lookup"><span data-stu-id="78a77-124">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="78a77-125">Vous pourrez terminer cette procédure plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="78a77-125">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="78a77-126">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="78a77-126">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="78a77-127">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="78a77-127">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="78a77-128">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="78a77-128">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="78a77-129">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="78a77-129">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="78a77-130">Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="78a77-130">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="78a77-131">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="78a77-131">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="78a77-132">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="78a77-132">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="78a77-133">Dans la boîte à outils, faites glisser un **itinéraire Service** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="78a77-133">From the Toolbox, drag an **Itinerary Service** model element to the design surface.</span></span> <span data-ttu-id="78a77-134">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="78a77-134">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="78a77-135">Cliquez sur le **nom** propriété, puis tapez **CategoryRoute**.</span><span class="sxs-lookup"><span data-stu-id="78a77-135">Click the **Name** property, and then type **CategoryRoute**.</span></span>  
  
    2.  <span data-ttu-id="78a77-136">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="78a77-136">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
    3.  <span data-ttu-id="78a77-137">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="78a77-137">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="78a77-138">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**</span><span class="sxs-lookup"><span data-stu-id="78a77-138">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**</span></span>  
  
3.  <span data-ttu-id="78a77-139">Avec le bouton droit le **résolveur** collection de la **CategoryRoute** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="78a77-139">Right-click the **Resolver** collection of the **CategoryRoute** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="78a77-140">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="78a77-140">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="78a77-141">Cliquez sur le **nom** propriété, puis tapez **CategorySearch**.</span><span class="sxs-lookup"><span data-stu-id="78a77-141">Click the **Name** property, and then type **CategorySearch**.</span></span>  
  
    2.  <span data-ttu-id="78a77-142">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Uddi3 programme de résolution d’Extension**.</span><span class="sxs-lookup"><span data-stu-id="78a77-142">In the **Resolver Implementation** drop-down list, click **Uddi3 Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="78a77-143">Dans le **Moniker du programme de résolution** la liste déroulante, cliquez sur **UDDI3**.</span><span class="sxs-lookup"><span data-stu-id="78a77-143">In the **Resolver Moniker** drop-down list, click **UDDI3**.</span></span>  
  
    4.  <span data-ttu-id="78a77-144">Cliquez sur le **recherche de catégorie** propriété, puis cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="78a77-144">Click the **Category Search** property, and then click the ellipsis button (…).</span></span>  
  
    5.  <span data-ttu-id="78a77-145">Dans le **nom de valeur de propriété éditeur** boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="78a77-145">In the **Name Value Property Editor** dialog box, click **Add**.</span></span>  
  
    6.  <span data-ttu-id="78a77-146">Cliquez sur le **nom** propriété, puis tapez **uddi:esb:biztalkapplication**.</span><span class="sxs-lookup"><span data-stu-id="78a77-146">Click the **Name** property, and then type **uddi:esb:biztalkapplication**.</span></span>  
  
    7.  <span data-ttu-id="78a77-147">Cliquez sur le **valeur** propriété, puis tapez **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="78a77-147">Click the **Value** property, and then type **GlobalBank.ESB**.</span></span>  
  
    8.  <span data-ttu-id="78a77-148">Dans le **nom de valeur de propriété éditeur** boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="78a77-148">In the **Name Value Property Editor** dialog box, click **Add**.</span></span>  
  
    9. <span data-ttu-id="78a77-149">Cliquez sur le **nom** propriété, puis tapez **uddi:esb:portname**.</span><span class="sxs-lookup"><span data-stu-id="78a77-149">Click the **Name** property, and then type **uddi:esb:portname**.</span></span>  
  
    10. <span data-ttu-id="78a77-150">Cliquez sur le **valeur** propriété, puis tapez **OrderFileServicev3**.</span><span class="sxs-lookup"><span data-stu-id="78a77-150">Click the **Value** property, and then type **OrderFileServicev3**.</span></span>  
  
    11. <span data-ttu-id="78a77-151">Dans le **nom de valeur de propriété éditeur** boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="78a77-151">In the **Name Value Property Editor** dialog box, click **Add**.</span></span>  
  
    12. <span data-ttu-id="78a77-152">Cliquez sur le **nom** propriété, puis tapez **uddi:esb:version**.</span><span class="sxs-lookup"><span data-stu-id="78a77-152">Click the **Name** property, and then type **uddi:esb:version**.</span></span>  
  
    13. <span data-ttu-id="78a77-153">Cliquez sur le **valeur** propriété, puis tapez **1**.</span><span class="sxs-lookup"><span data-stu-id="78a77-153">Click the **Value** property, and then type **1**.</span></span>  
  
    14. <span data-ttu-id="78a77-154">Cliquez sur **OK** pour fermer la **nom de valeur de propriété éditeur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="78a77-154">Click **OK** to close the **Name Value Property Editor** dialog box.</span></span>  
  
4.  <span data-ttu-id="78a77-155">Cliquez sur le **CategorySearch** programme de résolution, puis cliquez sur **Configuration du programme de résolution de Test**.</span><span class="sxs-lookup"><span data-stu-id="78a77-155">Right-click the **CategorySearch** resolver, and then click **Test Resolver Configuration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78a77-156">Vérifiez la sortie affichée dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="78a77-156">Verify the output displayed in the Output window.</span></span>  
  
5.  <span data-ttu-id="78a77-157">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="78a77-157">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="78a77-158">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **CategoryRoute** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="78a77-158">Drag a connection from the **ReceiveNAOrder** model element to the **CategoryRoute** model element.</span></span>  
  
6.  <span data-ttu-id="78a77-159">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **CategoryRoute** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="78a77-159">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **CategoryRoute** model element.</span></span> <span data-ttu-id="78a77-160">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="78a77-160">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="78a77-161">Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="78a77-161">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="78a77-162">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="78a77-162">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="78a77-163">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="78a77-163">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="78a77-164">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="78a77-164">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
7.  <span data-ttu-id="78a77-165">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **CategoryRoute** élément de modèle et la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="78a77-165">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **CategoryRoute** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="78a77-166">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="78a77-166">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="78a77-167">Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.</span><span class="sxs-lookup"><span data-stu-id="78a77-167">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="78a77-168">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="78a77-168">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="78a77-169">Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="78a77-169">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
8.  <span data-ttu-id="78a77-170">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="78a77-170">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="78a77-171">Faites glisser une connexion à partir de la **CategoryRoute** élément de modèle à la **SendPortFilter** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="78a77-171">Drag a connection from the **CategoryRoute** model element to the **SendPortFilter** model element.</span></span>  
  
9. <span data-ttu-id="78a77-172">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="78a77-172">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="78a77-173">Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="78a77-173">Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="78a77-174">Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="78a77-174">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="78a77-175">Dans Visual Studio, cliquez sur l’aire de conception de la **UDDI3CategorySearch** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="78a77-175">In Visual Studio, right-click the design surface of the **UDDI3CategorySearch** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78a77-176">La version XML de l’itinéraire s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78a77-176">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="78a77-177">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="78a77-177">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="78a77-178">Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (UDDI3CategorySearch.xml).</span><span class="sxs-lookup"><span data-stu-id="78a77-178">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (UDDI3CategorySearch.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="78a77-179">Pour tester la feuille de route</span><span class="sxs-lookup"><span data-stu-id="78a77-179">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="78a77-180">Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).</span><span class="sxs-lookup"><span data-stu-id="78a77-180">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="78a77-181">Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="78a77-181">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="78a77-182">Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="78a77-182">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="78a77-183">Sélectionnez **UDDI3CategorySearch.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="78a77-183">Select **UDDI3CategorySearch.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="78a77-184">Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.</span><span class="sxs-lookup"><span data-stu-id="78a77-184">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="78a77-185">Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="78a77-185">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="78a77-186">Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="78a77-186">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="78a77-187">Sélectionnez NAOrderDoc.xml, puis cliquez sur **ouvrir** pour le message de test de charge.</span><span class="sxs-lookup"><span data-stu-id="78a77-187">Select NAOrderDoc.xml, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="78a77-188">Cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="78a77-188">Click the **Submit Request** button.</span></span> <span data-ttu-id="78a77-189">Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="78a77-189">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="78a77-190">Dans l’Explorateur Windows, accédez à **C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out** et vérifiez que le **%MessageID%.xml** message a été écrit dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="78a77-190">In Windows Explorer, browse to **C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out** and verify that the **%MessageID%.xml** message has been written to the directory.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="78a77-191">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="78a77-191">Additional Resources</span></span>  
 <span data-ttu-id="78a77-192">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="78a77-192">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="78a77-193">Guide pratique pour résoudre un point de terminaison de service à l’aide d’une recherche de clé de liaison UDDI</span><span class="sxs-lookup"><span data-stu-id="78a77-193">How to: Resolve a Service Endpoint Using a UDDI Binding Key Search</span></span>](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  
  
-   [<span data-ttu-id="78a77-194">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="78a77-194">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="78a77-195">Utilisation de la résolution et du routage dynamiques</span><span class="sxs-lookup"><span data-stu-id="78a77-195">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)