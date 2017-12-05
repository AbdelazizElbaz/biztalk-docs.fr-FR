---
title: "Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f6373a8-d9d6-46c6-95e3-f62dd33c342a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 521b3768251cfcd31defe271a21d4b2d0bc771e6
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-select-an-itinerary-using-a-business-rules-policy"></a><span data-ttu-id="59a6b-102">Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="59a6b-102">How to: Select an Itinerary Using a Business Rules Policy</span></span>
## <a name="goal"></a><span data-ttu-id="59a6b-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="59a6b-103">Goal</span></span>  
 <span data-ttu-id="59a6b-104">Cette section montre comment créer des règles d’entreprise qui peuvent être utilisés pour sélectionner un itinéraire en fonction du contenu d’un message reçu et comment configurer le composant de pipeline de sélecteur de feuille de route au sein d’un générique d’itinéraire rampe d’entrée à appeler ces règles.</span><span class="sxs-lookup"><span data-stu-id="59a6b-104">This section demonstrates how to create business rules that can be used to select an itinerary based on the content of a received message and how to configure the Itinerary Selector pipeline component within a generic itinerary on-ramp to call these rules.</span></span> <span data-ttu-id="59a6b-105">Cette section décrit un scénario d’entreprise dans laquelle messages sont routés différemment, selon la région dans lequel réside le client.</span><span class="sxs-lookup"><span data-stu-id="59a6b-105">This section describes a business scenario in which messages are routed differently, based on the region in which the customer resides.</span></span>  
  
 <span data-ttu-id="59a6b-106">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="59a6b-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="59a6b-107">Itinéraires de modèle pour les divisions de l’ouest et orientale de client Global Bank.</span><span class="sxs-lookup"><span data-stu-id="59a6b-107">Model itineraries for the Western and Eastern divisions of customer Global Bank.</span></span>  
  
-   <span data-ttu-id="59a6b-108">Créer des stratégies de règles d’entreprise qui permet de sélectionner une feuille de route pour le traitement de la demande.</span><span class="sxs-lookup"><span data-stu-id="59a6b-108">Create business rules policies that will be used to select an itinerary for processing request.</span></span>  
  
-   <span data-ttu-id="59a6b-109">Configurer le composant de pipeline de sélecteur de feuille de route pour utiliser une stratégie de règles d’entreprise pour sélectionner la feuille de route approprié.</span><span class="sxs-lookup"><span data-stu-id="59a6b-109">Configure the Itinerary Selector pipeline component to use a business rules policy to select the appropriate itinerary.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="59a6b-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="59a6b-110">Prerequisites</span></span>  
 <span data-ttu-id="59a6b-111">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="59a6b-111">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="59a6b-112">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="59a6b-112">Before You Begin</span></span>  
 <span data-ttu-id="59a6b-113">Effectuez les tâches suivantes avant d’effectuer les étapes plus loin dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="59a6b-113">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
-   <span data-ttu-id="59a6b-114">Créer le message de test GlobalBank West.</span><span class="sxs-lookup"><span data-stu-id="59a6b-114">Create the GlobalBank West test message.</span></span>  
  
-   <span data-ttu-id="59a6b-115">Créer le message de test est de GlobalBank.</span><span class="sxs-lookup"><span data-stu-id="59a6b-115">Create the GlobalBank East test message.</span></span>  
  
 <span data-ttu-id="59a6b-116">Les procédures suivantes décrivent comment effectuer chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="59a6b-116">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-the-globalbank-west-test-message"></a><span data-ttu-id="59a6b-117">Pour créer le message de test GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="59a6b-117">To create the GlobalBank West test message</span></span>  
  
1.  <span data-ttu-id="59a6b-118">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="59a6b-118">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="59a6b-119">Créer une copie de NAOrderDoc.xml et nommez la copie West.xml.</span><span class="sxs-lookup"><span data-stu-id="59a6b-119">Create a copy of NAOrderDoc.xml, and then name the copy West.xml.</span></span>  
  
