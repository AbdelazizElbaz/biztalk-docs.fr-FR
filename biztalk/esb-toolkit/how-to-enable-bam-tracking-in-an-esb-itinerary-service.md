---
title: "Comment : activer le suivi BAM sur un Service d’itinéraire ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58859937-f8d0-4c33-9a7a-62fec8441936
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 011de667e06f4275fe75a28b6566a6bc393cf841
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-enable-bam-tracking-in-an-esb-itinerary-service"></a><span data-ttu-id="63984-102">Comment : activer le suivi BAM sur un Service d’itinéraire ESB</span><span class="sxs-lookup"><span data-stu-id="63984-102">How to: Enable BAM Tracking in an ESB Itinerary Service</span></span>
## <a name="goal"></a><span data-ttu-id="63984-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="63984-103">Goal</span></span>  
 <span data-ttu-id="63984-104">Cette section montre comment activer l’analyse BAM (Business Activity) suivi d’un itinéraire existant.</span><span class="sxs-lookup"><span data-stu-id="63984-104">This section demonstrates how to enable Business Activity Monitor (BAM) tracking for an existing itinerary.</span></span>  
  
 <span data-ttu-id="63984-105">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="63984-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="63984-106">Activer la propriété utilisée pour le suivi des Services d’itinéraire à l’aide du moniteur d’activité commerciale.</span><span class="sxs-lookup"><span data-stu-id="63984-106">Enable the property used for tracking Itinerary Services using Business Activity Monitor.</span></span>  
  
-   <span data-ttu-id="63984-107">Test de suivi BAM à l’aide de l’exemple d’application Client de Test d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="63984-107">Test BAM tracking using the Itinerary Test Client sample application.</span></span>  
  
-   <span data-ttu-id="63984-108">Vérifiez les résultats de l’analyse BAM à l’aide d’une requête SQL.</span><span class="sxs-lookup"><span data-stu-id="63984-108">Verify the BAM results using a SQL query.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="63984-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="63984-109">Prerequisites</span></span>  
 <span data-ttu-id="63984-110">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="63984-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="63984-111">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="63984-111">Before You Begin</span></span>  
 <span data-ttu-id="63984-112">Effectuez les tâches suivantes avant d’effectuer les étapes plus loin dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="63984-112">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
-   <span data-ttu-id="63984-113">Créer un modèle d’itinéraire langage spécifique à un domaine (DSL) ESB.</span><span class="sxs-lookup"><span data-stu-id="63984-113">Create an ESB itinerary domain-specific language (DSL) model.</span></span>  
  
-   <span data-ttu-id="63984-114">Configurez les propriétés de l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="63984-114">Configure the properties of the itinerary.</span></span>  
  
-   <span data-ttu-id="63984-115">Définir la structure de l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="63984-115">Define the structure of the itinerary.</span></span>  
  
 <span data-ttu-id="63984-116">Les procédures suivantes décrivent comment effectuer chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="63984-116">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="63984-117">Pour créer un modèle DSL de la feuille de route ESB</span><span class="sxs-lookup"><span data-stu-id="63984-117">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="63984-118">Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="63984-118">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="63984-119">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="63984-119">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="63984-120">Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **ItineraryDsl** dans le volet Modèles.</span><span class="sxs-lookup"><span data-stu-id="63984-120">In the **Add New Item** dialog box, click  **ItineraryDsl** in the Templates pane.</span></span>  
  
