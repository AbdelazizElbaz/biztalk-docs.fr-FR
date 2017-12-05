---
title: "Comment : résoudre un point de terminaison de Service à l’aide d’une recherche de clé de liaison de UDDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a685641-2beb-4153-a9ba-c766679ce48e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d286f3dd48daa7cc0ddd16f4abda601cf9e8a5f7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search"></a><span data-ttu-id="a37fd-102">Comment : résoudre un point de terminaison de Service à l’aide d’une recherche de clé de liaison de UDDI</span><span class="sxs-lookup"><span data-stu-id="a37fd-102">How to: Resolve a Service Endpoint Using a UDDI Binding Key Search</span></span>
## <a name="goal"></a><span data-ttu-id="a37fd-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="a37fd-103">Goal</span></span>  
 <span data-ttu-id="a37fd-104">Cette section montre comment utiliser le langage spécifique à un domaine (DSL), ESB concepteur pour créer une basée sur un itinéraire de routage qui utilise le Universal Description, Discovery, et résolveur Integration (UDDI) 3 pour localiser un point de terminaison de service à l’aide d’une clé de liaison recherche.</span><span class="sxs-lookup"><span data-stu-id="a37fd-104">This section demonstrates how to use the ESB Designer domain-specific language (DSL) to create an itinerary-based routing slip that uses the Universal Description, Discovery, and Integration (UDDI) 3 resolver to locate a service endpoint using a binding key search.</span></span> <span data-ttu-id="a37fd-105">Dans ce scénario, le point de terminaison de service sera un point de terminaison de fichiers publié dans UDDI.</span><span class="sxs-lookup"><span data-stu-id="a37fd-105">In this scenario, the service endpoint will be a file endpoint published in UDDI.</span></span>  
  
 <span data-ttu-id="a37fd-106">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a37fd-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="a37fd-107">Créer un bordereau d’itinéraire de routage pour résoudre un point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="a37fd-107">Create an itinerary routing slip to resolve a service endpoint.</span></span>  
  
-   <span data-ttu-id="a37fd-108">Configurer la feuille de route pour acheminer le message vers un point de terminaison de service à l’aide d’un programme de résolution UDDI 3.</span><span class="sxs-lookup"><span data-stu-id="a37fd-108">Configure the itinerary to route the message to a service endpoint using a UDDI 3 resolver.</span></span>  
  
-   <span data-ttu-id="a37fd-109">Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="a37fd-109">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a37fd-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a37fd-110">Prerequisites</span></span>  
 <span data-ttu-id="a37fd-111">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="a37fd-111">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="a37fd-112">Étapes</span><span class="sxs-lookup"><span data-stu-id="a37fd-112">Steps</span></span>  
  
#### <a name="to-create-an-itinerary-model"></a><span data-ttu-id="a37fd-113">Pour créer un modèle d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="a37fd-113">To create an itinerary model</span></span>  
  
1.  <span data-ttu-id="a37fd-114">Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="a37fd-114">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="a37fd-115">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-115">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="a37fd-116">Dans le **ajouter un nouvel élément** boîte de dialogue le **nom** , tapez **UDDI3BindingKeySearch**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-116">In the **Add New Item** dialog box, in the **Name** box, type **UDDI3BindingKeySearch**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="a37fd-117">Pour configurer les propriétés de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="a37fd-117">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="a37fd-118">Dans Visual Studio, cliquez sur l’aire de conception de **UDDI3BindingKeySearch.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-118">In Visual Studio, click the design surface of **UDDI3BindingKeySearch.itinerary**.</span></span> <span data-ttu-id="a37fd-119">Dans le **UDDI3BindingKeySearch** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a37fd-119">In the **UDDI3BindingKeySearch** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="a37fd-120">Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-120">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="a37fd-121">Sous le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="a37fd-121">Under the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="a37fd-122">Dans le **sélectionner un fichier XML** boîte de dialogue, tapez **C:\HowTos\Itineraries\UDDI3BindingKeySearch** dans les **nom de fichier** zone, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-122">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\UDDI3BindingKeySearch** in the **File name** box, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a37fd-123">Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local.</span><span class="sxs-lookup"><span data-stu-id="a37fd-123">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="a37fd-124">En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB.</span><span class="sxs-lookup"><span data-stu-id="a37fd-124">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="a37fd-125">Vous pourrez terminer cette procédure plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a37fd-125">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="a37fd-126">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="a37fd-126">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="a37fd-127">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="a37fd-127">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="a37fd-128">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a37fd-128">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="a37fd-129">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-129">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="a37fd-130">Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-130">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="a37fd-131">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-131">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="a37fd-132">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-132">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="a37fd-133">Dans la boîte à outils, faites glisser un **itinéraire Service** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="a37fd-133">From the Toolbox, drag an **Itinerary Service** model element to the design surface.</span></span> <span data-ttu-id="a37fd-134">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a37fd-134">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="a37fd-135">Cliquez sur le **nom** propriété, puis tapez **BindingKeyRoute**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-135">Click the **Name** property, and then type **BindingKeyRoute**.</span></span>  
  
    2.  <span data-ttu-id="a37fd-136">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-136">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
    3.  <span data-ttu-id="a37fd-137">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-137">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="a37fd-138">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-138">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
