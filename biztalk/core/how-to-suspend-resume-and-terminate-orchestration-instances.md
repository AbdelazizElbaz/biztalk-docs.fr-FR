---
title: "Comment suspendre, reprendre et terminer des Instances d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], resuming
- orchestrations, terminating
- managing [orchestrations], suspending
- orchestrations, resuming
- orchestrations, suspending
- managing [orchestrations], terminating
ms.assetid: 7b373dad-57d5-4696-9b29-a6c351d44fa8
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9528ac0e810a3d4e203733ab1cc5b041d3d61d31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-suspend-resume-and-terminate-orchestration-instances"></a><span data-ttu-id="c7ba8-102">Interruption, reprise et arrêt des instances de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="c7ba8-102">How to Suspend, Resume, and Terminate Orchestration Instances</span></span>
<span data-ttu-id="c7ba8-103">Cette rubrique décrit l'interruption, la reprise et l'arrêt d'une ou plusieurs instances de service d'une orchestration en cours d'exécution à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-103">This topic describes how to suspend, resume, and terminate one or more running service instances of an orchestration by using the BizTalk Server Administration console.</span></span> <span data-ttu-id="c7ba8-104">Une instance de service est une instance d'orchestration que BizTalk Server est en train de traiter ou qui a été sérialisée dans la base de données MessageBox pour un traitement ou suivi plus approfondi.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-104">A service instance is an instance of an orchestration that BizTalk Server is either processing or that has been serialized into the MessageBox for further processing or tracking.</span></span>  
  
 <span data-ttu-id="c7ba8-105">Les sections suivantes décrivent les effets de ces trois opérations :</span><span class="sxs-lookup"><span data-stu-id="c7ba8-105">The following describes the effects of these three operations:</span></span>  
  
-   <span data-ttu-id="c7ba8-106">**Suspendre.**</span><span class="sxs-lookup"><span data-stu-id="c7ba8-106">**Suspend.**</span></span> <span data-ttu-id="c7ba8-107">met l'instance de service en attente.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-107">This pauses the service instance.</span></span> <span data-ttu-id="c7ba8-108">Les messages en cours de traitement sont exécutés jusqu'à la fin.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-108">In-process messages run to completion.</span></span> <span data-ttu-id="c7ba8-109">Les messages sont toujours acheminés vers les instances de service mais ils ne sont pas traités.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-109">Messages are still routed to service instances, but are not processed.</span></span>  
  
-   <span data-ttu-id="c7ba8-110">**Reprendre.**</span><span class="sxs-lookup"><span data-stu-id="c7ba8-110">**Resume.**</span></span> <span data-ttu-id="c7ba8-111">reprend le traitement des instances interrompues.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-111">This resumes processing of suspended instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7ba8-112">Vous ne pouvez pas reprendre une instance à partir d'un état Point d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-112">You cannot resume an instance from a breakpoint state.</span></span> <span data-ttu-id="c7ba8-113">La reprise d'une instance dans cet état peut afficher l'état « En attente », mais l'instance risque d'échouer.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-113">Resuming such an instance may show a status of "Pending," but the instance will eventually fail.</span></span>  
  
-   <span data-ttu-id="c7ba8-114">**Mettre fin.**</span><span class="sxs-lookup"><span data-stu-id="c7ba8-114">**Terminate.**</span></span> <span data-ttu-id="c7ba8-115">termine le traitement de tous les messages.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-115">This terminates all message processing.</span></span> <span data-ttu-id="c7ba8-116">L'instance de service est supprimée des bases de données BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-116">The service instance is deleted from the BizTalk Server databases.</span></span> <span data-ttu-id="c7ba8-117">Les messages que l'instance de service est en train de traiter sont également supprimés, sauf ceux qui sont également référencés par une instance de service non arrêtée.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-117">Messages that the service instance is processing are also deleted, except for any messages that are also referenced by a service instance that is not being terminated.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c7ba8-118">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="c7ba8-118">Prerequisites</span></span>  
 <span data-ttu-id="c7ba8-119">Pour exécuter la procédure décrite dans cette rubrique, vous devez avoir ouvert une session en tant que membre du groupe des opérateurs de BizTalk Server ou du groupe d'administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-119">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Operators group or the BizTalk Server Administrators group.</span></span> <span data-ttu-id="c7ba8-120">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="c7ba8-120">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-start-stop-or-terminate-an-instance-of-an-orchestration"></a><span data-ttu-id="c7ba8-121">Pour démarrer, arrêter ou terminer une instance d'orchestration</span><span class="sxs-lookup"><span data-stu-id="c7ba8-121">To view start, stop, or terminate an instance of an orchestration</span></span>  
  
