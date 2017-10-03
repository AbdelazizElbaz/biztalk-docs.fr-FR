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
ms.openlocfilehash: 7d06bdea233c88fb740c728a414472d01a8fdc34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-select-an-itinerary-using-a-business-rules-policy"></a><span data-ttu-id="fc291-102">Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="fc291-102">How to: Select an Itinerary Using a Business Rules Policy</span></span>
## <a name="goal"></a><span data-ttu-id="fc291-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="fc291-103">Goal</span></span>  
 <span data-ttu-id="fc291-104">Cette section montre comment créer des règles d’entreprise qui peuvent être utilisés pour sélectionner un itinéraire en fonction du contenu d’un message reçu et comment configurer le composant de pipeline de sélecteur de feuille de route au sein d’un générique d’itinéraire rampe d’entrée à appeler ces règles.</span><span class="sxs-lookup"><span data-stu-id="fc291-104">This section demonstrates how to create business rules that can be used to select an itinerary based on the content of a received message and how to configure the Itinerary Selector pipeline component within a generic itinerary on-ramp to call these rules.</span></span> <span data-ttu-id="fc291-105">Cette section décrit un scénario d’entreprise dans laquelle messages sont routés différemment, selon la région dans lequel réside le client.</span><span class="sxs-lookup"><span data-stu-id="fc291-105">This section describes a business scenario in which messages are routed differently, based on the region in which the customer resides.</span></span>  
  
 <span data-ttu-id="fc291-106">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc291-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="fc291-107">Itinéraires de modèle pour les divisions de l’ouest et orientale de client Global Bank.</span><span class="sxs-lookup"><span data-stu-id="fc291-107">Model itineraries for the Western and Eastern divisions of customer Global Bank.</span></span>  
  
-   <span data-ttu-id="fc291-108">Créer des stratégies de règles d’entreprise qui permet de sélectionner une feuille de route pour le traitement de la demande.</span><span class="sxs-lookup"><span data-stu-id="fc291-108">Create business rules policies that will be used to select an itinerary for processing request.</span></span>  
  
-   <span data-ttu-id="fc291-109">Configurer le composant de pipeline de sélecteur de feuille de route pour utiliser une stratégie de règles d’entreprise pour sélectionner la feuille de route approprié.</span><span class="sxs-lookup"><span data-stu-id="fc291-109">Configure the Itinerary Selector pipeline component to use a business rules policy to select the appropriate itinerary.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fc291-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="fc291-110">Prerequisites</span></span>  
 <span data-ttu-id="fc291-111">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="fc291-111">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="fc291-112">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="fc291-112">Before You Begin</span></span>  
 <span data-ttu-id="fc291-113">Effectuez les tâches suivantes avant d’effectuer les étapes plus loin dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="fc291-113">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
-   <span data-ttu-id="fc291-114">Créer le message de test GlobalBank West.</span><span class="sxs-lookup"><span data-stu-id="fc291-114">Create the GlobalBank West test message.</span></span>  
  
-   <span data-ttu-id="fc291-115">Créer le message de test est de GlobalBank.</span><span class="sxs-lookup"><span data-stu-id="fc291-115">Create the GlobalBank East test message.</span></span>  
  
 <span data-ttu-id="fc291-116">Les procédures suivantes décrivent comment effectuer chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="fc291-116">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-the-globalbank-west-test-message"></a><span data-ttu-id="fc291-117">Pour créer le message de test GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="fc291-117">To create the GlobalBank West test message</span></span>  
  
1.  <span data-ttu-id="fc291-118">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="fc291-118">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="fc291-119">Créer une copie de NAOrderDoc.xml et nommez la copie West.xml.</span><span class="sxs-lookup"><span data-stu-id="fc291-119">Create a copy of NAOrderDoc.xml, and then name the copy West.xml.</span></span>  
  
3.  <span data-ttu-id="fc291-120">Dans le bloc-notes, ouvrez West.xml et modifiez la valeur de la **customerName** élément **GlobalBankWest**.</span><span class="sxs-lookup"><span data-stu-id="fc291-120">In Notepad, open West.xml, and then change the value of the **customerName** element to **GlobalBankWest**.</span></span>  
  
