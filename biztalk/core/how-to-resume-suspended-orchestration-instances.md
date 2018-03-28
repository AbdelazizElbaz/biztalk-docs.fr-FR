---
title: Comment reprendre les Instances d’Orchestration suspendues | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- instances, resuming [HAT]
- HAT, resuming orchestrations
- HAT, resuming pipelines
- orchestrations, resuming
- resuming, pipelines
- resuming, orchestrations
- HAT, debug mode
ms.assetid: da133183-68d9-48d1-9601-8f6d4d5b8898
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6696547ce3e918dc8d84b7cfcb4f24e31c8b70a0
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-resume-suspended-orchestration-instances"></a><span data-ttu-id="8182b-102">Reprise des instances de l'orchestration suspendues</span><span class="sxs-lookup"><span data-stu-id="8182b-102">How to Resume Suspended Orchestration Instances</span></span>
<span data-ttu-id="8182b-103">Si vous avez suspendu des instances de l'orchestration associées à l'état « Suspendu (peut être repris) », vous pouvez tenter de reprendre l'instance de l'orchestration à partir des résultats de requête ou du volet de visualisation.</span><span class="sxs-lookup"><span data-stu-id="8182b-103">If you have suspended orchestration instances that are listed as "suspended resumable," you can attempt to resume the orchestration instance from the query results or preview pane.</span></span> <span data-ttu-id="8182b-104">La reprise de l'instance de l'orchestration n'est possible que si vous avez remédié au problème sous-jacent qui a entraîné la suspension de cette instance.</span><span class="sxs-lookup"><span data-stu-id="8182b-104">Resuming the orchestration instance will only succeed if the underlying problem that caused the orchestration instance to become suspended has also been fixed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8182b-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8182b-105">Prerequisites</span></span>  
 <span data-ttu-id="8182b-106">Vous devez être connecté en tant que membre du groupe opérateurs BizTalk Server pour effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="8182b-106">You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.</span></span>  
  
### <a name="to-resume-suspended-orchestration-instances"></a><span data-ttu-id="8182b-107">Pour reprendre les instances de l'orchestration suspendues</span><span class="sxs-lookup"><span data-stu-id="8182b-107">To resume suspended orchestration instances</span></span>  
  
1.  <span data-ttu-id="8182b-108">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="8182b-108">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="8182b-109">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, puis cliquez sur le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8182b-109">In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="8182b-110">Dans le volet détails, cliquez sur le **nouvelle requête** onglet.</span><span class="sxs-lookup"><span data-stu-id="8182b-110">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="8182b-111">Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **Instances de Service suspendues** dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="8182b-111">In the **Query Expression** group, in the **Value** column, select **Suspended Service Instances** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="8182b-112">Procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="8182b-112">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="8182b-113">Pour reprendre une instance unique, dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez le **nom du Service** filtre et Ensuite, dans le **valeur** colonne, spécifiez le nom du service.</span><span class="sxs-lookup"><span data-stu-id="8182b-113">To resume a single instance, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select the **Service Name** filter and then in the **Value** column, specify the service name.</span></span>  
  
    -   <span data-ttu-id="8182b-114">Pour reprendre les instances en bloc, dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez **grouper les résultats selon** puis, dans le **valeur** colonne, spécifiez le nom du service.</span><span class="sxs-lookup"><span data-stu-id="8182b-114">To resume instances in bulk, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select **Group Results By** and then in the **Value** column, specify the service name.</span></span>  
  
6.  <span data-ttu-id="8182b-115">Cliquez sur **exécuter la requête**.</span><span class="sxs-lookup"><span data-stu-id="8182b-115">Click **Run Query**.</span></span>  
  
7.  <span data-ttu-id="8182b-116">Dans la liste de résultats de requête, cliquez sur l’instance d’orchestration que vous souhaitez reprendre, puis cliquez sur **reprendre une Instance** ou **reprendre les Instances**.</span><span class="sxs-lookup"><span data-stu-id="8182b-116">In the query results list, right-click the orchestration instance you want to resume, and then click **Resume Instance** or **Resume Instances**.</span></span> <span data-ttu-id="8182b-117">Cela vous permet de sélectionner les instances à reprendre.</span><span class="sxs-lookup"><span data-stu-id="8182b-117">This allows you to select which instances to resume.</span></span>  
  
     <span data-ttu-id="8182b-118">[États de l’Instance service](../core/service-instance-states.md) fournit des informations sur la sur l’état suspendu.</span><span class="sxs-lookup"><span data-stu-id="8182b-118">[Service Instance States](../core/service-instance-states.md) provides more information on the on the suspended state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8182b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8182b-119">See Also</span></span>  
 [<span data-ttu-id="8182b-120">Examen des échecs relatifs aux orchestrations, aux ports et aux messages</span><span class="sxs-lookup"><span data-stu-id="8182b-120">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)