3.  <span data-ttu-id="59a6b-120">Dans le bloc-notes, ouvrez West.xml et modifiez la valeur de la **customerName** élément **GlobalBankWest**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-120">In Notepad, open West.xml, and then change the value of the **customerName** element to **GlobalBankWest**.</span></span>  
  
4.  <span data-ttu-id="59a6b-121">Enregistrer West.xml en UTF-8, puis fermez le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="59a6b-121">Save West.xml as UTF-8, and then close Notepad.</span></span>  
  
#### <a name="to-create-the-globalbank-east-test-message"></a><span data-ttu-id="59a6b-122">Pour créer le message de test est de GlobalBank</span><span class="sxs-lookup"><span data-stu-id="59a6b-122">To create the GlobalBank East test message</span></span>  
  
1.  <span data-ttu-id="59a6b-123">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="59a6b-123">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="59a6b-124">Créer une copie de NAOrderDoc.xml et nommez la copie East.xml.</span><span class="sxs-lookup"><span data-stu-id="59a6b-124">Create a copy of NAOrderDoc.xml, and then name the copy East.xml.</span></span>  
  
3.  <span data-ttu-id="59a6b-125">Dans le bloc-notes, ouvrez East.xml et modifiez la valeur de la **customerName** élément **GlobalBankEast**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-125">In Notepad, open East.xml, and then change the value of the **customerName** element to **GlobalBankEast**.</span></span>  
  
4.  <span data-ttu-id="59a6b-126">Enregistrer East.xml en UTF-8, puis fermez le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="59a6b-126">Save East.xml as UTF-8, and then close Notepad.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="59a6b-127">Étapes</span><span class="sxs-lookup"><span data-stu-id="59a6b-127">Steps</span></span>  
  
#### <a name="to-create-a-business-rules-engine-bre-policy-to-select-an-itinerary-using-custom-message-properties"></a><span data-ttu-id="59a6b-128">Pour créer une stratégie du moteur de règles d’entreprise (BRE) pour sélectionner un itinéraire à l’aide des propriétés de message personnalisées</span><span class="sxs-lookup"><span data-stu-id="59a6b-128">To create a Business Rules Engine (BRE) policy to select an itinerary using custom message properties</span></span>  
  
1.  <span data-ttu-id="59a6b-129">Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur **BizTalk Server**, puis cliquez sur **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-129">Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="59a6b-130">Dans l’Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-130">In Policy Explorer, right-click **Policies**, and then click **Add New Policy**.</span></span> <span data-ttu-id="59a6b-131">Nom de la stratégie **ResolveItineraryBasedOnCustomer**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-131">Name the policy **ResolveItineraryBasedOnCustomer**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59a6b-132">Cette rubrique utilise la même stratégie de règles d’entreprise et les itinéraires comme ceux créés dans la rubrique [Comment : fractionner un échange et de router les Messages résultant vers plusieurs fichiers emplacements à l’aide de Distinct itinéraires](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md).</span><span class="sxs-lookup"><span data-stu-id="59a6b-132">This How-to topic uses the same business rules policy and itineraries as those created in the topic [How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md).</span></span> <span data-ttu-id="59a6b-133">Si vous avez déjà effectué cette section, vous pouvez ignorer la procédure, « pour créer et configurer un ESB rampe d’entrée » plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="59a6b-133">If you have already completed that section, you can skip to the procedure, "To create and configure an ESB on-ramp" later in this topic.</span></span>  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-west"></a><span data-ttu-id="59a6b-134">Pour ajouter une règle de sélection pour le client GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="59a6b-134">To add a selection rule for customer GlobalBank West</span></span>  
  
1.  <span data-ttu-id="59a6b-135">Dans le **ResolveItineraryBasedOnCustomer** stratégie, avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle règle**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-135">In the **ResolveItineraryBasedOnCustomer** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.</span></span> <span data-ttu-id="59a6b-136">Nommez la règle **SetGlobalBankWestItinerary**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-136">Name the rule **SetGlobalBankWestItinerary**.</span></span>  
  