4.  <span data-ttu-id="fc291-121">Enregistrer West.xml en UTF-8, puis fermez le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="fc291-121">Save West.xml as UTF-8, and then close Notepad.</span></span>  
  
#### <a name="to-create-the-globalbank-east-test-message"></a><span data-ttu-id="fc291-122">Pour créer le message de test est de GlobalBank</span><span class="sxs-lookup"><span data-stu-id="fc291-122">To create the GlobalBank East test message</span></span>  
  
1.  <span data-ttu-id="fc291-123">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="fc291-123">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="fc291-124">Créer une copie de NAOrderDoc.xml et nommez la copie East.xml.</span><span class="sxs-lookup"><span data-stu-id="fc291-124">Create a copy of NAOrderDoc.xml, and then name the copy East.xml.</span></span>  
  
3.  <span data-ttu-id="fc291-125">Dans le bloc-notes, ouvrez East.xml et modifiez la valeur de la **customerName** élément **GlobalBankEast**.</span><span class="sxs-lookup"><span data-stu-id="fc291-125">In Notepad, open East.xml, and then change the value of the **customerName** element to **GlobalBankEast**.</span></span>  
  
4.  <span data-ttu-id="fc291-126">Enregistrer East.xml en UTF-8, puis fermez le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="fc291-126">Save East.xml as UTF-8, and then close Notepad.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="fc291-127">Étapes</span><span class="sxs-lookup"><span data-stu-id="fc291-127">Steps</span></span>  
  
#### <a name="to-create-a-business-rules-engine-bre-policy-to-select-an-itinerary-using-custom-message-properties"></a><span data-ttu-id="fc291-128">Pour créer une stratégie du moteur de règles d’entreprise (BRE) pour sélectionner un itinéraire à l’aide des propriétés de message personnalisées</span><span class="sxs-lookup"><span data-stu-id="fc291-128">To create a Business Rules Engine (BRE) policy to select an itinerary using custom message properties</span></span>  
  
1.  <span data-ttu-id="fc291-129">Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[prague](../includes/prague-md.md)]** , puis cliquez sur **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="fc291-129">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="fc291-130">Dans l’Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="fc291-130">In Policy Explorer, right-click **Policies**, and then click **Add New Policy**.</span></span> <span data-ttu-id="fc291-131">Nom de la stratégie **ResolveItineraryBasedOnCustomer**.</span><span class="sxs-lookup"><span data-stu-id="fc291-131">Name the policy **ResolveItineraryBasedOnCustomer**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc291-132">Cette rubrique utilise la même stratégie de règles d’entreprise et les itinéraires comme ceux créés dans la rubrique [Comment : fractionner un échange et de router les Messages résultant vers plusieurs fichiers emplacements à l’aide de Distinct itinéraires](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md).</span><span class="sxs-lookup"><span data-stu-id="fc291-132">This How-to topic uses the same business rules policy and itineraries as those created in the topic [How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md).</span></span> <span data-ttu-id="fc291-133">Si vous avez déjà effectué cette section, vous pouvez ignorer la procédure, « pour créer et configurer un ESB rampe d’entrée » plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="fc291-133">If you have already completed that section, you can skip to the procedure, "To create and configure an ESB on-ramp" later in this topic.</span></span>  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-west"></a><span data-ttu-id="fc291-134">Pour ajouter une règle de sélection pour le client GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="fc291-134">To add a selection rule for customer GlobalBank West</span></span>  
  
1.  <span data-ttu-id="fc291-135">Dans le **ResolveItineraryBasedOnCustomer** stratégie, avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle règle**.</span><span class="sxs-lookup"><span data-stu-id="fc291-135">In the **ResolveItineraryBasedOnCustomer** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.</span></span> <span data-ttu-id="fc291-136">Nommez la règle **SetGlobalBankWestItinerary**.</span><span class="sxs-lookup"><span data-stu-id="fc291-136">Name the rule **SetGlobalBankWestItinerary**.</span></span>  
  
