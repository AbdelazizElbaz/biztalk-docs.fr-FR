---
title: "Encodage de prise en charge étendue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93a40fa6-d0da-416e-97fb-675ddde3f005
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e36c3baff4ac33f2878295791bb3f6615c1b25d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extended-encoding-support"></a><span data-ttu-id="668b1-102">Prise en charge du codage étendue</span><span class="sxs-lookup"><span data-stu-id="668b1-102">Extended Encoding Support</span></span>
<span data-ttu-id="668b1-103">Par défaut, le HL7 reçoivent pipeline, BTAHL72X, prend uniquement en charge le codage ASCII.</span><span class="sxs-lookup"><span data-stu-id="668b1-103">By default, the HL7 receive pipeline, BTAHL72X, only supports ASCII encoding.</span></span> <span data-ttu-id="668b1-104">Cela signifie que tous les caractères dans un message d’entrée avec une valeur équivalente supérieure à 127 sont remplacées par « ? ».</span><span class="sxs-lookup"><span data-stu-id="668b1-104">This means that any characters in an input message with an equivalent value greater than 127 are replaced with "?".</span></span> <span data-ttu-id="668b1-105">Il s’agit, car une valeur équivalente supérieure à 127 caractères ne sont pas représentés dans le jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="668b1-105">This is because characters with an equivalent value greater than 127 are not represented in the ASCII character set.</span></span>  
  
 [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]<span data-ttu-id="668b1-106">prend en charge pour les deux encodages nouvelle :</span><span class="sxs-lookup"><span data-stu-id="668b1-106"> provides support for two new encodings:</span></span>  
  
-   <span data-ttu-id="668b1-107">Europe occidentale</span><span class="sxs-lookup"><span data-stu-id="668b1-107">Western European</span></span>  
  
-   <span data-ttu-id="668b1-108">UTF-8</span><span class="sxs-lookup"><span data-stu-id="668b1-108">UTF-8</span></span>  
  
 <span data-ttu-id="668b1-109">Vous créez et créez un composant de pipeline personnalisé pour implémenter la prise en charge du codage étendue.</span><span class="sxs-lookup"><span data-stu-id="668b1-109">You create and build a custom pipeline component to implement extended encoding support.</span></span> <span data-ttu-id="668b1-110">Le composant de pipeline personnalisé utilise le BTAHL7 2.X désassembleur.</span><span class="sxs-lookup"><span data-stu-id="668b1-110">The custom pipeline component uses the BTAHL7 2.X Disassembler.</span></span> <span data-ttu-id="668b1-111">Vous créez un emplacement de réception qui utilise le pipeline personnalisé pour traiter les messages.</span><span class="sxs-lookup"><span data-stu-id="668b1-111">You create a receive location that uses the custom pipeline to process messages.</span></span> <span data-ttu-id="668b1-112">Pour tester l’emplacement de réception et un pipeline personnalisé, vous créez un port d’envoi qui utilise le 2.XSendPipeline BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="668b1-112">To test the receive location and custom pipeline, you create a send port that uses the BTAHL7 2.XSendPipeline.</span></span>  
  
### <a name="to-create-a-custom-pipeline"></a><span data-ttu-id="668b1-113">Pour créer un pipeline personnalisé</span><span class="sxs-lookup"><span data-stu-id="668b1-113">To create a custom pipeline</span></span>  
  
1.  <span data-ttu-id="668b1-114">Dans [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)], ajoutez un nouveau **projet BizTalk Server vide**.</span><span class="sxs-lookup"><span data-stu-id="668b1-114">In [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)], add a new **Empty BizTalk Server Project**.</span></span>  
  
2.  <span data-ttu-id="668b1-115">Dans l’Explorateur de solutions, cliquez sur le nouveau projet, cliquez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="668b1-115">In Solution Explorer, right-click the new project, click **Add**, and then click **New Item**.</span></span>  
  
