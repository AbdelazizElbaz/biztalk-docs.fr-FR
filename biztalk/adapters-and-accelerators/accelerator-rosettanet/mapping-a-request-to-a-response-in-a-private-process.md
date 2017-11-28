---
title: "Mappage d’une demande à une réponse dans un processus privé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, maps
- private processes, mapping requests
- private processes, customizing
- orchestrations, adding maps
- maps, adding to orchestrations
- maps, creating
- customizing private processes
- requests, mapping
- requests, private processes
ms.assetid: 5452c0a2-3a9b-43e7-bfa7-713eef0eab3b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6bd67be0bbe70794f6fe6f77d388b69660e2d1ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mapping-a-request-to-a-response-in-a-private-process"></a><span data-ttu-id="50e54-102">Mappage d’une demande à une réponse dans un processus privé</span><span class="sxs-lookup"><span data-stu-id="50e54-102">Mapping a Request to a Response in a Private Process</span></span>
<span data-ttu-id="50e54-103">Cette rubrique décrit comment mapper un message de demande reçu par le processus de répondeur, à partir de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] processus répondeur public, un message de réponse qui peut être envoyé à la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processus de répondeur public.</span><span class="sxs-lookup"><span data-stu-id="50e54-103">This topic describes how to map a request message received by the private responder process—from the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] public responder process, to a response message that can be sent to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] public responder process.</span></span>  
  
 <span data-ttu-id="50e54-104">Lorsqu’un répondeur reçoit un message de demande, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] achemine le message de demande à partir de l’orchestration de processus publics, à l’orchestration de processus privé, le programme de métier (LOB).</span><span class="sxs-lookup"><span data-stu-id="50e54-104">When a responder receives a request message, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] routes the request message from the public-process orchestration, to the private-process orchestration, to the line-of-business (LOB) program.</span></span> <span data-ttu-id="50e54-105">Le répondeur nécessite le contenu du service de réponse à partir du programme métier pour générer un message de réponse RosettaNet à l’initiateur.</span><span class="sxs-lookup"><span data-stu-id="50e54-105">The responder requires the response service content from the LOB program to generate a RosettaNet response message back to the initiator.</span></span> <span data-ttu-id="50e54-106">De nombreux éléments dans le message de réponse sont remplies en utilisant les valeurs du message de demande.</span><span class="sxs-lookup"><span data-stu-id="50e54-106">Many of the elements in the response message are populated using the values from the request message.</span></span> <span data-ttu-id="50e54-107">Par conséquent, vous pouvez incorporer un mappage dans l’orchestration de processus privé répondeur générer le message de contenu du service de réponse dans le format requis pour le programme LOB.</span><span class="sxs-lookup"><span data-stu-id="50e54-107">As a result, you can incorporate a map in the responder private-process orchestration to help the LOB program generate the response service-content message in the required format.</span></span>  
  
 <span data-ttu-id="50e54-108">Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK contient les exemples suivants que vous pouvez utiliser lorsque vous ajoutez un mappage à un répondeur privé-processus :</span><span class="sxs-lookup"><span data-stu-id="50e54-108">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK contains the following samples that you can use when you add a map to a responder private-process:</span></span>  
  
-   [<span data-ttu-id="50e54-109">Demande de 3A2 d’exemple de mappage de réponse 3A2</span><span class="sxs-lookup"><span data-stu-id="50e54-109">3A2 Request to 3A2 Response Map Sample</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)  
  
-   [<span data-ttu-id="50e54-110">Demande de 3 a 4 pour un exemple de mappage de réponse 3 a 4</span><span class="sxs-lookup"><span data-stu-id="50e54-110">3A4 Request to 3A4 Response Map Sample</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md)  
  
-   [<span data-ttu-id="50e54-111">Orchestration Action PIPAutomation double</span><span class="sxs-lookup"><span data-stu-id="50e54-111">Double Action PIPAutomation Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)  
  
-   [<span data-ttu-id="50e54-112">Orchestration de répondeur de 3 a 4 à l’aide d’une règle d’entreprise</span><span class="sxs-lookup"><span data-stu-id="50e54-112">3A4 Private Responder Orchestration Using a Business Rule</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)  
  
### <a name="to-create-the-map"></a><span data-ttu-id="50e54-113">Pour créer le mappage</span><span class="sxs-lookup"><span data-stu-id="50e54-113">To create the map</span></span>  
  
