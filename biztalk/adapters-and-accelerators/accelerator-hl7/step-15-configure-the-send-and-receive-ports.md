---
title: "Étape 15 : Configurer l’envoi et Ports de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message enrichment tutorial, ports
ms.assetid: d532b196-473e-4c8f-b4ed-acef674fc698
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 020d83db1db86f9ff9ce116578cf58f19ba08241
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-15-configure-the-send-and-receive-ports"></a><span data-ttu-id="6ead8-102">Étape 15 : Configurer l’envoi et Ports de réception</span><span class="sxs-lookup"><span data-stu-id="6ead8-102">Step 15: Configure the Send and Receive Ports</span></span>
<span data-ttu-id="6ead8-103">Dans les étapes précédentes, vous créé un envoi logique à l’aide du Concepteur d’Orchestration de port de réception et définissez la liaison de port pour « Spécifier plus tard ».</span><span class="sxs-lookup"><span data-stu-id="6ead8-103">In previous steps, you created a logical send and receive port using Orchestration Designer and set the port binding to "Specify Later".</span></span> <span data-ttu-id="6ead8-104">Dans cette étape, vous utilisez l’Explorateur BizTalk pour finaliser la configuration du port en définissant les emplacements source et destination physiques et de liaison des ports physiques aux ports logiques que vous avez créé dans l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="6ead8-104">In this step, you use BizTalk Explorer to finalize the port configuration by defining the physical source and destination locations and binding the physical ports to the logical ports that you created in the orchestration.</span></span>  
  
## <a name="configure-the-send-and-receive-ports"></a><span data-ttu-id="6ead8-105">Configurer l’envoi et de ports de réception</span><span class="sxs-lookup"><span data-stu-id="6ead8-105">Configure the send and receive ports</span></span>  
  
1.  <span data-ttu-id="6ead8-106">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-106">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
2.  <span data-ttu-id="6ead8-107">Avec le bouton droit **Ports d’envoi**, pointez sur Nouveau, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-107">Right-click **Send Ports**, point to New, and then click **Static One-way Send Port**.</span></span>  
  
3.  <span data-ttu-id="6ead8-108">Dans la boîte de dialogue Propriétés de Port d’envoi dans le **nom** , tapez **MLLPSendPort**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-108">In the Send Port Properties dialog box, in the **Name** box, type **MLLPSendPort**.</span></span>  
  
4.  <span data-ttu-id="6ead8-109">Pour **Type**, sélectionnez **MLLP**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-109">For **Type**, select **MLLP**.</span></span>  
  
5.  <span data-ttu-id="6ead8-110">Cliquez sur le **configurer** bouton à droite de la **Type** champ.</span><span class="sxs-lookup"><span data-stu-id="6ead8-110">Click the **Configure** button to the right of the **Type** field.</span></span>  
  
6.  <span data-ttu-id="6ead8-111">Dans la boîte de dialogue Propriétés du Transport MLLP pour **nom de la connexion** entrez **MLLPConnection**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-111">In the MLLP Transport Properties dialog box, for **Connection Name** enter **MLLPConnection**.</span></span> <span data-ttu-id="6ead8-112">Pour **hôte** entrez **localhost**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-112">For **Host** enter **localhost**.</span></span> <span data-ttu-id="6ead8-113">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-113">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="6ead8-114">Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-114">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="6ead8-115">Dans la Console d’Administration, cliquez sur **MLLPSendPort** de port, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-115">In the Administration Console, right-click **MLLPSendPort** port, and then click **Start**.</span></span>  
  
9. <span data-ttu-id="6ead8-116">Développez **paramètres de plateforme**, cliquez sur **Instances d’hôte**, avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-116">Expand **Platform Settings**, click **Host Instances**, right-click **BizTalkServerApplication**, and then click **Start**.</span></span> <span data-ttu-id="6ead8-117">Si l’hôte est déjà en cours d’exécution, cliquez sur **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-117">If the host is already running, click **Restart**.</span></span>  
  