3.  <span data-ttu-id="668b1-116">Dans le **ajouter un nouvel élément** boîte de dialogue zone, ajoutez une nouvelle **Pipeline de réception**.</span><span class="sxs-lookup"><span data-stu-id="668b1-116">In the **Add New Item** dialog box, add a new **Receive Pipeline**.</span></span>  
  
4.  <span data-ttu-id="668b1-117">Dans la boîte à outils de pipeline, faites glisser le **BTAHL7 2.X désassembleur** à l’éditeur de pipeline et déposez-le sur le **désassembler** étape **Déposer ici** cible.</span><span class="sxs-lookup"><span data-stu-id="668b1-117">From the pipeline toolbox, drag the **BTAHL7 2.X Disassembler** to the pipeline editor and drop it onto the **Disassemble** stage **Drop Here** target.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="668b1-118">Si le désassembleur 2.7 BTAHL7 ne se trouve pas dans la boîte à outils, avec le bouton droit dans la boîte à outils, puis cliquez sur **choisir des éléments de**.</span><span class="sxs-lookup"><span data-stu-id="668b1-118">If the BTAHL7 2.7 Disassembler is not in the toolbox, right-click in the toolbox, and click **Choose Items**.</span></span> <span data-ttu-id="668b1-119">Dans le **choisir des éléments de boîte à outils** boîte de dialogue le **composant de Pipeline BizTalk** onglet, sélectionnez le **BTAHL7 2.X désassembleur** case à cocher, puis cliquez sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="668b1-119">In the **Choose Toolbox Items** dialog box, on the **BizTalk Pipeline Component** tab, select the **BTAHL7 2.X Disassembler** check box, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="668b1-120">Dans le volet Propriétés pour le **BTAHL7 2.X désassembleur**, à partir de la **codage de jeu de caractères** la liste déroulante, sélectionnez **Europe occidentale** ou **UTF8**codage.</span><span class="sxs-lookup"><span data-stu-id="668b1-120">In the Properties pane for the **BTAHL7 2.X Disassembler**, from the **Encoding charset** drop-down list, select **Western European** or **UTF8** encoding.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="668b1-121">HL7 prend uniquement en charge ASCII (la valeur par défaut), Europe et encodage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="668b1-121">HL7 only supports ASCII (the default), Western European, and UTF8 encoding.</span></span> <span data-ttu-id="668b1-122">Ne sélectionnez pas les autres options d’encodage HL7 ne prenant pas en charge les.</span><span class="sxs-lookup"><span data-stu-id="668b1-122">Do not select the other encoding options because HL7 does not support them.</span></span>  
  
6.  <span data-ttu-id="668b1-123">Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="668b1-123">On the **File** menu, click **Save All**.</span></span>  
  
7.  <span data-ttu-id="668b1-124">Déployez le projet.</span><span class="sxs-lookup"><span data-stu-id="668b1-124">Deploy the project.</span></span>  
  
     <span data-ttu-id="668b1-125">Créer un nouvel emplacement de réception à continuer.</span><span class="sxs-lookup"><span data-stu-id="668b1-125">Create a new receive location to continue.</span></span>  
  
### <a name="to-create-a-receive-location-that-uses-the-custom-pipeline"></a><span data-ttu-id="668b1-126">Pour créer un emplacement de réception qui utilise le pipeline personnalisé</span><span class="sxs-lookup"><span data-stu-id="668b1-126">To create a receive location that uses the custom pipeline</span></span>  
  
