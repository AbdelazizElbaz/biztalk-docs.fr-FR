---
title: "Comment : acheminer un Message basé sur le contexte du Message à l’aide d’une stratégie de règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d3b68de-6b24-46fe-ae0d-91afb630bc19
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717e0180ba92d49751342e00a4d0367832084135
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-dynamically-route-a-message-based-on-message-context-using-a-business-rules-policy"></a><span data-ttu-id="c36e8-102">Comment : acheminer un Message basé sur le contexte du Message à l’aide d’une stratégie de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="c36e8-102">How to: Dynamically Route a Message Based on Message Context Using a Business Rules Policy</span></span>
## <a name="goal"></a><span data-ttu-id="c36e8-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="c36e8-103">Goal</span></span>  
 <span data-ttu-id="c36e8-104">Cette section montre comment créer un itinéraire qui détermine les points de terminaison de message, selon les propriétés de contexte de message, à l’aide un [!INCLUDE[prague](../includes/prague-md.md)] stratégie du moteur de règles d’entreprise (BRE), puis les itinéraires du message à l’aide de la [!INCLUDE[prague](../includes/prague-md.md)] adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="c36e8-104">This section demonstrates how to create an itinerary that determines message endpoints, based on message context properties, using a [!INCLUDE[prague](../includes/prague-md.md)] Business Rules Engine (BRE) policy, and then routes the message using the [!INCLUDE[prague](../includes/prague-md.md)] FILE adapter.</span></span>  
  
 <span data-ttu-id="c36e8-105">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c36e8-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="c36e8-106">Créer une stratégie de règles d’entreprise pour évaluer le type de message.</span><span class="sxs-lookup"><span data-stu-id="c36e8-106">Create a business rules policy to evaluate message type.</span></span>  
  
-   <span data-ttu-id="c36e8-107">Créer un bordereau d’itinéraire de routage pour acheminer dynamiquement à l’aide d’une stratégie de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="c36e8-107">Create an itinerary routing slip to dynamically route using a business rules policy.</span></span>  
  
-   <span data-ttu-id="c36e8-108">Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="c36e8-108">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c36e8-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="c36e8-109">Prerequisites</span></span>  
 <span data-ttu-id="c36e8-110">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="c36e8-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="c36e8-111">Étapes</span><span class="sxs-lookup"><span data-stu-id="c36e8-111">Steps</span></span>  
 <span data-ttu-id="c36e8-112">**Pour créer une stratégie BRE pour router un message à l’aide des propriétés de contexte de message**</span><span class="sxs-lookup"><span data-stu-id="c36e8-112">**To create a BRE policy to route a message using message context properties**</span></span>  
  
1.  <span data-ttu-id="c36e8-113">Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[prague](../includes/prague-md.md)]** , puis cliquez sur **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-113">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="c36e8-114">Dans l’Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-114">In Policy Explorer, right-click **Policies**, and then click **Add New Policy**.</span></span> <span data-ttu-id="c36e8-115">Nom de la stratégie **RouteBasedOnMessageType**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-115">Name the policy **RouteBasedOnMessageType**.</span></span>  
  
 <span data-ttu-id="c36e8-116">**Pour ajouter une règle de routage pour les commandes Amérique du Nord**</span><span class="sxs-lookup"><span data-stu-id="c36e8-116">**To add a routing rule for North American orders**</span></span>  
  
1.  <span data-ttu-id="c36e8-117">Dans le **RouteBasedOnMessageType** stratégie, avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle règle**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-117">In the **RouteBasedOnMessageType** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.</span></span> <span data-ttu-id="c36e8-118">Nommez la règle **SetNAOrderEndpoint**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-118">Name the rule **SetNAOrderEndpoint**.</span></span>  
  
2.  <span data-ttu-id="c36e8-119">Dans la fenêtre de la règle, cliquez sur **Conditions**, pointez sur **prédicats**, puis cliquez sur **égal**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-119">In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.</span></span>  
  