2.  <span data-ttu-id="fc291-137">Dans l’Explorateur de faits, cliquez sur le **schémas XML** droit **schémas**, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="fc291-137">In Facts Explorer, click the **XML Schemas** tab, right-click **Schemas**, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="fc291-138">Dans le **les fichiers de schéma** boîte de dialogue, accédez à C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB. DynamicResolution.Schemas, sélectionnez **NAOrderDoc.xsd**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="fc291-138">In the **Schema Files** dialog box, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas, select **NAOrderDoc.xsd**, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc291-139">Voici le schéma qui définit le message NAOrderDoc.xml, qui a été utilisé pour créer les messages ouest / est que vous allez utiliser pour le test.</span><span class="sxs-lookup"><span data-stu-id="fc291-139">This is the schema that defines the NAOrderDoc.xml message, which was used to create the West and East messages you will use for testing.</span></span>  
  
4.  <span data-ttu-id="fc291-140">Dans l’Explorateur de faits, cliquez sur **NAOrderDoc.xsd**, cliquez sur le **Type de Document** propriété dans le volet Propriétés, puis tapez **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span><span class="sxs-lookup"><span data-stu-id="fc291-140">In Facts Explorer, click **NAOrderDoc.xsd**, click the **Document Type** property in the Properties pane, and then type **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc291-141">Il s’agit du nom qualifié complet du schéma.</span><span class="sxs-lookup"><span data-stu-id="fc291-141">This is the fully qualified name of the schema.</span></span>  
  
5.  <span data-ttu-id="fc291-142">Dans l’Explorateur de faits, développez **NAOrderDoc.xsd**, puis développez **OrderDoc**.</span><span class="sxs-lookup"><span data-stu-id="fc291-142">In Facts Explorer, expand **NAOrderDoc.xsd**, and then expand **OrderDoc**.</span></span>  
  
6.  <span data-ttu-id="fc291-143">Dans la fenêtre de la règle, cliquez sur **Conditions**, pointez sur **prédicats**, puis cliquez sur **égal**.</span><span class="sxs-lookup"><span data-stu-id="fc291-143">In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.</span></span>  
  
7.  <span data-ttu-id="fc291-144">Dans l’Explorateur de faits, faites glisser le **customerName** élément à la **argument1** nœud sous **Conditions**.</span><span class="sxs-lookup"><span data-stu-id="fc291-144">From Facts Explorer, drag the **customerName** element to the **argument1** node under **Conditions**.</span></span>  
  
8.  <span data-ttu-id="fc291-145">Cliquez sur le **argument2** nœud, puis tapez **GlobalBankWest**.</span><span class="sxs-lookup"><span data-stu-id="fc291-145">Click the **argument2** node, and then type **GlobalBankWest**.</span></span>  
  
9. <span data-ttu-id="fc291-146">Dans l’Explorateur de faits, cliquez sur le **vocabulaires** onglet. Développez le **ESB. Feuille de route** vocabulaire, développez **Version 1.1**, puis faites glisser le **définir un nom de feuille de route** définition **Actions**.</span><span class="sxs-lookup"><span data-stu-id="fc291-146">In Facts Explorer, click the **Vocabularies** tab. Expand the **ESB.Itinerary** vocabulary, expand **Version 1.1**, and then drag the **Set Itinerary Name** definition to **Actions**.</span></span>  
  
10. <span data-ttu-id="fc291-147">Cliquez sur  **\<une chaîne vide >**, puis tapez **GlobalBankWestItinerary**.</span><span class="sxs-lookup"><span data-stu-id="fc291-147">Click **\<empty string>**, and then type **GlobalBankWestItinerary**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc291-148">Plus loin dans cette rubrique, vous allez créer cette feuille de route pour traiter les messages de GlobalBank West.</span><span class="sxs-lookup"><span data-stu-id="fc291-148">Later in this How-to topic, you will create this itinerary to process messages from GlobalBank West.</span></span>  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-east"></a><span data-ttu-id="fc291-149">Pour ajouter une règle de sélection pour le client GlobalBank est</span><span class="sxs-lookup"><span data-stu-id="fc291-149">To add a selection rule for Customer GlobalBank East</span></span>  
  
1.  <span data-ttu-id="fc291-150">Dans l’Explorateur de stratégies, cliquez sur le **SetGlobalBankWestItinerary** de règle, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="fc291-150">In Policy Explorer, right-click the **SetGlobalBankWestItinerary** rule, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="fc291-151">Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="fc291-151">Right-click **Version 1.0 (not saved)**, and then click **Paste**.</span></span>  
  