4.  <span data-ttu-id="63984-121">Dans le **nom** , tapez **BamTracking**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="63984-121">In the **Name** box, type **BamTracking**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="63984-122">Pour configurer les propriétés de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="63984-122">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="63984-123">Dans Visual Studio, cliquez sur l’aire de conception de **BamTracking.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="63984-123">In Visual Studio, click the design surface of **BamTracking.itinerary**.</span></span> <span data-ttu-id="63984-124">Dans le **BamTracking** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="63984-124">In the **BamTracking** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="63984-125">Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.</span><span class="sxs-lookup"><span data-stu-id="63984-125">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="63984-126">Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="63984-126">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="63984-127">Dans le **sélectionner un fichier XML** boîte de dialogue le **nom de fichier** , tapez **C:\HowTos\Itineraries\BamTracking** puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="63984-127">In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\BamTracking** and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="63984-128">Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local.</span><span class="sxs-lookup"><span data-stu-id="63984-128">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="63984-129">En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB.</span><span class="sxs-lookup"><span data-stu-id="63984-129">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="63984-130">Vous pourrez terminer cette procédure plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="63984-130">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="63984-131">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="63984-131">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="63984-132">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="63984-132">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="63984-133">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="63984-133">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="63984-134">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="63984-134">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="63984-135">Dans le **extendeur** la liste déroulante, cliquez sur **Extension du Service ESB rampe d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="63984-135">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="63984-136">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="63984-136">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="63984-137">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="63984-137">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="63984-138">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de la **rampe d’entrée** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="63984-138">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="63984-139">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="63984-139">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="63984-140">Cliquez sur le **nom** propriété, puis tapez **MapNAOrderToCNOrder**.</span><span class="sxs-lookup"><span data-stu-id="63984-140">Click the **Name** property, and then type **MapNAOrderToCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="63984-141">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **Extension du Service de messagerie itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="63984-141">In the **Itinerary Service Extender** drop-down list, click **Messaging Itinerary Service Extension**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="63984-142">Cette propriété définit que le processus a lieu dans un pipeline (messagerie).</span><span class="sxs-lookup"><span data-stu-id="63984-142">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="63984-143">Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Extension du Service d’Orchestration itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="63984-143">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="63984-144">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="63984-144">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="63984-145">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Transform**.</span><span class="sxs-lookup"><span data-stu-id="63984-145">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
3.  <span data-ttu-id="63984-146">Avec le bouton droit le **résolveur** collection de la **MapNAOrderToCNOrder** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="63984-146">Right-click the **Resolver** collection of the **MapNAOrderToCNOrder** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="63984-147">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="63984-147">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="63984-148">Cliquez sur le **nom** propriété, puis tapez **StaticallySpecifyTheMap**.</span><span class="sxs-lookup"><span data-stu-id="63984-148">Click the **Name** property, and then type **StaticallySpecifyTheMap**.</span></span>  
  
    2.  <span data-ttu-id="63984-149">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="63984-149">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="63984-150">Dans le **transformer un Type** la liste déroulante, cliquez sur **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span><span class="sxs-lookup"><span data-stu-id="63984-150">In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span></span>  
  
    4.  <span data-ttu-id="63984-151">Dans le **TransportName** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="63984-151">In the **TransportName** drop-down list, click **FILE**.</span></span>  
  
4.  <span data-ttu-id="63984-152">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="63984-152">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="63984-153">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **MapNAOrderToCNOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="63984-153">Drag a connection from the **ReceiveNAOrder** model element to the **MapNAOrderToCNOrder** model element.</span></span>  
  
5.  <span data-ttu-id="63984-154">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **MapNAOrderToCNOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="63984-154">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **MapNAOrderToCNOrder** model element.</span></span> <span data-ttu-id="63984-155">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="63984-155">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="63984-156">Cliquez sur le **nom** propriété, puis tapez **SendCNOrder**.</span><span class="sxs-lookup"><span data-stu-id="63984-156">Click the **Name** property, and then type **SendCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="63984-157">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="63984-157">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="63984-158">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="63984-158">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="63984-159">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="63984-159">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
6.  <span data-ttu-id="63984-160">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **MapNAOrderToCNOrder** élément de modèle et la **SendCNOrder**élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="63984-160">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **MapNAOrderToCNOrder** model element and the **SendCNOrder** model element.</span></span> <span data-ttu-id="63984-161">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="63984-161">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="63984-162">Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.</span><span class="sxs-lookup"><span data-stu-id="63984-162">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="63984-163">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe itinéraire Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="63984-163">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="63984-164">Dans le **rampe** déroulante liste, développez **SendCNOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="63984-164">In the **Off-Ramp** drop-down list, expand **SendCNOrder**, and then click **Send Handlers**.</span></span>  
  
7.  <span data-ttu-id="63984-165">Avec le bouton droit le **résolveur** collection de la **SendPortFilter** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="63984-165">Right-click the **Resolver** collection of the **SendPortFilter** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="63984-166">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="63984-166">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="63984-167">Cliquez sur le **nom** propriété, puis tapez **ConfigureFolderSettings**.</span><span class="sxs-lookup"><span data-stu-id="63984-167">Click the **Name** property, and then type **ConfigureFolderSettings**.</span></span>  
  
    2.  <span data-ttu-id="63984-168">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="63984-168">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="63984-169">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="63984-169">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="63984-170">Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\BAM%MessageID%.xml**</span><span class="sxs-lookup"><span data-stu-id="63984-170">Click the **Transport Location** property, and then type **C:\HowTos\Out\BAM%MessageID%.xml**</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="63984-171">Chaque rampe aura un itinéraire service associé ; la combinaison des propriétés du service d’itinéraire et les propriétés de la rampe définir l’abonnement du port d’envoi dynamique.</span><span class="sxs-lookup"><span data-stu-id="63984-171">Each off-ramp will have an itinerary service associated with it; the combination of the itinerary service properties and the properties of the off-ramp define the subscription of the dynamic send port.</span></span>  
  
8.  <span data-ttu-id="63984-172">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="63984-172">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="63984-173">Faites glisser une connexion à partir de la **MapNAOrderToCNOrder** élément de modèle à la **SendPortFilter** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="63984-173">Drag a connection from the **MapNAOrderToCNOrder** model element to the **SendPortFilter** model element.</span></span>  
  
9. <span data-ttu-id="63984-174">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="63984-174">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="63984-175">Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendCNOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="63984-175">Drag a connection from the **SendPortFilter** model element to the **SendCNOrder** model element.</span></span>  
  