3.  <span data-ttu-id="c36e8-120">Dans l’Explorateur de faits, développez le **ESB. ContextInfo** vocabulaire, développez **Version 1.0**, puis faites glisser le **Type de contexte de Message** fait à la **argument1** nœud sous  **Conditions**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-120">In Facts Explorer, expand the **ESB.ContextInfo** vocabulary, expand **Version 1.0**, and then drag the **Context Message Type** fact to the **argument1** node under **Conditions**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c36e8-121">La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut plusieurs vocabulaires qui peuvent être utilisés pour créer des règles.</span><span class="sxs-lookup"><span data-stu-id="c36e8-121">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes several vocabularies that can be used for creating rules.</span></span> <span data-ttu-id="c36e8-122">Certains d'entre eux doivent être remplacé ou augmentée avec vos propres vocabulaires.</span><span class="sxs-lookup"><span data-stu-id="c36e8-122">Some of these should be replaced or augmented with your own vocabularies.</span></span> <span data-ttu-id="c36e8-123">Par exemple, le **DynamicRunTimeMaptypes** stratégie contient des définitions pour les cartes fournies dans le **GlobalBank** exemples.</span><span class="sxs-lookup"><span data-stu-id="c36e8-123">For example, the **DynamicRunTimeMaptypes** policy has definitions for the maps provided in the **GlobalBank** samples.</span></span>  
  
4.  <span data-ttu-id="c36e8-124">Cliquez sur le **argument2** nœud, puis tapez **http://globalbank.esb.dynamicresolution.com/northamericanservices/#OrderDoc**</span><span class="sxs-lookup"><span data-stu-id="c36e8-124">Click the **argument2** node, and then type **http://globalbank.esb.dynamicresolution.com/northamericanservices/#OrderDoc**</span></span>  
  
5.  <span data-ttu-id="c36e8-125">Dans l’Explorateur de faits, développez le **ESB. EndPointInfo** vocabulaire, développez **Version 1.0**, puis faites glisser le **définir l’emplacement du Transport Point de terminaison sortants** définition **Actions**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-125">In Facts Explorer, expand the **ESB.EndPointInfo** vocabulary, expand **Version 1.0**, and then drag the **Set End Point Outbound Transport Location** definition to **Actions**.</span></span>  
  
6.  <span data-ttu-id="c36e8-126">Cliquez sur  **\<une chaîne vide >**, puis tapez **C:\HowTos\Out\NorthAmerica%MessageID%.xml**</span><span class="sxs-lookup"><span data-stu-id="c36e8-126">Click **\<empty string>**, and then type **C:\HowTos\Out\NorthAmerica%MessageID%.xml**</span></span>  
  
7.  <span data-ttu-id="c36e8-127">Dans l’Explorateur de faits, faites glisser le **définir le Type de Transport Point de terminaison sortants** définition **Actions**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-127">From Facts Explorer, drag the **Set End Point Outbound Transport Type** definition to **Actions**.</span></span>  
  
8.  <span data-ttu-id="c36e8-128">Dans l’Explorateur de faits, développez le **ESB. TansportTypes** vocabulaire, développez **Version 1.0**, puis faites glisser le **adaptateur fournisseurs** définition  **\<une chaîne vide >**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-128">In Facts Explorer, expand the **ESB.TansportTypes** vocabulary, expand **Version 1.0**, and then drag the **Adaptor Providers** definition to **\<empty string>**.</span></span>  
  
9. <span data-ttu-id="c36e8-129">Dans le volet Actions, développez le **adaptateur fournisseurs** liste déroulante, puis cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-129">In the Actions pane, expand the **Adaptor Providers** drop-down list, and then click **FILE**.</span></span>  
  
 <span data-ttu-id="c36e8-130">**Pour publier et déployer la stratégie**</span><span class="sxs-lookup"><span data-stu-id="c36e8-130">**To publish and deploy the policy**</span></span>  
  
1.  <span data-ttu-id="c36e8-131">Dans l’Explorateur de stratégies, sous la **RouteBasedOnMessageType** stratégie, le bouton droit sur **Version 1.0 (non enregistrée)**, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-131">In Policy Explorer, under the **RouteBasedOnMessageType** policy, right click **Version 1.0 (not saved)**, and then click **Publish**.</span></span>  
  
2.  <span data-ttu-id="c36e8-132">Dans l’Explorateur de stratégies, sous la **RouteBasedOnMessageType** stratégie, le bouton droit sur **Version 1.0 - publiée**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-132">In Policy Explorer, under the **RouteBasedOnMessageType** policy, right click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
 <span data-ttu-id="c36e8-133">**Pour créer un modèle d’itinéraire langage spécifique à un domaine (DSL) ESB**</span><span class="sxs-lookup"><span data-stu-id="c36e8-133">**To create an ESB itinerary domain-specific language (DSL) model**</span></span>  
  
