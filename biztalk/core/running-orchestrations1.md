---
title: "En cours d’exécution Orchestrations1 | Documents Microsoft"
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
- host instances, stopping and restarting
- orchestrations, compiling
- orchestrations, deploying
ms.assetid: b992bdba-630d-4f28-aca8-c568f3c27968
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c215009d6b911831c74ac22b2c03ceae45e74a62
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="running-orchestrations"></a><span data-ttu-id="5123d-102">Orchestrations en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="5123d-102">Running Orchestrations</span></span>
<span data-ttu-id="5123d-103">Les procédures suivantes expliquent comment construire, déployer, lier et démarrer une orchestration.</span><span class="sxs-lookup"><span data-stu-id="5123d-103">The following procedures describe how to build, deploy, bind, and start an orchestration.</span></span>  
  
## <a name="creating-a-strong-name-key"></a><span data-ttu-id="5123d-104">Création d'une clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="5123d-104">Creating a Strong Name Key</span></span>  
  
#### <a name="to-create-a-strong-name-key"></a><span data-ttu-id="5123d-105">Pour créer une clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="5123d-105">To create a strong name key</span></span>  
  
1.  <span data-ttu-id="5123d-106">Démarrez une invite de commandes [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5123d-106">Start a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt.</span></span>  
  
2.  <span data-ttu-id="5123d-107">Accédez à un projet existant, par exemple, \<lecteur\>: \Adapter_Install\biztalk2010\my_project.</span><span class="sxs-lookup"><span data-stu-id="5123d-107">Change directories to an existing project, for example, \<drive\>:\Adapter_Install\biztalk2010\my_project.</span></span>  
  
3.  <span data-ttu-id="5123d-108">Tapez la commande suivante à l'invite, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="5123d-108">Type the following in the command prompt and press ENTER:</span></span>  
  
     `sn -k SSOSchedule.snk`  
  
## <a name="compiling-and-deploying-an-orchestration"></a><span data-ttu-id="5123d-109">Compilation et déploiement d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="5123d-109">Compiling and Deploying an Orchestration</span></span>  
  
#### <a name="to-compile-and-deploy-an-orchestration"></a><span data-ttu-id="5123d-110">Pour compiler et déployer une orchestration</span><span class="sxs-lookup"><span data-stu-id="5123d-110">To compile and deploy an orchestration</span></span>  
  
1.  <span data-ttu-id="5123d-111">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur le projet SSOSchedule, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5123d-111">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click the SSOSchedule project, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="5123d-112">Cliquez sur **propriétés communes**, puis développez le **Assembly** nœud.</span><span class="sxs-lookup"><span data-stu-id="5123d-112">Click **Common Properties**, and expand the **Assembly** node.</span></span>  
  
3.  <span data-ttu-id="5123d-113">Entrez le chemin d’accès à SSOSchedule.snk dans les **fichier de clé d’Assembly** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="5123d-113">Enter the path to SSOSchedule.snk in the **Assembly Key File** text box.</span></span>  
  
4.  <span data-ttu-id="5123d-114">Vérifiez que configuration\déploiement\serveur contient un point (.) ou le nom de votre ordinateur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5123d-114">Verify that Configuration Properties\Deployment\Server contains a dot (.) or your computer name, and click **OK**.</span></span>  
  
5.  <span data-ttu-id="5123d-115">Dans l’Explorateur de solutions, cliquez sur **SSOSchedule**, puis cliquez sur **reconstruire**.</span><span class="sxs-lookup"><span data-stu-id="5123d-115">In Solution Explorer, right-click **SSOSchedule**, and click **Rebuild**.</span></span>  
  
6.  <span data-ttu-id="5123d-116">Cliquez sur le **SSOSchedule**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="5123d-116">Right-click the **SSOSchedule**, and click **Deploy**.</span></span>  
  
## <a name="starting-the-orchestration"></a><span data-ttu-id="5123d-117">Démarrage de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="5123d-117">Starting the Orchestration</span></span>  
  
#### <a name="to-start-the-orchestration"></a><span data-ttu-id="5123d-118">Pour démarrer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="5123d-118">To start the orchestration</span></span>  
  
1.  <span data-ttu-id="5123d-119">Dans la console Administration de BizTalk Server, sélectionnez l'orchestration que vous souhaitez démarrer.</span><span class="sxs-lookup"><span data-stu-id="5123d-119">In the BizTalk Administration console, select the orchestration you want to start.</span></span>  
  
2.  <span data-ttu-id="5123d-120">Avec le bouton droit de l’orchestration, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="5123d-120">Right-click the orchestration and click **Start**.</span></span>  
  
## <a name="stopping-and-restarting-a-host-instance"></a><span data-ttu-id="5123d-121">Arrêt et redémarrage d'une instance de l'hôte</span><span class="sxs-lookup"><span data-stu-id="5123d-121">Stopping and Restarting a Host Instance</span></span>  
 <span data-ttu-id="5123d-122">Une fois l'exemple déployé, vous devez redémarrer l'instance de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="5123d-122">After deploying the sample, you must restart the host instance.</span></span>  
  
#### <a name="to-stop-and-restart-a-host-instance"></a><span data-ttu-id="5123d-123">Pour arrêter et redémarrer une instance de l'hôte</span><span class="sxs-lookup"><span data-stu-id="5123d-123">To stop and restart a host instance</span></span>  
  
1.  <span data-ttu-id="5123d-124">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis sélectionnez **Administration de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="5123d-124">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and select **BizTalk Server Administration.**</span></span>  
  
2.  <span data-ttu-id="5123d-125">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, double-cliquez sur le **Microsoft BizTalk Server (local)** nœud, puis développez **hôtes**.</span><span class="sxs-lookup"><span data-stu-id="5123d-125">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, double-click the **Microsoft BizTalk Server (local)** node, and expand **Hosts**.</span></span>  
  
3.  <span data-ttu-id="5123d-126">Dans le volet gauche, sélectionnez le **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="5123d-126">In the left pane, select the **BizTalkServerApplication**.</span></span>  
  
4.  <span data-ttu-id="5123d-127">Dans le volet droit, cliquez sur l’instance d’hôte (par exemple, le nom d’ordinateur), puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="5123d-127">In the right pane, right-click the host instance (for example, the computer name), and click **Stop**.</span></span>  
  
     <span data-ttu-id="5123d-128">L’état de l’instance d’hôte devient **arrêté**.</span><span class="sxs-lookup"><span data-stu-id="5123d-128">The status of the host instance changes to **Stopped**.</span></span>  
  
5.  <span data-ttu-id="5123d-129">Dans le volet droit, cliquez sur l’instance d’hôte, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="5123d-129">In the right pane, right-click the host instance and click **Start**.</span></span>  
  
     <span data-ttu-id="5123d-130">L’état de l’instance d’hôte devient **attente de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="5123d-130">The status of the host instance changes to **Start pending**.</span></span>  
  
     <span data-ttu-id="5123d-131">Pour modifier l’état à **en cours d’exécution**, cliquez sur **Actualiser**, ou cliquez sur l’instance d’hôte, puis cliquez **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="5123d-131">To change the status to **Running**, click **Refresh**, or right-click the host instance and then click **Refresh**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5123d-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5123d-132">See Also</span></span>  
 [<span data-ttu-id="5123d-133">Sécurité de la carte</span><span class="sxs-lookup"><span data-stu-id="5123d-133">Security in the adapter</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)