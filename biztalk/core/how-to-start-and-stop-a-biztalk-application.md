---
title: "Comment démarrer et arrêter une Application BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- starting
- starting, applications
- managing [applications], starting
- managing [applications], stopping
- applications, starting
- stopping, applications
- applications, stopping
- stopping
ms.assetid: f9f83e99-a1e2-4dfd-b3be-60d3ec2cbcc4
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faacb2561b63d0e946c3408810db146e083f3e13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-start-and-stop-a-biztalk-application"></a><span data-ttu-id="43903-102">Démarrage et arrêt d'une application BizTalk</span><span class="sxs-lookup"><span data-stu-id="43903-102">How to Start and Stop a BizTalk Application</span></span>
<span data-ttu-id="43903-103">Cette rubrique décrit comment arrêter et démarrer une application BizTalk à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="43903-103">This topic describes how to use the BizTalk Server Administration console to start and stop a BizTalk application.</span></span>  
  
 <span data-ttu-id="43903-104">Avant de commencer une application, les liaisons doivent être configurés pour toutes les orchestrations qu’elle contient, comme décrit dans [comment configurer les liaisons d’une Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="43903-104">Before you can start an application, bindings must be configured for all orchestrations it contains, as described in [How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).</span></span>  
  
 <span data-ttu-id="43903-105">Lorsque vous démarrez une application, vous pouvez sélectionner une ou plusieurs des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="43903-105">When you start an application, you can select one or more of the following options, as follows:</span></span>  
  
-   <span data-ttu-id="43903-106">Inscrire et démarrer toutes les orchestrations</span><span class="sxs-lookup"><span data-stu-id="43903-106">Enlist and start all orchestrations.</span></span>  
  
-   <span data-ttu-id="43903-107">Inscrire et démarrer tous les ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="43903-107">Enlist and start all send ports.</span></span>  
  
-   <span data-ttu-id="43903-108">Inscrire et démarrer tous les groupes de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="43903-108">Enlist and start all send port groups.</span></span>  
  
-   <span data-ttu-id="43903-109">Activer tous les emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="43903-109">Enable all receive locations.</span></span>  
  
-   <span data-ttu-id="43903-110">Démarrer toutes les instances d'hôte associées</span><span class="sxs-lookup"><span data-stu-id="43903-110">Start all associated host instances.</span></span>  
  
-   <span data-ttu-id="43903-111">Reprendre les instances suspendues</span><span class="sxs-lookup"><span data-stu-id="43903-111">Resume suspended instances.</span></span>  
  
-   <span data-ttu-id="43903-112">Déployer toutes les stratégies.</span><span class="sxs-lookup"><span data-stu-id="43903-112">Deploy all policies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43903-113">Seules les stratégies publiées dans l’application sont déployées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="43903-113">Only published policies in the application are deployed automatically.</span></span> <span data-ttu-id="43903-114">Si une stratégie ne peut pas être publiée, elle n’est pas déployée.</span><span class="sxs-lookup"><span data-stu-id="43903-114">If a policy is not published, it will not be deployed.</span></span>  
  
 <span data-ttu-id="43903-115">Lorsque vous arrêtez une application, vous pouvez sélectionner l'une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="43903-115">When you stop an application, you can select one of the following options:</span></span>  
  
-   <span data-ttu-id="43903-116">**Partielle arrêter - autoriser les instances en cours de continuer.**</span><span class="sxs-lookup"><span data-stu-id="43903-116">**Partial Stop - Allow running instances to continue.**</span></span> <span data-ttu-id="43903-117">cette option désactive tous les emplacements de réception dans l'application, mais laisse tous les autres artefacts dans l'état précédent.</span><span class="sxs-lookup"><span data-stu-id="43903-117">This option disables all receive locations in the application, but leaves all other artifacts in their previous state.</span></span> <span data-ttu-id="43903-118">Cela permet aux instances en cours de finir de traiter les messages actuellement dans le système.</span><span class="sxs-lookup"><span data-stu-id="43903-118">This allows running instances to complete processing messages that are currently in the system.</span></span> <span data-ttu-id="43903-119">Notez que si une transaction de message nécessite plusieurs entrées, elle ne pourra peut-être pas être terminée lorsque vous utilisez cette option.</span><span class="sxs-lookup"><span data-stu-id="43903-119">Note that if a message transaction requires multiple inputs, it may not be able to complete when you use this option.</span></span>  
  
-   <span data-ttu-id="43903-120">**Partielle arrêt - suspendre les instances en cours d’exécution.**</span><span class="sxs-lookup"><span data-stu-id="43903-120">**Partial Stop - Suspend running instances.**</span></span> <span data-ttu-id="43903-121">cette option désactive tous les emplacements de réception et arrête toutes les orchestrations et tous les ports d’envoi de l’application.</span><span class="sxs-lookup"><span data-stu-id="43903-121">This option disables all receive locations and stops all orchestrations and send ports in the application.</span></span> <span data-ttu-id="43903-122">Elle ne désinscrit aucun artefact et n'annule aucun déploiement d'artefact.</span><span class="sxs-lookup"><span data-stu-id="43903-122">It does not unenlist or undeploy any artifacts.</span></span> <span data-ttu-id="43903-123">Utilisez cette option si vous souhaitez suspendre l’application temporairement.</span><span class="sxs-lookup"><span data-stu-id="43903-123">Use this option when you want to temporarily pause the application.</span></span>  
  
-   <span data-ttu-id="43903-124">**Arrêt complet - arrêter les instances.**</span><span class="sxs-lookup"><span data-stu-id="43903-124">**Full Stop - Terminate instances.**</span></span> <span data-ttu-id="43903-125">cette option désactive tous les emplacements de réception, arrête et désinscrit toutes les orchestrations et tous les ports d'envoi et annule le déploiement de toutes les stratégies de l'application.</span><span class="sxs-lookup"><span data-stu-id="43903-125">This option disables all receive locations, stops and unenlists all orchestrations and send ports, and undeploys all policies in the application.</span></span> <span data-ttu-id="43903-126">Utilisez cette option si vous souhaitez annuler complètement le déploiement d’une application.</span><span class="sxs-lookup"><span data-stu-id="43903-126">Use this option when you want to completely undeploy an application.</span></span> <span data-ttu-id="43903-127">Notez que toutes les instances en cours d’exécution qui sont toujours en cours de traitement de message n’iront pas au bout de leur opération.</span><span class="sxs-lookup"><span data-stu-id="43903-127">Note that any running instances that are still processing messages will not complete processing.</span></span> <span data-ttu-id="43903-128">Pour plus d’informations, consultez [annulation du déploiement des Applications BizTalk](../core/undeploying-biztalk-applications.md).</span><span class="sxs-lookup"><span data-stu-id="43903-128">For more information, see [Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="43903-129">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="43903-129">Prerequisites</span></span>  
 <span data-ttu-id="43903-130">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="43903-130">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="43903-131">Les opérateurs BizTalk peuvent procéder à un arrêt partiel, mais pas complet.</span><span class="sxs-lookup"><span data-stu-id="43903-131">BizTalk Operators can perform a partial stop, but not a full stop.</span></span> <span data-ttu-id="43903-132">De plus, les opérateurs BizTalk peuvent démarrer une application si tous les artefacts sont inscrits.</span><span class="sxs-lookup"><span data-stu-id="43903-132">In addition, BizTalk Operators can start an application if all artifacts are enlisted.</span></span> <span data-ttu-id="43903-133">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="43903-133">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-start-or-stop-a-biztalk-application"></a><span data-ttu-id="43903-134">Pour démarrer ou arrêter une application BizTalk</span><span class="sxs-lookup"><span data-stu-id="43903-134">To start or stop a BizTalk application</span></span>  
  
1.  <span data-ttu-id="43903-135">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="43903-135">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="43903-136">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="43903-136">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="43903-137">Cliquez sur l’application BizTalk que vous souhaitez démarrer ou arrêter, puis cliquez sur **Démarrer** ou **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="43903-137">Right-click the BizTalk application that you want to start or stop, and then click **Start** or **Stop**.</span></span>  
  
4.  <span data-ttu-id="43903-138">Options d’arrêt vous cliquez sur ou sélectionnez le début **Démarrer** ou **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="43903-138">Select the start or stop options you want and click **Start** or **Stop**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43903-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43903-139">See Also</span></span>  
 <span data-ttu-id="43903-140">[Déploiement et gestion des Applications BizTalk](../core/deploying-and-managing-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="43903-140">[Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="43903-141">Mise à jour des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="43903-141">Updating BizTalk Applications</span></span>](../core/updating-biztalk-applications.md)