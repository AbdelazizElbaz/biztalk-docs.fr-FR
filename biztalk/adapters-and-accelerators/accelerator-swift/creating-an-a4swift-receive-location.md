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
ms.openlocfilehash: e3f0835c6d83efc9db91f5c1d63e91f4c143399d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-an-a4swift-receive-location"></a><span data-ttu-id="52248-102">Emplacement de réception de création d’un A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="52248-102">Creating an A4SWIFT Receive Location</span></span>
<span data-ttu-id="52248-103">Vous devez créer un [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] emplacement de réception pour activer la réception des messages à partir du réseau rapide par [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="52248-103">You must create an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive location to enable message reception from the SWIFT network by [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], as shown in the following figure.</span></span> <span data-ttu-id="52248-104">L’emplacement de réception reçoit les messages de fichier plat à partir d’un dossier de fichiers entrant.</span><span class="sxs-lookup"><span data-stu-id="52248-104">The receive location receives flat file messages from an inbound file folder.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-receive-location-configuration.gif "A4SWIFT_Receive_Location_Configuration")  
  
 <span data-ttu-id="52248-105">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="52248-105">**Summary**</span></span>  
  
 <span data-ttu-id="52248-106">Créer et lier un port de réception unidirectionnel, puis créer et activer un emplacement de réception avec les propriétés suivantes et les composants :</span><span class="sxs-lookup"><span data-stu-id="52248-106">Create and bind a one-way receive port, and then create and enable a receive location with the following properties and components:</span></span>  
  
|<span data-ttu-id="52248-107">Composants/propriété</span><span class="sxs-lookup"><span data-stu-id="52248-107">Property/Components</span></span>|<span data-ttu-id="52248-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="52248-108">Setting</span></span>|  
|--------------------------|-------------|  
|<span data-ttu-id="52248-109">Port de réception</span><span class="sxs-lookup"><span data-stu-id="52248-109">Receive port</span></span>|<span data-ttu-id="52248-110">Port unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="52248-110">One-way port</span></span>|  
|<span data-ttu-id="52248-111">Type de transport </span><span class="sxs-lookup"><span data-stu-id="52248-111">Transport type</span></span>|<span data-ttu-id="52248-112">FILE</span><span class="sxs-lookup"><span data-stu-id="52248-112">FILE</span></span>|  
|<span data-ttu-id="52248-113">Adresse URI</span><span class="sxs-lookup"><span data-stu-id="52248-113">Address URI</span></span>|<span data-ttu-id="52248-114">Nom du dossier que vous souhaitez recevoir le message</span><span class="sxs-lookup"><span data-stu-id="52248-114">Name of the folder that you want to receive the message</span></span>|  
|<span data-ttu-id="52248-115">Masque de fichier</span><span class="sxs-lookup"><span data-stu-id="52248-115">File mask</span></span>|<span data-ttu-id="52248-116">\*.  *\<extension >*, où \< *extension*> est l’extension d’entrant message de fichier plat</span><span class="sxs-lookup"><span data-stu-id="52248-116">\*.*\<extension>*, where \<*extension*> is the extension of the incoming flat file message</span></span>|  
|<span data-ttu-id="52248-117">Gestionnaire de réception</span><span class="sxs-lookup"><span data-stu-id="52248-117">Receive handler</span></span>|<span data-ttu-id="52248-118">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="52248-118">BizTalkServerApplication</span></span>|  
|<span data-ttu-id="52248-119">Pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="52248-119">Receive pipeline</span></span>|<span data-ttu-id="52248-120">Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipeline de réception qui vous avez créé</span><span class="sxs-lookup"><span data-stu-id="52248-120">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive pipeline that you created</span></span>|  
  
### <a name="to-add-the-receive-port-and-location"></a><span data-ttu-id="52248-121">Pour ajouter le port de réception et l’emplacement</span><span class="sxs-lookup"><span data-stu-id="52248-121">To add the receive port and location</span></span>  
  