10. <span data-ttu-id="6ead8-118">Cliquez sur **Orchestrations**, avec le bouton droit **BTAHL7_Project.Doorbell_Orchestration**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-118">Click **Orchestrations**, right-click **BTAHL7_Project.Doorbell_Orchestration**, and then click **Properties**.</span></span>  
  
11. <span data-ttu-id="6ead8-119">Dans la boîte de dialogue Propriétés d’Orchestration dans l’arborescence de la console, cliquez sur **liaisons**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-119">In the Orchestration Properties dialog box, in the console tree, click **Bindings**.</span></span>  
  
12. <span data-ttu-id="6ead8-120">Dans le **liaisons** volet, pour **hôte**, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="6ead8-120">In the **Bindings** pane, for **Host**, select **BizTalkServerApplication**.</span></span>  
  
13. <span data-ttu-id="6ead8-121">Pour **SOAPReceivePort**, sélectionnez **WebPort_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort** dans les **Ports de réception** colonne.</span><span class="sxs-lookup"><span data-stu-id="6ead8-121">For **SOAPReceivePort**, select **WebPort_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort** in the **Receive Ports** column.</span></span>  
  
14. <span data-ttu-id="6ead8-122">Pour **MLLPSendPort**, sélectionnez **MLLPSendPort** dans les **groupes de ports d’envoi d’envoi** colonne.</span><span class="sxs-lookup"><span data-stu-id="6ead8-122">For **MLLPSendPort**, select **MLLPSendPort** in the **Send Ports/Send Port Groups** column.</span></span>  
  
15. <span data-ttu-id="6ead8-123">Cliquez sur **OK** pour enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="6ead8-123">Click **OK** to save the changes.</span></span>  
  
## <a name="msh-5-and-msh-6"></a><span data-ttu-id="6ead8-124">MSH 5 et 6 de MSH</span><span class="sxs-lookup"><span data-stu-id="6ead8-124">MSH 5 and MSH 6</span></span>  
 <span data-ttu-id="6ead8-125">Les champs d’en-tête MSH 5 et 6 de MSH contiennent l’application de destination, des installations, respectivement.</span><span class="sxs-lookup"><span data-stu-id="6ead8-125">The MSH 5 and MSH 6 header fields contain the destination application and facility, respectively.</span></span> <span data-ttu-id="6ead8-126">Dans l’Explorateur de Configuration, vous pouvez spécifier les valeurs pour chacun des trois composants de MSH 5 et 6 de MSH, dans les cas où vous souhaitez que les informations de destination dans le message doit être modifié.</span><span class="sxs-lookup"><span data-stu-id="6ead8-126">In Configuration Explorer, you can specify the values for each of the three components of MSH 5 and MSH 6, in cases when you want the destination information in the message to be changed.</span></span> <span data-ttu-id="6ead8-127">Il s’agit d’un scénario probable lorsque le message d’origine n’inclut pas les informations spécifiques aux tiers.</span><span class="sxs-lookup"><span data-stu-id="6ead8-127">This is a likely scenario when the original message does not include party-specific information.</span></span> <span data-ttu-id="6ead8-128">Cette étape s’applique dans le modèle déclaratif (serveur de publication/abonné).</span><span class="sxs-lookup"><span data-stu-id="6ead8-128">This step is applicable in the declarative (publisher/subscriber) model.</span></span> <span data-ttu-id="6ead8-129">Vous effectuez cette étape si elle est applicable dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="6ead8-129">You perform this step if it is applicable in your environment.</span></span> <span data-ttu-id="6ead8-130">Pour plus d’informations sur la définition de ces valeurs, consultez [Parties - Explorateur de Configuration de BTAHL7](parties-tab.md).</span><span class="sxs-lookup"><span data-stu-id="6ead8-130">For more information about setting these values, see [Parties - BTAHL7 Configuration Explorer](parties-tab.md).</span></span>  
  
 <span data-ttu-id="6ead8-131">Passez à [étape 16 : démarrer l’Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="6ead8-131">Proceed to [Step 16: Start the Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ead8-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ead8-132">See Also</span></span>  
 [<span data-ttu-id="6ead8-133">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="6ead8-133">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)