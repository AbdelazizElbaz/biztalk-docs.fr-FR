---
title: "En cours d’exécution Orchestrations2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong name keys, creating
- orchestrations
- creating strong name keys
- compiling orchestrations
- host instances, stopping and restarting
- deployment, orchestrations
- orchestrations, compiling
- orchestrations, deploying
- stopping host instances
- restarting host instances
ms.assetid: a098d552-d302-44f6-9af9-d77d16549fd3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55d8e16b7af574a73dc8fc813c29ecd5917ce4d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-orchestrations"></a><span data-ttu-id="7387f-102">Orchestrations en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="7387f-102">Running Orchestrations</span></span>
<span data-ttu-id="7387f-103">Les procédures suivantes expliquent comment construire, déployer, lier et démarrer une orchestration.</span><span class="sxs-lookup"><span data-stu-id="7387f-103">The following procedures describe how to build, deploy, bind, and start an orchestration.</span></span>  
  
## <a name="creating-a-strong-name-key"></a><span data-ttu-id="7387f-104">Création d'une clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="7387f-104">Creating a Strong Name Key</span></span>  
  
#### <a name="to-create-a-strong-name-key"></a><span data-ttu-id="7387f-105">Pour créer une clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="7387f-105">To create a strong name key</span></span>  
  
1.  <span data-ttu-id="7387f-106">Ouvrir un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="7387f-106">Open a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt.</span></span>  
  
2.  <span data-ttu-id="7387f-107">Accédez aux répertoires d'un projet existant, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="7387f-107">Change directories to an existing project and press ENTER.</span></span>  
  
     <span data-ttu-id="7387f-108">Exemple :</span><span class="sxs-lookup"><span data-stu-id="7387f-108">For example:</span></span>  
  
     <span data-ttu-id="7387f-109">**\<lecteur > : \Adapter_Install\biztalk\my_project**</span><span class="sxs-lookup"><span data-stu-id="7387f-109">**\<drive>:\Adapter_Install\biztalk\my_project**</span></span>  
  
3.  <span data-ttu-id="7387f-110">Tapez ce qui suit à l'invite de commandes, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="7387f-110">Type the following at the command prompt and press ENTER:</span></span>  
  
     `sn -k SSOSchedule.snk`  
  
## <a name="compiling-and-deploying-an-orchestration"></a><span data-ttu-id="7387f-111">Compilation et déploiement d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="7387f-111">Compiling and Deploying an Orchestration</span></span>  
  
#### <a name="to-compile-and-deploy-an-orchestration"></a><span data-ttu-id="7387f-112">Pour compiler et déployer une orchestration</span><span class="sxs-lookup"><span data-stu-id="7387f-112">To compile and deploy an orchestration</span></span>  
  
1.  <span data-ttu-id="7387f-113">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Explorateur de solutions, cliquez sur le **SSOSchedule** le projet, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7387f-113">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click the **SSOSchedule** project, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="7387f-114">Cliquez sur **propriétés communes**, puis développez le **Assembly** nœud.</span><span class="sxs-lookup"><span data-stu-id="7387f-114">Click **Common Properties**, and expand the **Assembly** node.</span></span>  
  
3.  <span data-ttu-id="7387f-115">Entrez le chemin d’accès à SSOSchedule.snk dans les **fichier de clé d’Assembly** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="7387f-115">Enter the path to SSOSchedule.snk in the **Assembly Key File** text box.</span></span>  
  
4.  <span data-ttu-id="7387f-116">Vérifiez que configuration\déploiement\serveur est un point (.) ou le nom de votre ordinateur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7387f-116">Verify that Configuration Properties\Deployment\Server is a dot (.) or your computer name, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="7387f-117">Dans l’Explorateur de solutions, cliquez sur **SSOSchedule**, puis cliquez sur **reconstruire**.</span><span class="sxs-lookup"><span data-stu-id="7387f-117">In Solution Explorer, right-click **SSOSchedule**, and then click **Rebuild**.</span></span>  
  
6.  <span data-ttu-id="7387f-118">Avec le bouton droit **SSOSchedule**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="7387f-118">Right-click **SSOSchedule**, and then click **Deploy**.</span></span>  
  
## <a name="starting-the-orchestration"></a><span data-ttu-id="7387f-119">Démarrage de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="7387f-119">Starting the Orchestration</span></span>  
  
#### <a name="to-start-the-orchestration"></a><span data-ttu-id="7387f-120">Pour démarrer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="7387f-120">To start the orchestration</span></span>  
  
1.  <span data-ttu-id="7387f-121">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="7387f-121">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration.**</span></span>  
  
2.  <span data-ttu-id="7387f-122">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez l’élément application, puis sur **Orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="7387f-122">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand the desired application, and then click **Orchestrations**.</span></span>  
  
3.  <span data-ttu-id="7387f-123">Dans le volet de détails, cliquez sur l’orchestration, sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="7387f-123">In the details pane, right-click the orchestration and click **Start**.</span></span>  
  
## <a name="stopping-and-restarting-a-host-instance"></a><span data-ttu-id="7387f-124">Arrêt et redémarrage d'une instance de l'hôte</span><span class="sxs-lookup"><span data-stu-id="7387f-124">Stopping and Restarting a Host Instance</span></span>  
 <span data-ttu-id="7387f-125">Une l'exemple déployé, vous devez redémarrer l'instance de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="7387f-125">After you deploy the sample, you must restart the host instance.</span></span>  
  
#### <a name="to-stop-and-restart-a-host-instance"></a><span data-ttu-id="7387f-126">Pour arrêter et redémarrer une instance de l'hôte</span><span class="sxs-lookup"><span data-stu-id="7387f-126">To stop and restart a host instance</span></span>  
  
1.  <span data-ttu-id="7387f-127">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="7387f-127">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration.**</span></span>  
  
2.  <span data-ttu-id="7387f-128">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur  **Instances de l’hôte**.</span><span class="sxs-lookup"><span data-stu-id="7387f-128">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="7387f-129">Dans le volet droit, cliquez sur l’instance d’hôte (par exemple, le nom d’ordinateur), puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="7387f-129">In the right pane, right-click the host instance (for example, the computer name), and click **Stop**.</span></span>  
  
     <span data-ttu-id="7387f-130">L’état de l’instance d’hôte devient **arrêté**.</span><span class="sxs-lookup"><span data-stu-id="7387f-130">The status of the host instance changes to **Stopped**.</span></span>  
  
4.  <span data-ttu-id="7387f-131">Dans le volet droit, cliquez sur l’instance d’hôte, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="7387f-131">In the right pane, right-click the host instance and click **Start**.</span></span>  
  
     <span data-ttu-id="7387f-132">L’état de l’instance d’hôte devient **attente de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="7387f-132">The status of the host instance changes to **Start pending**.</span></span>  
  
     <span data-ttu-id="7387f-133">Pour modifier l’état à **en cours d’exécution** et cliquez sur **Actualiser**, ou cliquez sur l’instance d’hôte, puis cliquez **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="7387f-133">To change the status to **Running** and click **Refresh**, or right-click the host instance and then click **Refresh**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7387f-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7387f-134">See Also</span></span>  
 [<span data-ttu-id="7387f-135">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="7387f-135">Using Single Sign-On</span></span>](../core/using-single-sign-on2.md)