1.  <span data-ttu-id="c36e8-134">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="c36e8-134">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="c36e8-135">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-135">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="c36e8-136">Dans le **nom** , tapez **MessageType**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-136">In the **Name** box, type **MessageType**, and then click **Add**.</span></span>  
  
 <span data-ttu-id="c36e8-137">**Pour configurer les propriétés de la feuille de route**</span><span class="sxs-lookup"><span data-stu-id="c36e8-137">**To configure the properties of the itinerary**</span></span>  
  
1.  <span data-ttu-id="c36e8-138">Dans Visual Studio, cliquez sur l’aire de conception de **MessageType.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-138">In Visual Studio, click the design surface of **MessageType.itinerary**.</span></span> <span data-ttu-id="c36e8-139">Dans le **MessageType** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="c36e8-139">In the **MessageType** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="c36e8-140">Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-140">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="c36e8-141">Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="c36e8-141">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="c36e8-142">Dans le **sélectionner un fichier XML** boîte de dialogue le **nom de fichier** , tapez **C:\HowTos\Itineraries\MessageType**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-142">In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\MessageType**, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="c36e8-143">Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local.</span><span class="sxs-lookup"><span data-stu-id="c36e8-143">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="c36e8-144">Exportation d’un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB.</span><span class="sxs-lookup"><span data-stu-id="c36e8-144">Exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="c36e8-145">Vous pourrez terminer cette procédure plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c36e8-145">You will complete this process later in this How-to topic.</span></span>  
  
 <span data-ttu-id="c36e8-146">**Pour définir la structure de la feuille de route**</span><span class="sxs-lookup"><span data-stu-id="c36e8-146">**To define the structure of the itinerary**</span></span>  
  
1.  <span data-ttu-id="c36e8-147">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="c36e8-147">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="c36e8-148">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="c36e8-148">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="c36e8-149">Cliquez sur le **nom** propriété, puis tapez **ReceiveOrders**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-149">Click the **Name** property, and then type **ReceiveOrders**.</span></span>  
  
    2.  <span data-ttu-id="c36e8-150">Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-150">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="c36e8-151">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-151">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="c36e8-152">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-152">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="c36e8-153">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de la **rampe d’entrée** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="c36e8-153">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="c36e8-154">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="c36e8-154">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="c36e8-155">Cliquez sur le **nom** propriété, puis tapez **BreRoute**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-155">Click the **Name** property, and then type **BreRoute**.</span></span>  
  
    2.  <span data-ttu-id="c36e8-156">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-156">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="c36e8-157">Cette propriété définit que le processus a lieu dans un pipeline (messagerie).</span><span class="sxs-lookup"><span data-stu-id="c36e8-157">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="c36e8-158">Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-158">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="c36e8-159">Dans le **conteneur** déroulante liste, développez **ReceiveOrders**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-159">In the **Container** drop-down list, expand **ReceiveOrders**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="c36e8-160">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-160">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
3.  <span data-ttu-id="c36e8-161">Avec le bouton droit le **résolveur** collection de la **BreRoute** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-161">Right-click the **Resolver** collection of the **BreRoute** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="c36e8-162">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="c36e8-162">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="c36e8-163">Cliquez sur le **nom** propriété, puis tapez **ByMessageType**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-163">Click the **Name** property, and then type **ByMessageType**.</span></span>  
  
    2.  <span data-ttu-id="c36e8-164">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension du programme de résolution Bre**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-164">In the **Resolver Implementation** drop-down list, click **Bre Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="c36e8-165">Dans le **stratégie** la liste déroulante, cliquez sur **RouteBasedOnMessageType v 1.0**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-165">In the **Policy** drop-down list, click **RouteBasedOnMessageType v 1.0**.</span></span>  
  
4.  <span data-ttu-id="c36e8-166">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-166">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="c36e8-167">Faites glisser une connexion à partir de la **ReceiveOrders** élément de modèle à la **BreRoute** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="c36e8-167">Drag a connection from the **ReceiveOrders** model element to the **BreRoute** model element.</span></span>  
  
5.  <span data-ttu-id="c36e8-168">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **BreRoute** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="c36e8-168">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **BreRoute** model element.</span></span> <span data-ttu-id="c36e8-169">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="c36e8-169">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="c36e8-170">Cliquez sur le **nom** propriété, puis tapez **SendBasedOnType**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-170">Click the **Name** property, and then type **SendBasedOnType**.</span></span>  
  
    2.  <span data-ttu-id="c36e8-171">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-171">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="c36e8-172">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-172">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="c36e8-173">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-173">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
