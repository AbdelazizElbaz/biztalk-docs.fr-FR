---
title: "Étape 3 : Création d’une Application métier Contoso est mappé pour le prix et la disponibilité du projet à l’aide du mappeur de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, creating LOB maps
ms.assetid: a947e0ac-f0cb-4be9-85a8-09daf3675b1a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3478997abd4e5bb15bfeb977e05ca3edc7348e0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-creating-the-contoso-lob-application-maps-for-the-price-and-availability-project-using-biztalk-mapper"></a><span data-ttu-id="80648-102">Étape 3 : Créer les mappages d’applications métier Contoso pour le prix et le projet de disponibilité à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="80648-102">Step 3: Creating the Contoso LOB Application Maps for the Price and Availability Project Using BizTalk Mapper</span></span>
<span data-ttu-id="80648-103">Dans cette étape, vous créez deux mappages qui définissent la transformation nécessaire pour échanger les messages entre les deux partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="80648-103">In this step, you create two maps that define the transformation required to successfully exchange messages between the two trading partners.</span></span> <span data-ttu-id="80648-104">Pour ce scénario, le système ERP de Contoso a déjà standardisé en un format de message pour une demande de prix et de disponibilité.</span><span class="sxs-lookup"><span data-stu-id="80648-104">For this scenario, the Contoso ERP system has already standardized on a message format for a Price and Availability request.</span></span> <span data-ttu-id="80648-105">Les deux cartes mappera les messages de demande et de réponse du partenaire commercial, Fabrikam, vers et depuis ces messages définies par l’utilisateur de Contoso, respectivement.</span><span class="sxs-lookup"><span data-stu-id="80648-105">The two maps will map the request and response messages from the trading partner, Fabrikam, to and from those internally defined Contoso messages, respectively.</span></span>  
  
### <a name="to-add-a-reference-for-the-3a2-priceandavailability-request-schema"></a><span data-ttu-id="80648-106">Pour ajouter une référence pour le schéma de demande de PriceAndAvailability 3A2</span><span class="sxs-lookup"><span data-stu-id="80648-106">To add a reference for the 3A2 PriceAndAvailability Request schema</span></span>  
  
1.  <span data-ttu-id="80648-107">Dans l’Explorateur de solutions, cliquez sur le projet ContosoPriceAndAvailability, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="80648-107">In Solution Explorer, right-click the ContosoPriceAndAvailability project, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="80648-108">Dans la boîte de dialogue Ajouter une référence, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="80648-108">In the Add Reference dialog box, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="80648-109">Déplacer vers le dossier  *\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\Bin, puis sélectionnez le **Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll**  assembly.</span><span class="sxs-lookup"><span data-stu-id="80648-109">Move to the folder *\<drive>*:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\Bin, and then select the **Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll** assembly.</span></span>  
  
4.  <span data-ttu-id="80648-110">Cliquez sur **ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="80648-110">Click **Add**, and then click **OK**.</span></span>  
  
### <a name="to-create-the-3a2-priceandavailability-request-to-contoso-priceandavailability-request-map"></a><span data-ttu-id="80648-111">Pour créer la demande de PriceAndAvailability 3A2 au mappage de demande de Contoso PriceAndAvailability</span><span class="sxs-lookup"><span data-stu-id="80648-111">To create the 3A2 PriceAndAvailability request to Contoso PriceAndAvailability request map</span></span>  
  
1.  <span data-ttu-id="80648-112">Dans l’Explorateur de solutions, cliquez sur le projet ContosoPriceAndAvailability, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="80648-112">In Solution Explorer, right-click the ContosoPriceAndAvailability project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="80648-113">Dans l’ajouter un nouvel élément - ContosoPriceAndAvailability boîte de dialogue, sélectionnez **les fichiers de mappage** dans le volet des catégories, puis sélectionnez **carte** dans les **modèles** volet.</span><span class="sxs-lookup"><span data-stu-id="80648-113">In the Add New Item - ContosoPriceAndAvailability dialog box, select **Map Files** in the Categories pane, and then select **Map** in the **Templates** pane.</span></span> <span data-ttu-id="80648-114">Dans le **nom** , tapez **PIP3A2RequestToContosoPriceRequest**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="80648-114">In the **Name** box, type **PIP3A2RequestToContosoPriceRequest**, and then click **Add**.</span></span>  
  
### <a name="to-associate-the-schemas-for-the-pip3a2requesttocontosopricerequest-map"></a><span data-ttu-id="80648-115">Pour associer les schémas de la carte PIP3A2RequestToContosoPriceRequest</span><span class="sxs-lookup"><span data-stu-id="80648-115">To associate the schemas for the PIP3A2RequestToContosoPriceRequest map</span></span>  
  
1.  <span data-ttu-id="80648-116">Dans le Mappeur BizTalk (avec PIP3A2RequestToContosoPriceRequest.btm affiché), dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.</span><span class="sxs-lookup"><span data-stu-id="80648-116">In BizTalk Mapper (with PIP3A2RequestToContosoPriceRequest.btm displayed), in the Source Schema pane, click **Open Source Schema**.</span></span>  
  
