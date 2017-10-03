---
title: "Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6152560-5ff0-4bdc-818c-e906b9642f52
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b090ae83f0ca36bb4ae95795480d5f0d1661f16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console-using-the-sql-adapter"></a><span data-ttu-id="29145-102">Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server à l’aide de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="29145-102">Step 2: Configure the Orchestration in BizTalk Server Administration Console using the SQL adapter</span></span>
<span data-ttu-id="29145-103">![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="29145-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="29145-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="29145-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="29145-105">**Objectif :** dans cette étape, vous effectuez les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="29145-105">**Objective:** In this step, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="29145-106">Créer un WCF-Custom envoi-port de réception pour envoyer et recevoir des messages à partir de la base de données SQL Server à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="29145-106">Create a WCF-Custom send-receive port to send and receive messages from the SQL Server database using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="29145-107">Configurer ce port pour utiliser les mappages que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="29145-107">Configure this port to use the maps you created in the previous step.</span></span>  
  
-   <span data-ttu-id="29145-108">Configurer l’orchestration vous avez déployé à l’étape précédente pour utiliser le port WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="29145-108">Configure the orchestration you deployed in the previous step to use the WCF-Custom port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="29145-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="29145-109">Prerequisites</span></span>  
 <span data-ttu-id="29145-110">Doit avoir déployé l’orchestration BizTalk pour laquelle vous souhaitez configurer le port WCF-Custom, comme décrit dans [étape 1 : modifier le projet BizTalk à l’aide de l’adaptateur SQL vPrev](../../adapters-and-accelerators/adapter-sql/step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="29145-110">You should have deployed the BizTalk orchestration for which you want to configure the WCF-Custom port as described in [Step 1: Modify the vPrev BizTalk Project using the SQL adapter](../../adapters-and-accelerators/adapter-sql/step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter.md).</span></span>  
  
### <a name="to-create-a-wcf-custom-port"></a><span data-ttu-id="29145-111">Pour créer un port personnalisé WCF</span><span class="sxs-lookup"><span data-stu-id="29145-111">To create a WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="29145-112">Lorsque vous générez le schéma pour une opération sur la base de données SQL Server à l’aide [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], un fichier de liaison est également ajouté au projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="29145-112">When you generate schema for an operation on the SQL Server database using [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], a binding file is also added to the BizTalk project.</span></span> <span data-ttu-id="29145-113">Vous pouvez importer ce fichier de liaison dans votre BizTalk application pour créer un WCF-Custom envoi-port de réception.</span><span class="sxs-lookup"><span data-stu-id="29145-113">You can import this binding file into your BizTalk application to create a WCF-Custom send-receive port.</span></span> <span data-ttu-id="29145-114">Pour obtenir des instructions sur l’importation d’un fichier de liaison, consultez [l’importation des liaisons](http://msdn.microsoft.com/library/48de3a04-4ce8-4ba9-91b6-7e125689fd53).</span><span class="sxs-lookup"><span data-stu-id="29145-114">For instructions on importing a binding file, see [Importing Bindings](http://msdn.microsoft.com/library/48de3a04-4ce8-4ba9-91b6-7e125689fd53).</span></span>  
  
2.  <span data-ttu-id="29145-115">Après avoir importé le fichier de liaison, un port d’envoi est créé sous le **Ports d’envoi** dossier dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="29145-115">After you import the binding file, a send port is created under the **Send Ports** folder in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
3.  <span data-ttu-id="29145-116">Cliquez sur le port WCF-Custom, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="29145-116">Right-click the WCF-Custom port, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="29145-117">Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur le **général** onglet. Dans le volet droit, cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="29145-117">From the left pane of the send port properties dialog box, click the **General** tab. From the right pane, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="29145-118">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet, spécifiez les informations d’identification pour se connecter à une base de données SQL Server, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="29145-118">In the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab, specify the credentials to connect to a SQL Server database, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="29145-119">Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages entrants**.</span><span class="sxs-lookup"><span data-stu-id="29145-119">From the left pane of the send port properties dialog box, click **Inbound Maps**.</span></span> <span data-ttu-id="29145-120">Dans le volet droit, cliquez sur le champ sous le **carte** colonne et à partir de la liste déroulante, sélectionnez **ResponseMap**.</span><span class="sxs-lookup"><span data-stu-id="29145-120">From the right pane, click the field under the **Map** column, and from the drop-down select **ResponseMap**.</span></span>  
  
     <span data-ttu-id="29145-121">![Configurer le mappage entrant](../../adapters-and-accelerators/adapter-sql/media/21e5a23c-7319-4324-8f09-52118ebeeea9.gif "21e5a23c-7319-4324-8f09-52118ebeeea9")</span><span class="sxs-lookup"><span data-stu-id="29145-121">![Configure inbound map](../../adapters-and-accelerators/adapter-sql/media/21e5a23c-7319-4324-8f09-52118ebeeea9.gif "21e5a23c-7319-4324-8f09-52118ebeeea9")</span></span>  
  
7.  <span data-ttu-id="29145-122">Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages sortants**.</span><span class="sxs-lookup"><span data-stu-id="29145-122">From the left pane of the send port properties dialog box, click **Outbound Maps**.</span></span> <span data-ttu-id="29145-123">Dans le volet droit, cliquez sur le champ sous le **carte** colonne et à partir de la liste déroulante, sélectionnez **RequestMap**.</span><span class="sxs-lookup"><span data-stu-id="29145-123">From the right pane, click the field under the **Map** column, and from the drop-down select **RequestMap**.</span></span>  
  
     <span data-ttu-id="29145-124">![Configurer le mappage sortant](../../adapters-and-accelerators/adapter-sql/media/5b54e09b-8784-4df6-a279-e8aed813114e.gif "5b54e09b-8784-4df6-a279-e8aed813114e")</span><span class="sxs-lookup"><span data-stu-id="29145-124">![Configure outbound map](../../adapters-and-accelerators/adapter-sql/media/5b54e09b-8784-4df6-a279-e8aed813114e.gif "5b54e09b-8784-4df6-a279-e8aed813114e")</span></span>  
  
8.  <span data-ttu-id="29145-125">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="29145-125">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="29145-126">Pour configurer l’application BizTalk</span><span class="sxs-lookup"><span data-stu-id="29145-126">To configure the BizTalk application</span></span>  
  
1.  <span data-ttu-id="29145-127">Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez l’Application BizTalk où l’orchestration est déployée.</span><span class="sxs-lookup"><span data-stu-id="29145-127">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and then expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2.  <span data-ttu-id="29145-128">Cliquez sur l’application BizTalk, puis sélectionnez **configurer**.</span><span class="sxs-lookup"><span data-stu-id="29145-128">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3.  <span data-ttu-id="29145-129">Dans le volet gauche, cliquez sur l’orchestration à configurer.</span><span class="sxs-lookup"><span data-stu-id="29145-129">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="29145-130">Dans le volet droit, à partir de la **hôte** liste déroulante, sélectionnez une instance d’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="29145-130">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4.  <span data-ttu-id="29145-131">Sous le **liaisons** zone, mapper les ports logiques de l’orchestration BizTalk pour les ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="29145-131">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
    1.  <span data-ttu-id="29145-132">Sélectionnez le port de fichier dans lequel vous allez déposer un message de demande.</span><span class="sxs-lookup"><span data-stu-id="29145-132">Select the file port where you will drop a request message.</span></span> <span data-ttu-id="29145-133">L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="29145-133">The BizTalk orchestration will consume the request message and send it to the SQL Server database.</span></span>  
  
    2.  <span data-ttu-id="29145-134">Sélectionnez le port de fichier dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="29145-134">Select the file port where the BizTalk orchestration will drop the response message containing the response from the SQL Server database.</span></span>  
  
    3.  <span data-ttu-id="29145-135">Sélectionnez le port d’envoi WCF-Custom que vous avez créé précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="29145-135">Select the WCF-Custom send port you created earlier in this topic.</span></span>  
  
    4.  <span data-ttu-id="29145-136">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="29145-136">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="29145-137">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="29145-137">Next Steps</span></span>  
 <span data-ttu-id="29145-138">Vous avez maintenant terminé la migration de votre projet BizTalk de vPrev à un projet BizTalk qui envoie des messages à la base de données SQL Server à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="29145-138">You have now completed migration of your vPrev BizTalk project to a BizTalk project that sends messages to the SQL Server database using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="29145-139">Vous devez maintenant tester l’application migrée de BizTalk en envoyant un message de demande pour effectuer une opération d’insertion sur la base de données SQL Server, comme décrit dans [étape 3 : tester l’Application migrée qui utilise l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/step-3-test-the-migrated-application-that-uses-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="29145-139">You must now test the migrated BizTalk application by sending a request message to perform an Insert operation on the SQL Server database, as described in [Step 3: Test the Migrated Application that uses the SQL adapter](../../adapters-and-accelerators/adapter-sql/step-3-test-the-migrated-application-that-uses-the-sql-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29145-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29145-140">See Also</span></span>  
 [<span data-ttu-id="29145-141">Didacticiel 1 : Migrer des projets BizTalk à l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="29145-141">Tutorial 1: Migrate BizTalk Projects to the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/tutorial-1-migrate-biztalk-projects-to-the-sql-adapter.md)