---
title: "Comment : fractionner un échange et de router les Messages résultants vers plusieurs emplacements de fichier à l’aide d’itinéraires distinctes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccd46bee-e4a1-4846-8bde-b0460bda1e72
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c752c4b98f6a68e0a86ba4a418eab0705a7c513
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-split-an-interchange-and-route-the-resulting-messages-to-multiple-file-locations-using-distinct-itineraries"></a><span data-ttu-id="da8dc-102">Comment : fractionner un échange et de router les Messages résultants vers plusieurs emplacements de fichier à l’aide d’itinéraires distinctes</span><span class="sxs-lookup"><span data-stu-id="da8dc-102">How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries</span></span>
## <a name="goal"></a><span data-ttu-id="da8dc-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="da8dc-103">Goal</span></span>  
 <span data-ttu-id="da8dc-104">Cette section montre comment créer un ESB rampe d’entrée qui utilise le **ItinerarySelectReceiveXml** bon de pipeline et comment configurer les composants du pipeline pour fractionner un échange entrant, puis sélectionnez le routage approprié pour chaque message résultant, selon le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="da8dc-104">This section demonstrates how to create an ESB on-ramp that uses the **ItinerarySelectReceiveXml** pipeline and how to configure the pipeline's components to split an inbound interchange and select the appropriate routing slip for each resulting message, based on message context.</span></span> <span data-ttu-id="da8dc-105">Sélection d’itinéraire est résolue à l’aide d’une stratégie de règles d’entreprise, et les messages sont routés différemment selon la région dans lequel réside le client.</span><span class="sxs-lookup"><span data-stu-id="da8dc-105">Itinerary selection will be resolved using a business rules policy, and messages will be routed differently based on the region in which the customer resides.</span></span>  
  
 <span data-ttu-id="da8dc-106">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="da8dc-107">Créer un ESB rampe d’entrée qui fractionne un échange XML.</span><span class="sxs-lookup"><span data-stu-id="da8dc-107">Create an ESB on-ramp that splits an XML interchange.</span></span>  
  
-   <span data-ttu-id="da8dc-108">Configurer le composant de pipeline de sélecteur de feuille de route pour utiliser une stratégie de règles d’entreprise pour sélectionner la feuille de route approprié.</span><span class="sxs-lookup"><span data-stu-id="da8dc-108">Configure the Itinerary Selector pipeline component to use a business rules policy to select the appropriate itinerary.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="da8dc-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="da8dc-109">Prerequisites</span></span>  
 <span data-ttu-id="da8dc-110">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="da8dc-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="da8dc-111">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="da8dc-111">Before You Begin</span></span>  
 <span data-ttu-id="da8dc-112">Effectuez les tâches suivantes avant d’effectuer les étapes plus loin dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="da8dc-112">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
-   <span data-ttu-id="da8dc-113">Créer les artefacts requis.</span><span class="sxs-lookup"><span data-stu-id="da8dc-113">Create the required artifacts.</span></span>  
  
-   <span data-ttu-id="da8dc-114">Ajouter un projet de schémas à la solution de modèles.</span><span class="sxs-lookup"><span data-stu-id="da8dc-114">Add a schemas project to the Patterns solution.</span></span>  
  
-   <span data-ttu-id="da8dc-115">Ajouter les artefacts de projet de schémas.</span><span class="sxs-lookup"><span data-stu-id="da8dc-115">Add the artifacts to the Schemas project.</span></span>  
  
-   <span data-ttu-id="da8dc-116">Créer une stratégie BRE pour sélectionner un itinéraire à l’aide des propriétés de message personnalisées.</span><span class="sxs-lookup"><span data-stu-id="da8dc-116">Create a BRE policy to select an itinerary using custom message properties.</span></span>  
  
-   <span data-ttu-id="da8dc-117">Ajouter une règle de sélection pour le client GlobalBank West.</span><span class="sxs-lookup"><span data-stu-id="da8dc-117">Add a selection rule for customer GlobalBank West.</span></span>  
  
-   <span data-ttu-id="da8dc-118">Ajouter une règle de sélection pour le client est de GlobalBank.</span><span class="sxs-lookup"><span data-stu-id="da8dc-118">Add a selection rule for customer GlobalBank East.</span></span>  
  
-   <span data-ttu-id="da8dc-119">Publier et déployer la stratégie.</span><span class="sxs-lookup"><span data-stu-id="da8dc-119">Publish and deploy the policy.</span></span>  
  
-   <span data-ttu-id="da8dc-120">Créer un modèle d’itinéraire langage spécifique à un domaine (DSL) pour les messages GlobalBank West ESB.</span><span class="sxs-lookup"><span data-stu-id="da8dc-120">Create an ESB itinerary domain-specific language (DSL) model for GlobalBank West messages.</span></span>  
  
-   <span data-ttu-id="da8dc-121">Configurez les propriétés de l’itinéraire GlobalBank West.</span><span class="sxs-lookup"><span data-stu-id="da8dc-121">Configure the properties of the GlobalBank West itinerary.</span></span>  
  
-   <span data-ttu-id="da8dc-122">Définir la structure de la feuille de route GlobalBank West.</span><span class="sxs-lookup"><span data-stu-id="da8dc-122">Define the structure of the GlobalBank West itinerary.</span></span>  
  