3.  <span data-ttu-id="fc291-152">Dans le **nom de la nouvelle règle** boîte de dialogue, tapez **SetGlobalBankEastItinerary**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc291-152">In the **New Rule Name** dialog box, type **SetGlobalBankEastItinerary**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="fc291-153">Dans l’Explorateur de stratégies, cliquez sur le **SetGlobalBankEastItinerary** règle.</span><span class="sxs-lookup"><span data-stu-id="fc291-153">In Policy Explorer, click the **SetGlobalBankEastItinerary** rule.</span></span>  
  
5.  <span data-ttu-id="fc291-154">Dans le **Conditions** section, cliquez sur **GlobalBankWest**, puis cliquez sur **réinitialiser l’argument**.</span><span class="sxs-lookup"><span data-stu-id="fc291-154">In the **Conditions** section, right-click **GlobalBankWest**, and then click **Reset argument**.</span></span>  
  
6.  <span data-ttu-id="fc291-155">Cliquez sur **argument2**, puis tapez **GlobalBankEast**.</span><span class="sxs-lookup"><span data-stu-id="fc291-155">Click **argument2**, and then type **GlobalBankEast**.</span></span>  
  
7.  <span data-ttu-id="fc291-156">Dans le **Actions** section, cliquez sur **GlobalBankWestItinerary**, puis cliquez sur **réinitialiser l’argument**.</span><span class="sxs-lookup"><span data-stu-id="fc291-156">In the **Actions** section, right-click **GlobalBankWestItinerary**, and then click **Reset argument**.</span></span>  
  
8.  <span data-ttu-id="fc291-157">Cliquez sur  **\<une chaîne vide >** , puis tapez **GlobalBankEastItinerary**.</span><span class="sxs-lookup"><span data-stu-id="fc291-157">Click **\<empty string>** and then type **GlobalBankEastItinerary**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc291-158">Plus loin dans la rubrique de procédure, vous allez créer cette feuille de route pour traiter les messages à partir de GlobalBank est.</span><span class="sxs-lookup"><span data-stu-id="fc291-158">Later in the How-to topic, you will create this itinerary to process messages from GlobalBank East.</span></span>  
  
#### <a name="to-publish-and-deploy-the-policy"></a><span data-ttu-id="fc291-159">Pour publier et déployer la stratégie</span><span class="sxs-lookup"><span data-stu-id="fc291-159">To publish and deploy the policy</span></span>  
  
1.  <span data-ttu-id="fc291-160">Dans l’Explorateur de stratégies, sous la **ResolveItineraryBasedOnCustomer** stratégie, le bouton droit sur **Version 1.0 (non enregistrée)**, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="fc291-160">In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, right click **Version 1.0 (not saved)**, and then click **Publish**.</span></span>  
  
2.  <span data-ttu-id="fc291-161">Dans l’Explorateur de stratégies, sous la **ResolveItineraryBasedOnCustomer** stratégie, le bouton droit sur **Version 1.0 - publiée**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="fc291-161">In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, right click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model-for-globalbank-west-messages"></a><span data-ttu-id="fc291-162">Pour créer un modèle d’itinéraire langage spécifique à un domaine (DSL) ESB pour les messages GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="fc291-162">To create an ESB itinerary domain-specific language (DSL) model for GlobalBank West messages</span></span>  
  
1.  <span data-ttu-id="fc291-163">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="fc291-163">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="fc291-164">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="fc291-164">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="fc291-165">Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet Modèles, cliquez sur **ItineraryDsl**.</span><span class="sxs-lookup"><span data-stu-id="fc291-165">In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.</span></span>  
  
4.  <span data-ttu-id="fc291-166">Dans le **nom** , tapez **GlobalBankWestItinerary**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="fc291-166">In the **Name** box, type **GlobalBankWestItinerary**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-globalbank-west-itinerary"></a><span data-ttu-id="fc291-167">Pour configurer les propriétés de l’itinéraire GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="fc291-167">To configure the properties of the GlobalBank West itinerary</span></span>  
  
