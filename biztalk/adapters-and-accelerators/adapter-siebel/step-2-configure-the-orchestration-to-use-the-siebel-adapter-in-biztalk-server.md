---
title: "Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41338723-055d-46b4-acee-6969ea79fac0
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa0ed6c6609ccca3d13ea0eba46f9e2d0ee6cc14
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console-with-the-siebel-adapter"></a><span data-ttu-id="691ae-102">Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="691ae-102">Step 2: Configure the Orchestration in BizTalk Server Administration Console with the Siebel adapter</span></span>
<span data-ttu-id="691ae-103">![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="691ae-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="691ae-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="691ae-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="691ae-105">**Objectif :** dans cette étape, vous effectuez les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="691ae-105">**Objective:** In this step, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="691ae-106">Créer un WCF-Custom envoi-port de réception pour envoyer et recevoir des messages du système Siebel à l’aide du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="691ae-106">Create a WCF-Custom send-receive port to send and receive messages from the Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="691ae-107">Configurer ce port pour utiliser les mappages que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="691ae-107">Configure this port to use the maps you created in the previous step.</span></span>  
  
-   <span data-ttu-id="691ae-108">Configurer l’orchestration vous avez déployé dans la dernière étape pour utiliser le port WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="691ae-108">Configure the orchestration you deployed in the last step to use the WCF-Custom port.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="691ae-109">Condition préalable</span><span class="sxs-lookup"><span data-stu-id="691ae-109">Prerequisite</span></span>  
  
-   <span data-ttu-id="691ae-110">Vous devez avoir déployé l’orchestration BizTalk pour laquelle vous souhaitez configurer le port WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="691ae-110">You must have deployed the BizTalk orchestration for which you want to configure the WCF-Custom port.</span></span>  
  
### <a name="to-create-a-wcf-custom-port"></a><span data-ttu-id="691ae-111">Pour créer un port personnalisé WCF</span><span class="sxs-lookup"><span data-stu-id="691ae-111">To create a WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="691ae-112">Lorsque vous générez le schéma pour une opération sur le système Siebel en utilisant [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], un fichier de liaison est également ajouté au projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="691ae-112">When you generate schema for an operation on the Siebel system using [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], a binding file is also added to the BizTalk project.</span></span> <span data-ttu-id="691ae-113">Vous pouvez importer ce fichier de liaison dans votre BizTalk application pour créer un WCF-Custom envoi-port de réception.</span><span class="sxs-lookup"><span data-stu-id="691ae-113">You can import this binding file into your BizTalk application to create a WCF-Custom send-receive port.</span></span> <span data-ttu-id="691ae-114">Pour obtenir des instructions sur l’importation d’un fichier de liaison, consultez [l’importation des liaisons](http://msdn.microsoft.com/library/908ab90c-2ba2-4c65-9f74-10579f06e372).</span><span class="sxs-lookup"><span data-stu-id="691ae-114">For instructions on importing a binding file, see [Importing Bindings](http://msdn.microsoft.com/library/908ab90c-2ba2-4c65-9f74-10579f06e372).</span></span>  
  
2.  <span data-ttu-id="691ae-115">Après avoir importé le fichier de liaison, un port d’envoi est créé sous le **Ports d’envoi** dossier dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="691ae-115">After you import the binding file, a send port is created under the **Send Ports** folder in the BizTalk Server Administration console.</span></span>  
  
3.  <span data-ttu-id="691ae-116">Cliquez sur le port WCF-Custom, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="691ae-116">Right-click the WCF-Custom port, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="691ae-117">Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur le **général** onglet. Dans le volet droit, cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="691ae-117">From the left pane of the send port properties dialog box, click the **General** tab. From the right pane, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="691ae-118">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet et spécifier les informations d’identification pour se connecter à un système Siebel.</span><span class="sxs-lookup"><span data-stu-id="691ae-118">In the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and specify the credentials to connect to a Siebel system.</span></span>  
  
6.  <span data-ttu-id="691ae-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="691ae-119">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="691ae-120">Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages entrants**.</span><span class="sxs-lookup"><span data-stu-id="691ae-120">From the left pane of the send port properties dialog box, click **Inbound Maps**.</span></span> <span data-ttu-id="691ae-121">Dans le volet droit, cliquez sur le champ sous le **carte** colonne et à partir de la liste déroulante, sélectionnez **ResponseMap**.</span><span class="sxs-lookup"><span data-stu-id="691ae-121">From the right pane, click the field under the **Map** column, and from the drop-down select **ResponseMap**.</span></span>  
  
     <span data-ttu-id="691ae-122">![Configurer le mappage entrant](../../adapters-and-accelerators/adapter-siebel/media/e1ceee98-9f10-40f1-a611-88d3a2c102a9.gif "e1ceee98-9f10-40f1-a611-88d3a2c102a9")</span><span class="sxs-lookup"><span data-stu-id="691ae-122">![Configure inbound map](../../adapters-and-accelerators/adapter-siebel/media/e1ceee98-9f10-40f1-a611-88d3a2c102a9.gif "e1ceee98-9f10-40f1-a611-88d3a2c102a9")</span></span>  
  
8.  <span data-ttu-id="691ae-123">Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages sortants**.</span><span class="sxs-lookup"><span data-stu-id="691ae-123">From the left pane of the send port properties dialog box, click **Outbound Maps**.</span></span> <span data-ttu-id="691ae-124">Dans le volet droit, cliquez sur le champ sous le **carte** colonne et à partir de la liste déroulante, sélectionnez **RequestMap**.</span><span class="sxs-lookup"><span data-stu-id="691ae-124">From the right pane, click the field under the **Map** column, and from the drop-down select **RequestMap**.</span></span>  
  
     <span data-ttu-id="691ae-125">![Configurer le mappage sortant](../../adapters-and-accelerators/adapter-siebel/media/8f8efeaa-d5cd-4ed3-b2f3-a600c48c3bb9.gif "8f8efeaa-d5cd-4ed3-b2f3-a600c48c3bb9")</span><span class="sxs-lookup"><span data-stu-id="691ae-125">![Configure outbound map](../../adapters-and-accelerators/adapter-siebel/media/8f8efeaa-d5cd-4ed3-b2f3-a600c48c3bb9.gif "8f8efeaa-d5cd-4ed3-b2f3-a600c48c3bb9")</span></span>  
  
9. <span data-ttu-id="691ae-126">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="691ae-126">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="691ae-127">Pour configurer l’application BizTalk</span><span class="sxs-lookup"><span data-stu-id="691ae-127">To configure the BizTalk application</span></span>  
  
1.  <span data-ttu-id="691ae-128">Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, développez l’Application BizTalk où l’orchestration est déployée.</span><span class="sxs-lookup"><span data-stu-id="691ae-128">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2.  <span data-ttu-id="691ae-129">Cliquez sur l’application BizTalk, puis sélectionnez **configurer**.</span><span class="sxs-lookup"><span data-stu-id="691ae-129">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3.  <span data-ttu-id="691ae-130">Dans le volet gauche, cliquez sur l’orchestration à configurer.</span><span class="sxs-lookup"><span data-stu-id="691ae-130">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="691ae-131">Dans le volet droit, à partir de la **hôte** liste déroulante, sélectionnez une instance d’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="691ae-131">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4.  <span data-ttu-id="691ae-132">Sous le **liaisons** zone, mapper les ports logiques de l’orchestration BizTalk pour les ports physiques dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="691ae-132">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the BizTalk Server Administration console.</span></span>  
  
    1.  <span data-ttu-id="691ae-133">Sélectionnez le port de fichier dans lequel vous allez déposer un message de demande.</span><span class="sxs-lookup"><span data-stu-id="691ae-133">Select the file port where you will drop a request message.</span></span> <span data-ttu-id="691ae-134">L’orchestration BizTalk consommer le message de demande et l’envoyer au système Siebel.</span><span class="sxs-lookup"><span data-stu-id="691ae-134">The BizTalk orchestration will consume the request message and send it to the Siebel system.</span></span>  
  
    2.  <span data-ttu-id="691ae-135">Sélectionnez le port de fichier dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à partir du système Siebel.</span><span class="sxs-lookup"><span data-stu-id="691ae-135">Select the file port where the BizTalk orchestration will drop the response message containing the response from the Siebel system.</span></span>  
  
    3.  <span data-ttu-id="691ae-136">Sélectionnez le port d’envoi WCF-Custom que vous avez créé précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="691ae-136">Select the WCF-Custom send port you created earlier in this topic.</span></span>  
  
    4.  <span data-ttu-id="691ae-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="691ae-137">Click **OK**.</span></span>  
  
     <span data-ttu-id="691ae-138">Pour plus d’informations sur la configuration d’une application, consultez « Configuration d’une Application » à [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).</span><span class="sxs-lookup"><span data-stu-id="691ae-138">For more information about configuring an application, see "How to Configure an Application" at [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="691ae-139">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="691ae-139">Next Steps</span></span>  
 <span data-ttu-id="691ae-140">Vous avez maintenant terminé la migration de votre projet BizTalk de vPrev à un projet BizTalk qui envoie des messages au système Siebel à l’aide de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="691ae-140">You have now completed migration of your vPrev BizTalk project to a BizTalk project that sends messages to the Siebel system using the WCF-based [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="691ae-141">Vous devez maintenant tester l’application migrée de BizTalk en envoyant un message de demande pour appeler l’opération d’insertion sur le composant de gestion de compte, comme décrit dans [étape 3 : tester l’Application migrée avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-test-the-migrated-application-with-the-siebel-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="691ae-141">You must now test the migrated BizTalk application by sending a request message to invoke the Insert operation on the Account business component, as described in [Step 3: Test the Migrated Application with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/step-3-test-the-migrated-application-with-the-siebel-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691ae-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="691ae-142">See Also</span></span>  
 [<span data-ttu-id="691ae-143">Didacticiel 2 : Migration des projets BizTalk dans Siebel</span><span class="sxs-lookup"><span data-stu-id="691ae-143">Tutorial 2: Migrating BizTalk Projects in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/tutorial-2-migrating-biztalk-projects-in-siebel.md)