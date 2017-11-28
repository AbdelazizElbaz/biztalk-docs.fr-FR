---
title: "Étape 2 : Définition et publication du vocabulaire pour Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vocabularies, creating
- vocabularies, publishing
- private process tutorial, creating vocabularies
ms.assetid: e23880c0-772c-48c6-a6b5-32eb951527c8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15937a1235cc1776be38fe2b0e5529c19d3f6fd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-defining-and-publishing-the-vocabulary-for-contoso"></a><span data-ttu-id="1de3f-102">Étape 2 : Définition et publication du vocabulaire pour Contoso</span><span class="sxs-lookup"><span data-stu-id="1de3f-102">Step 2: Defining and Publishing the Vocabulary for Contoso</span></span>
<span data-ttu-id="1de3f-103">Dans ce scénario, Contoso implémente une stratégie commerciale qui permet de s'assurer que le stock est toujours disponible en cas d'urgence.</span><span class="sxs-lookup"><span data-stu-id="1de3f-103">In this scenario, Contoso implements a business policy that makes sure that inventory is always on hand if an emergency occurs.</span></span> <span data-ttu-id="1de3f-104">Vous créez des stratégies d’entreprise à l’aide de l’éditeur des règles d’entreprise dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1de3f-104">You create business policies using the Business Rule Composer in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="1de3f-105">Dans cette étape, vous créez le vocabulaire à utiliser quand vous définissez la stratégie commerciale.</span><span class="sxs-lookup"><span data-stu-id="1de3f-105">In this step, you create the vocabulary to use when you define the business policy.</span></span>  
  
### <a name="to-add-a-new-vocabulary"></a><span data-ttu-id="1de3f-106">Pour ajouter un nouveau vocabulaire</span><span class="sxs-lookup"><span data-stu-id="1de3f-106">To add a new vocabulary</span></span>  
  
1.  <span data-ttu-id="1de3f-107">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-107">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="1de3f-108">Dans la boîte de dialogue Ouvrir le magasin de règles, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-108">In the Open Rule Store dialog box, click **OK**.</span></span>  
  
3.  <span data-ttu-id="1de3f-109">Dans le volet Explorateur de faits, sous l'onglet **Vocabulaires** , cliquez avec le bouton droit sur **Vocabulaires**, puis cliquez sur **Ajouter un nouveau vocabulaire**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-109">In the Facts Explorer pane, on the **Vocabularies** tab, right-click **Vocabularies**, and then click **Add New Vocabulary**.</span></span>  
  
4.  <span data-ttu-id="1de3f-110">Nommez le vocabulaire **3A2PriceAvailabilityVocabulary**, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-110">Name the vocabulary **3A2PriceAvailabilityVocabulary**, and then press **Enter**.</span></span>  
  
### <a name="to-define-a-constant-vocabulary-value"></a><span data-ttu-id="1de3f-111">Pour définir une valeur constante de vocabulaire</span><span class="sxs-lookup"><span data-stu-id="1de3f-111">To define a constant vocabulary value</span></span>  
  
1.  <span data-ttu-id="1de3f-112">Dans l'Éditeur des règles d'entreprise, cliquez sur **3A2PriceAvailabilityVocabulary**, cliquez avec le bouton droit sur **Version 1.0 (non enregistrée)**, puis cliquez sur **Ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-112">In Business Rule Composer, click **3A2PriceAvailabilityVocabulary**, right-click **Version 1.0(not saved)**, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="1de3f-113">Dans la page **Assistant Définition de vocabulaire** , sélectionnez **Valeur constante, plage de valeurs ou ensemble de valeurs**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-113">On the **Vocabulary Definition Wizard** page, select **Constant Value, Range of Values, or Set of Values**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="1de3f-114">Dans la page **Valeur constante, plage de valeurs ou ensemble de valeurs** , dans la zone **Nom de la définition** , tapez **Quantité d'urgence nécessaire**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-114">On the **Constant Value, Range of Values, or Set of Values** page, in the **Definition name** box, type **Emergency Quantity Needed**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="1de3f-115">Dans la page **Définir une valeur constante** , dans la zone **Valeur** , tapez **800**, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-115">On the **Define a Constant Value** page, in the **Value** box, type **800**, and then click **Finish**.</span></span>  
  
### <a name="to-define-an-xml-document-get-element"></a><span data-ttu-id="1de3f-116">Pour définir l'élément 'Get' d'un document XML</span><span class="sxs-lookup"><span data-stu-id="1de3f-116">To define an XML document 'Get' element</span></span>  
  
1.  <span data-ttu-id="1de3f-117">Dans l'Éditeur des règles d'entreprise, dans le volet Explorateur de faits, cliquez avec le bouton droit sur **Version 1.0 (non enregistrée)** sous **3A2PriceAvailabilityVocabulary**, puis cliquez sur **Ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-117">In Business Rule Composer, in the Facts Explorer pane, right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityVocabulary**, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="1de3f-118">Sur le **VocabularyDefinition Assistant** page, sélectionnez **Document élément ou attribut XML**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-118">On the **VocabularyDefinition Wizard** page, select **XML Document Element or Attribute**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="1de3f-119">Dans la page **Élément ou attribut de document XML** , dans la zone **Nom de la définition** , tapez **Quantité disponible**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-119">On the **XML Document Element or Attribute** page, in the **Definition Name** box, type **Quantity Available**.</span></span>  
  