1.  <span data-ttu-id="fc291-168">Dans Visual Studio, cliquez sur l’aire de conception de **GlobalBankWestItinerary.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="fc291-168">In Visual Studio, click the design surface of **GlobalBankWestItinerary.itinerary**.</span></span> <span data-ttu-id="fc291-169">Dans le **GlobalBankWestItinerary** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc291-169">In the **GlobalBankWestItinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fc291-170">Dans le **modèle exportateur** la liste déroulante, cliquez sur **exportateur de feuille de route de base de données**.</span><span class="sxs-lookup"><span data-stu-id="fc291-170">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="fc291-171">Cliquez sur le bouton de sélection (...) à côté du **base de données de la feuille de route** propriété.</span><span class="sxs-lookup"><span data-stu-id="fc291-171">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="fc291-172">Dans le **propriétés de connexion** boîte de dialogue, choisissez le serveur SQL qui héberge la base de données de référentiel d’itinéraire, puis spécifiez le nom de la base de données (le nom par défaut est **EsbItineraryDb**).</span><span class="sxs-lookup"><span data-stu-id="fc291-172">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="fc291-173">Dans le **état de la feuille de route** la liste déroulante, cliquez sur **déployées**.</span><span class="sxs-lookup"><span data-stu-id="fc291-173">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc291-174">Cette étape vous permet d’exporter l’itinéraire sur un référentiel central ; itinéraires peuvent être sélectionnés et attachés à partir de ce référentiel lors de la réception du message.</span><span class="sxs-lookup"><span data-stu-id="fc291-174">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository upon message reception.</span></span> <span data-ttu-id="fc291-175">Vous configurerez ultérieurement le composant de pipeline de sélecteur de feuille de route pour utiliser le programme de résolution du moteur des règles d’entreprise (BRI) à évaluer les messages entrants, puis sélectionnez la feuille de route approprié à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="fc291-175">You will later configure the Itinerary Selector pipeline component to use the Business Rules Engine resolver (BRI) to evaluate inbound messages and select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="fc291-176">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="fc291-176">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="fc291-177">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="fc291-177">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="fc291-178">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc291-178">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fc291-179">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="fc291-179">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="fc291-180">Dans le **extendeur** la liste déroulante, cliquez sur **Extension du Service ESB rampe d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="fc291-180">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="fc291-181">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="fc291-181">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="fc291-182">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="fc291-182">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="fc291-183">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **ReceiveNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="fc291-183">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="fc291-184">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc291-184">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fc291-185">Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="fc291-185">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="fc291-186">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="fc291-186">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="fc291-187">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="fc291-187">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="fc291-188">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="fc291-188">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="fc291-189">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **ReceiveNAOrder** élément de modèle et la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="fc291-189">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="fc291-190">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc291-190">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fc291-191">Cliquez sur le **nom** propriété, puis tapez **RouteMessage**.</span><span class="sxs-lookup"><span data-stu-id="fc291-191">Click the **Name** property, and then type **RouteMessage**.</span></span>  
  
    2.  <span data-ttu-id="fc291-192">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe itinéraire Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="fc291-192">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="fc291-193">Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="fc291-193">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="fc291-194">Avec le bouton droit le **résolveur** collection de la **RouteMessage** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="fc291-194">Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="fc291-195">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc291-195">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fc291-196">Cliquez sur le **nom** propriété, puis tapez **StaticResolver**.</span><span class="sxs-lookup"><span data-stu-id="fc291-196">Click the **Name** property, and then type **StaticResolver**.</span></span>  
  
    2.  <span data-ttu-id="fc291-197">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="fc291-197">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="fc291-198">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="fc291-198">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="fc291-199">Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\West%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="fc291-199">Click the **Transport Location** property, and then type **C:\HowTos\Out\West%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="fc291-200">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="fc291-200">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="fc291-201">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteMessage** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="fc291-201">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessage** model element.</span></span>  
  
6.  <span data-ttu-id="fc291-202">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="fc291-202">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="fc291-203">Faites glisser une connexion à partir de la **RouteMessage** élément de modèle à la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="fc291-203">Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a><span data-ttu-id="fc291-204">Pour exporter le modèle vers la base de données d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="fc291-204">To export the model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="fc291-205">Dans Visual Studio, cliquez sur l’aire de conception de la **GlobalBankWestItinerary** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="fc291-205">In Visual Studio, right-click the design surface of the **GlobalBankWestItinerary** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc291-206">L’itinéraire a été exporté vers la base de données d’itinéraire et peut maintenant être utilisé par le composant de sélecteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="fc291-206">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.</span></span>  
  