1.  <span data-ttu-id="c7ba8-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="c7ba8-123">Sélectionnez le groupe BizTalk pour afficher la page Hub associée.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-123">Select the BizTalk Group to display the Group Hub page.</span></span>  
  
3.  <span data-ttu-id="c7ba8-124">Sous **travail en cours**, cliquez sur **des instances de service en cours d’exécution**.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-124">Under **Work in Progress**, click **Running service instances**.</span></span>  
  
     <span data-ttu-id="c7ba8-125">Le volet de résultats de la requête situé dans la section inférieure de la page affiche toutes les instances de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-125">The query results panel in the lower section of the page displays all instances of the orchestration.</span></span>  
  
4.  <span data-ttu-id="c7ba8-126">Pour affiner la requête et afficher d’autres instances de l’orchestration, cliquez sur la zone sous **valeur** pour le **recherche de** , sélectionnez le type d’instance à afficher, puis cliquez sur **exécuter la requête** .</span><span class="sxs-lookup"><span data-stu-id="c7ba8-126">To refine the query and view different instances for the orchestration, click the box under **Value** for the **Search For** field, select the instance type to view, and then click **Run Query**.</span></span> <span data-ttu-id="c7ba8-127">Pour plus d'informations sur la création des requêtes, consultez les rubriques relatives à la recherche dans la section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-127">For more information about creating queries, see the topics on searching under See Also.</span></span>  
  
5.  <span data-ttu-id="c7ba8-128">Cliquez sur l’instance souhaitée, puis cliquez sur **Suspend**, **reprise**, ou **Terminate**.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-128">Right-click the instance you want and click **Suspend**, **Resume**, or **Terminate**.</span></span> <span data-ttu-id="c7ba8-129">Cette fonctionnalité vous permet de sélectionner les instances à reprendre.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-129">This functionality allows you to select which instances to resume.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c7ba8-130">Pour appliquer l'opération à plusieurs instances, maintenez la touche CTRL enfoncée, puis cliquez sur les instances souhaitées.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-130">To perform the operation on multiple instances, hold down the CTRL key and click the instances you want.</span></span> <span data-ttu-id="c7ba8-131">Cliquez sur une instance, puis cliquez sur **Suspend**, **reprise**, ou **Terminate**.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-131">Then right-click an instance and click **Suspend**, **Resume**, or **Terminate**.</span></span>  
  
     <span data-ttu-id="c7ba8-132">[États de l’Instance service](../core/service-instance-states.md) fournit des informations sur l’état suspendu.</span><span class="sxs-lookup"><span data-stu-id="c7ba8-132">[Service Instance States](../core/service-instance-states.md) provides more information on the suspended state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7ba8-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7ba8-133">See Also</span></span>  
 <span data-ttu-id="c7ba8-134">[La gestion des Orchestrations](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="c7ba8-134">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="c7ba8-135">[Comment rechercher des Instances de Service en cours d’exécution](../core/how-to-search-for-running-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="c7ba8-135">[How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md) </span></span>  
 [<span data-ttu-id="c7ba8-136">Comment rechercher des Instances de Service suspendues</span><span class="sxs-lookup"><span data-stu-id="c7ba8-136">How to Search for Suspended Service Instances</span></span>](../core/how-to-search-for-suspended-service-instances.md)