4.  <span data-ttu-id="1de3f-120">Cliquez sur **Parcourir** (en regard du champ **Schema** ), accédez au projet **ContosoPriceAndAvailability** dans votre dossier de solutions, sélectionnez le schéma **ContosoPriceAndAvailability.xsd** , puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-120">Click **Browse** (next to the **Schema** field), move to the **ContosoPriceAndAvailability** project in your solution folder, select the **ContosoPriceAndAvailability.xsd** schema, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="1de3f-121">Dans la boîte de dialogue Sélectionner une liaison, développez **rootPriceResponse**, développez **Products**, sélectionnez l'élément **NumberAvailable** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-121">In the Select Binding dialog box, expand **rootPriceResponse**, expand **Products**, select the **NumberAvailable** element, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="1de3f-122">Dans la page **Élément ou attribut de document XML** , dans la zone **Type de document** , assurez-vous que la valeur est **ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-122">On the **XML Document Element or Attribute** page, in the **Document Type** box, ensure that the value is **ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.</span></span>  
  
7.  <span data-ttu-id="1de3f-123">Dans la section **Sélectionner une opération** , sélectionnez **Effectuer une opération "Get"**, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-123">In the **Select operation** section, select **Perform "Get" Operation**, and then click **Finish**.</span></span>  
  
### <a name="to-define-an-xml-document-set-element"></a><span data-ttu-id="1de3f-124">Pour définir l'élément 'Set' d'un document XML</span><span class="sxs-lookup"><span data-stu-id="1de3f-124">To define an XML document 'Set' element</span></span>  
  
1.  <span data-ttu-id="1de3f-125">Dans l'Éditeur des règles d'entreprise, dans le volet Explorateur de faits, cliquez avec le bouton droit sur **Version 1.0 (non enregistrée)** sous **3A2PriceAvailabilityVocabulary**, puis cliquez sur **Ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-125">In Business Rule Composer, in the Facts Explorer pane, right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityVocabulary**, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="1de3f-126">Sur le **VocabularyDefinition Assistant** page, sélectionnez **Document élément ou attribut XML**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-126">On the **VocabularyDefinition Wizard** page, select **XML Document Element or Attribute**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="1de3f-127">Dans la page **Élément ou attribut de document XML** , dans la zone **Nom de la définition** , tapez **Quantité disponible finale**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-127">On the **XML Document Element or Attribute** page, in the **Definition Name** box, type **Final Quantity Available**.</span></span>  
  
4.  <span data-ttu-id="1de3f-128">Cliquez sur **Parcourir** (en regard du champ **Schema** ), accédez au projet **ContosoPriceAndAvailability** dans votre dossier de solutions, sélectionnez le schéma **ContosoPriceAndAvailability.xsd** , puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-128">Click **Browse** (next to the **Schema** field), move to the **ContosoPriceAndAvailability** project in your solution folder, select the **ContosoPriceAndAvailability.xsd** schema, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="1de3f-129">Dans le **sélectionnez une liaison** boîte de dialogue, développez **rootPriceResponse**, développez **produits**, puis sélectionnez le **NumberAvailable** élément.</span><span class="sxs-lookup"><span data-stu-id="1de3f-129">In the **Select Binding** dialog box, expand **rootPriceResponse**, expand **Products**, and then select the **NumberAvailable** element.</span></span> <span data-ttu-id="1de3f-130">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-130">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="1de3f-131">Dans la page **Élément ou attribut de document XML** , dans la zone **Type de document** , assurez-vous que la valeur est **ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-131">On the **XML Document Element or Attribute** page, in the **Document Type** box, ensure that the value is **ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.</span></span>  
  
7.  <span data-ttu-id="1de3f-132">Dans la section **Sélectionner une opération** , sélectionnez **Effectuer une opération "Set"**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-132">In the **Select operation** section, select **Perform "Set" Operation**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="1de3f-133">Dans la page **Indiquez le nom complet** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-133">In the **Specify the Display Name** page, click **Finish**.</span></span>  
  
### <a name="to-save-and-publish-the-vocabulary"></a><span data-ttu-id="1de3f-134">Pour enregistrer et publier le vocabulaire</span><span class="sxs-lookup"><span data-stu-id="1de3f-134">To save and publish the vocabulary</span></span>  
  
1.  <span data-ttu-id="1de3f-135">Dans l'Éditeur des règles d'entreprise, dans le volet Explorateur de faits, cliquez avec le bouton droit sur **Version 1.0 (non enregistrée)** sous **3A2PriceAvailabilityVocabulary**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-135">In Business Rule Composer, in the Facts Explorer pane, right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityVocabulary**, and then click **Save**.</span></span>  
  
2.  <span data-ttu-id="1de3f-136">Cliquez avec le bouton droit sur le même nœud **Version 1.0** , puis cliquez sur **Publier**.</span><span class="sxs-lookup"><span data-stu-id="1de3f-136">Right-click that same **Version 1.0** node and then click **Publish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1de3f-137">Laissez l'Éditeur des règles d'entreprise ouvert pour l'étape suivante du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="1de3f-137">Leave the Business Rule Composer open for the next step in the tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1de3f-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1de3f-138">See Also</span></span>  
 [<span data-ttu-id="1de3f-139">Étape 3 : Définition, la publication et le déploiement de la stratégie d’entreprise pour Contoso</span><span class="sxs-lookup"><span data-stu-id="1de3f-139">Step 3: Defining, Publishing, and Deploying the Business Policy for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-defining-publishing-and-deploying-the-business-policy-for-contoso.md)