2.  <span data-ttu-id="fc291-207">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="fc291-207">Save all project artifacts.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-east-message"></a><span data-ttu-id="fc291-208">Pour créer un modèle DSL ESB d’itinéraire pour le message de GlobalBank est</span><span class="sxs-lookup"><span data-stu-id="fc291-208">To create an ESB itinerary DSL model for GlobalBank East message</span></span>  
  
1.  <span data-ttu-id="fc291-209">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="fc291-209">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="fc291-210">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="fc291-210">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="fc291-211">Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet Modèles, cliquez sur **ItineraryDsl**.</span><span class="sxs-lookup"><span data-stu-id="fc291-211">In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.</span></span>  
  
4.  <span data-ttu-id="fc291-212">Dans le **nom** , tapez **GlobalBankEastItinerary**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="fc291-212">In the **Name** box, type **GlobalBankEastItinerary**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-globalbank-east-itinerary"></a><span data-ttu-id="fc291-213">Pour configurer les propriétés de l’itinéraire GlobalBank est</span><span class="sxs-lookup"><span data-stu-id="fc291-213">To configure the properties of the GlobalBank East itinerary</span></span>  
  
1.  <span data-ttu-id="fc291-214">Dans Visual Studio, cliquez sur l’aire de conception de **GlobalBankEastItinerary.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="fc291-214">In Visual Studio, click the design surface of **GlobalBankEastItinerary.itinerary**.</span></span> <span data-ttu-id="fc291-215">Dans le **GlobalBankEastItinerary** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc291-215">In the **GlobalBankEastItinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fc291-216">Dans le **modèle exportateur** la liste déroulante, cliquez sur **exportateur de feuille de route de base de données**.</span><span class="sxs-lookup"><span data-stu-id="fc291-216">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="fc291-217">Cliquez sur le bouton de sélection (...) à côté du **base de données de la feuille de route** propriété.</span><span class="sxs-lookup"><span data-stu-id="fc291-217">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="fc291-218">Dans le **propriétés de connexion** boîte de dialogue, choisissez le serveur SQL qui héberge la base de données de référentiel d’itinéraire, puis spécifiez le nom de la base de données (le nom par défaut est **EsbItineraryDb**).</span><span class="sxs-lookup"><span data-stu-id="fc291-218">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="fc291-219">Dans le **état de la feuille de route** la liste déroulante, cliquez sur **déployées**.</span><span class="sxs-lookup"><span data-stu-id="fc291-219">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc291-220">Cette étape vous permet d’exporter l’itinéraire sur un référentiel central ; itinéraires peuvent être sélectionnés et attachés à partir de ce référentiel lorsque les messages sont reçus.</span><span class="sxs-lookup"><span data-stu-id="fc291-220">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when messages are received.</span></span> <span data-ttu-id="fc291-221">Vous configurerez ultérieurement le composant de pipeline de sélecteur de feuille de route pour utiliser le programme de résolution BRI à évaluer les messages entrants, puis sélectionnez la feuille de route approprié à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="fc291-221">You will later configure the Itinerary Selector pipeline component to use the BRI resolver to evaluate inbound messages and select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="fc291-222">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="fc291-222">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="fc291-223">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="fc291-223">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="fc291-224">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc291-224">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fc291-225">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="fc291-225">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="fc291-226">Dans le **extendeur** la liste déroulante, cliquez sur **Extension du Service ESB rampe d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="fc291-226">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="fc291-227">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="fc291-227">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="fc291-228">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="fc291-228">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="fc291-229">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **ReceiveNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="fc291-229">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="fc291-230">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc291-230">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fc291-231">Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="fc291-231">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="fc291-232">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="fc291-232">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="fc291-233">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="fc291-233">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="fc291-234">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="fc291-234">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="fc291-235">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **ReceiveNAOrder** élément de modèle et la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="fc291-235">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="fc291-236">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc291-236">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fc291-237">Cliquez sur le **nom** propriété, puis tapez **RouteMessage**.</span><span class="sxs-lookup"><span data-stu-id="fc291-237">Click the **Name** property, and then type **RouteMessage**.</span></span>  
  
    2.  <span data-ttu-id="fc291-238">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe itinéraire Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="fc291-238">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="fc291-239">Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="fc291-239">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="fc291-240">Avec le bouton droit le **résolveur** collection de la **RouteMessage** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="fc291-240">Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="fc291-241">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc291-241">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fc291-242">Cliquez sur le **nom** propriété, puis tapez **StaticResolver**.</span><span class="sxs-lookup"><span data-stu-id="fc291-242">Click the **Name** property, and then type **StaticResolver**.</span></span>  
  
    2.  <span data-ttu-id="fc291-243">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="fc291-243">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="fc291-244">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="fc291-244">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="fc291-245">Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\East%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="fc291-245">Click the **Transport Location** property, and then type **C:\HowTos\Out\East%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="fc291-246">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="fc291-246">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="fc291-247">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteMessage** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="fc291-247">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessage** model element.</span></span>  
  
