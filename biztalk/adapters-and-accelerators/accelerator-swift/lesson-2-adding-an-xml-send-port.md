---
title: "Leçon 2 : Ajout d’un Port d’envoi XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, XML ports
- XML ports
ms.assetid: 03b2ee43-7874-4ef9-b716-8e16e96d8382
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06b110b911c8cba2dbc643928e8b97e3746935a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-adding-an-xml-send-port"></a><span data-ttu-id="100fb-102">Leçon 2 : Ajout d’un Port d’envoi XML</span><span class="sxs-lookup"><span data-stu-id="100fb-102">Lesson 2: Adding an XML Send Port</span></span>
<span data-ttu-id="100fb-103">Un port d’envoi vous permet de définir la façon dont vous souhaitez que les messages envoyés.</span><span class="sxs-lookup"><span data-stu-id="100fb-103">You use a send port to define how you want the messages sent.</span></span> <span data-ttu-id="100fb-104">Dans cette leçon, vous créez un port d’envoi pour définir la façon dont les messages XML doivent être envoyés.</span><span class="sxs-lookup"><span data-stu-id="100fb-104">In this lesson, you create a send port to define how XML messages should be sent.</span></span>  
  
### <a name="to-add-an-xml-send-port"></a><span data-ttu-id="100fb-105">Pour ajouter un port d’envoi XML</span><span class="sxs-lookup"><span data-stu-id="100fb-105">To add an XML send port</span></span>  
  
1.  <span data-ttu-id="100fb-106">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="100fb-106">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="100fb-107">Dans la boîte de dialogue Propriétés de Port d’envoi dans le **nom** , tapez **MT103_XML_SendPort**.</span><span class="sxs-lookup"><span data-stu-id="100fb-107">In the Send Port Properties dialog box, in the **Name** box, type **MT103_XML_SendPort**.</span></span>  
  
3.  <span data-ttu-id="100fb-108">Dans le **Transport** section, pour le **Type** zone, cliquez sur la liste déroulante, puis sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="100fb-108">In the **Transport** section, for the **Type** box, click the drop-down list, and then select **FILE**.</span></span>  
  
4.  <span data-ttu-id="100fb-109">Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.</span><span class="sxs-lookup"><span data-stu-id="100fb-109">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
5.  <span data-ttu-id="100fb-110">Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="100fb-110">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="100fb-111">Dans la boîte de dialogue Rechercher un dossier, déplacer vers le  **\<lecteur > : \Labs\Outbound** dossier, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="100fb-111">In the Browse For Folder dialog box, move to the **\<drive>:\Labs\Outbound** folder, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="100fb-112">Dans la boîte de dialogue Propriétés du Transport FILE, vérifiez que **%MessageID%.xml** est entré dans le **nom de fichier** zone, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="100fb-112">In the FILE Transport Properties dialog box, ensure that **%MessageID%.xml** is entered in the **File Name** box, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="100fb-113">Dans la boîte de dialogue Propriétés de Port d’envoi, vérifiez que **BizTalkServerApplication** est sélectionné pour le **Gestionnaire d’envoi** qui **PassThruTransmit** est sélectionné pour le **Pipeline d’envoi** boîte.</span><span class="sxs-lookup"><span data-stu-id="100fb-113">In the Send Port Properties dialog box, ensure that **BizTalkServerApplication** is selected for the **Send handler** box, and that **PassThruTransmit** is selected for the **Send pipeline** box.</span></span>  
  
9. <span data-ttu-id="100fb-114">Dans le volet gauche, cliquez sur **filtres**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="100fb-114">In the left pane, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="100fb-115">Utiliser</span><span class="sxs-lookup"><span data-stu-id="100fb-115">Use this</span></span>|<span data-ttu-id="100fb-116">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="100fb-116">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="100fb-117">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="100fb-117">**Property**</span></span>|<span data-ttu-id="100fb-118">Sélectionnez **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="100fb-118">Select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="100fb-119">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="100fb-119">**Operator**</span></span>|<span data-ttu-id="100fb-120">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="100fb-120">Select **==**.</span></span>|  
    |<span data-ttu-id="100fb-121">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="100fb-121">**Value**</span></span>|<span data-ttu-id="100fb-122">Type **MT103_FlatFile_ReceivePort**.</span><span class="sxs-lookup"><span data-stu-id="100fb-122">Type **MT103_FlatFile_ReceivePort**.</span></span>|  
    |<span data-ttu-id="100fb-123">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="100fb-123">**Group**</span></span>|<span data-ttu-id="100fb-124">Sélectionnez **et**.</span><span class="sxs-lookup"><span data-stu-id="100fb-124">Select **And**.</span></span>|  
  
