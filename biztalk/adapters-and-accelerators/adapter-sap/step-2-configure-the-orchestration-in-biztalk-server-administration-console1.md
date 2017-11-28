---
title: "Étape 2 : Configurer l’Orchestration de BizTalk Server Administration Console1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestration, configruing in BizTalk Server Administration console
- WCF-Custom port, creating
- migration
ms.assetid: fb057bce-5702-4ea0-8ed5-e299d3a78a11
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1783e56891ffd6d5d27058eab1df8a60663f481b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console"></a><span data-ttu-id="87175-102">Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="87175-102">Step 2: Configure the Orchestration in BizTalk Server Administration Console</span></span>
<span data-ttu-id="87175-103">![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="87175-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="87175-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="87175-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="87175-105">**Objectif :** dans cette étape, vous effectuez les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="87175-105">**Objective:** In this step, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="87175-106">Créer un WCF-Custom envoi-port de réception pour envoyer et recevoir des messages du système SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="87175-106">Create a WCF-Custom send-receive port to send and receive messages from the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="87175-107">Configurer ce port pour utiliser les mappages que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="87175-107">Configure this port to use the maps that you created in the previous step.</span></span>  
  
-   <span data-ttu-id="87175-108">Configurer l’orchestration vous avez déployé dans la dernière étape pour utiliser le port WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="87175-108">Configure the orchestration you deployed in the last step to use the WCF-Custom port.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="87175-109">Condition préalable</span><span class="sxs-lookup"><span data-stu-id="87175-109">Prerequisite</span></span>  
  
-   <span data-ttu-id="87175-110">Déployez l’orchestration de BizTalk pour laquelle vous souhaitez configurer le port WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="87175-110">Deploy the BizTalk orchestration for which you want to configure the WCF-Custom port.</span></span>  
  
### <a name="to-create-a-wcf-custom-port"></a><span data-ttu-id="87175-111">Pour créer un port personnalisé WCF</span><span class="sxs-lookup"><span data-stu-id="87175-111">To create a WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="87175-112">Lorsque vous générez le schéma pour un RFC en utilisant le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], un fichier de liaison est également ajouté au projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="87175-112">When you generate schema for an RFC using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], a binding file is also added to the BizTalk project.</span></span> <span data-ttu-id="87175-113">Vous pouvez importer ce fichier de liaison dans votre BizTalk application pour créer un WCF-Custom envoi-port de réception.</span><span class="sxs-lookup"><span data-stu-id="87175-113">You can import this binding file into your BizTalk application to create a WCF-Custom send-receive port.</span></span> <span data-ttu-id="87175-114">Pour obtenir des instructions sur l’importation d’un fichier de liaison, consultez [l’importation des liaisons](http://msdn.microsoft.com/library/c927efde-29bd-4efe-9da5-942e7da65dbf).</span><span class="sxs-lookup"><span data-stu-id="87175-114">For instructions on importing a binding file, see [Importing Bindings](http://msdn.microsoft.com/library/c927efde-29bd-4efe-9da5-942e7da65dbf).</span></span>  
  
2.  <span data-ttu-id="87175-115">Après avoir importé le fichier de liaison, un port d’envoi est créé sous le **Ports d’envoi** dossier dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="87175-115">After you import the binding file, a send port is created under the **Send Ports** folder in the BizTalk Server Administration console.</span></span>  
  
3.  <span data-ttu-id="87175-116">Cliquez sur le port WCF-Custom, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="87175-116">Right-click the WCF-Custom port, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="87175-117">Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur le **général** onglet. Dans le volet droit, cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="87175-117">From the left pane of the send port properties dialog box, click the **General** tab. From the right pane, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="87175-118">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet et spécifier les informations d’identification pour se connecter à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="87175-118">In the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab, and specify the credentials to connect to an SAP system.</span></span>  
  
6.  <span data-ttu-id="87175-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="87175-119">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="87175-120">Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages entrants**.</span><span class="sxs-lookup"><span data-stu-id="87175-120">From the left pane of the send port properties dialog box, click **Inbound Maps**.</span></span> <span data-ttu-id="87175-121">Dans le volet droit, cliquez sur le champ sous le **carte** colonne, puis, dans la liste déroulante, sélectionnez **ResponseMap**.</span><span class="sxs-lookup"><span data-stu-id="87175-121">From the right pane, click the field under the **Map** column, and from the drop-down, select **ResponseMap**.</span></span>  
  
     <span data-ttu-id="87175-122">![Configurer le mappage entrant sur le port WCF personnalisé](../../adapters-and-accelerators/adapter-sap/media/10129a7d-211b-464b-b05a-b3ea72f46873.gif "10129a7d-211b-464b-b05a-b3ea72f46873")</span><span class="sxs-lookup"><span data-stu-id="87175-122">![Configure the inbound map on the WCF custom port](../../adapters-and-accelerators/adapter-sap/media/10129a7d-211b-464b-b05a-b3ea72f46873.gif "10129a7d-211b-464b-b05a-b3ea72f46873")</span></span>  
  
8.  <span data-ttu-id="87175-123">Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **les mappages sortants.**</span><span class="sxs-lookup"><span data-stu-id="87175-123">From the left pane of the send port properties dialog box, click **Outbound Maps.**</span></span> <span data-ttu-id="87175-124">Dans le volet droit, cliquez sur le champ sous le **carte** colonne, puis, dans la liste déroulante, sélectionnez **RequestMap**.</span><span class="sxs-lookup"><span data-stu-id="87175-124">From the right pane, click the field under the **Map** column, and from the drop-down, select **RequestMap**.</span></span>  
  
     <span data-ttu-id="87175-125">![Configurer le mappage sortant sur le port WCF personnalisé](../../adapters-and-accelerators/adapter-sap/media/4ffcb4cd-4f53-4b67-92e2-3225d15d97ee.gif "4ffcb4cd-4f53-4b67-92e2-3225d15d97ee")</span><span class="sxs-lookup"><span data-stu-id="87175-125">![Configure the outbound map on the WCF custom port](../../adapters-and-accelerators/adapter-sap/media/4ffcb4cd-4f53-4b67-92e2-3225d15d97ee.gif "4ffcb4cd-4f53-4b67-92e2-3225d15d97ee")</span></span>  
  
9. <span data-ttu-id="87175-126">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="87175-126">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="87175-127">Pour configurer l’application BizTalk</span><span class="sxs-lookup"><span data-stu-id="87175-127">To configure the BizTalk application</span></span>  
  
1.  <span data-ttu-id="87175-128">Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez l’Application BizTalk où l’orchestration est déployée.</span><span class="sxs-lookup"><span data-stu-id="87175-128">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and then expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2.  <span data-ttu-id="87175-129">Cliquez sur l’application BizTalk, puis sélectionnez **configurer**.</span><span class="sxs-lookup"><span data-stu-id="87175-129">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3.  <span data-ttu-id="87175-130">Dans le volet gauche, cliquez sur l’orchestration à configurer.</span><span class="sxs-lookup"><span data-stu-id="87175-130">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="87175-131">Dans le volet droit, à partir de la **hôte** liste déroulante, sélectionnez une instance d’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="87175-131">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4.  <span data-ttu-id="87175-132">Sous le **liaisons** zone, mapper les ports logiques de l’orchestration BizTalk pour les ports physiques dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="87175-132">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the BizTalk Server Administration console.</span></span>  
  
    1.  <span data-ttu-id="87175-133">Sélectionnez le port de fichier dans lequel vous allez déposer un message de demande.</span><span class="sxs-lookup"><span data-stu-id="87175-133">Select the file port where you will drop a request message.</span></span> <span data-ttu-id="87175-134">L’orchestration BizTalk consommer le message de demande et l’envoyer au système SAP.</span><span class="sxs-lookup"><span data-stu-id="87175-134">The BizTalk orchestration will consume the request message and send it to the SAP system.</span></span>  
  
    2.  <span data-ttu-id="87175-135">Sélectionnez le port de fichier dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse du système SAP.</span><span class="sxs-lookup"><span data-stu-id="87175-135">Select the file port where the BizTalk orchestration will drop the response message containing the response from the SAP system.</span></span>  
  
    3.  <span data-ttu-id="87175-136">Sélectionnez le port d’envoi WCF-custom que vous avez créé précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="87175-136">Select the WCF-custom send port you created earlier in this topic.</span></span>  
  
    4.  <span data-ttu-id="87175-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="87175-137">Click **OK**.</span></span>  
  
     <span data-ttu-id="87175-138">Pour plus d’informations sur la configuration d’une application, consultez « Configuration d’une Application » à [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).</span><span class="sxs-lookup"><span data-stu-id="87175-138">For more information about configuring an application, see "How to Configure an Application" at [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="87175-139">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="87175-139">Next Steps</span></span>  
 <span data-ttu-id="87175-140">Vous avez maintenant terminé la migration de votre projet BizTalk de vPrev à un projet BizTalk qui envoie des messages au système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="87175-140">You have now completed migration of your vPrev BizTalk project to a BizTalk project that sends messages to the SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="87175-141">Vous devez maintenant tester l’application migrée de BizTalk en envoyant un message de demande pour appeler le RFC SD_RFC_CUSTOMER_GET, comme décrit dans [étape 3 : tester l’Application migrée](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application6.md).</span><span class="sxs-lookup"><span data-stu-id="87175-141">You must now test the migrated BizTalk application by sending a request message to invoke the SD_RFC_CUSTOMER_GET RFC, as described in [Step 3: Test the Migrated Application](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application6.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87175-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87175-142">See Also</span></span>  
 [<span data-ttu-id="87175-143">Didacticiel 2 : Migration d’un projet BizTalk RFC SAP</span><span class="sxs-lookup"><span data-stu-id="87175-143">Tutorial 2: Migrating an SAP RFC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-2-migrating-an-sap-rfc-biztalk-project.md)