6.  <span data-ttu-id="fc291-248">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="fc291-248">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="fc291-249">Faites glisser une connexion à partir de la **RouteMessage** élément de modèle à la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="fc291-249">Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a><span data-ttu-id="fc291-250">Pour exporter le modèle vers la base de données d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="fc291-250">To export the model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="fc291-251">Dans Visual Studio, cliquez sur l’aire de conception de la **GlobalBankEastItinerary** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="fc291-251">In Visual Studio, right-click the design surface of the **GlobalBankEastItinerary** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc291-252">L’itinéraire a été exporté vers la base de données d’itinéraire et peut maintenant être utilisé par le composant de sélecteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="fc291-252">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.</span></span>  
  
2.  <span data-ttu-id="fc291-253">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="fc291-253">Save all project artifacts.</span></span>  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a><span data-ttu-id="fc291-254">Pour créer et configurer un ESB rampe d’entrée</span><span class="sxs-lookup"><span data-stu-id="fc291-254">To create and configure an ESB on-ramp</span></span>  
  
1.  <span data-ttu-id="fc291-255">Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[prague](../includes/prague-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="fc291-255">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="fc291-256">Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, développez **groupe BizTalk**, développez **Applications**, puis développez **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="fc291-256">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand **Microsoft.Practices.ESB**.</span></span>  
  
3.  <span data-ttu-id="fc291-257">Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="fc291-257">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
4.  <span data-ttu-id="fc291-258">Dans le **sélectionner un Port de réception** boîte de dialogue, cliquez sur **OnRamp.Itinerary**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc291-258">In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="fc291-259">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez **OnRamp.Itinerary.HowTo**.</span><span class="sxs-lookup"><span data-stu-id="fc291-259">In the **Receive Location Properties** dialog box, in the **Name** box, type **OnRamp.Itinerary.HowTo**.</span></span>  
  
6.  <span data-ttu-id="fc291-260">Dans le **Type** la liste déroulante, cliquez sur **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="fc291-260">In the **Type** drop-down list, click **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="fc291-261">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de réception** , tapez **C:\HowTos\DropFolder**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc291-261">In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type **C:\HowTos\DropFolder**, and then click **OK**.</span></span>  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a><span data-ttu-id="fc291-262">Pour configurer le composant de pipeline du sélecteur de feuille de route</span><span class="sxs-lookup"><span data-stu-id="fc291-262">To configure the Itinerary Selector pipeline component</span></span>  
  
1.  <span data-ttu-id="fc291-263">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **pipeline de réception** la liste déroulante, cliquez sur **ItinerarySelectReceiveXml**, puis cliquez sur le bouton de sélection (...) ).</span><span class="sxs-lookup"><span data-stu-id="fc291-263">In the **Receive Location Properties** dialog box, in the **Receive pipeline** drop-down list, click **ItinerarySelectReceiveXml**, and then click the ellipsis button (...).</span></span>  
  