2.  <span data-ttu-id="80648-117">Dans la boîte de dialogue Sélecteur de Type BizTalk, développez **ContosoPriceAndAvailability**, développez **références**, développez **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, puis Développez **schémas.**</span><span class="sxs-lookup"><span data-stu-id="80648-117">In the BizTalk Type Picker dialog box, expand **ContosoPriceAndAvailability**, expand **References**, expand **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, and then expand **Schemas.**</span></span>  
  
3.  <span data-ttu-id="80648-118">Sélectionnez **Microsoft.Solutions.BTARN.Schemas.RNPIPs.**</span><span class="sxs-lookup"><span data-stu-id="80648-118">Select **Microsoft.Solutions.BTARN.Schemas.RNPIPs.**</span></span>  
  
     <span data-ttu-id="80648-119">**_3A2PriceAndAvailabilityQueryMessageGuideline_v1_3**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="80648-119">**_3A2PriceAndAvailabilityQueryMessageGuideline_v1_3**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="80648-120">Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.</span><span class="sxs-lookup"><span data-stu-id="80648-120">In the Destination Schema pane, click **Open Destination Schema**.</span></span>  
  
5.  <span data-ttu-id="80648-121">Dans la boîte de dialogue Sélecteur de Type BizTalk, développez **ContosoPriceAndAvailability**, puis développez **schémas**.</span><span class="sxs-lookup"><span data-stu-id="80648-121">In the BizTalk Type Picker dialog box, expand **ContosoPriceAndAvailability**, and then expand **Schemas**.</span></span>  
  
6.  <span data-ttu-id="80648-122">Sélectionnez le **ContosoPriceAndAvailability.ContosoPriceSchema** schéma, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="80648-122">Select the **ContosoPriceAndAvailability.ContosoPriceSchema** schema, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="80648-123">Dans le nœud racine de la boîte de dialogue de schéma cible, sélectionnez le **rootPriceRequest** schéma, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="80648-123">In the Root Node for Target Schema dialog box, select the **rootPriceRequest** schema, and then click **OK**.</span></span>  
  
### <a name="to-link-schema-fields-in-the-pip3a2requesttocontosopricerequest-map"></a><span data-ttu-id="80648-124">Pour lier des champs de schéma dans le mappage de PIP3A2RequestToContosoPriceRequest</span><span class="sxs-lookup"><span data-stu-id="80648-124">To link schema fields in the PIP3A2RequestToContosoPriceRequest map</span></span>  
  
1.  <span data-ttu-id="80648-125">Dans le volet Schéma de Destination, cliquez sur le  **\<schéma >** nœud, puis cliquez sur **développer le nœud d’arborescence**.</span><span class="sxs-lookup"><span data-stu-id="80648-125">In the Destination Schema pane, right-click the **\<Schema>** node, and then click **Expand Tree Node**.</span></span>  
  
2.  <span data-ttu-id="80648-126">Dans le volet Schéma Source, cliquez sur le  **\<schéma >** nœud, puis cliquez sur **développer le nœud d’arborescence**.</span><span class="sxs-lookup"><span data-stu-id="80648-126">In the Source Schema pane, right-click the **\<Schema>** node, and then click **Expand Tree Node**.</span></span>  
  
3.  <span data-ttu-id="80648-127">Faites glisser le **GlobalProductIdentifier** au champ la **ProductID** champ dans le volet Schéma de Destination.</span><span class="sxs-lookup"><span data-stu-id="80648-127">Drag the **GlobalProductIdentifier** field to the **ProductID** field in the Destination Schema pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="80648-128">Vous pouvez trouver la **GlobalProductIdentifier** champ dans le nœud Pip3A2PriceAndAvailabilityQuery/ProductPriceAndAvailabilityQuery /</span><span class="sxs-lookup"><span data-stu-id="80648-128">You can find the **GlobalProductIdentifier** field in the node Pip3A2PriceAndAvailabilityQuery/ProductPriceAndAvailabilityQuery/</span></span>  
    >   
    >  <span data-ttu-id="80648-129">ProductPriceAndAvailability/ProductLineItem/productUnit /</span><span class="sxs-lookup"><span data-stu-id="80648-129">ProductPriceAndAvailability/ProductLineItem/productUnit/</span></span>  
    >   
    >  <span data-ttu-id="80648-130">ProductPackageDescription/ProductIdentification.</span><span class="sxs-lookup"><span data-stu-id="80648-130">ProductPackageDescription/ProductIdentification.</span></span>  
  
4.  <span data-ttu-id="80648-131">Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="80648-131">On the **File** menu, click **Save All** to save your changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80648-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80648-132">See Also</span></span>  
 [<span data-ttu-id="80648-133">Création et configuration des Ports BizTalk pour Contoso</span><span class="sxs-lookup"><span data-stu-id="80648-133">Creating and Configuring BizTalk Ports for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-biztalk-ports-for-contoso.md)