-   <span data-ttu-id="da8dc-123">Exporter le modèle de GlobalBank West vers la base de données d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="da8dc-123">Export the GlobalBank West model to the itinerary database.</span></span>  
  
-   <span data-ttu-id="da8dc-124">Créer un modèle DSL ESB d’itinéraire pour les messages de GlobalBank est.</span><span class="sxs-lookup"><span data-stu-id="da8dc-124">Create an ESB itinerary DSL model for GlobalBank East messages.</span></span>  
  
-   <span data-ttu-id="da8dc-125">Configurez les propriétés de l’itinéraire GlobalBank est.</span><span class="sxs-lookup"><span data-stu-id="da8dc-125">Configure the properties of the GlobalBank East itinerary.</span></span>  
  
-   <span data-ttu-id="da8dc-126">Définir la structure de la feuille de route GlobalBank est.</span><span class="sxs-lookup"><span data-stu-id="da8dc-126">Define the structure of the GlobalBank East itinerary.</span></span>  
  
-   <span data-ttu-id="da8dc-127">Exporter le modèle GlobalBank est à la base de données d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="da8dc-127">Export the GlobalBank East model to the itinerary database.</span></span>  
  
     <span data-ttu-id="da8dc-128">Les procédures suivantes décrivent comment effectuer chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="da8dc-128">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-the-required-artifacts"></a><span data-ttu-id="da8dc-129">Pour créer les artefacts requis</span><span class="sxs-lookup"><span data-stu-id="da8dc-129">To create the required artifacts</span></span>  
  
1.  <span data-ttu-id="da8dc-130">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="da8dc-130">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="da8dc-131">Créer un nouveau document texte nommé OrderDocEnvelope.xsd.</span><span class="sxs-lookup"><span data-stu-id="da8dc-131">Create a new text document named OrderDocEnvelope.xsd.</span></span>  
  
3.  <span data-ttu-id="da8dc-132">Ouvrez le schéma OrderDocEnvelope.xsd dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="da8dc-132">Open the OrderDocEnvelope.xsd schema in Notepad.</span></span>  
  
4.  <span data-ttu-id="da8dc-133">Modifier le document en utilisant le code suivant.</span><span class="sxs-lookup"><span data-stu-id="da8dc-133">Edit the document using the following code.</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <xs:schema xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://ESB.BizUnit.Map.Test" targetNamespace="http://ESB.BizUnit.Map.Test" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
      <xs:import schemaLocation="GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc" namespace="http://globalbank.esb.dynamicresolution.com/northamericanservices/" />  
      <xs:annotation>  
        <xs:appinfo>  
          <b:schemaInfo is_envelope="yes" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" />  
          <b:references>  
            <b:reference targetNamespace="http://globalbank.esb.dynamicresolution.com/northamericanservices/" />  
          </b:references>  
        </xs:appinfo>  
      </xs:annotation>  
      <xs:element name="OrderEnvelope">  
        <xs:annotation>  
          <xs:appinfo>  
            <b:recordInfo body_xpath="/*[local-name()='OrderEnvelope' and namespace-uri()='http://ESB.BizUnit.Map.Test']" />  
          </xs:appinfo>  
        </xs:annotation>  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element ref="ns0:OrderDoc" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
5.  <span data-ttu-id="da8dc-134">Enregistrer OrderDocEnvelope.xsd en UTF-8, puis fermez le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="da8dc-134">Save OrderDocEnvelope.xsd as UTF-8, and then close Notepad.</span></span>  
  
6.  <span data-ttu-id="da8dc-135">Dans le dossier C:\HowTos, créez un nouveau document texte nommé Batch.xml.</span><span class="sxs-lookup"><span data-stu-id="da8dc-135">In the C:\HowTos folder, create a new text document named Batch.xml.</span></span>  
  
7.  <span data-ttu-id="da8dc-136">Dans le bloc-notes, ouvrez Batch.xml.</span><span class="sxs-lookup"><span data-stu-id="da8dc-136">In Notepad, open Batch.xml.</span></span>  
  