2.  <span data-ttu-id="59a6b-137">Dans l’Explorateur de faits, cliquez sur le **schémas XML** droit **schémas**, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-137">In Facts Explorer, click the **XML Schemas** tab, right-click **Schemas**, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="59a6b-138">Dans le **les fichiers de schéma** boîte de dialogue, accédez à C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB. DynamicResolution.Schemas, sélectionnez **NAOrderDoc.xsd**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-138">In the **Schema Files** dialog box, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas, select **NAOrderDoc.xsd**, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59a6b-139">Voici le schéma qui définit le message NAOrderDoc.xml, qui a été utilisé pour créer les messages ouest / est que vous allez utiliser pour le test.</span><span class="sxs-lookup"><span data-stu-id="59a6b-139">This is the schema that defines the NAOrderDoc.xml message, which was used to create the West and East messages you will use for testing.</span></span>  
  
4.  <span data-ttu-id="59a6b-140">Dans l’Explorateur de faits, cliquez sur **NAOrderDoc.xsd**, cliquez sur le **Type de Document** propriété dans le volet Propriétés, puis tapez **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-140">In Facts Explorer, click **NAOrderDoc.xsd**, click the **Document Type** property in the Properties pane, and then type **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59a6b-141">Il s’agit du nom qualifié complet du schéma.</span><span class="sxs-lookup"><span data-stu-id="59a6b-141">This is the fully qualified name of the schema.</span></span>  
  
5.  <span data-ttu-id="59a6b-142">Dans l’Explorateur de faits, développez **NAOrderDoc.xsd**, puis développez **OrderDoc**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-142">In Facts Explorer, expand **NAOrderDoc.xsd**, and then expand **OrderDoc**.</span></span>  
  
6.  <span data-ttu-id="59a6b-143">Dans la fenêtre de la règle, cliquez sur **Conditions**, pointez sur **prédicats**, puis cliquez sur **égal**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-143">In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.</span></span>  
  
7.  <span data-ttu-id="59a6b-144">Dans l’Explorateur de faits, faites glisser le **customerName** élément à la **argument1** nœud sous **Conditions**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-144">From Facts Explorer, drag the **customerName** element to the **argument1** node under **Conditions**.</span></span>  
  
8.  <span data-ttu-id="59a6b-145">Cliquez sur le **argument2** nœud, puis tapez **GlobalBankWest**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-145">Click the **argument2** node, and then type **GlobalBankWest**.</span></span>  
  
9. <span data-ttu-id="59a6b-146">Dans l’Explorateur de faits, cliquez sur le **vocabulaires** onglet. Développez le **ESB. Feuille de route** vocabulaire, développez **Version 1.1**, puis faites glisser le **définir un nom de feuille de route** définition **Actions**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-146">In Facts Explorer, click the **Vocabularies** tab. Expand the **ESB.Itinerary** vocabulary, expand **Version 1.1**, and then drag the **Set Itinerary Name** definition to **Actions**.</span></span>  
  
10. <span data-ttu-id="59a6b-147">Cliquez sur  **\<une chaîne vide\>**, puis tapez **GlobalBankWestItinerary**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-147">Click **\<empty string\>**, and then type **GlobalBankWestItinerary**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59a6b-148">Plus loin dans cette rubrique, vous allez créer cette feuille de route pour traiter les messages de GlobalBank West.</span><span class="sxs-lookup"><span data-stu-id="59a6b-148">Later in this How-to topic, you will create this itinerary to process messages from GlobalBank West.</span></span>  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-east"></a><span data-ttu-id="59a6b-149">Pour ajouter une règle de sélection pour le client GlobalBank est</span><span class="sxs-lookup"><span data-stu-id="59a6b-149">To add a selection rule for Customer GlobalBank East</span></span>  
  
1.  <span data-ttu-id="59a6b-150">Dans l’Explorateur de stratégies, cliquez sur le **SetGlobalBankWestItinerary** de règle, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-150">In Policy Explorer, right-click the **SetGlobalBankWestItinerary** rule, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="59a6b-151">Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-151">Right-click **Version 1.0 (not saved)**, and then click **Paste**.</span></span>  
  