1.  <span data-ttu-id="50e54-114">Démarrez **Microsoft Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="50e54-114">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="50e54-115">Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="50e54-115">On the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="50e54-116">Recherchez le dossier qui contient le projet BizTalk qui contient l’orchestration de processus privé auquel vous souhaitez ajouter la carte.</span><span class="sxs-lookup"><span data-stu-id="50e54-116">Locate the folder that contains the BizTalk project that contains the private-process orchestration to which you want to add the map.</span></span>  
  
4.  <span data-ttu-id="50e54-117">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet, pointez sur **Ajouter**, puis cliquez sur **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="50e54-117">In Solution Explorer, right-click the project, point to **Add**, and then click **New Item**.</span></span>  
  
5.  <span data-ttu-id="50e54-118">Dans la fenêtre Ajouter un nouvel élément, dans le **catégories** volet, cliquez sur **les fichiers de mappage**.</span><span class="sxs-lookup"><span data-stu-id="50e54-118">In the Add New Item window, in the **Categories** pane, click **Map Files**.</span></span> <span data-ttu-id="50e54-119">Dans le volet Modèles, cliquez sur **carte**.</span><span class="sxs-lookup"><span data-stu-id="50e54-119">In the Templates pane, click **Map**.</span></span> <span data-ttu-id="50e54-120">Dans le **nom** zone, tapez un nom pour la carte, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="50e54-120">In the **Name** box, type a name for the map, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="50e54-121">Dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.</span><span class="sxs-lookup"><span data-stu-id="50e54-121">In the Source Schema pane, click **Open Source Schema**.</span></span>  
  
7.  <span data-ttu-id="50e54-122">Dans la fenêtre de sélecteur de Type BizTalk, développez **schémas**, sélectionnez le schéma PIP pour le message de demande que vous souhaitez mapper à partir de, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50e54-122">In the BizTalk Type Picker window, expand **Schemas**, select the PIP schema for the request message that you want to map from, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="50e54-123">Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.</span><span class="sxs-lookup"><span data-stu-id="50e54-123">In the Destination Schema pane, click **Open Destination Schema**.</span></span>  
  
9. <span data-ttu-id="50e54-124">Dans la fenêtre de sélecteur de Type BizTalk, développez **références**, développez **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, développez **schémas**, sélectionnez le schéma PIP pour le message de réponse auquel vous souhaitez mapper, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50e54-124">In the BizTalk Type Picker window, expand **References**, expand **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, expand **Schemas**, select the PIP schema for the response message to which you want to map, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="50e54-125">Cliquez sur le \< *schéma*> nœud de schéma source, puis cliquez sur **développer le nœud d’arborescence**.</span><span class="sxs-lookup"><span data-stu-id="50e54-125">Right-click the \<*Schema*> node of the source schema, and then click **Expand Tree Node**.</span></span>  
  
11. <span data-ttu-id="50e54-126">Répétez l’étape 10 pour le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="50e54-126">Repeat step 10 for the destination schema.</span></span>  
  
12. <span data-ttu-id="50e54-127">Dans le volet Schéma Source, cliquez et maintenez sur un champ que vous souhaitez mapper à un champ du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="50e54-127">In the Source Schema pane, click and hold on a field that you want to map to a field in the destination schema.</span></span> <span data-ttu-id="50e54-128">Faites glisser vers le nœud correspondant dans le volet Schéma de Destination.</span><span class="sxs-lookup"><span data-stu-id="50e54-128">Drag to the corresponding node in the Destination Schema pane.</span></span>  
  
13. <span data-ttu-id="50e54-129">Répétez l’étape 12 pour tous les champs que vous devez effectuer un mappage entre les deux schémas.</span><span class="sxs-lookup"><span data-stu-id="50e54-129">Repeat step 12 for all fields that you have to map between the two schemas.</span></span>  
  
14. <span data-ttu-id="50e54-130">Validez et testez le mappage.</span><span class="sxs-lookup"><span data-stu-id="50e54-130">Validate and test the map.</span></span> <span data-ttu-id="50e54-131">Pour plus d’informations, consultez la rubrique « Compilation et test des cartes » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="50e54-131">For more information, see the "Compiling and Testing Maps" topic in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
### <a name="to-add-the-map-to-the-orchestration"></a><span data-ttu-id="50e54-132">Pour ajouter le mappage à l’orchestration</span><span class="sxs-lookup"><span data-stu-id="50e54-132">To add the map to the orchestration</span></span>  
  