2.  <span data-ttu-id="fc291-264">Utilisez le **configurer le Pipeline** boîte de dialogue pour configurer les éléments suivants **itinéraire sélecteur** les propriétés du composant :</span><span class="sxs-lookup"><span data-stu-id="fc291-264">Use the **Configure Pipeline** dialog box to configure the following **Itinerary Selector** component properties:</span></span>  
  
    1.  <span data-ttu-id="fc291-265">Cliquez sur le **ItineraryFactKey** propriété, puis tapez **Resolver.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="fc291-265">Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.</span></span>  
  
    2.  <span data-ttu-id="fc291-266">Cliquez sur le **ResolverConnectionString** propriété, puis tapez **BRI :\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true ;**</span><span class="sxs-lookup"><span data-stu-id="fc291-266">Click the **ResolverConnectionString** property, and then type **BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**</span></span>  
  
    3.  <span data-ttu-id="fc291-267">Cliquez sur **OK** pour fermer la **configurer le Pipeline** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="fc291-267">Click **OK** to close the **Configure Pipeline** dialog box.</span></span>  
  
3.  <span data-ttu-id="fc291-268">Cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="fc291-268">Click **OK** to close the **Receive Location Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="fc291-269">Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, avec le bouton droit le **OnRamp.Itinerary.HowTo** emplacement de réception, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="fc291-269">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Enable**.</span></span>  
  
#### <a name="to-test-the-itinerary-selector-and-business-rules"></a><span data-ttu-id="fc291-270">Pour tester le sélecteur d’itinéraire et les règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="fc291-270">To test the itinerary selector and business rules</span></span>  
  
1.  <span data-ttu-id="fc291-271">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="fc291-271">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="fc291-272">Copie (ne déplacez pas) les fichiers East.xml et West.xml dans le dossier Dossier_dépôt.</span><span class="sxs-lookup"><span data-stu-id="fc291-272">Copy (do not move) the files East.xml and West.xml to the DropFolder folder.</span></span>  
  
3.  <span data-ttu-id="fc291-273">Accédez à C:\HowTos\Out. Vérifiez que les messages East%MessageID%.xml et West%MessageID%.xml ont été écrits dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="fc291-273">Browse to C:\HowTos\Out. Verify that the East%MessageID%.xml and West%MessageID%.xml messages have been written to the directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc291-274">Si elle est identique à l’exception de la valeur de l’élément client, les messages ont été traités à l’aide d’itinéraires différents, selon la résolution du composant de pipeline sélecteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="fc291-274">Though identical except for the value of the customer element, the messages were processed using different itineraries, based on the resolution of the Itinerary Selector pipeline component.</span></span>  
  
4.  <span data-ttu-id="fc291-275">Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, avec le bouton droit le **OnRamp.Itinerary.HowTo** emplacement de réception, puis cliquez sur **désactiver**.</span><span class="sxs-lookup"><span data-stu-id="fc291-275">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Disable**.</span></span>  
  
5.  <span data-ttu-id="fc291-276">Après le **OnRamp.Itinerary.HowTo** recevoir d’emplacement est désactivée, faites un clic droit, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="fc291-276">After the **OnRamp.Itinerary.HowTo** receive location is disabled, right-click it, and then click **Delete**.</span></span> <span data-ttu-id="fc291-277">Dans le **emplacement de réception de confirmer la suppression** boîte de dialogue, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="fc291-277">In the **Confirm delete receive location** dialog box, click **Yes**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="fc291-278">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="fc291-278">Additional Resources</span></span>  
 <span data-ttu-id="fc291-279">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc291-279">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="fc291-280">Comment : fractionner un échange et de router les Messages résultants vers plusieurs emplacements de fichier à l’aide d’itinéraires distinctes</span><span class="sxs-lookup"><span data-stu-id="fc291-280">How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries</span></span>](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)  
  
-   [<span data-ttu-id="fc291-281">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="fc291-281">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="fc291-282">Installer et exécuter l’exemple de résolution dynamique</span><span class="sxs-lookup"><span data-stu-id="fc291-282">Installing and Running the Dynamic Resolution Sample</span></span>](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [<span data-ttu-id="fc291-283">À l’aide de la résolution dynamique et le routage</span><span class="sxs-lookup"><span data-stu-id="fc291-283">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [<span data-ttu-id="fc291-284">Modèles de routage de messages</span><span class="sxs-lookup"><span data-stu-id="fc291-284">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)