1.  <span data-ttu-id="668b1-127">Sur le **Démarrer** menu, cliquez sur **programmes**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="668b1-127">On the **Start** menu, click **Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="668b1-128">Dans la console Administration de BizTalk Server, développez [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, développez l’application vous avez désigné pour votre assembly de pipeline (par défaut, **BizTalk Application 1**), avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **Unidirectionnel emplacement de réception**.</span><span class="sxs-lookup"><span data-stu-id="668b1-128">In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, expand the application you designated for your pipeline assembly (by default, **BizTalk Application 1**), right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
3.  <span data-ttu-id="668b1-129">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **pipeline de réception** liste déroulante, sélectionnez le nom personnalisé de pipeline que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="668b1-129">In the **Receive Location Properties** dialog box, in the **Receive pipeline** drop-down list, select the name of the custom pipeline you created.</span></span> <span data-ttu-id="668b1-130">(Il s’agit du nom de l’objet de pipeline personnalisé, pas le BTAHL7 de pipeline 2 X.)</span><span class="sxs-lookup"><span data-stu-id="668b1-130">(This is the name of the custom pipeline object, not the BTAHL7 2X pipeline.)</span></span>  
  
### <a name="to-create-a-send-port-to-test-the-receive-location-and-pipeline"></a><span data-ttu-id="668b1-131">Pour créer un port d’envoi pour tester l’emplacement de réception et un pipeline</span><span class="sxs-lookup"><span data-stu-id="668b1-131">To create a send port to test the receive location and pipeline</span></span>  
  
1.  <span data-ttu-id="668b1-132">Sur le **Démarrer** menu, cliquez sur **programmes**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="668b1-132">On the **Start** menu, click **Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="668b1-133">Dans la console Administration de BizTalk Server, développez [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, développez l’application vous avez désigné pour votre assembly de pipeline (par défaut, **BizTalk Application 1**), avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="668b1-133">In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, expand the application you designated for your pipeline assembly (by default, **BizTalk Application 1**), right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
3.  <span data-ttu-id="668b1-134">Dans le **propriétés de Port d’envoi** boîte de dialogue le **pipeline d’envoi** la liste déroulante, sélectionnez **BTAHL72XSendPipeline**.</span><span class="sxs-lookup"><span data-stu-id="668b1-134">In the **Send Port Properties** dialog box, in the **Send pipeline** drop-down list, select **BTAHL72XSendPipeline**.</span></span>  
  
### <a name="to-test-the-receive-location-and-pipeline"></a><span data-ttu-id="668b1-135">Pour tester l’emplacement de réception et un pipeline</span><span class="sxs-lookup"><span data-stu-id="668b1-135">To test the receive location and pipeline</span></span>  
  
-   <span data-ttu-id="668b1-136">Supprimer un fichier contenant des caractères spéciaux et enregistré avec le même encodage spécifié dans le pipeline personnalisé dans l’emplacement indiqué dans l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="668b1-136">Drop a file containing special characters and saved with the same encoding you specified in the custom pipeline into the location designated in the receive location.</span></span> <span data-ttu-id="668b1-137">Le fichier à l’emplacement de sortie doit conserver les caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="668b1-137">The file at the output location should preserve the special characters.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="668b1-138">Si vous essayez de traiter un fichier qui utilise un encodage non pris en charge (n’oubliez pas qu’uniquement ASCII, Europe et UTF-8 sont prises en charge), une erreur est consignée dans l’Observateur d’événements Application avec l’ID d’erreur : 5633.</span><span class="sxs-lookup"><span data-stu-id="668b1-138">If you attempt to process a file that uses a non-supported encoding (remember that only ASCII, Western European, and UTF8 are supported), an error is logged in the Application Event Viewer with error ID: 5633.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="668b1-139">Si vous testez un pipeline personnalisé configuré pour l’encodage UTF-8, les caractères de la marque d’ordre d’octet (BOM) doit être attaché au message que vous passez.</span><span class="sxs-lookup"><span data-stu-id="668b1-139">If you are testing a custom pipeline configured for UTF8 encoding, you should attach Byte Order Mark (BOM) characters to the message you are passing.</span></span> <span data-ttu-id="668b1-140">Si vous testez un pipeline personnalisé configuré pour l’encodage Occidental, n’attachez pas les caractères de nomenclature.</span><span class="sxs-lookup"><span data-stu-id="668b1-140">If you are testing a custom pipeline configured for Western European encoding, do not attach BOM characters.</span></span>