10. <span data-ttu-id="100fb-125">Cliquez à l’intérieur de la ligne suivante de la propriété et procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="100fb-125">Click inside the next property line and do the following:</span></span>  
  
    |<span data-ttu-id="100fb-126">Utiliser</span><span class="sxs-lookup"><span data-stu-id="100fb-126">Use this</span></span>|<span data-ttu-id="100fb-127">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="100fb-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="100fb-128">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="100fb-128">**Property**</span></span>|<span data-ttu-id="100fb-129">Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**</span><span class="sxs-lookup"><span data-stu-id="100fb-129">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**</span></span>|  
    |<span data-ttu-id="100fb-130">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="100fb-130">**Operator**</span></span>|<span data-ttu-id="100fb-131">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="100fb-131">Select **==**.</span></span>|  
    |<span data-ttu-id="100fb-132">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="100fb-132">**Value**</span></span>|<span data-ttu-id="100fb-133">Type **False** pour les messages valides.</span><span class="sxs-lookup"><span data-stu-id="100fb-133">Type **False** for valid messages.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="100fb-134">Vous ajoutez le **» Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed == False «** clause d’expression de filtre afin que le port d’envoi envoie uniquement analyser et de valider les messages.</span><span class="sxs-lookup"><span data-stu-id="100fb-134">You add the **"Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed == False"** filter expression clause so that the send port sends only successfully parsed and validated messages.</span></span> <span data-ttu-id="100fb-135">Contrairement à un pipeline de réception à l’aide de native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] désassembleurs, les [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] désassembleur ne suspend pas un message (erroné) ayant échoué, mais à la place le publie dans la MessageBox et la marque comme étant a échoué, en utilisant les propriétés promues.</span><span class="sxs-lookup"><span data-stu-id="100fb-135">Unlike a receive pipeline using native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] disassemblers, the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] disassembler will not suspend a failed (erroneous) message, but instead publishes it to the MessageBox and marks it as failed, using promoted properties.</span></span> <span data-ttu-id="100fb-136">A4SWIFT attache une représentation XML des erreurs qui ont été collectés pour le message ayant échoué avant de le publier dans MessageBox.</span><span class="sxs-lookup"><span data-stu-id="100fb-136">A4SWIFT attaches an XML representation of the errors that were collected to the failed message before publishing it to the MessageBox.</span></span>  
    > <span data-ttu-id="100fb-137">Sans inclure le « Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed == False « clause d’expression de filtre, votre port d’envoi envoie tous les messages : a réussi ou échoué.</span><span class="sxs-lookup"><span data-stu-id="100fb-137">Without including the "Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed == False" filter expression clause, your send port will send all messages: passed or failed.</span></span> <span data-ttu-id="100fb-138">Pour plus d’informations sur les abonnements aux messages ayant échoué, consultez [utilisation des abonnements de Message d’échec de](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).</span><span class="sxs-lookup"><span data-stu-id="100fb-138">For more information about failed message subscriptions, see [Working with Failed Message Subscriptions](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).</span></span>  
  
11. <span data-ttu-id="100fb-139">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="100fb-139">Click **Apply**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="100fb-140">Dans la Console Administration de BizTalk Server, dans **Ports d’envoi**, avec le bouton droit **MT103_XML_SendPort**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="100fb-140">In the BizTalk Server Administration Console, in **Send Ports**, right-click **MT103_XML_SendPort**, and then click **Start**.</span></span>  
  
 <span data-ttu-id="100fb-141">Passez à [Module 6 : déployer les règles d’entreprise](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md).</span><span class="sxs-lookup"><span data-stu-id="100fb-141">Proceed to [Module 6: Deploying the Business Rules](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md).</span></span>