10. <span data-ttu-id="63984-176">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="63984-176">Save all project artifacts.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="63984-177">Étapes</span><span class="sxs-lookup"><span data-stu-id="63984-177">Steps</span></span>  
  
#### <a name="to-modify-the-itinerary"></a><span data-ttu-id="63984-178">Pour modifier la feuille de route</span><span class="sxs-lookup"><span data-stu-id="63984-178">To modify the itinerary</span></span>  
  
1.  <span data-ttu-id="63984-179">Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="63984-179">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="63984-180">Dans l’Explorateur de solutions, double-cliquez sur **BamTracking.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="63984-180">In Solution Explorer, double-click **BamTracking.itinerary**.</span></span>  
  
3.  <span data-ttu-id="63984-181">Cliquez sur le **MapNAOrderToCNOrder** élément de service d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="63984-181">Click the **MapNAOrderToCNOrder** itinerary service element.</span></span>  
  
4.  <span data-ttu-id="63984-182">Dans le **MapNAOrderToCNOrder** fenêtre Propriétés, cliquez sur **True** dans les **suivi activé** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="63984-182">In the **MapNAOrderToCNOrder** Properties window, click **True** in the **Tracking Enabled** drop-down list.</span></span>  
  
5.  <span data-ttu-id="63984-183">Cliquez sur le **SendPortFilter** élément de service d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="63984-183">Click the **SendPortFilter** itinerary service element.</span></span>  
  
6.  <span data-ttu-id="63984-184">Dans le **SendPortFilter** fenêtre Propriétés, cliquez sur **True** dans les **suivi activé** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="63984-184">In the **SendPortFilter** Properties window, click **True** in the **Tracking Enabled** drop-down list.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="63984-185">Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="63984-185">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="63984-186">Dans Visual Studio, cliquez sur l’aire de conception de la **BamTracking** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="63984-186">In Visual Studio, right-click the design surface of the **BamTracking** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63984-187">La version XML de l’itinéraire s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63984-187">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="63984-188">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="63984-188">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="63984-189">Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (BamTracking.xml).</span><span class="sxs-lookup"><span data-stu-id="63984-189">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (BamTracking.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="63984-190">Pour tester la feuille de route</span><span class="sxs-lookup"><span data-stu-id="63984-190">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="63984-191">Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).</span><span class="sxs-lookup"><span data-stu-id="63984-191">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="63984-192">Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="63984-192">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="63984-193">Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="63984-193">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="63984-194">Sélectionnez **BamTracking.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="63984-194">Select **BamTracking.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="63984-195">Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.</span><span class="sxs-lookup"><span data-stu-id="63984-195">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="63984-196">Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="63984-196">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="63984-197">Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="63984-197">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="63984-198">Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.</span><span class="sxs-lookup"><span data-stu-id="63984-198">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="63984-199">Cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="63984-199">Click the **Submit Request** button.</span></span> <span data-ttu-id="63984-200">Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="63984-200">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="63984-201">Dans l’Explorateur Windows, accédez à C:\HowTos\Out. Vérifiez que le message BAM%MessageID%.xml a été écrit dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="63984-201">In Windows Explorer, browse to C:\HowTos\Out. Verify that the BAM%MessageID%.xml message has been written to the directory.</span></span>  
  
#### <a name="to-verify-message-tracking"></a><span data-ttu-id="63984-202">Pour vérifier le suivi des messages</span><span class="sxs-lookup"><span data-stu-id="63984-202">To verify message tracking</span></span>  
  
1.  <span data-ttu-id="63984-203">Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)], puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="63984-203">Click **Start** on the taskbar, point to **All Programs**, point to [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="63984-204">Cliquez sur **Nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="63984-204">Click **New Query**.</span></span>  
  
3.  <span data-ttu-id="63984-205">Dans le volet de requête, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="63984-205">In the query pane, type the following:</span></span>  
  
    ```  
    SELECT *  
    FROM [BAMPrimaryImport].[dbo].[bam_ItineraryServiceActivity_Completed]  
    GO  
    ```  
  
4.  <span data-ttu-id="63984-206">Cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="63984-206">Click **Execute**.</span></span>  
  
5.  <span data-ttu-id="63984-207">Dans le volet de résultats, utilisez le **TimeStamp** colonne pour localiser l’entrée la plus récente.</span><span class="sxs-lookup"><span data-stu-id="63984-207">In the Results pane, use the **TimeStamp** column to locate the most recent entry.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="63984-208">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="63984-208">Additional Resources</span></span>  
 <span data-ttu-id="63984-209">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="63984-209">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="63984-210">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="63984-210">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="63984-211">Modèles de routage des messages</span><span class="sxs-lookup"><span data-stu-id="63984-211">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)  
  
-   [<span data-ttu-id="63984-212">Utilisation de la résolution et du routage dynamiques</span><span class="sxs-lookup"><span data-stu-id="63984-212">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)