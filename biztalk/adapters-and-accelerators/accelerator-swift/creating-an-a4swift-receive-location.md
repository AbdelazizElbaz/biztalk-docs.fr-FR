---
title: "Emplacement de réception de création d’un A4SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
ms.assetid: 712cf42f-8d71-47e9-b2bf-3da158b74fe4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11c77b7b28c65c4743998f7d4c54d9c7cd48437f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-an-a4swift-receive-location"></a><span data-ttu-id="e891b-102">Emplacement de réception de création d’un A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="e891b-102">Creating an A4SWIFT Receive Location</span></span>
<span data-ttu-id="e891b-103">Vous devez créer un [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] emplacement de réception pour activer la réception des messages à partir du réseau rapide par [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="e891b-103">You must create an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive location to enable message reception from the SWIFT network by [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], as shown in the following figure.</span></span> <span data-ttu-id="e891b-104">L’emplacement de réception reçoit les messages de fichier plat à partir d’un dossier de fichiers entrant.</span><span class="sxs-lookup"><span data-stu-id="e891b-104">The receive location receives flat file messages from an inbound file folder.</span></span>  
  
 <span data-ttu-id="e891b-105">![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-receive-location-configuration.gif "A4SWIFT_Receive_Location_Configuration")</span><span class="sxs-lookup"><span data-stu-id="e891b-105">![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-receive-location-configuration.gif "A4SWIFT_Receive_Location_Configuration")</span></span>  
  
 <span data-ttu-id="e891b-106">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="e891b-106">**Summary**</span></span>  
  
 <span data-ttu-id="e891b-107">Créer et lier un port de réception unidirectionnel, puis créer et activer un emplacement de réception avec les propriétés suivantes et les composants :</span><span class="sxs-lookup"><span data-stu-id="e891b-107">Create and bind a one-way receive port, and then create and enable a receive location with the following properties and components:</span></span>  
  
|<span data-ttu-id="e891b-108">Composants/propriété</span><span class="sxs-lookup"><span data-stu-id="e891b-108">Property/Components</span></span>|<span data-ttu-id="e891b-109">Paramètre</span><span class="sxs-lookup"><span data-stu-id="e891b-109">Setting</span></span>|  
|--------------------------|-------------|  
|<span data-ttu-id="e891b-110">Port de réception</span><span class="sxs-lookup"><span data-stu-id="e891b-110">Receive port</span></span>|<span data-ttu-id="e891b-111">Port unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="e891b-111">One-way port</span></span>|  
|<span data-ttu-id="e891b-112">Type de transport </span><span class="sxs-lookup"><span data-stu-id="e891b-112">Transport type</span></span>|<span data-ttu-id="e891b-113">FILE</span><span class="sxs-lookup"><span data-stu-id="e891b-113">FILE</span></span>|  
|<span data-ttu-id="e891b-114">Adresse URI</span><span class="sxs-lookup"><span data-stu-id="e891b-114">Address URI</span></span>|<span data-ttu-id="e891b-115">Nom du dossier que vous souhaitez recevoir le message</span><span class="sxs-lookup"><span data-stu-id="e891b-115">Name of the folder that you want to receive the message</span></span>|  
|<span data-ttu-id="e891b-116">Masque de fichier</span><span class="sxs-lookup"><span data-stu-id="e891b-116">File mask</span></span>|<span data-ttu-id="e891b-117">\*.  *\<extension\>*, où \< *extension* \> est l’extension d’entrant message de fichier plat</span><span class="sxs-lookup"><span data-stu-id="e891b-117">\*.*\<extension\>*, where \<*extension*\> is the extension of the incoming flat file message</span></span>|  
|<span data-ttu-id="e891b-118">Gestionnaire de réception</span><span class="sxs-lookup"><span data-stu-id="e891b-118">Receive handler</span></span>|<span data-ttu-id="e891b-119">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="e891b-119">BizTalkServerApplication</span></span>|  
|<span data-ttu-id="e891b-120">Pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="e891b-120">Receive pipeline</span></span>|<span data-ttu-id="e891b-121">Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipeline de réception qui vous avez créé</span><span class="sxs-lookup"><span data-stu-id="e891b-121">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive pipeline that you created</span></span>|  
  
### <a name="to-add-the-receive-port-and-location"></a><span data-ttu-id="e891b-122">Pour ajouter le port de réception et l’emplacement</span><span class="sxs-lookup"><span data-stu-id="e891b-122">To add the receive port and location</span></span>  
  
1.  <span data-ttu-id="e891b-123">Démarrer **Administration de BizTalk Server** console.</span><span class="sxs-lookup"><span data-stu-id="e891b-123">Start **BizTalk Server Administration** console.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e891b-124">La Console Administration de BizTalk Server peut également être ouvert à partir de Visual Studio en cliquant sur **Administration de BizTalk Server** dans les **outils** menu.</span><span class="sxs-lookup"><span data-stu-id="e891b-124">The BizTalk Server Administration Console can also be opened from within Visual Studio by clicking **BizTalk Server Administration** in the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="e891b-125">Dans la Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="e891b-125">In Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="e891b-126">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="e891b-126">Right-click **Receive Ports**, point to **New**, and then click **One-Way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="e891b-127">Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez un nom pour le port de réception.</span><span class="sxs-lookup"><span data-stu-id="e891b-127">In the Receive Port Properties dialog box, in the **Name** box, type a name for the receive port.</span></span>  
  
5.  <span data-ttu-id="e891b-128">Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e891b-128">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="e891b-129">Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="e891b-129">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
7.  <span data-ttu-id="e891b-130">Dans la boîte de dialogue un Port de réception, sélectionnez, cliquez sur le port de réception que vous venez de créer, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e891b-130">In the Select a Receive Port dialog box, click the receive port that you just created, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="e891b-131">Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez un nom pour l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="e891b-131">In the Receive Location Properties dialog box, in the **Name** box, type a name for the receive location.</span></span>  
  
9. <span data-ttu-id="e891b-132">Dans le **Transport** section, pour le **Type** zone de texte, cliquez sur la liste déroulante et sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="e891b-132">In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.</span></span>  
  
10. <span data-ttu-id="e891b-133">Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.</span><span class="sxs-lookup"><span data-stu-id="e891b-133">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
11. <span data-ttu-id="e891b-134">Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="e891b-134">In the FILE Transport Properties dialog box, click **Browse**.</span></span> <span data-ttu-id="e891b-135">Déplacer vers le dossier que vous souhaitez recevoir le message.</span><span class="sxs-lookup"><span data-stu-id="e891b-135">Move to the folder that you want to receive the message.</span></span> <span data-ttu-id="e891b-136">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e891b-136">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e891b-137">Si ce dossier n’existe pas, vous pouvez créer à l’aide de la **créer un nouveau dossier** commande.</span><span class="sxs-lookup"><span data-stu-id="e891b-137">If this folder does not exist, you can create it using the **Make New Folder** command.</span></span>  
  
12. <span data-ttu-id="e891b-138">Dans la boîte de dialogue Propriétés du Transport FILE, dans le **masque de fichier** , entrez  **\*.\<* extension*\>**, où \<* extension* \> est l’extension de fichier plat entrant d’un message, par exemple en tant que **.txt**.</span><span class="sxs-lookup"><span data-stu-id="e891b-138">In the FILE Transport Properties dialog box, in the **File Mask** box, enter **\*.\<*extension*\>**, where \<*extension*\> is the extension of the incoming flat file message, such as **.txt**.</span></span> <span data-ttu-id="e891b-139">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e891b-139">Click **OK**.</span></span>  
  
13. <span data-ttu-id="e891b-140">Dans la boîte de dialogue Propriétés de l’emplacement de réception, vérifiez que **BizTalkServerApplication** est entré pour le **Gestionnaire de réception** boîte.</span><span class="sxs-lookup"><span data-stu-id="e891b-140">In the Receive Location Properties dialog box, ensure that **BizTalkServerApplication** is entered for the **Receive handler** box.</span></span>  
  
14. <span data-ttu-id="e891b-141">Pour le **Pipeline de réception** , sélectionnez votre pipeline de réception personnalisé dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e891b-141">For the **Receive Pipeline** box, select your custom receive pipeline from the drop-down list.</span></span>  
  
15. <span data-ttu-id="e891b-142">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e891b-142">Click **Apply**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="e891b-143">Dans la Console Administration de BizTalk Server, cliquez sur **emplacements de réception**, cliquez sur l’emplacement de réception que vous venez de créée, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="e891b-143">In the BizTalk Server Administration Console, click **Receive Locations**, right-click the receive location that you just created, and then click **Enable**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e891b-144">Une fois que l’emplacement de réception, BizTalk interroge activement votre dossier de fichiers.</span><span class="sxs-lookup"><span data-stu-id="e891b-144">After you enable the receive location, BizTalk actively polls your file folder.</span></span>