1.  <span data-ttu-id="50e54-133">Dans l’Explorateur de solutions, double-cliquez sur l’orchestration de processus privé.</span><span class="sxs-lookup"><span data-stu-id="50e54-133">In Solution Explorer, double-click the private-process orchestration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50e54-134">Assurez-vous que l’orchestration comporte des références aux assemblys qui contiennent les schémas.</span><span class="sxs-lookup"><span data-stu-id="50e54-134">Make sure that the orchestration has references to the assemblies that contain the schemas.</span></span>  
  
2.  <span data-ttu-id="50e54-135">Dans la boîte à outils, cliquez sur le **transformer** mettre en forme et faites-le glisser vers le point dans l’orchestration à laquelle vous devez transformer le message de demande dans le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="50e54-135">In the Toolbox, click the **Transform** shape, and drag it to the point in the orchestration at which you have to transform the request message into the response message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50e54-136">Pour obtenir un exemple de l’emplacement de la **transformer** mettre en forme, consultez l’orchestration PIP3A4PrivateResponder.odx.</span><span class="sxs-lookup"><span data-stu-id="50e54-136">For an example of the placement of the **Transform** shape, see the PIP3A4PrivateResponder.odx orchestration.</span></span> <span data-ttu-id="50e54-137">Il se trouve dans \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR.</span><span class="sxs-lookup"><span data-stu-id="50e54-137">It is located in \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR.</span></span> <span data-ttu-id="50e54-138">Cet exemple place le **transformer** sous la forme immédiatement la **IsActivityDoubleAction** forme.</span><span class="sxs-lookup"><span data-stu-id="50e54-138">This sample puts the **Transform** shape immediately under the **IsActivityDoubleAction** shape.</span></span> <span data-ttu-id="50e54-139">Pour plus d’informations, consultez [3 a 4 privé répondeur Orchestration à l’aide une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).</span><span class="sxs-lookup"><span data-stu-id="50e54-139">For more information, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50e54-140">Pour obtenir un exemple de comment vous pouvez incorporer plusieurs mappages pour plusieurs adresses PIP, consultez [Orchestration Double Action PIPAutomation](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="50e54-140">For an example of how you can incorporate multiple maps for multiple PIPs, see [Double Action PIPAutomation Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md).</span></span>  
  
3.  <span data-ttu-id="50e54-141">Dans l’aire de conception d’orchestration, cliquez sur **ConstructMessage1**.</span><span class="sxs-lookup"><span data-stu-id="50e54-141">On the orchestration design surface, click **ConstructMessage1**.</span></span> <span data-ttu-id="50e54-142">Dans la fenêtre Propriétés, tapez un nom pour la forme et un nom pour le message doit être construite.</span><span class="sxs-lookup"><span data-stu-id="50e54-142">In the Properties window, type a name for the shape, and a name for the message to be constructed.</span></span>  
  
4.  <span data-ttu-id="50e54-143">Dans l’aire de conception d’orchestration, cliquez sur **transformer**.</span><span class="sxs-lookup"><span data-stu-id="50e54-143">On the orchestration design surface, click **Transform**.</span></span> <span data-ttu-id="50e54-144">Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (**...** ) à côté **nom de mappage**.</span><span class="sxs-lookup"><span data-stu-id="50e54-144">In the Properties window, click the ellipsis button (**...**) next to **Map Name**.</span></span>  
  
5.  <span data-ttu-id="50e54-145">Dans la fenêtre de la transformation de Configuration, cliquez sur **mappage existant**et dans **nom de mappage complet**, cliquez sur la carte que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="50e54-145">In the Transform Configuration window, click **Existing Map**, and in **Fully Qualified Map Name**, click the map that you just created.</span></span>  
  
6.  <span data-ttu-id="50e54-146">Sous **transformer**, cliquez sur **Source**.</span><span class="sxs-lookup"><span data-stu-id="50e54-146">Under **Transform**, click **Source**.</span></span> <span data-ttu-id="50e54-147">Cliquez sur la zone vide sous la variable et sélectionnez le nom du message de demande dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="50e54-147">Click the empty box under variable, and select the name of the request message from the drop-down list.</span></span>  
  
7.  <span data-ttu-id="50e54-148">Sous **transformer**, cliquez sur **Destination**.</span><span class="sxs-lookup"><span data-stu-id="50e54-148">Under **Transform**, click **Destination**.</span></span> <span data-ttu-id="50e54-149">Cliquez sur la zone vide sous la variable et sélectionnez le nom du message de réponse dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="50e54-149">Click the empty box under variable, and select the name of the response message from the drop-down list.</span></span>  
  
8.  <span data-ttu-id="50e54-150">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50e54-150">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e54-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50e54-151">See Also</span></span>  
 [<span data-ttu-id="50e54-152">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="50e54-152">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)