6.  <span data-ttu-id="c36e8-174">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **BreRoute** élément de modèle et la **SendBasedOnType** modèle élément.</span><span class="sxs-lookup"><span data-stu-id="c36e8-174">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **BreRoute** model element and the **SendBasedOnType** model element.</span></span> <span data-ttu-id="c36e8-175">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="c36e8-175">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="c36e8-176">Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-176">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="c36e8-177">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-177">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="c36e8-178">Dans le **rampe** déroulante liste, développez **SendBasedOnType**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-178">In the **Off-Ramp** drop-down list, expand **SendBasedOnType**, and then click **Send Handlers**.</span></span>  
  
7.  <span data-ttu-id="c36e8-179">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-179">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="c36e8-180">Faites glisser une connexion à partir de la **BreRoute** élément de modèle à la **SendPortFilter** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="c36e8-180">Drag a connection from the **BreRoute** model element to the **SendPortFilter** model element.</span></span>  
  
8.  <span data-ttu-id="c36e8-181">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-181">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="c36e8-182">Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendBasedOnType** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="c36e8-182">Drag a connection from the **SendPortFilter** model element to the **SendBasedOnType** model element.</span></span>  
  
 <span data-ttu-id="c36e8-183">**Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire**</span><span class="sxs-lookup"><span data-stu-id="c36e8-183">**To export the model for use with the Itinerary Test Client**</span></span>  
  
1.  <span data-ttu-id="c36e8-184">Dans Visual Studio, cliquez sur l’aire de conception de la **MessageType** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-184">In Visual Studio, right-click the design surface of the **MessageType** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c36e8-185">La version XML de l’itinéraire s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c36e8-185">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="c36e8-186">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="c36e8-186">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="c36e8-187">Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (MessageType.xml).</span><span class="sxs-lookup"><span data-stu-id="c36e8-187">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (MessageType.xml).</span></span>  
  
 <span data-ttu-id="c36e8-188">**Pour tester la feuille de route**</span><span class="sxs-lookup"><span data-stu-id="c36e8-188">**To test the itinerary**</span></span>  
  
1.  <span data-ttu-id="c36e8-189">Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).</span><span class="sxs-lookup"><span data-stu-id="c36e8-189">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="c36e8-190">Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="c36e8-190">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="c36e8-191">Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="c36e8-191">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="c36e8-192">Sélectionnez **MessageType.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="c36e8-192">Select **MessageType.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="c36e8-193">Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.</span><span class="sxs-lookup"><span data-stu-id="c36e8-193">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="c36e8-194">Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="c36e8-194">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="c36e8-195">Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="c36e8-195">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="c36e8-196">Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.</span><span class="sxs-lookup"><span data-stu-id="c36e8-196">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="c36e8-197">Cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="c36e8-197">Click the **Submit Request** button.</span></span> <span data-ttu-id="c36e8-198">Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c36e8-198">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="c36e8-199">Dans l’Explorateur Windows, accédez à C:\HowTos\Out\\.</span><span class="sxs-lookup"><span data-stu-id="c36e8-199">In Windows Explorer, browse to C:\HowTos\Out\\.</span></span> <span data-ttu-id="c36e8-200">Vérifiez que le message NorthAmerica%MessageID%.xml a été écrit dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="c36e8-200">Verify that the NorthAmerica%MessageID%.xml message has been written to the directory.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="c36e8-201">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="c36e8-201">Additional Resources</span></span>  
 <span data-ttu-id="c36e8-202">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c36e8-202">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="c36e8-203">Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="c36e8-203">How to: Select an Itinerary Using a Business Rules Policy</span></span>](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [<span data-ttu-id="c36e8-204">Comment : transformer un Message et router le Message résultant à un emplacement de fichier à l’aide d’un bon d’itinéraire de routage</span><span class="sxs-lookup"><span data-stu-id="c36e8-204">How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip</span></span>](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [<span data-ttu-id="c36e8-205">Comment : implémenter en fonction du contenu routage à l’aide d’une entreprise règles de stratégie pour un Type connu</span><span class="sxs-lookup"><span data-stu-id="c36e8-205">How to: Implement Content-Based Routing Using a Business Rules Policy for a Known Message Type</span></span>](../esb-toolkit/apply-content-based-routing-using-business-rules-policy-for-known-message-type.md)  
  
-   [<span data-ttu-id="c36e8-206">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="c36e8-206">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="c36e8-207">Modèles de routage de messages</span><span class="sxs-lookup"><span data-stu-id="c36e8-207">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)  
  
-   [<span data-ttu-id="c36e8-208">À l’aide de la résolution dynamique et le routage</span><span class="sxs-lookup"><span data-stu-id="c36e8-208">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)