8.  <span data-ttu-id="da8dc-137">Modifier le document en utilisant le code suivant.</span><span class="sxs-lookup"><span data-stu-id="da8dc-137">Edit the document using the following code.</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <ns0:OrderEnvelope xmlns:ns0="http://ESB.BizUnit.Map.Test">  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankWest</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>10</ns0:requestType>  
      </ns0:OrderDoc>  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankEast</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>11</ns0:requestType>  
      </ns0:OrderDoc>  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankEast</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>12</ns0:requestType>  
      </ns0:OrderDoc>  
    </ns0:OrderEnvelope>  
    ```  
  
9. <span data-ttu-id="da8dc-138">Enregistrez et fermez Batch.xml.</span><span class="sxs-lookup"><span data-stu-id="da8dc-138">Save and close Batch.xml.</span></span>  
  
#### <a name="to-add-a-schemas-project-to-the-patterns-solution"></a><span data-ttu-id="da8dc-139">Pour ajouter un projet de schémas à la solution de modèles</span><span class="sxs-lookup"><span data-stu-id="da8dc-139">To add a schemas project to the Patterns solution</span></span>  
  
1.  <span data-ttu-id="da8dc-140">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="da8dc-140">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="da8dc-141">Dans l’Explorateur de solutions, cliquez sur **Solution « Modèles »**, pointez sur **ajouter**, puis cliquez sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-141">In Solution Explorer, right-click **Solution 'Patterns'**, point to **Add**, and then click **New Project**.</span></span>  
  
3.  <span data-ttu-id="da8dc-142">Dans le **ajouter un nouveau projet** boîte de dialogue, dans le volet types de projet, cliquez sur **projets BizTalk**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="da8dc-142">In the **Add New Project** dialog box, in the Project types pane, click **BizTalk Projects**, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="da8dc-143">Dans le volet Modèles, cliquez sur **projet BizTalk Server vide**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-143">In the Templates pane, click **Empty BizTalk Server Project**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-144">Dans le **nom** , tapez **Patterns.Schemas**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-144">In the **Name** box, type **Patterns.Schemas**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="da8dc-145">Dans l’Explorateur de solutions, cliquez sur **Patterns.Schemas**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-145">In Solution Explorer, right-click **Patterns.Schemas**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="da8dc-146">Dans la fenêtre Propriétés, sur le **signature** onglet, sélectionnez le **signer l’assembly** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="da8dc-146">In the Properties window, on the **Signing** tab, select the **Sign the assembly** check box.</span></span>  
  
6.  <span data-ttu-id="da8dc-147">Dans le **choisir un fichier de clé de nom fort** la liste déroulante, cliquez sur  **\<nouveau... >**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-147">In the **Choose a strong name key file** drop-down list, click **\<New...>**.</span></span>  
  
7.  <span data-ttu-id="da8dc-148">Dans le **créer une clé de nom fort** boîte de dialogue zone, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-148">In the **Create Strong Name Key** dialog box, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="da8dc-149">Dans le **nom de fichier de clé** , tapez **fractionnement**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-149">In the **Key file name** box, type **Splitting**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-150">Désactivez le **protéger mon fichier de clé avec un mot de passe** case à cocher, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-150">Clear the **Protect my key file with a password** check box, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="da8dc-151">Dans la fenêtre Propriétés, sur le **déploiement** sous l’onglet du **nom de l’Application** , tapez **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-151">In the Properties window, on the **Deployment** tab, in the **Application Name** box, type **Microsoft.Practices.ESB**.</span></span>  
  
9. <span data-ttu-id="da8dc-152">Fermez la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="da8dc-152">Close the Properties window.</span></span>  
  
#### <a name="to-add-the-artifacts-to-the-schemas-project"></a><span data-ttu-id="da8dc-153">Pour ajouter les artefacts de projet de schémas</span><span class="sxs-lookup"><span data-stu-id="da8dc-153">To add the artifacts to the Schemas project</span></span>  
  
1.  <span data-ttu-id="da8dc-154">Dans l’Explorateur de solutions, cliquez sur **Patterns.Schemas**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-154">In Solution Explorer, right-click **Patterns.Schemas**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="da8dc-155">Sur le **Parcourir** onglet de la **ajouter une référence** boîte de dialogue, recherchez et sélectionnez C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB. DynamicResolution.Schemas\bin\Debug\GlobalBank.ESB.DynamicResolution.Schemas.dll, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-155">On the **Browse** tab of the **Add Reference** dialog box, browse to and select C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas\bin\Debug\GlobalBank.ESB.DynamicResolution.Schemas.dll, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="da8dc-156">Dans l’Explorateur de solutions, cliquez sur **Patterns.Schemas**, pointez sur **ajouter**, puis cliquez sur **élément existant**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-156">In Solution Explorer, right-click **Patterns.Schemas**, point to **Add**, and then click **Existing Item**.</span></span>  
  
4.  <span data-ttu-id="da8dc-157">Dans le **ajouter un élément existant** boîte de dialogue, recherchez et sélectionnez C:\HowTos\OrderDocEnvelope.xsd, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-157">In the **Add Existing Item** dialog box, browse to and select C:\HowTos\OrderDocEnvelope.xsd, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="da8dc-158">Enregistrez tous les artefacts de solution.</span><span class="sxs-lookup"><span data-stu-id="da8dc-158">Save all solution artifacts.</span></span>  
  
6.  <span data-ttu-id="da8dc-159">Dans l’Explorateur de solutions, cliquez sur **Patterns.Schemas**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-159">In Solution Explorer, right-click **Patterns.Schemas**, and then click **Deploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da8dc-160">Cette rubrique utilise la même stratégie de règles d’entreprise et les itinéraires comme ceux créés dans le [Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="da8dc-160">This How-to topic uses the same business rules policy and itineraries as those created in the [How to: Select an Itinerary Using a Business Rules Policy](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md) topic.</span></span> <span data-ttu-id="da8dc-161">Si vous n’avez pas encore effectué de cette section, effectuez les étapes supplémentaires suivantes.</span><span class="sxs-lookup"><span data-stu-id="da8dc-161">If you have not already completed that section, please complete the following additional steps.</span></span> <span data-ttu-id="da8dc-162">Si vous avez terminé cette section, passez directement à la section « Étapes ».</span><span class="sxs-lookup"><span data-stu-id="da8dc-162">If you have completed that section, continue directly to the "Steps" section.</span></span>  
  
#### <a name="to-create-a-business-rules-engine-bre-policy-to-select-an-itinerary-using-custom-message-properties"></a><span data-ttu-id="da8dc-163">Pour créer une stratégie du moteur de règles d’entreprise (BRE) pour sélectionner un itinéraire à l’aide des propriétés de message personnalisées</span><span class="sxs-lookup"><span data-stu-id="da8dc-163">To create a Business Rules Engine (BRE) policy to select an itinerary using custom message properties</span></span>  
  
1.  <span data-ttu-id="da8dc-164">Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[prague](../includes/prague-md.md)]** , puis cliquez sur **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-164">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="da8dc-165">Dans l’Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-165">In Policy Explorer, right-click **Policies**, and then click **Add New Policy**.</span></span> <span data-ttu-id="da8dc-166">Nom de la stratégie **ResolveItineraryBasedOnCustomer**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-166">Name the policy **ResolveItineraryBasedOnCustomer**.</span></span>  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-west"></a><span data-ttu-id="da8dc-167">Pour ajouter une règle de sélection pour le client GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="da8dc-167">To add a selection rule for customer GlobalBank West</span></span>  
  
1.  <span data-ttu-id="da8dc-168">Dans le **ResolveItineraryBasedOnCustomer** stratégie, avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle règle**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-168">In the **ResolveItineraryBasedOnCustomer** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.</span></span> <span data-ttu-id="da8dc-169">Nommez la règle **SetGlobalBankWestItinerary**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-169">Name the rule **SetGlobalBankWestItinerary**.</span></span>  
  
2.  <span data-ttu-id="da8dc-170">Dans l’Explorateur de faits, cliquez sur le **schémas XML** droit **schémas**, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-170">In Facts Explorer, click the **XML Schemas** tab, right-click **Schemas**, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="da8dc-171">Dans le **les fichiers de schéma** boîte de dialogue, accédez à C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB. DynamicResolution.Schemas, sélectionnez NAOrderDoc.xsd, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-171">In the **Schema Files** dialog box, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas, select NAOrderDoc.xsd, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da8dc-172">Voici le schéma qui définit le message NAOrderDoc.xml, qui a été utilisé pour créer les messages ouest / est que vous allez utiliser pour le test.</span><span class="sxs-lookup"><span data-stu-id="da8dc-172">This is the schema that defines the NAOrderDoc.xml message, which was used to create the West and East messages you will use for testing.</span></span>  
  
4.  <span data-ttu-id="da8dc-173">Dans l’Explorateur de faits, cliquez sur NAOrderDoc.xsd, cliquez sur le **Type de Document** propriété dans le volet Propriétés, puis tapez **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-173">In Facts Explorer, click NAOrderDoc.xsd, click the **Document Type** property in the Properties pane, and then type **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da8dc-174">Il s’agit du nom qualifié complet du schéma.</span><span class="sxs-lookup"><span data-stu-id="da8dc-174">This is the fully qualified name of the schema.</span></span>  
  
5.  <span data-ttu-id="da8dc-175">Dans l’Explorateur de faits, développez **NAOrderDoc.xsd**, puis développez **OrderDoc**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-175">In Facts Explorer, expand **NAOrderDoc.xsd**, and then expand **OrderDoc**.</span></span>  
  
6.  <span data-ttu-id="da8dc-176">Dans la fenêtre de la règle, cliquez sur **Conditions**, pointez sur **prédicats**, puis cliquez sur **égal**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-176">In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.</span></span>  
  
7.  <span data-ttu-id="da8dc-177">Dans l’Explorateur de faits, faites glisser le **customerName** élément à la **argument1** nœud sous **Conditions**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-177">From Facts Explorer, drag the **customerName** element to the **argument1** node under **Conditions**.</span></span>  
  
8.  <span data-ttu-id="da8dc-178">Cliquez sur le **argument2** nœud, puis tapez **GlobalBankWest**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-178">Click the **argument2** node, and then type **GlobalBankWest**.</span></span>  
  
9. <span data-ttu-id="da8dc-179">Dans l’Explorateur de faits, cliquez sur le **vocabulaires** onglet. Développez le **ESB. Feuille de route** vocabulaire, développez **Version 1.1**, puis faites glisser le **définir un nom de feuille de route** définition **Actions**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-179">In Facts Explorer, click the **Vocabularies** tab. Expand the **ESB.Itinerary** vocabulary, expand **Version 1.1**, and then drag the **Set Itinerary Name** definition to **Actions**.</span></span>  
  
10. <span data-ttu-id="da8dc-180">Cliquez sur  **\<une chaîne vide >** , puis tapez **GlobalBankWestItinerary**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-180">Click **\<empty string>** and then type **GlobalBankWestItinerary**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da8dc-181">Plus loin dans cette rubrique, vous allez créer cette feuille de route pour traiter les messages de GlobalBank West.</span><span class="sxs-lookup"><span data-stu-id="da8dc-181">Later in this How-to topic, you will create this itinerary to process messages from GlobalBank West.</span></span>  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-east"></a><span data-ttu-id="da8dc-182">Pour ajouter une règle de sélection pour le client est de GlobalBank</span><span class="sxs-lookup"><span data-stu-id="da8dc-182">To add a selection rule for customer GlobalBank East</span></span>  
  
1.  <span data-ttu-id="da8dc-183">Dans l’Explorateur de stratégies, cliquez sur le **SetGlobalBankWestItinerary** de règle, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-183">In Policy Explorer, right-click the **SetGlobalBankWestItinerary** rule, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="da8dc-184">Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-184">Right-click **Version 1.0 (not saved)**, and then click **Paste**.</span></span>  
  
3.  <span data-ttu-id="da8dc-185">Dans le **nom de la nouvelle règle** boîte de dialogue, tapez **SetGlobalBankEastItinerary**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-185">In the **New Rule Name** dialog box, type **SetGlobalBankEastItinerary**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="da8dc-186">Dans l’Explorateur de stratégies, cliquez sur le **SetGlobalBankEastItinerary** règle.</span><span class="sxs-lookup"><span data-stu-id="da8dc-186">In Policy Explorer, click the **SetGlobalBankEastItinerary** rule.</span></span>  
  
5.  <span data-ttu-id="da8dc-187">Dans le **Conditions** section, cliquez sur **GlobalBankWest**, puis cliquez sur **réinitialiser l’argument**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-187">In the **Conditions** section, right-click **GlobalBankWest**, and then click **Reset argument**.</span></span>  
  
6.  <span data-ttu-id="da8dc-188">Cliquez sur **argument2**, puis tapez **GlobalBankEast**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-188">Click **argument2**, and then type **GlobalBankEast**.</span></span>  
  
7.  <span data-ttu-id="da8dc-189">Dans le **Actions** section, cliquez sur **GlobalBankWestItinerary**, puis cliquez sur **réinitialiser l’argument**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-189">In the **Actions** section, right-click **GlobalBankWestItinerary**, and then click **Reset argument**.</span></span>  
  
8.  <span data-ttu-id="da8dc-190">Cliquez sur  **\<une chaîne vide >** , puis tapez **GlobalBankEastItinerary.**</span><span class="sxs-lookup"><span data-stu-id="da8dc-190">Click **\<empty string>** and then type **GlobalBankEastItinerary.**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da8dc-191">Plus loin dans cette rubrique, vous allez créer cette feuille de route pour traiter les messages à partir de GlobalBank est.</span><span class="sxs-lookup"><span data-stu-id="da8dc-191">Later in this How-to topic, you will create this itinerary to process messages from GlobalBank East.</span></span>  
  
#### <a name="to-publish-and-deploy-the-policy"></a><span data-ttu-id="da8dc-192">Pour publier et déployer la stratégie</span><span class="sxs-lookup"><span data-stu-id="da8dc-192">To publish and deploy the policy</span></span>  
  
1.  <span data-ttu-id="da8dc-193">Dans l’Explorateur de stratégies, sous la **ResolveItineraryBasedOnCustomer** stratégie, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-193">In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, click **Version 1.0 (not saved)**, and then click **Publish**.</span></span>  
  
2.  <span data-ttu-id="da8dc-194">Dans l’Explorateur de stratégies, sous la **ResolveItineraryBasedOnCustomer** stratégie, cliquez sur **Version 1.0 - publiée**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-194">In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-west-messages"></a><span data-ttu-id="da8dc-195">Pour créer un modèle DSL ESB d’itinéraire pour les messages GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="da8dc-195">To create an ESB itinerary DSL model for GlobalBank West messages</span></span>  
  
1.  <span data-ttu-id="da8dc-196">Dans  **[!INCLUDE[vs2010](../includes/vs2010-md.md)]** , ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="da8dc-196">In **[!INCLUDE[vs2010](../includes/vs2010-md.md)]**, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="da8dc-197">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-197">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="da8dc-198">Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet Modèles, cliquez sur **ItineraryDsl**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-198">In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.</span></span>  
  
4.  <span data-ttu-id="da8dc-199">Dans le **nom** , tapez **GlobalBankWestItinerary**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-199">In the **Name** box, type **GlobalBankWestItinerary**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-globalbank-west-itinerary"></a><span data-ttu-id="da8dc-200">Pour configurer les propriétés de l’itinéraire GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="da8dc-200">To configure the properties of the GlobalBank West itinerary</span></span>  
  
1.  <span data-ttu-id="da8dc-201">Dans Visual Studio, cliquez sur l’aire de conception de **GlobalBankWestItinerary.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-201">In Visual Studio, click the design surface of **GlobalBankWestItinerary.itinerary**.</span></span> <span data-ttu-id="da8dc-202">Dans le **GlobalBankWestItinerary** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-202">In the **GlobalBankWestItinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="da8dc-203">Dans le **modèle exportateur** la liste déroulante, cliquez sur **exportateur de feuille de route de base de données**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-203">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-204">Cliquez sur le bouton de sélection (...) à côté du **base de données de la feuille de route** propriété.</span><span class="sxs-lookup"><span data-stu-id="da8dc-204">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="da8dc-205">Dans le **propriétés de connexion** boîte de dialogue, choisissez le serveur SQL qui héberge la base de données de référentiel d’itinéraire, puis spécifiez le nom de la base de données (le nom par défaut est **EsbItineraryDb**).</span><span class="sxs-lookup"><span data-stu-id="da8dc-205">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="da8dc-206">Dans le **état de la feuille de route** la liste déroulante, cliquez sur **déployées**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-206">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da8dc-207">Cette étape vous permet d’exporter l’itinéraire sur un référentiel central ; itinéraires peuvent être sélectionnés et attachés à partir de ce référentiel lorsque les messages sont reçus.</span><span class="sxs-lookup"><span data-stu-id="da8dc-207">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when messages are received.</span></span> <span data-ttu-id="da8dc-208">Vous configurerez ultérieurement le composant de pipeline de sélecteur de feuille de route pour utiliser le programme de résolution BRI à évaluer les messages entrants, puis sélectionnez la feuille de route approprié à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="da8dc-208">You will later configure the Itinerary Selector pipeline component to use the BRI resolver to evaluate inbound messages and select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-globalbank-west-itinerary"></a><span data-ttu-id="da8dc-209">Pour définir la structure de la feuille de route GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="da8dc-209">To define the structure of the GlobalBank West itinerary</span></span>  
  
1.  <span data-ttu-id="da8dc-210">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="da8dc-210">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="da8dc-211">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-211">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="da8dc-212">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-212">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-213">Dans le **extendeur** la liste déroulante, cliquez sur **Extension du Service ESB rampe d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-213">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="da8dc-214">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-214">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="da8dc-215">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-215">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="da8dc-216">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **ReceiveNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="da8dc-216">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="da8dc-217">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-217">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="da8dc-218">Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-218">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-219">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-219">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="da8dc-220">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-220">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="da8dc-221">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-221">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="da8dc-222">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **ReceiveNAOrder** élément de modèle et la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="da8dc-222">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="da8dc-223">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-223">In the **ItineraryService1** properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="da8dc-224">Cliquez sur le **nom** propriété, puis tapez **RouteMessage**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-224">Click the **Name** property, and then type **RouteMessage**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-225">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe itinéraire Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-225">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="da8dc-226">Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-226">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="da8dc-227">Avec le bouton droit le **résolveur** collection de la **RouteMessage** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-227">Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="da8dc-228">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-228">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="da8dc-229">Cliquez sur le **nom** propriété, puis tapez **StaticResolver**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-229">Click the **Name** property, and then type **StaticResolver**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-230">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-230">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="da8dc-231">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-231">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="da8dc-232">Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\West%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-232">Click the **Transport Location** property, and then type **C:\HowTos\Out\West%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="da8dc-233">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-233">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="da8dc-234">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteMessage** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="da8dc-234">Drag a connection from the **ReceiveNAOrder** model element to the  **RouteMessage** model element.</span></span>  
  
6.  <span data-ttu-id="da8dc-235">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-235">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="da8dc-236">Faites glisser une connexion à partir de la **RouteMessage** élément de modèle à la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="da8dc-236">Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-globalbank-west-model-to-the-itinerary-database"></a><span data-ttu-id="da8dc-237">Pour exporter le modèle de GlobalBank West vers la base de données d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="da8dc-237">To export the GlobalBank West model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="da8dc-238">Dans Visual Studio, cliquez sur l’aire de conception de la **GlobalBankWestItinerary** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-238">In Visual Studio, right-click the design surface of the **GlobalBankWestItinerary** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da8dc-239">L’itinéraire a été exporté vers la base de données d’itinéraire et peut maintenant être utilisé par le composant de sélecteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="da8dc-239">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.</span></span>  
  
2.  <span data-ttu-id="da8dc-240">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="da8dc-240">Save all project artifacts.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-east-message"></a><span data-ttu-id="da8dc-241">Pour créer un modèle DSL ESB d’itinéraire pour le message de GlobalBank est</span><span class="sxs-lookup"><span data-stu-id="da8dc-241">To create an ESB itinerary DSL model for GlobalBank East message</span></span>  
  
1.  <span data-ttu-id="da8dc-242">Dans  **[!INCLUDE[vs2010](../includes/vs2010-md.md)]** , ouvrez C:\HowTos\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="da8dc-242">In **[!INCLUDE[vs2010](../includes/vs2010-md.md)]**, open C:\HowTos\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="da8dc-243">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-243">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="da8dc-244">Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet Modèles, cliquez sur **ItineraryDsl**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-244">In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.</span></span>  
  
4.  <span data-ttu-id="da8dc-245">Dans le **nom** , tapez **GlobalBankEastItinerary**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-245">In the **Name** box, type **GlobalBankEastItinerary**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-globalbank-east-itinerary"></a><span data-ttu-id="da8dc-246">Pour configurer les propriétés de l’itinéraire GlobalBank est</span><span class="sxs-lookup"><span data-stu-id="da8dc-246">To configure the properties of the GlobalBank East itinerary</span></span>  
  
1.  <span data-ttu-id="da8dc-247">Dans Visual Studio, cliquez sur l’aire de conception de **GlobalBankEastItinerary.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-247">In Visual Studio, click the design surface of **GlobalBankEastItinerary.itinerary**.</span></span> <span data-ttu-id="da8dc-248">Dans le **GlobalBankEastItinerary** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-248">In the **GlobalBankEastItinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="da8dc-249">Dans le **modèle exportateur** la liste déroulante, cliquez sur **exportateur de feuille de route de base de données**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-249">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-250">Cliquez sur le bouton de sélection (...) à côté du **base de données de la feuille de route** propriété.</span><span class="sxs-lookup"><span data-stu-id="da8dc-250">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="da8dc-251">Dans le **propriétés de connexion** boîte de dialogue, choisissez le serveur SQL qui héberge la base de données de référentiel d’itinéraire, puis spécifiez le nom de la base de données (le nom par défaut est **EsbItineraryDb**).</span><span class="sxs-lookup"><span data-stu-id="da8dc-251">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="da8dc-252">Dans le **état de la feuille de route** la liste déroulante, cliquez sur **déployées**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-252">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da8dc-253">Cette étape vous permet d’exporter l’itinéraire sur un référentiel central ; itinéraires peuvent être sélectionnés et attachés à partir de ce référentiel lorsque les messages sont reçus.</span><span class="sxs-lookup"><span data-stu-id="da8dc-253">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when messages are received.</span></span> <span data-ttu-id="da8dc-254">Vous configurerez ultérieurement le composant de pipeline de sélecteur de feuille de route pour utiliser le programme de résolution BRI à évaluer les messages entrants, puis sélectionnez la feuille de route approprié à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="da8dc-254">You will later configure the Itinerary Selector pipeline component to use the BRI resolver to evaluate inbound messages and select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-globalbank-east-itinerary"></a><span data-ttu-id="da8dc-255">Pour définir la structure de la feuille de route GlobalBank est</span><span class="sxs-lookup"><span data-stu-id="da8dc-255">To define the structure of the GlobalBank East itinerary</span></span>  
  
1.  <span data-ttu-id="da8dc-256">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="da8dc-256">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="da8dc-257">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-257">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="da8dc-258">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-258">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-259">Dans le **extendeur** la liste déroulante, cliquez sur **Extension du Service ESB rampe d’entrée**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-259">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="da8dc-260">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-260">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="da8dc-261">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-261">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="da8dc-262">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **ReceiveNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="da8dc-262">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="da8dc-263">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-263">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="da8dc-264">Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-264">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-265">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-265">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="da8dc-266">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-266">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="da8dc-267">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-267">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="da8dc-268">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **ReceiveNAOrder** élément de modèle et la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="da8dc-268">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="da8dc-269">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-269">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="da8dc-270">Cliquez sur le **nom** propriété, puis tapez **RouteMessage**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-270">Click the **Name** property, and then type **RouteMessage**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-271">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe itinéraire Service Extension**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-271">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="da8dc-272">Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-272">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="da8dc-273">Avec le bouton droit le **résolveur** collection de la **RouteMessage** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-273">Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="da8dc-274">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-274">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="da8dc-275">Cliquez sur le **nom** propriété, puis tapez **StaticResolver**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-275">Click the **Name** property, and then type **StaticResolver**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-276">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-276">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="da8dc-277">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-277">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="da8dc-278">Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\East%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-278">Click the **Transport Location** property, and then type **C:\HowTos\Out\East%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="da8dc-279">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-279">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="da8dc-280">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteMessage** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="da8dc-280">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessage** model element.</span></span>  
  
6.  <span data-ttu-id="da8dc-281">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-281">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="da8dc-282">Faites glisser une connexion à partir de la **RouteMessage** élément de modèle à la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="da8dc-282">Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-globalbank-east-model-to-the-itinerary-database"></a><span data-ttu-id="da8dc-283">Pour exporter le modèle GlobalBank est à la base de données d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="da8dc-283">To export the GlobalBank East model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="da8dc-284">Dans Visual Studio, cliquez sur l’aire de conception de la **GlobalBankEastItinerary** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-284">In Visual Studio, right-click the design surface of the **GlobalBankEastItinerary** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da8dc-285">L’itinéraire a été exporté vers la base de données d’itinéraire et peut maintenant être utilisé par le composant de sélecteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="da8dc-285">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.</span></span>  
  
2.  <span data-ttu-id="da8dc-286">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="da8dc-286">Save all project artifacts.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="da8dc-287">Étapes</span><span class="sxs-lookup"><span data-stu-id="da8dc-287">Steps</span></span>  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a><span data-ttu-id="da8dc-288">Pour créer et configurer un ESB rampe d’entrée</span><span class="sxs-lookup"><span data-stu-id="da8dc-288">To create and configure an ESB on-ramp</span></span>  
  
1.  <span data-ttu-id="da8dc-289">Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[prague](../includes/prague-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-289">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="da8dc-290">Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, développez **groupe BizTalk**, développez **Applications**, puis développez **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-290">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand **Microsoft.Practices.ESB**.</span></span>  
  
3.  <span data-ttu-id="da8dc-291">Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-291">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
4.  <span data-ttu-id="da8dc-292">Dans le **sélectionner un Port de réception** boîte de dialogue, cliquez sur **OnRamp.Itinerary**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-292">In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="da8dc-293">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez **OnRamp.Itinerary.HowTo**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-293">In the **Receive Location Properties** dialog box, in the **Name** box, type **OnRamp.Itinerary.HowTo**.</span></span>  
  
6.  <span data-ttu-id="da8dc-294">Dans le **Type** la liste déroulante, cliquez sur **fichier** puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-294">In the **Type** drop-down list, click **FILE,** and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="da8dc-295">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de réception** , tapez **C:\HowTos\DropFolder**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-295">In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type **C:\HowTos\DropFolder**, and then click **OK**.</span></span>  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a><span data-ttu-id="da8dc-296">Pour configurer le composant de pipeline du sélecteur de feuille de route</span><span class="sxs-lookup"><span data-stu-id="da8dc-296">To configure the Itinerary Selector pipeline component</span></span>  
  
1.  <span data-ttu-id="da8dc-297">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **ItinerarySelectReceiveXml** dans les **pipeline de réception** déroulante liste, puis cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="da8dc-297">In the **Receive Location Properties** dialog box, click **ItinerarySelectReceiveXml** in the **Receive pipeline** drop-down list, and then click the ellipsis button (...).</span></span>  
  
2.  <span data-ttu-id="da8dc-298">Utilisez le **configurer le Pipeline** boîte de dialogue pour configurer les éléments suivants **itinéraire sélecteur** les propriétés du composant :</span><span class="sxs-lookup"><span data-stu-id="da8dc-298">Use the **Configure Pipeline** dialog box to configure the following **Itinerary Selector** component properties:</span></span>  
  
    1.  <span data-ttu-id="da8dc-299">Cliquez sur le **ItineraryFactKey** propriété, puis tapez **Resolver.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-299">Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.</span></span>  
  
    2.  <span data-ttu-id="da8dc-300">Cliquez sur le **ResolverConnectionString** propriété, puis tapez **BRI :\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true ;**</span><span class="sxs-lookup"><span data-stu-id="da8dc-300">Click the **ResolverConnectionString** property, and then type **BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**</span></span>  
  
    3.  <span data-ttu-id="da8dc-301">Cliquez sur **OK** pour fermer la **configurer le Pipeline** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="da8dc-301">Click **OK** to close the **Configure Pipeline** dialog box.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="da8dc-302">Étant donné que cet réception emplacement est désassemblage d’un échange XML, aucune configuration de composant désassembleur XML est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="da8dc-302">Because this receive location is disassembling an XML interchange, no XML Disassembler component configuration is required.</span></span>  
  
3.  <span data-ttu-id="da8dc-303">Cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="da8dc-303">Click **OK** to close the **Receive Location Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="da8dc-304">Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, avec le bouton droit le **OnRamp.Itinerary.HowTo** emplacement de réception, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-304">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Enable**.</span></span>  
  
#### <a name="to-test-the-itinerary-selector-and-business-rules"></a><span data-ttu-id="da8dc-305">Pour tester le sélecteur d’itinéraire et les règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="da8dc-305">To test the Itinerary Selector and business rules</span></span>  
  
1.  <span data-ttu-id="da8dc-306">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="da8dc-306">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="da8dc-307">Copie (ne déplacez pas) Batch.xml dans le dossier Dossier_dépôt.</span><span class="sxs-lookup"><span data-stu-id="da8dc-307">Copy (do not move) Batch.xml to the DropFolder folder.</span></span>  
  
3.  <span data-ttu-id="da8dc-308">Accédez à C:\HowTos\Out. Vérifiez qu’un seul message West%MessageID%.xml et deux messages East%MessageID%.xml ont été écrits dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="da8dc-308">Browse to C:\HowTos\Out. Verify that one West%MessageID%.xml message and two East%MessageID%.xml messages have been written to the directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da8dc-309">Bien que les messages sont identiques à l’exception de la valeur de l’élément client, ils ont été traités à l’aide d’itinéraires différents, selon la résolution du composant de pipeline sélecteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="da8dc-309">Although the messages are identical except for the value of the customer element, they were processed using different itineraries, based on the resolution of the Itinerary Selector pipeline component.</span></span>  
  
4.  <span data-ttu-id="da8dc-310">Dans la [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, avec le bouton droit le OnRamp.Itinerary.HowTo emplacement de réception, puis cliquez sur Désactiver.</span><span class="sxs-lookup"><span data-stu-id="da8dc-310">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, right-click the OnRamp.Itinerary.HowTo receive location, and then click Disable.</span></span>  
  
5.  <span data-ttu-id="da8dc-311">Après le **OnRamp.Itinerary.HowTo** recevoir d’emplacement est désactivée, faites un clic droit, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-311">After the **OnRamp.Itinerary.HowTo** receive location is disabled, right-click it, and then click **Delete**.</span></span> <span data-ttu-id="da8dc-312">Dans le **emplacement de réception de confirmer la suppression** boîte de dialogue, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="da8dc-312">In the **Confirm delete receive location** dialog box, click **Yes**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="da8dc-313">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="da8dc-313">Additional Resources</span></span>  
 <span data-ttu-id="da8dc-314">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="da8dc-314">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="da8dc-315">Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="da8dc-315">How to: Select an Itinerary Using a Business Rules Policy</span></span>](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [<span data-ttu-id="da8dc-316">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="da8dc-316">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="da8dc-317">Installer et exécuter l’exemple de résolution dynamique</span><span class="sxs-lookup"><span data-stu-id="da8dc-317">Installing and Running the Dynamic Resolution Sample</span></span>](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [<span data-ttu-id="da8dc-318">À l’aide de la résolution dynamique et le routage</span><span class="sxs-lookup"><span data-stu-id="da8dc-318">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [<span data-ttu-id="da8dc-319">Modèles de routage de messages</span><span class="sxs-lookup"><span data-stu-id="da8dc-319">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)