3.  <span data-ttu-id="59a6b-152">Dans le **nom de la nouvelle règle** boîte de dialogue, tapez **SetGlobalBankEastItinerary**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-152">In the **New Rule Name** dialog box, type **SetGlobalBankEastItinerary**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="59a6b-153">Dans l’Explorateur de stratégies, cliquez sur le **SetGlobalBankEastItinerary** règle.</span><span class="sxs-lookup"><span data-stu-id="59a6b-153">In Policy Explorer, click the **SetGlobalBankEastItinerary** rule.</span></span>  
  
5.  <span data-ttu-id="59a6b-154">Dans le **Conditions** section, cliquez sur **GlobalBankWest**, puis cliquez sur **réinitialiser l’argument**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-154">In the **Conditions** section, right-click **GlobalBankWest**, and then click **Reset argument**.</span></span>  
  
6.  <span data-ttu-id="59a6b-155">Cliquez sur **argument2**, puis tapez **GlobalBankEast**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-155">Click **argument2**, and then type **GlobalBankEast**.</span></span>  
  
7.  <span data-ttu-id="59a6b-156">Dans le **Actions** section, cliquez sur **GlobalBankWestItinerary**, puis cliquez sur **réinitialiser l’argument**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-156">In the **Actions** section, right-click **GlobalBankWestItinerary**, and then click **Reset argument**.</span></span>  
  
8.  <span data-ttu-id="59a6b-157">Cliquez sur  **\<une chaîne vide\>**  , puis tapez **GlobalBankEastItinerary**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-157">Click **\<empty string\>** and then type **GlobalBankEastItinerary**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59a6b-158">Plus loin dans la rubrique de procédure, vous allez créer cette feuille de route pour traiter les messages à partir de GlobalBank est.</span><span class="sxs-lookup"><span data-stu-id="59a6b-158">Later in the How-to topic, you will create this itinerary to process messages from GlobalBank East.</span></span>  
  
#### <a name="to-publish-and-deploy-the-policy"></a><span data-ttu-id="59a6b-159">Pour publier et déployer la stratégie</span><span class="sxs-lookup"><span data-stu-id="59a6b-159">To publish and deploy the policy</span></span>  
  
1.  <span data-ttu-id="59a6b-160">Dans l’Explorateur de stratégies, sous la **ResolveItineraryBasedOnCustomer** stratégie, le bouton droit sur **Version 1.0 (non enregistrée)**, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-160">In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, right click **Version 1.0 (not saved)**, and then click **Publish**.</span></span>  
  
2.  <span data-ttu-id="59a6b-161">Dans l’Explorateur de stratégies, sous la **ResolveItineraryBasedOnCustomer** stratégie, le bouton droit sur **Version 1.0 - publiée**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-161">In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, right click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model-for-globalbank-west-messages"></a><span data-ttu-id="59a6b-162">Pour créer un modèle d’itinéraire langage spécifique à un domaine (DSL) ESB pour les messages GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="59a6b-162">To create an ESB itinerary domain-specific language (DSL) model for GlobalBank West messages</span></span>  
  
1.  <span data-ttu-id="59a6b-163">Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="59a6b-163">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="59a6b-164">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-164">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="59a6b-165">Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet Modèles, cliquez sur **ItineraryDsl**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-165">In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.</span></span>  
  
4.  <span data-ttu-id="59a6b-166">Dans le **nom** , tapez **GlobalBankWestItinerary**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-166">In the **Name** box, type **GlobalBankWestItinerary**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-globalbank-west-itinerary"></a><span data-ttu-id="59a6b-167">Pour configurer les propriétés de l’itinéraire GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="59a6b-167">To configure the properties of the GlobalBank West itinerary</span></span>  
  