1.  <span data-ttu-id="52248-122">Démarrer **Administration de BizTalk Server** console.</span><span class="sxs-lookup"><span data-stu-id="52248-122">Start **BizTalk Server Administration** console.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="52248-123">La Console Administration de BizTalk Server peut également être ouvert à partir de Visual Studio en cliquant sur **Administration de BizTalk Server** dans les **outils** menu.</span><span class="sxs-lookup"><span data-stu-id="52248-123">The BizTalk Server Administration Console can also be opened from within Visual Studio by clicking **BizTalk Server Administration** in the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="52248-124">Dans la Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="52248-124">In Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="52248-125">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="52248-125">Right-click **Receive Ports**, point to **New**, and then click **One-Way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="52248-126">Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez un nom pour le port de réception.</span><span class="sxs-lookup"><span data-stu-id="52248-126">In the Receive Port Properties dialog box, in the **Name** box, type a name for the receive port.</span></span>  
  
5.  <span data-ttu-id="52248-127">Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="52248-127">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="52248-128">Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="52248-128">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
7.  <span data-ttu-id="52248-129">Dans la boîte de dialogue un Port de réception, sélectionnez, cliquez sur le port de réception que vous venez de créer, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="52248-129">In the Select a Receive Port dialog box, click the receive port that you just created, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="52248-130">Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez un nom pour l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="52248-130">In the Receive Location Properties dialog box, in the **Name** box, type a name for the receive location.</span></span>  
  
9. <span data-ttu-id="52248-131">Dans le **Transport** section, pour le **Type** zone de texte, cliquez sur la liste déroulante et sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="52248-131">In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.</span></span>  
  
10. <span data-ttu-id="52248-132">Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.</span><span class="sxs-lookup"><span data-stu-id="52248-132">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
11. <span data-ttu-id="52248-133">Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="52248-133">In the FILE Transport Properties dialog box, click **Browse**.</span></span> <span data-ttu-id="52248-134">Déplacer vers le dossier que vous souhaitez recevoir le message.</span><span class="sxs-lookup"><span data-stu-id="52248-134">Move to the folder that you want to receive the message.</span></span> <span data-ttu-id="52248-135">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="52248-135">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="52248-136">Si ce dossier n’existe pas, vous pouvez créer à l’aide de la **créer un nouveau dossier** commande.</span><span class="sxs-lookup"><span data-stu-id="52248-136">If this folder does not exist, you can create it using the **Make New Folder** command.</span></span>  
  
12. <span data-ttu-id="52248-137">Dans la boîte de dialogue Propriétés du Transport FILE, dans le **masque de fichier** , entrez  **\*.\<* extension*>**, où \<* extension*> est l’extension d’entrant message de fichier plat, par exemple **.txt**.</span><span class="sxs-lookup"><span data-stu-id="52248-137">In the FILE Transport Properties dialog box, in the **File Mask** box, enter **\*.\<*extension*>**, where \<*extension*> is the extension of the incoming flat file message, such as **.txt**.</span></span> <span data-ttu-id="52248-138">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="52248-138">Click **OK**.</span></span>  
  
13. <span data-ttu-id="52248-139">Dans la boîte de dialogue Propriétés de l’emplacement de réception, vérifiez que **BizTalkServerApplication** est entré pour le **Gestionnaire de réception** boîte.</span><span class="sxs-lookup"><span data-stu-id="52248-139">In the Receive Location Properties dialog box, ensure that **BizTalkServerApplication** is entered for the **Receive handler** box.</span></span>  
  
14. <span data-ttu-id="52248-140">Pour le **Pipeline de réception** , sélectionnez votre pipeline de réception personnalisé dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="52248-140">For the **Receive Pipeline** box, select your custom receive pipeline from the drop-down list.</span></span>  
  
15. <span data-ttu-id="52248-141">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="52248-141">Click **Apply**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="52248-142">Dans la Console Administration de BizTalk Server, cliquez sur **emplacements de réception**, cliquez sur l’emplacement de réception que vous venez de créée, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="52248-142">In the BizTalk Server Administration Console, click **Receive Locations**, right-click the receive location that you just created, and then click **Enable**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="52248-143">Une fois que l’emplacement de réception, BizTalk interroge activement votre dossier de fichiers.</span><span class="sxs-lookup"><span data-stu-id="52248-143">After you enable the receive location, BizTalk actively polls your file folder.</span></span>