3.  <span data-ttu-id="a37fd-139">Avec le bouton droit le **résolveur** collection de la **BindingKeyRoute** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-139">Right-click the **Resolver** collection of the **BindingKeyRoute** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="a37fd-140">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a37fd-140">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="a37fd-141">Cliquez sur le **nom** propriété, puis tapez **BindingKeySearch**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-141">Click the **Name** property, and then type **BindingKeySearch**.</span></span>  
  
    2.  <span data-ttu-id="a37fd-142">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Uddi3 programme de résolution d’Extension**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-142">In the **Resolver Implementation** drop-down list, click **Uddi3 Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="a37fd-143">Dans le **Moniker du programme de résolution** la liste déroulante, cliquez sur **UDDI3**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-143">In the **Resolver Moniker** drop-down list, click **UDDI3**.</span></span>  
  
    4.  <span data-ttu-id="a37fd-144">Cliquez sur le **clé de liaison** propriété, puis tapez **uddi:esb:orderfileservicev3.1**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-144">Click the **Binding key** property, and then type **uddi:esb:orderfileservicev3.1**.</span></span>  
  
4.  <span data-ttu-id="a37fd-145">Cliquez sur le **BindingKeySearch** programme de résolution, puis cliquez sur **Configuration du programme de résolution de Test**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-145">Right-click the **BindingKeySearch** resolver, and then click **Test Resolver Configuration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a37fd-146">Vérifiez la sortie affichée dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="a37fd-146">Verify the output displayed in the Output window.</span></span>  
  
5.  <span data-ttu-id="a37fd-147">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-147">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="a37fd-148">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **BindingKeyRoute** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a37fd-148">Drag a connection from the **ReceiveNAOrder** model element to the **BindingKeyRoute** model element.</span></span>  
  
6.  <span data-ttu-id="a37fd-149">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **BindingKeyRoute** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a37fd-149">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **BindingKeyRoute** model element.</span></span> <span data-ttu-id="a37fd-150">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a37fd-150">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="a37fd-151">Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-151">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="a37fd-152">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-152">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="a37fd-153">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-153">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="a37fd-154">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-154">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
7.  <span data-ttu-id="a37fd-155">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **BindingKeyRoute** élément de modèle et la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a37fd-155">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **BindingKeyRoute** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="a37fd-156">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a37fd-156">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="a37fd-157">Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-157">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="a37fd-158">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-158">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="a37fd-159">Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-159">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
8.  <span data-ttu-id="a37fd-160">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-160">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="a37fd-161">Faites glisser une connexion à partir de la **BindingKeyRoute** élément de modèle à la **SendPortFilter** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a37fd-161">Drag a connection from the **BindingKeyRoute** model element to the **SendPortFilter** model element.</span></span>  
  
9. <span data-ttu-id="a37fd-162">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-162">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="a37fd-163">Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a37fd-163">Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="a37fd-164">Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="a37fd-164">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="a37fd-165">Dans Visual Studio, cliquez sur l’aire de conception de la **UDDI3BindingKeySearch** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-165">In Visual Studio, right-click the design surface of the **UDDI3BindingKeySearch** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a37fd-166">La version XML de l’itinéraire s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a37fd-166">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="a37fd-167">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="a37fd-167">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="a37fd-168">Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (UDDI3BindingKeySearch.xml).</span><span class="sxs-lookup"><span data-stu-id="a37fd-168">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (UDDI3BindingKeySearch.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="a37fd-169">Pour tester la feuille de route</span><span class="sxs-lookup"><span data-stu-id="a37fd-169">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="a37fd-170">Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).</span><span class="sxs-lookup"><span data-stu-id="a37fd-170">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="a37fd-171">Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="a37fd-171">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="a37fd-172">Dans la boîte de dialogue Ouvrir un fichier itinéraire, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="a37fd-172">In the Open Itinerary File dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="a37fd-173">Sélectionnez UDDI3BindingKeySearch.xml, puis cliquez sur Ouvrir pour charger la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="a37fd-173">Select UDDI3BindingKeySearch.xml, and then click Open to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="a37fd-174">Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.</span><span class="sxs-lookup"><span data-stu-id="a37fd-174">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="a37fd-175">Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="a37fd-175">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="a37fd-176">Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="a37fd-176">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="a37fd-177">Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.</span><span class="sxs-lookup"><span data-stu-id="a37fd-177">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="a37fd-178">Cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="a37fd-178">Click the **Submit Request** button.</span></span> <span data-ttu-id="a37fd-179">Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="a37fd-179">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="a37fd-180">Dans l’Explorateur Windows, accédez à C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out. Vérifiez que le message %MessageID%.xml a été écrit dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="a37fd-180">In Windows Explorer, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out. Verify that the %MessageID%.xml message has been written to the directory.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="a37fd-181">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a37fd-181">Additional Resources</span></span>  
 <span data-ttu-id="a37fd-182">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a37fd-182">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="a37fd-183">Guide pratique pour résoudre un point de terminaison de service à l’aide d’une recherche de catégorie UDDI</span><span class="sxs-lookup"><span data-stu-id="a37fd-183">How to: Resolve a Service Endpoint Using a UDDI Category Search</span></span>](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  
  
-   [<span data-ttu-id="a37fd-184">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="a37fd-184">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="a37fd-185">Utilisation de la résolution et du routage dynamiques</span><span class="sxs-lookup"><span data-stu-id="a37fd-185">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)