1.  <span data-ttu-id="59a6b-168">Dans Visual Studio, cliquez sur l’aire de conception de **GlobalBankWestItinerary.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-168">In Visual Studio, click the design surface of **GlobalBankWestItinerary.itinerary**.</span></span> <span data-ttu-id="59a6b-169">Dans le **GlobalBankWestItinerary** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="59a6b-169">In the **GlobalBankWestItinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="59a6b-170">Dans le **modèle exportateur** la liste déroulante, cliquez sur **exportateur de feuille de route de base de données**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-170">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="59a6b-171">Cliquez sur le bouton de sélection (...) à côté du **base de données de la feuille de route** propriété.</span><span class="sxs-lookup"><span data-stu-id="59a6b-171">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="59a6b-172">Dans le **propriétés de connexion** boîte de dialogue, choisissez le serveur SQL qui héberge la base de données de référentiel d’itinéraire, puis spécifiez le nom de la base de données (le nom par défaut est **EsbItineraryDb**).</span><span class="sxs-lookup"><span data-stu-id="59a6b-172">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="59a6b-173">Dans le **état de la feuille de route** la liste déroulante, cliquez sur **déployées**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-173">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59a6b-174">Cette étape vous permet d’exporter l’itinéraire sur un référentiel central ; itinéraires peuvent être sélectionnés et attachés à partir de ce référentiel lors de la réception du message.</span><span class="sxs-lookup"><span data-stu-id="59a6b-174">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository upon message reception.</span></span> <span data-ttu-id="59a6b-175">Vous configurerez ultérieurement le composant de pipeline de sélecteur de feuille de route pour utiliser le programme de résolution du moteur des règles d’entreprise (BRI) à évaluer les messages entrants, puis sélectionnez la feuille de route approprié à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="59a6b-175">You will later configure the Itinerary Selector pipeline component to use the Business Rules Engine resolver (BRI) to evaluate inbound messages and select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="59a6b-176">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="59a6b-176">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="59a6b-177">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="59a6b-177">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="59a6b-178">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="59a6b-178">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="59a6b-179">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-179">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="59a6b-180">Dans le **extendeur** la liste déroulante, cliquez sur **Extension du Service ESB rampe d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-180">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="59a6b-181">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-181">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="59a6b-182">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-182">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="59a6b-183">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **ReceiveNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="59a6b-183">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="59a6b-184">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="59a6b-184">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="59a6b-185">Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-185">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="59a6b-186">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-186">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="59a6b-187">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-187">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="59a6b-188">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-188">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="59a6b-189">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **ReceiveNAOrder** élément de modèle et la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="59a6b-189">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="59a6b-190">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="59a6b-190">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="59a6b-191">Cliquez sur le **nom** propriété, puis tapez **RouteMessage**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-191">Click the **Name** property, and then type **RouteMessage**.</span></span>  
  
    2.  <span data-ttu-id="59a6b-192">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe itinéraire Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-192">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="59a6b-193">Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-193">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="59a6b-194">Avec le bouton droit le **résolveur** collection de la **RouteMessage** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-194">Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="59a6b-195">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="59a6b-195">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="59a6b-196">Cliquez sur le **nom** propriété, puis tapez **StaticResolver**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-196">Click the **Name** property, and then type **StaticResolver**.</span></span>  
  
    2.  <span data-ttu-id="59a6b-197">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-197">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="59a6b-198">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-198">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="59a6b-199">Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\West%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-199">Click the **Transport Location** property, and then type **C:\HowTos\Out\West%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="59a6b-200">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-200">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="59a6b-201">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteMessage** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="59a6b-201">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessage** model element.</span></span>  
  
6.  <span data-ttu-id="59a6b-202">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-202">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="59a6b-203">Faites glisser une connexion à partir de la **RouteMessage** élément de modèle à la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="59a6b-203">Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a><span data-ttu-id="59a6b-204">Pour exporter le modèle vers la base de données d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="59a6b-204">To export the model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="59a6b-205">Dans Visual Studio, cliquez sur l’aire de conception de la **GlobalBankWestItinerary** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-205">In Visual Studio, right-click the design surface of the **GlobalBankWestItinerary** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59a6b-206">L’itinéraire a été exporté vers la base de données d’itinéraire et peut maintenant être utilisé par le composant de sélecteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="59a6b-206">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.</span></span>  
  
