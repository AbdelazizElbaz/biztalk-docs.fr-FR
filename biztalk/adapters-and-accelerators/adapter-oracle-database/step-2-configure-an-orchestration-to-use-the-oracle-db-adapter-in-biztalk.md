---
title: "Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server pour utiliser l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 598b4ab0-ff22-4dfa-aa9c-774c60c90227
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b348a21a54ece0e5db736e18f60c9bed2b8d047d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console-to-use-the-oracle-database-adapter"></a><span data-ttu-id="cd61c-102">Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server pour utiliser l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="cd61c-102">Step 2: Configure the Orchestration in BizTalk Server Administration Console to use the Oracle Database adapter</span></span>
<span data-ttu-id="cd61c-103">![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="cd61c-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="cd61c-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="cd61c-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="cd61c-105">**Objectif :** dans cette étape, vous effectuez les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="cd61c-105">**Objective:** In this step, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="cd61c-106">Créer un WCF-Custom envoi-port de réception pour envoyer et recevoir des messages à partir de la base de données Oracle à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd61c-106">Create a WCF-Custom send-receive port to send and receive messages from the Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="cd61c-107">Configurer ce port pour utiliser les mappages que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="cd61c-107">Configure this port to use the maps you created in the previous step.</span></span>  
  
-   <span data-ttu-id="cd61c-108">Configurer l’orchestration vous avez déployé dans la dernière étape pour utiliser le port WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="cd61c-108">Configure the orchestration you deployed in the last step to use the WCF-Custom port.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="cd61c-109">Condition préalable</span><span class="sxs-lookup"><span data-stu-id="cd61c-109">Prerequisite</span></span>  
  
-   <span data-ttu-id="cd61c-110">Vous devez avoir déployé l’orchestration BizTalk pour laquelle vous souhaitez configurer le port WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="cd61c-110">You must have deployed the BizTalk orchestration for which you want to configure the WCF-Custom port.</span></span>  
  
### <a name="to-create-a-wcf-custom-port"></a><span data-ttu-id="cd61c-111">Pour créer un port personnalisé WCF</span><span class="sxs-lookup"><span data-stu-id="cd61c-111">To create a WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="cd61c-112">Lorsque vous générez le schéma pour une opération sur la base de données Oracle à l’aide [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], un fichier de liaison est également ajouté au projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="cd61c-112">When you generate schema for an operation on the Oracle database using [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], a binding file is also added to the BizTalk project.</span></span> <span data-ttu-id="cd61c-113">Vous pouvez importer ce fichier de liaison dans votre BizTalk application pour créer un WCF-Custom envoi-port de réception.</span><span class="sxs-lookup"><span data-stu-id="cd61c-113">You can import this binding file into your BizTalk application to create a WCF-Custom send-receive port.</span></span> <span data-ttu-id="cd61c-114">Pour obtenir des instructions sur l’importation d’un fichier de liaison, consultez [l’importation des liaisons](http://msdn.microsoft.com/library/4cac9267-8bd8-453b-96b4-5c038912463f).</span><span class="sxs-lookup"><span data-stu-id="cd61c-114">For instructions on importing a binding file, see [Importing Bindings](http://msdn.microsoft.com/library/4cac9267-8bd8-453b-96b4-5c038912463f).</span></span>  
  
2.  <span data-ttu-id="cd61c-115">Après avoir importé le fichier de liaison, un port d’envoi est créé sous le **Ports d’envoi** dossier dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="cd61c-115">After you import the binding file, a send port is created under the **Send Ports** folder in the BizTalk Server Administration console.</span></span>  
  
3.  <span data-ttu-id="cd61c-116">Cliquez sur le port WCF-Custom, sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="cd61c-116">Right-click the WCF-Custom port and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="cd61c-117">Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur le **général** onglet. Dans le volet droit, cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="cd61c-117">From the left pane of the send port properties dialog box, click the **General** tab. From the right pane, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="cd61c-118">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet et spécifier les informations d’identification pour se connecter à une base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="cd61c-118">In the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab, and specify the credentials to connect to an Oracle database.</span></span>  
  
6.  <span data-ttu-id="cd61c-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cd61c-119">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="cd61c-120">Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages entrants**.</span><span class="sxs-lookup"><span data-stu-id="cd61c-120">From the left pane of the send port properties dialog box, click **Inbound Maps**.</span></span> <span data-ttu-id="cd61c-121">Dans le volet droit, cliquez sur le champ sous le **carte** colonne et à partir de la liste déroulante, sélectionnez **ResponseMap**.</span><span class="sxs-lookup"><span data-stu-id="cd61c-121">From the right pane, click the field under the **Map** column, and from the drop-down select **ResponseMap**.</span></span>  
  
     <span data-ttu-id="cd61c-122">![Configurer le mappage entrant](../../adapters-and-accelerators/adapter-oracle-database/media/a5e49da1-fe34-46fe-80ca-9316d217171a.gif "a5e49da1-fe34-46fe-80ca-9316d217171a")</span><span class="sxs-lookup"><span data-stu-id="cd61c-122">![Configure inbound map](../../adapters-and-accelerators/adapter-oracle-database/media/a5e49da1-fe34-46fe-80ca-9316d217171a.gif "a5e49da1-fe34-46fe-80ca-9316d217171a")</span></span>  
  
8.  <span data-ttu-id="cd61c-123">Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages sortants**.</span><span class="sxs-lookup"><span data-stu-id="cd61c-123">From the left pane of the send port properties dialog box, click **Outbound Maps**.</span></span> <span data-ttu-id="cd61c-124">Dans le volet droit, cliquez sur le champ sous le **carte** colonne et à partir de la liste déroulante, sélectionnez **RequestMap**.</span><span class="sxs-lookup"><span data-stu-id="cd61c-124">From the right pane, click the field under the **Map** column, and from the drop-down select **RequestMap**.</span></span>  
  
     <span data-ttu-id="cd61c-125">![Configurer le mappage sortant](../../adapters-and-accelerators/adapter-oracle-database/media/697b23d8-4231-4718-8a52-8013fac35e3e.gif "697b23d8-4231-4718-8a52-8013fac35e3e")</span><span class="sxs-lookup"><span data-stu-id="cd61c-125">![Configure outbound map](../../adapters-and-accelerators/adapter-oracle-database/media/697b23d8-4231-4718-8a52-8013fac35e3e.gif "697b23d8-4231-4718-8a52-8013fac35e3e")</span></span>  
  
9. <span data-ttu-id="cd61c-126">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cd61c-126">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="cd61c-127">Pour configurer l’application BizTalk</span><span class="sxs-lookup"><span data-stu-id="cd61c-127">To configure the BizTalk application</span></span>  
  
1.  <span data-ttu-id="cd61c-128">Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, développez l’Application BizTalk où l’orchestration est déployée.</span><span class="sxs-lookup"><span data-stu-id="cd61c-128">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2.  <span data-ttu-id="cd61c-129">Cliquez sur l’application BizTalk, puis sélectionnez **configurer**.</span><span class="sxs-lookup"><span data-stu-id="cd61c-129">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3.  <span data-ttu-id="cd61c-130">Dans le volet gauche, cliquez sur l’orchestration à configurer.</span><span class="sxs-lookup"><span data-stu-id="cd61c-130">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="cd61c-131">Dans le volet droit, à partir de la **hôte** liste déroulante, sélectionnez une instance d’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="cd61c-131">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4.  <span data-ttu-id="cd61c-132">Sous le **liaisons** zone, mapper les ports logiques de l’orchestration BizTalk pour les ports physiques dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="cd61c-132">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the BizTalk Server Administration console.</span></span>  
  
    1.  <span data-ttu-id="cd61c-133">Sélectionnez le port de fichier dans lequel vous allez déposer un message de demande.</span><span class="sxs-lookup"><span data-stu-id="cd61c-133">Select the file port where you will drop a request message.</span></span> <span data-ttu-id="cd61c-134">L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="cd61c-134">The BizTalk orchestration will consume the request message and send it to the Oracle database.</span></span>  
  
    2.  <span data-ttu-id="cd61c-135">Sélectionnez le port de fichier dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="cd61c-135">Select the file port where the BizTalk orchestration will drop the response message containing the response from the Oracle database.</span></span>  
  
    3.  <span data-ttu-id="cd61c-136">Sélectionnez le port d’envoi WCF-Custom que vous avez créé précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="cd61c-136">Select the WCF-Custom send port you created earlier in this topic.</span></span>  
  
    4.  <span data-ttu-id="cd61c-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cd61c-137">Click **OK**.</span></span>  
  
     <span data-ttu-id="cd61c-138">Pour plus d’informations sur la configuration d’une application, consultez « Configuration d’une Application » à [http://go.microsoft.com/fwlink/?LinkID=196961](http://go.microsoft.com/fwlink/?LinkID=196961).</span><span class="sxs-lookup"><span data-stu-id="cd61c-138">For more information about configuring an application, see "How to Configure an Application" at [http://go.microsoft.com/fwlink/?LinkID=196961](http://go.microsoft.com/fwlink/?LinkID=196961).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="cd61c-139">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="cd61c-139">Next Steps</span></span>  
 <span data-ttu-id="cd61c-140">Vous avez maintenant terminé la migration de votre projet BizTalk de vPrev à un projet BizTalk qui envoie des messages à la base de données Oracle à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd61c-140">You have now completed migration of your vPrev BizTalk project to a BizTalk project that sends messages to the Oracle database using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="cd61c-141">Vous devez maintenant tester l’application migrée de BizTalk en envoyant un message de demande pour effectuer une opération d’insertion sur la base de données Oracle, comme décrit dans [étape 3 : tester l’application migrée à l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/step-3-test-the-migrated-application-to-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="cd61c-141">You must now test the migrated BizTalk application by sending a request message to perform an Insert operation on the Oracle database, as described in [Step 3: Test the migrated application to Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/step-3-test-the-migrated-application-to-oracle-database-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd61c-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd61c-142">See Also</span></span>  
 <span data-ttu-id="cd61c-143">[Didacticiel : Migration des projets BizTalk](https://msdn.microsoft.com/library/dd788186(v=bts.80).aspx)</span><span class="sxs-lookup"><span data-stu-id="cd61c-143">[Tutorial: Migrating BizTalk Projects](https://msdn.microsoft.com/library/dd788186(v=bts.80).aspx)</span></span>