---
title: "Arrêter une Instance d’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1f2e0c1-a387-4182-82ef-e25f49ac509b
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 837b08c30263b48ad481c7e03820cfba0b6c0ecc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="stop-a-host-instance"></a><span data-ttu-id="d5554-102">Arrêter une Instance d’hôte</span><span class="sxs-lookup"><span data-stu-id="d5554-102">Stop a Host Instance</span></span>

## <a name="overview"></a><span data-ttu-id="d5554-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="d5554-103">Overview</span></span>
<span data-ttu-id="d5554-104">Vous pouvez utiliser la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration ou de Windows Management Instrumentation (WMI) pour arrêter les instances de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="d5554-104">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or Windows Management Instrumentation (WMI) to stop host instances.</span></span> <span data-ttu-id="d5554-105">Vous devez arrêter une instance d'hôte avant de pouvoir la supprimer ou avant de pouvoir désinstaller BizTalk Server d'un ordinateur donné.</span><span class="sxs-lookup"><span data-stu-id="d5554-105">You must stop a host instance before you can delete it or remove BizTalk Server from a computer.</span></span> <span data-ttu-id="d5554-106">Vous pouvez arrêter une instance d'hôte installée et démarrée.</span><span class="sxs-lookup"><span data-stu-id="d5554-106">You can stop a host instance that is installed and started.</span></span> <span data-ttu-id="d5554-107">Pour plus d’informations sur les instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md).</span><span class="sxs-lookup"><span data-stu-id="d5554-107">For more information about host instances, see [Host Instances](../core/host-instances.md).</span></span>  
  
 <span data-ttu-id="d5554-108">Pour plus d’informations sur l’utilisation de WMI pour arrêter une instance d’hôte, consultez **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="d5554-108">For information about using WMI to stop a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="d5554-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d5554-109">Prerequisites</span></span>  
 <span data-ttu-id="d5554-110">Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs BizTalk Server ou du groupe des administrateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="d5554-110">To perform this procedure, you must be logged on as a member of the Administrators group and the BizTalk Server Administrators group.</span></span>  
  
 <span data-ttu-id="d5554-111">Vous devez également être un membre du rôle de la base de données SQL Server db_securityadmin et du rôle SQL Server securityadmin sur les serveurs sur lesquels se trouvent les bases de données suivantes :</span><span class="sxs-lookup"><span data-stu-id="d5554-111">In addition, you must also be a member of the db_securityadmin SQL Server Database role and the securityadmin SQL Server Role on the server(s) where the following databases are:</span></span>  
  
-   <span data-ttu-id="d5554-112">importation principale BAM (BAMPrimaryImport).</span><span class="sxs-lookup"><span data-stu-id="d5554-112">BAM Primary Import (BAMPrimaryImport)</span></span>  
  
-   <span data-ttu-id="d5554-113">gestion BizTalk (BizTalkMgmtDb) ;</span><span class="sxs-lookup"><span data-stu-id="d5554-113">BizTalk Management (BizTalkMgmtDb)</span></span>  
  
-   <span data-ttu-id="d5554-114">MessageBox BizTalk (BizTalkMsgBoxDb) (tout) ;</span><span class="sxs-lookup"><span data-stu-id="d5554-114">BizTalk MessageBox (BizTalkMsgBoxDb) (all)</span></span>  
  
-   <span data-ttu-id="d5554-115">suivis BizTalk (BizTalkDTADb) ;</span><span class="sxs-lookup"><span data-stu-id="d5554-115">BizTalk Tracking (BizTalk DTADb)</span></span>  
  
-   <span data-ttu-id="d5554-116">moteur des règles (BizTalkRuleEngineDb) ;</span><span class="sxs-lookup"><span data-stu-id="d5554-116">Rule Engine (BizTalkRuleEngineDb)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d5554-117">Nous vous recommandons de mettre à jour les informations de compte des instances d'hôte à l'aide de la console Administration de BizTalk Server ou d'un script WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="d5554-117">We recommend that you update account information for host instances by using the BizTalk Server Administration Console or a Windows Management Instrumentation (WMI) script.</span></span> <span data-ttu-id="d5554-118">De cette manière, BizTalk Server peut mettre à jour les informations de compte dans les bases de données BizTalk Server et peut synchroniser la configuration de sécurité entre les bases de données et l'instance d'hôte.</span><span class="sxs-lookup"><span data-stu-id="d5554-118">This ensures that BizTalk Server can update the account information in the BizTalk Server databases and keep the security configuration between the databases and host instance synchronized.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="d5554-119">Étapes</span><span class="sxs-lookup"><span data-stu-id="d5554-119">Steps</span></span>
  
1.  <span data-ttu-id="d5554-120">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="d5554-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="d5554-121">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="d5554-121">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="d5554-122">Dans le volet de détails, cliquez sur l’instance d’hôte que vous voulez arrêter, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="d5554-122">In the details pane, right-click the host instance you want to stop, and then click **Stop**.</span></span>  
  
     <span data-ttu-id="d5554-123">L’état de l’instance d’hôte devient **arrêté**.</span><span class="sxs-lookup"><span data-stu-id="d5554-123">The status of the host instance changes to **Stopped**.</span></span>  
  
 <span data-ttu-id="d5554-124">Après avoir arrêté une instance d'hôte, vous pouvez la démarrer, la supprimer ou désinstaller BizTalk Server de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d5554-124">After you stop a host instance, you can start it, delete it, or remove BizTalk Server from the computer.</span></span> <span data-ttu-id="d5554-125">Pour plus d’informations sur le démarrage d’une instance d’hôte, consultez [comment démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md).</span><span class="sxs-lookup"><span data-stu-id="d5554-125">For information about starting a host instance, see [How to Start a Host Instance](../core/how-to-start-a-host-instance.md).</span></span> <span data-ttu-id="d5554-126">Pour plus d’informations sur la suppression d’une instance d’hôte, consultez [comment supprimer une Instance d’hôte](../core/how-to-delete-a-host-instance.md).</span><span class="sxs-lookup"><span data-stu-id="d5554-126">For information about deleting a host instance, see [How to Delete a Host Instance](../core/how-to-delete-a-host-instance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5554-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5554-127">See Also</span></span>  
 <span data-ttu-id="d5554-128">[La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md) </span><span class="sxs-lookup"><span data-stu-id="d5554-128">[Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md) </span></span>  
 <span data-ttu-id="d5554-129">[L’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="d5554-129">[How to Add a Host Instance](../core/how-to-add-a-host-instance.md) </span></span>  
 <span data-ttu-id="d5554-130">[Comment démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="d5554-130">[How to Start a Host Instance](../core/how-to-start-a-host-instance.md) </span></span>  
 <span data-ttu-id="d5554-131">[Comment supprimer une Instance d’hôte](../core/how-to-delete-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="d5554-131">[How to Delete a Host Instance](../core/how-to-delete-a-host-instance.md) </span></span>  
 [<span data-ttu-id="d5554-132">Comment modifier les propriétés de l’Instance hôte</span><span class="sxs-lookup"><span data-stu-id="d5554-132">How to Modify Host Instance Properties</span></span>](../core/how-to-modify-host-instance-properties.md)