2.  <span data-ttu-id="59a6b-207">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="59a6b-207">Save all project artifacts.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-east-message"></a><span data-ttu-id="59a6b-208">Pour créer un modèle DSL ESB d’itinéraire pour le message de GlobalBank est</span><span class="sxs-lookup"><span data-stu-id="59a6b-208">To create an ESB itinerary DSL model for GlobalBank East message</span></span>  
  
1.  <span data-ttu-id="59a6b-209">Dans Visual Studio, ouvrez C:\HowTos\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="59a6b-209">In Visual Studio, open C:\HowTos\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="59a6b-210">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-210">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="59a6b-211">Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet Modèles, cliquez sur **ItineraryDsl**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-211">In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.</span></span>  
  
4.  <span data-ttu-id="59a6b-212">Dans le **nom** , tapez **GlobalBankEastItinerary**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-212">In the **Name** box, type **GlobalBankEastItinerary**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-globalbank-east-itinerary"></a><span data-ttu-id="59a6b-213">Pour configurer les propriétés de l’itinéraire GlobalBank est</span><span class="sxs-lookup"><span data-stu-id="59a6b-213">To configure the properties of the GlobalBank East itinerary</span></span>  
  
1.  <span data-ttu-id="59a6b-214">Dans Visual Studio, cliquez sur l’aire de conception de **GlobalBankEastItinerary.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-214">In Visual Studio, click the design surface of **GlobalBankEastItinerary.itinerary**.</span></span> <span data-ttu-id="59a6b-215">Dans le **GlobalBankEastItinerary** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="59a6b-215">In the **GlobalBankEastItinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="59a6b-216">Dans le **modèle exportateur** la liste déroulante, cliquez sur **exportateur de feuille de route de base de données**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-216">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="59a6b-217">Cliquez sur le bouton de sélection (...) à côté du **base de données de la feuille de route** propriété.</span><span class="sxs-lookup"><span data-stu-id="59a6b-217">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="59a6b-218">Dans le **propriétés de connexion** boîte de dialogue, choisissez le serveur SQL qui héberge la base de données de référentiel d’itinéraire, puis spécifiez le nom de la base de données (le nom par défaut est **EsbItineraryDb**).</span><span class="sxs-lookup"><span data-stu-id="59a6b-218">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="59a6b-219">Dans le **état de la feuille de route** la liste déroulante, cliquez sur **déployées**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-219">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59a6b-220">Cette étape vous permet d’exporter l’itinéraire sur un référentiel central ; itinéraires peuvent être sélectionnés et attachés à partir de ce référentiel lorsque les messages sont reçus.</span><span class="sxs-lookup"><span data-stu-id="59a6b-220">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when messages are received.</span></span> <span data-ttu-id="59a6b-221">Vous configurerez ultérieurement le composant de pipeline de sélecteur de feuille de route pour utiliser le programme de résolution BRI à évaluer les messages entrants, puis sélectionnez la feuille de route approprié à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="59a6b-221">You will later configure the Itinerary Selector pipeline component to use the BRI resolver to evaluate inbound messages and select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="59a6b-222">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="59a6b-222">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="59a6b-223">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="59a6b-223">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="59a6b-224">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="59a6b-224">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="59a6b-225">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-225">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="59a6b-226">Dans le **extendeur** la liste déroulante, cliquez sur **Extension du Service ESB rampe d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-226">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="59a6b-227">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-227">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="59a6b-228">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-228">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="59a6b-229">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **ReceiveNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="59a6b-229">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="59a6b-230">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="59a6b-230">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="59a6b-231">Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-231">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="59a6b-232">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-232">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="59a6b-233">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-233">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="59a6b-234">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-234">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="59a6b-235">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **ReceiveNAOrder** élément de modèle et la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="59a6b-235">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="59a6b-236">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="59a6b-236">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="59a6b-237">Cliquez sur le **nom** propriété, puis tapez **RouteMessage**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-237">Click the **Name** property, and then type **RouteMessage**.</span></span>  
  
    2.  <span data-ttu-id="59a6b-238">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe itinéraire Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-238">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="59a6b-239">Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-239">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="59a6b-240">Avec le bouton droit le **résolveur** collection de la **RouteMessage** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-240">Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="59a6b-241">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="59a6b-241">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="59a6b-242">Cliquez sur le **nom** propriété, puis tapez **StaticResolver**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-242">Click the **Name** property, and then type **StaticResolver**.</span></span>  
  
    2.  <span data-ttu-id="59a6b-243">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-243">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="59a6b-244">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-244">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="59a6b-245">Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\East%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-245">Click the **Transport Location** property, and then type **C:\HowTos\Out\East%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="59a6b-246">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-246">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="59a6b-247">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteMessage** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="59a6b-247">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessage** model element.</span></span>  
  
