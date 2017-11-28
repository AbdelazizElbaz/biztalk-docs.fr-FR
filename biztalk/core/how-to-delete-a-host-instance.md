---
title: "Supprimer une Instance d’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35a06480-0962-4bdc-add2-56f979a2f1c9
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 798ea341ef61b15729dd15742eef7701641e7547
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delete-a-host-instance"></a><span data-ttu-id="8c35a-102">Supprimer une Instance d’hôte</span><span class="sxs-lookup"><span data-stu-id="8c35a-102">Delete a Host Instance</span></span>

## <a name="overview"></a><span data-ttu-id="8c35a-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="8c35a-103">Overview</span></span>
<span data-ttu-id="8c35a-104">La console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou Windows Management Instrumentation (WMI) permet de supprimer des instances de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="8c35a-104">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or Windows Management Instrumentation (WMI) to delete host instances.</span></span> <span data-ttu-id="8c35a-105">Pour plus d’informations sur les instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md).</span><span class="sxs-lookup"><span data-stu-id="8c35a-105">For more information about host instances, see [Host Instances](../core/host-instances.md).</span></span> <span data-ttu-id="8c35a-106">Pour plus d’informations sur l’utilisation de WMI pour supprimer une instance d’hôte, consultez **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="8c35a-106">For information about using WMI to delete a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="8c35a-107">Lorsque vous supprimez une instance d'hôte, l'instance du composant d'exécution de BizTalk Server est supprimée du serveur associé et la base de données de gestion BizTalk est mise à jour pour supprimer cette instance de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="8c35a-107">When you delete a host instance, the instance of the BizTalk Server runtime is removed from the associated server and the BizTalk Management database is updated to remove that instance from the host.</span></span>  
  
 <span data-ttu-id="8c35a-108">Pour éviter de perdre des messages lorsque vous supprimez une instance d'hôte, BizTalk Server termine tous les traitements avant la suppression effective de l'instance.</span><span class="sxs-lookup"><span data-stu-id="8c35a-108">To avoid losing messages when you delete a host instance, BizTalk Server completes all processing before the instance is actually removed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8c35a-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8c35a-109">Prerequisites</span></span>  
 <span data-ttu-id="8c35a-110">Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs BizTalk Server ou du groupe des administrateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="8c35a-110">To perform this procedure, you must be logged on as a member of the Administrators group and the BizTalk Server Administrators group.</span></span>  
  
 <span data-ttu-id="8c35a-111">Vous devez également être un membre du rôle de la base de données SQL Server db_securityadmin et du rôle SQL Server securityadmin sur les serveurs sur lesquels se trouvent les bases de données suivantes :</span><span class="sxs-lookup"><span data-stu-id="8c35a-111">In addition, you must also be a member of the db_securityadmin SQL Server Database role and the securityadmin SQL Server Role on the server(s) where the following databases are:</span></span>  
  
-   <span data-ttu-id="8c35a-112">importation principale BAM (BAMPrimaryImport).</span><span class="sxs-lookup"><span data-stu-id="8c35a-112">BAM Primary Import (BAMPrimaryImport)</span></span>  
  
-   <span data-ttu-id="8c35a-113">gestion BizTalk (BizTalkMgmtDb) ;</span><span class="sxs-lookup"><span data-stu-id="8c35a-113">BizTalk Management (BizTalkMgmtDb)</span></span>  
  
-   <span data-ttu-id="8c35a-114">MessageBox BizTalk (BizTalkMsgBoxDb) (tout) ;</span><span class="sxs-lookup"><span data-stu-id="8c35a-114">BizTalk MessageBox (BizTalkMsgBoxDb) (all)</span></span>  
  
-   <span data-ttu-id="8c35a-115">suivis BizTalk (BizTalkDTADb) ;</span><span class="sxs-lookup"><span data-stu-id="8c35a-115">BizTalk Tracking (BizTalk DTADb)</span></span>  
  
-   <span data-ttu-id="8c35a-116">moteur des règles (BizTalkRuleEngineDb) ;</span><span class="sxs-lookup"><span data-stu-id="8c35a-116">Rule Engine (BizTalkRuleEngineDb)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8c35a-117">Nous vous recommandons de mettre à jour les informations de compte des instances d'hôte à l'aide de la console Administration de BizTalk Server ou d'un script WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="8c35a-117">We recommend that you update account information for host instances by using the BizTalk Server Administration Console or a Windows Management Instrumentation (WMI) script.</span></span> <span data-ttu-id="8c35a-118">De cette manière, BizTalk Server peut mettre à jour les informations de compte dans les bases de données BizTalk Server et peut synchroniser la configuration de sécurité entre les bases de données et l'instance d'hôte.</span><span class="sxs-lookup"><span data-stu-id="8c35a-118">This ensures that BizTalk Server can update the account information in the BizTalk Server databases and keep the security configuration between the databases and host instance synchronized.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="8c35a-119">Étapes</span><span class="sxs-lookup"><span data-stu-id="8c35a-119">Steps</span></span>
  
1.  <span data-ttu-id="8c35a-120">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="8c35a-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="8c35a-121">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="8c35a-121">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="8c35a-122">Dans le volet de détails, cliquez sur l’instance d’hôte que vous souhaitez supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="8c35a-122">In the details pane, right-click the host instance you want to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="8c35a-123">Dans le **confirmer supprimer une instance hôte** boîte de dialogue, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="8c35a-123">In the **Confirm delete host instance** dialog box, click **Yes**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c35a-124">Si BizTalk Server ne peut pas supprimer l'instance de l'hôte, une boîte de dialogue vous permettant d'imposer la suppression de l'instance de l'hôte s'affiche.</span><span class="sxs-lookup"><span data-stu-id="8c35a-124">If BizTalk Server cannot delete the host instance, a dialog box appears in which you can force the deletion of the host instance.</span></span> <span data-ttu-id="8c35a-125">Après avoir lu les informations fournies, cliquez sur **Oui** pour supprimer l’instance d’hôte.</span><span class="sxs-lookup"><span data-stu-id="8c35a-125">After reading the information provided, click **Yes** to delete the host instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c35a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c35a-126">See Also</span></span>  
 <span data-ttu-id="8c35a-127">[La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md) </span><span class="sxs-lookup"><span data-stu-id="8c35a-127">[Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md) </span></span>  
 <span data-ttu-id="8c35a-128">[L’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="8c35a-128">[How to Add a Host Instance](../core/how-to-add-a-host-instance.md) </span></span>  
 <span data-ttu-id="8c35a-129">[Comment démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="8c35a-129">[How to Start a Host Instance](../core/how-to-start-a-host-instance.md) </span></span>  
 <span data-ttu-id="8c35a-130">[Comment arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="8c35a-130">[How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md) </span></span>  
 [<span data-ttu-id="8c35a-131">Comment modifier les propriétés de l’Instance hôte</span><span class="sxs-lookup"><span data-stu-id="8c35a-131">How to Modify Host Instance Properties</span></span>](../core/how-to-modify-host-instance-properties.md)