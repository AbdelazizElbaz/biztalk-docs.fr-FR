---
title: La gestion des Orchestrations | Documents Microsoft
description: "Liens de travailler avec les orchestrations dans BizTalk Server, y compris le début, arrêter, lier, configurer, activer le suivi interrompre et bien plus encore"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2553eec3-b863-45fb-90af-7eddcfa7add7
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18cd12c202822c4d9ff849cc762b55e8f4880d80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-orchestrations"></a><span data-ttu-id="a62c7-103">Gérer les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="a62c7-103">Manage Orchestrations</span></span>

## <a name="overview"></a><span data-ttu-id="a62c7-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="a62c7-104">Overview</span></span>
<span data-ttu-id="a62c7-105">Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] la console Administration pour gérer les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="a62c7-105">This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to manage orchestrations.</span></span> <span data-ttu-id="a62c7-106">Une orchestration est un processus d'entreprise exécutable.</span><span class="sxs-lookup"><span data-stu-id="a62c7-106">An orchestration is an executable business process.</span></span> <span data-ttu-id="a62c7-107">Pour plus d’informations générales sur les orchestrations, consultez [Orchestrations](../core/orchestrations.md).</span><span class="sxs-lookup"><span data-stu-id="a62c7-107">For background information about orchestrations, see [Orchestrations](../core/orchestrations.md).</span></span>  

## <a name="add-to-application"></a><span data-ttu-id="a62c7-108">Ajouter à l’application</span><span class="sxs-lookup"><span data-stu-id="a62c7-108">Add to application</span></span>  
 <span data-ttu-id="a62c7-109">Les orchestrations sont créées dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et compilées dans les assemblys BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a62c7-109">Orchestrations are built in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and compiled into BizTalk assemblies.</span></span> <span data-ttu-id="a62c7-110">Vous ne pouvez pas ajouter de manière individuelle une orchestration à une application. L'ajout d'une orchestration à une application s'effectue dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="a62c7-110">You cannot add an orchestration to an application individually; an orchestration is added to an application as follows:</span></span>  
  
-   <span data-ttu-id="a62c7-111">Lorsque vous ajoutez un assembly BizTalk contenant une orchestration à l’application, comme décrit dans [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="a62c7-111">When you add a BizTalk assembly containing an orchestration to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
-   <span data-ttu-id="a62c7-112">Lorsque vous importez un fichier .msi dans une application qui comprend un assembly BizTalk contenant une orchestration, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="a62c7-112">When you import an .msi file into an application that includes a BizTalk assembly containing an orchestration, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="a62c7-113">Lorsqu’un développeur déploie dans une application d’un assembly contenant une orchestration à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], comme décrit dans [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="a62c7-113">When a developer deploys into an application an assembly containing an orchestration from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  

## <a name="biztalk-administration-tasks"></a><span data-ttu-id="a62c7-114">Tâches d’Administration de BizTalk</span><span class="sxs-lookup"><span data-stu-id="a62c7-114">BizTalk Administration tasks</span></span>  
 <span data-ttu-id="a62c7-115">La console Administration permet d'effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="a62c7-115">You use the administration console to perform the following actions, as described in this section:</span></span>  
  
-   <span data-ttu-id="a62c7-116">Configurer des liaisons pour l'orchestration en liant l'orchestration aux ports de réception et d'envoi appropriés, ainsi qu'à l'hôte, ou supprimer ces liaisons de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-116">Configure bindings for the orchestration by binding the orchestration to the appropriate send and receive ports and host, or remove these bindings from the orchestration.</span></span>  
  
-   <span data-ttu-id="a62c7-117">Configurer le suivi des messages pour l'orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-117">Configure message tracking for the orchestration.</span></span>  
  
-   <span data-ttu-id="a62c7-118">Afficher les informations sur l'instance pour l'orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-118">View instance information for the orchestration.</span></span>  
  
-   <span data-ttu-id="a62c7-119">Inscrire l'orchestration sur l'hôte approprié ou la désinscrire de l'hôte</span><span class="sxs-lookup"><span data-stu-id="a62c7-119">Enlist the orchestration to the appropriate host or unenlist the orchestration from the host.</span></span>  
  
-   <span data-ttu-id="a62c7-120">Démarrer ou arrêter l'orchestration de manière qu'elle commence ou arrête le traitement des messages</span><span class="sxs-lookup"><span data-stu-id="a62c7-120">Start or stop the orchestration so that it starts or stops processing messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a62c7-121">Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="a62c7-121">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="a62c7-122">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="a62c7-122">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="a62c7-123">Le développeur utilise le Concepteur d’Orchestration pour créer des orchestrations, comme décrit dans [création d’Orchestrations à l’aide de concepteur d’Orchestration](../core/creating-orchestrations-using-orchestration-designer.md).</span><span class="sxs-lookup"><span data-stu-id="a62c7-123">The developer uses Orchestration Designer to create orchestrations, as described in [Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md).</span></span> <span data-ttu-id="a62c7-124">Il peut gérer les orchestrations au cours du processus de développement à l'aide de la console d'administration, comme décrit dans cette section.</span><span class="sxs-lookup"><span data-stu-id="a62c7-124">The developer can manage orchestrations during the development process by using the administration console, as described in this section.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a62c7-125">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a62c7-125">Next steps</span></span>
  
-   [<span data-ttu-id="a62c7-126">Configurer les liaisons d’une Orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-126">Configure Bindings for an Orchestration</span></span>](../core/how-to-configure-bindings-for-an-orchestration.md)  
  
-   [<span data-ttu-id="a62c7-127">Annuler la liaison d’une Orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-127">Unbind an Orchestration</span></span>](../core/how-to-unbind-an-orchestration.md)  
  
-   [<span data-ttu-id="a62c7-128">Configurer le suivi d’une Orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-128">Configure Tracking for an Orchestration</span></span>](../core/how-to-configure-tracking-for-an-orchestration.md)  
  
-   [<span data-ttu-id="a62c7-129">Afficher les informations d’Instance pour une Orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-129">View Instance Information for an Orchestration</span></span>](../core/how-to-view-instance-information-for-an-orchestration.md)  
  
-   [<span data-ttu-id="a62c7-130">Supprimer une Orchestration à partir d’une Application</span><span class="sxs-lookup"><span data-stu-id="a62c7-130">Remove an Orchestration from an Application</span></span>](../core/how-to-remove-an-orchestration-from-an-application.md)  
  
-   [<span data-ttu-id="a62c7-131">Inscrire une Orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-131">Enlist an Orchestration</span></span>](../core/how-to-enlist-an-orchestration.md)  
  
-   [<span data-ttu-id="a62c7-132">Désinscrire une Orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-132">Unenlist an Orchestration</span></span>](../core/how-to-unenlist-an-orchestration.md)  
  
-   [<span data-ttu-id="a62c7-133">Démarrer une Orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-133">Start an Orchestration</span></span>](../core/how-to-start-an-orchestration.md)  
  
-   [<span data-ttu-id="a62c7-134">Arrêter une Orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-134">Stop an Orchestration</span></span>](../core/how-to-stop-an-orchestration.md)  
  
-   [<span data-ttu-id="a62c7-135">Interrompre, reprendre et arrêter les Instances d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-135">Suspend, Resume, and Terminate Orchestration Instances</span></span>](../core/how-to-suspend-resume-and-terminate-orchestration-instances.md)  
  
-   [<span data-ttu-id="a62c7-136">Mise à niveau d’une Orchestration</span><span class="sxs-lookup"><span data-stu-id="a62c7-136">Upgrade an Orchestration</span></span>](../core/how-to-upgrade-an-orchestration.md)