6.  <span data-ttu-id="59a6b-248">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-248">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="59a6b-249">Faites glisser une connexion à partir de la **RouteMessage** élément de modèle à la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="59a6b-249">Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a><span data-ttu-id="59a6b-250">Pour exporter le modèle vers la base de données d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="59a6b-250">To export the model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="59a6b-251">Dans Visual Studio, cliquez sur l’aire de conception de la **GlobalBankEastItinerary** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-251">In Visual Studio, right-click the design surface of the **GlobalBankEastItinerary** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59a6b-252">L’itinéraire a été exporté vers la base de données d’itinéraire et peut maintenant être utilisé par le composant de sélecteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="59a6b-252">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.</span></span>  
  
2.  <span data-ttu-id="59a6b-253">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="59a6b-253">Save all project artifacts.</span></span>  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a><span data-ttu-id="59a6b-254">Pour créer et configurer un ESB rampe d’entrée</span><span class="sxs-lookup"><span data-stu-id="59a6b-254">To create and configure an ESB on-ramp</span></span>  
  
1.  <span data-ttu-id="59a6b-255">Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur **BizTalk Server**, puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-255">Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="59a6b-256">Dans la Console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-256">In the BizTalk Server Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand **Microsoft.Practices.ESB**.</span></span>  
  
3.  <span data-ttu-id="59a6b-257">Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-257">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
4.  <span data-ttu-id="59a6b-258">Dans le **sélectionner un Port de réception** boîte de dialogue, cliquez sur **OnRamp.Itinerary**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-258">In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="59a6b-259">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez **OnRamp.Itinerary.HowTo**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-259">In the **Receive Location Properties** dialog box, in the **Name** box, type **OnRamp.Itinerary.HowTo**.</span></span>  
  
6.  <span data-ttu-id="59a6b-260">Dans le **Type** la liste déroulante, cliquez sur **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-260">In the **Type** drop-down list, click **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="59a6b-261">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de réception** , tapez **C:\HowTos\DropFolder**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-261">In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type **C:\HowTos\DropFolder**, and then click **OK**.</span></span>  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a><span data-ttu-id="59a6b-262">Pour configurer le composant de pipeline du sélecteur de feuille de route</span><span class="sxs-lookup"><span data-stu-id="59a6b-262">To configure the Itinerary Selector pipeline component</span></span>  
  
1.  <span data-ttu-id="59a6b-263">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **pipeline de réception** la liste déroulante, cliquez sur **ItinerarySelectReceiveXml**, puis cliquez sur le bouton de sélection (...) ).</span><span class="sxs-lookup"><span data-stu-id="59a6b-263">In the **Receive Location Properties** dialog box, in the **Receive pipeline** drop-down list, click **ItinerarySelectReceiveXml**, and then click the ellipsis button (...).</span></span>  
  
