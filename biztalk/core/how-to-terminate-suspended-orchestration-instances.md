---
title: Comment arrêter les Instances d’Orchestration suspendues | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, terminating [HAT]
- messages, saving [HAT]
- HAT, saving messages
- HAT, terminating pipelines
- HAT, terminiating orchestrations
- orchestrations, terminating [HAT]
ms.assetid: b5d44cce-b05c-47f9-9015-5b10c2312bf1
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dc0160be5aeeef43b9595953893b4ea1af82c62
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-terminate-suspended-orchestration-instances"></a><span data-ttu-id="e46b0-102">Arrêt des instances de l'orchestration suspendues</span><span class="sxs-lookup"><span data-stu-id="e46b0-102">How to Terminate Suspended Orchestration Instances</span></span>
<span data-ttu-id="e46b0-103">Vous pouvez terminer des instances d'orchestration suspendues ou des ports à partir des résultats de la requête ou du volet de visualisation dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e46b0-103">You can terminate any suspended orchestration instances or ports from the Query results or preview pane in the BizTalk Server Administration Console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e46b0-104">Chaque instance d’un livraison chronologique des messages un port d’envoi peut avoir plusieurs messages sont associés.</span><span class="sxs-lookup"><span data-stu-id="e46b0-104">Each instance of an ordered delivery a send port may have several messages associated with it.</span></span> <span data-ttu-id="e46b0-105">Afin d'éviter une perte des données ou un arrêt accidentel, vérifiez l'ensemble de ces associations avant de mettre fin à une instance.</span><span class="sxs-lookup"><span data-stu-id="e46b0-105">To prevent accidental termination or data loss, be sure you have reviewed all such associations before terminating an instance.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e46b0-106">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e46b0-106">Prerequisites</span></span>  
 <span data-ttu-id="e46b0-107">Vous devez être connecté en tant que membre du groupe opérateurs BizTalk Server pour effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="e46b0-107">You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.</span></span>  
  
### <a name="to-terminate-suspended-orchestration-instances"></a><span data-ttu-id="e46b0-108">Pour terminer les instances de l'orchestration suspendues</span><span class="sxs-lookup"><span data-stu-id="e46b0-108">To terminate suspended orchestration instances</span></span>  
  
1.  <span data-ttu-id="e46b0-109">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="e46b0-109">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e46b0-110">Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez sur le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e46b0-110">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="e46b0-111">Dans le volet détails, cliquez sur le **nouvelle requête** onglet.</span><span class="sxs-lookup"><span data-stu-id="e46b0-111">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="e46b0-112">Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **Instances de Service suspendues** dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e46b0-112">In the **Query Expression** group, in the **Value** column, select **Suspended Service Instances** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="e46b0-113">Procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="e46b0-113">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="e46b0-114">Pour mettre fin à une instance unique, dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez le **nom du Service** filtre puis, dans le **valeur** colonne, spécifiez le nom du service.</span><span class="sxs-lookup"><span data-stu-id="e46b0-114">To terminate a single instance, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select the **Service Name** filter and then in the **Value** column, specify the service name.</span></span>  
  
    -   <span data-ttu-id="e46b0-115">Pour arrêter les instances en bloc, dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez **grouper les résultats selon** , puis dans le **valeur** colonne, spécifiez le nom du service.</span><span class="sxs-lookup"><span data-stu-id="e46b0-115">To terminate instances in bulk, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select **Group Results By** and then in the **Value** column, specify the service name.</span></span>  
  
6.  <span data-ttu-id="e46b0-116">Cliquez sur **exécuter la requête**.</span><span class="sxs-lookup"><span data-stu-id="e46b0-116">Click **Run Query**.</span></span>  
  
7.  <span data-ttu-id="e46b0-117">Dans la liste de résultats de requête, cliquez sur l’instance d’orchestration ou le groupe d’instances que vous souhaitez terminer, puis cliquez sur **arrêter l’Instance** ou **arrêter les Instances**.</span><span class="sxs-lookup"><span data-stu-id="e46b0-117">In the query results list, right-click the orchestration instance or group of instances you want to terminate, and then click **Terminate Instance** or **Terminate Instances**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e46b0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e46b0-118">See Also</span></span>  
 [<span data-ttu-id="e46b0-119">Examen des échecs relatifs aux orchestrations, aux ports et aux messages</span><span class="sxs-lookup"><span data-stu-id="e46b0-119">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)