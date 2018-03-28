---
title: Comment suspendre des Instances d’Orchestration ou des Ports | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, suspending
- instances, suspending
- suspending
- HAT, suspending orchestrations
- HAT, suspending pipelines
- suspending, ports
- suspending, orchestrations
- orchestrations, suspending
- HAT, suspending ports
- suspending, instances
- ports, suspending
ms.assetid: cacc7e58-7d3e-4d6b-adb0-618fdc4f0d89
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62d91c8d1e02b7283a430f7c82c572b6a989d108
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-suspend-orchestration-instances-or-ports"></a><span data-ttu-id="79102-102">Interruption des instances d'orchestration ou des ports</span><span class="sxs-lookup"><span data-stu-id="79102-102">How to Suspend Orchestration Instances or Ports</span></span>
<span data-ttu-id="79102-103">Vous pouvez suspendre des instances d'orchestration ou des ports à partir de la liste des résultats de la requête dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="79102-103">You can suspend orchestration instances or ports from a query results list in the BizTalk Server Administration Console.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="79102-104">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="79102-104">Prerequisites</span></span>  
 <span data-ttu-id="79102-105">Vous devez être connecté en tant que membre du groupe opérateurs BizTalk Server pour effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="79102-105">You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.</span></span>  
  
### <a name="to-suspend-orchestration-instances-or-ports"></a><span data-ttu-id="79102-106">Pour suspendre des instances d'orchestration ou des ports</span><span class="sxs-lookup"><span data-stu-id="79102-106">To suspend orchestration instances or ports</span></span>  
  
1.  <span data-ttu-id="79102-107">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="79102-107">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="79102-108">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, puis cliquez sur le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="79102-108">In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="79102-109">Dans le volet détails, cliquez sur le **nouvelle requête** onglet.</span><span class="sxs-lookup"><span data-stu-id="79102-109">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="79102-110">Dans le **Expression de requête** groupe, dans le **valeur** colonne, sélectionnez **en cours d’exécution des Instances de Service** dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="79102-110">In the **Query Expression** group, in the **Value** column, select **Running Service Instances** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="79102-111">Procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="79102-111">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="79102-112">Pour interrompre une instance unique, dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez le **nom du Service** filtre et Ensuite, dans le **valeur** colonne, spécifiez le nom du service.</span><span class="sxs-lookup"><span data-stu-id="79102-112">To suspend a single instance, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select the **Service Name** filter and then in the **Value** column, specify the service name.</span></span>  
  
    -   <span data-ttu-id="79102-113">Pour suspendre les instances en bloc, dans le **nom de champ** colonne, dans la zone de liste déroulante vide en regard de l’astérisque (**\***), sélectionnez **grouper les résultats selon** puis, dans le **valeur** colonne, spécifiez le nom du service.</span><span class="sxs-lookup"><span data-stu-id="79102-113">To suspend instances in bulk, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select **Group Results By** and then in the **Value** column, specify the service name.</span></span>  
  
6.  <span data-ttu-id="79102-114">Cliquez sur **exécuter la requête**.</span><span class="sxs-lookup"><span data-stu-id="79102-114">Click **Run Query**.</span></span>  
  
7.  <span data-ttu-id="79102-115">Dans la liste de résultats de requête, cliquez sur l’orchestration active ou le port que vous souhaitez suspendre, puis cliquez sur **suspendre l’Instance** ou **suspendre les Instances**.</span><span class="sxs-lookup"><span data-stu-id="79102-115">In the query results list, right-click the active orchestration or port you want to suspend, and then click **Suspend Instance** or **Suspend Instances**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79102-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79102-116">See Also</span></span>  
 [<span data-ttu-id="79102-117">Examen des échecs relatifs aux orchestrations, aux ports et aux messages</span><span class="sxs-lookup"><span data-stu-id="79102-117">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)