2.  <span data-ttu-id="59a6b-264">Utilisez le **configurer le Pipeline** boîte de dialogue pour configurer les éléments suivants **itinéraire sélecteur** les propriétés du composant :</span><span class="sxs-lookup"><span data-stu-id="59a6b-264">Use the **Configure Pipeline** dialog box to configure the following **Itinerary Selector** component properties:</span></span>  
  
    1.  <span data-ttu-id="59a6b-265">Cliquez sur le **ItineraryFactKey** propriété, puis tapez **Resolver.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-265">Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.</span></span>  
  
    2.  <span data-ttu-id="59a6b-266">Cliquez sur le **ResolverConnectionString** propriété, puis tapez **BRI :\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true ;**</span><span class="sxs-lookup"><span data-stu-id="59a6b-266">Click the **ResolverConnectionString** property, and then type **BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**</span></span>  
  
    3.  <span data-ttu-id="59a6b-267">Cliquez sur **OK** pour fermer la **configurer le Pipeline** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="59a6b-267">Click **OK** to close the **Configure Pipeline** dialog box.</span></span>  
  
3.  <span data-ttu-id="59a6b-268">Cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="59a6b-268">Click **OK** to close the **Receive Location Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="59a6b-269">Dans la Console Administration de BizTalk Server, cliquez sur le **OnRamp.Itinerary.HowTo** emplacement de réception, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-269">In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Enable**.</span></span>  
  
#### <a name="to-test-the-itinerary-selector-and-business-rules"></a><span data-ttu-id="59a6b-270">Pour tester le sélecteur d’itinéraire et les règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="59a6b-270">To test the itinerary selector and business rules</span></span>  
  
1.  <span data-ttu-id="59a6b-271">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="59a6b-271">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="59a6b-272">Copie (ne déplacez pas) les fichiers East.xml et West.xml dans le dossier Dossier_dépôt.</span><span class="sxs-lookup"><span data-stu-id="59a6b-272">Copy (do not move) the files East.xml and West.xml to the DropFolder folder.</span></span>  
  
3.  <span data-ttu-id="59a6b-273">Accédez à C:\HowTos\Out. Vérifiez que les messages East%MessageID%.xml et West%MessageID%.xml ont été écrits dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="59a6b-273">Browse to C:\HowTos\Out. Verify that the East%MessageID%.xml and West%MessageID%.xml messages have been written to the directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59a6b-274">Si elle est identique à l’exception de la valeur de l’élément client, les messages ont été traités à l’aide d’itinéraires différents, selon la résolution du composant de pipeline sélecteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="59a6b-274">Though identical except for the value of the customer element, the messages were processed using different itineraries, based on the resolution of the Itinerary Selector pipeline component.</span></span>  
  
4.  <span data-ttu-id="59a6b-275">Dans la Console Administration de BizTalk Server, cliquez sur le **OnRamp.Itinerary.HowTo** emplacement de réception, puis cliquez sur **désactiver**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-275">In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Disable**.</span></span>  
  
5.  <span data-ttu-id="59a6b-276">Après le **OnRamp.Itinerary.HowTo** recevoir d’emplacement est désactivée, faites un clic droit, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-276">After the **OnRamp.Itinerary.HowTo** receive location is disabled, right-click it, and then click **Delete**.</span></span> <span data-ttu-id="59a6b-277">Dans le **emplacement de réception de confirmer la suppression** boîte de dialogue, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="59a6b-277">In the **Confirm delete receive location** dialog box, click **Yes**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="59a6b-278">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="59a6b-278">Additional Resources</span></span>  
 <span data-ttu-id="59a6b-279">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="59a6b-279">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="59a6b-280">Guide pratique pour fractionner un échange et router les messages résultants vers plusieurs emplacements de fichier à l’aide d’itinéraires distincts</span><span class="sxs-lookup"><span data-stu-id="59a6b-280">How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries</span></span>](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)  
  
-   [<span data-ttu-id="59a6b-281">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="59a6b-281">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="59a6b-282">Installation et exécution de l’exemple de résolution dynamique</span><span class="sxs-lookup"><span data-stu-id="59a6b-282">Installing and Running the Dynamic Resolution Sample</span></span>](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [<span data-ttu-id="59a6b-283">Utilisation de la résolution et du routage dynamiques</span><span class="sxs-lookup"><span data-stu-id="59a6b-283">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [<span data-ttu-id="59a6b-284">Modèles de routage des messages</span><span class="sxs-lookup"><span data-stu-id="59a6b-284">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)