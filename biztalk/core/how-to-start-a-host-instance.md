---
title: "Démarrer une Instance d’hôte | Documents Microsoft"
description: "Utilisez l’Administration de BizTalk pour démarrer une instance d’hôte dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a96a4362-2147-4b8e-a270-bf9a17477ba3
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd5cccc48b33dda4b6458f8dfa8f56a84ad3cd62
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="start-a-host-instance"></a><span data-ttu-id="f016e-103">Démarrer une Instance d’hôte</span><span class="sxs-lookup"><span data-stu-id="f016e-103">Start a Host Instance</span></span>
<span data-ttu-id="f016e-104">Vous pouvez utiliser la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou Windows Management Instrumentation (WMI) pour démarrer des instances d'hôte.</span><span class="sxs-lookup"><span data-stu-id="f016e-104">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or Windows Management Instrumentation (WMI) to start host instances.</span></span> <span data-ttu-id="f016e-105">Après avoir ajouté ou arrêté une instance d'hôte, vous devez la démarrer pour qu'elle s'exécute et achemine des messages vers les bases de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="f016e-105">After you add or stop a host instance, you must start it so that it is running and routing messages to the MessageBox databases.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f016e-106">Le compte de service que vous spécifiez pour une instance d'hôte doit être un membre du groupe Windows pour l'hôte associé.</span><span class="sxs-lookup"><span data-stu-id="f016e-106">The service account that you specify for a host instance should be a member of the Windows group for the associated host.</span></span> <span data-ttu-id="f016e-107">Sinon, cette instance risque de ne pas disposer des autorisations ou de l'authentification appropriées au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="f016e-107">Otherwise, the host instance may not have the appropriate permissions or authentication at run time.</span></span> <span data-ttu-id="f016e-108">En outre, pour des raisons de sécurité, le compte doit disposer de privilèges minimaux, car les orchestrations hébergées par l'instance de l'hôte peuvent exécuter un code personnalisé potentiellement nuisible.</span><span class="sxs-lookup"><span data-stu-id="f016e-108">In addition, for security reasons, the account should have minimum privileges because orchestrations hosted by the host instance might execute potentially malicious custom code.</span></span>  
  
 <span data-ttu-id="f016e-109">Pour plus d’informations sur les instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md).</span><span class="sxs-lookup"><span data-stu-id="f016e-109">For more information about host instances, see [Host Instances](../core/host-instances.md).</span></span> <span data-ttu-id="f016e-110">Pour plus d’informations sur l’utilisation de WMI pour démarrer une instance d’hôte, consultez **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="f016e-110">For information about using WMI to start a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="f016e-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f016e-111">Prerequisites</span></span>  
 <span data-ttu-id="f016e-112">Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs BizTalk Server ou du groupe des administrateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="f016e-112">To perform this procedure, you must be logged on as a member of the Administrators group and the BizTalk Server Administrators group.</span></span>  
  
 <span data-ttu-id="f016e-113">Vous devez également être un membre du rôle de la base de données SQL Server db_securityadmin et du rôle SQL Server securityadmin sur les serveurs sur lesquels se trouvent les bases de données suivantes :</span><span class="sxs-lookup"><span data-stu-id="f016e-113">In addition, you must also be a member of the db_securityadmin SQL Server Database role and the securityadmin SQL Server Role on the server(s) where the following databases are:</span></span>  
  
-   <span data-ttu-id="f016e-114">importation principale BAM (BAMPrimaryImport).</span><span class="sxs-lookup"><span data-stu-id="f016e-114">BAM Primary Import (BAMPrimaryImport)</span></span>  
  
-   <span data-ttu-id="f016e-115">gestion BizTalk (BizTalkMgmtDb) ;</span><span class="sxs-lookup"><span data-stu-id="f016e-115">BizTalk Management (BizTalkMgmtDb)</span></span>  
  
-   <span data-ttu-id="f016e-116">MessageBox BizTalk (BizTalkMsgBoxDb) (tout) ;</span><span class="sxs-lookup"><span data-stu-id="f016e-116">BizTalk MessageBox (BizTalkMsgBoxDb) (all)</span></span>  
  
-   <span data-ttu-id="f016e-117">suivis BizTalk (BizTalkDTADb) ;</span><span class="sxs-lookup"><span data-stu-id="f016e-117">BizTalk Tracking (BizTalk DTADb)</span></span>  
  
-   <span data-ttu-id="f016e-118">moteur des règles (BizTalkRuleEngineDb) ;</span><span class="sxs-lookup"><span data-stu-id="f016e-118">Rule Engine (BizTalkRuleEngineDb)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f016e-119">Nous vous recommandons de mettre à jour les informations de compte des instances d'hôte à l'aide de la console Administration de BizTalk Server ou d'un script WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="f016e-119">We recommend that you update account information for host instances by using the BizTalk Server Administration Console or a Windows Management Instrumentation (WMI) script.</span></span> <span data-ttu-id="f016e-120">De cette manière, BizTalk Server peut mettre à jour les informations de compte dans les bases de données BizTalk Server et peut synchroniser la configuration de sécurité entre les bases de données et l'instance d'hôte.</span><span class="sxs-lookup"><span data-stu-id="f016e-120">This ensures that BizTalk Server can update the account information in the BizTalk Server databases and keep the security configuration between the databases and host instance synchronized.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="f016e-121">Étapes</span><span class="sxs-lookup"><span data-stu-id="f016e-121">Steps</span></span>
  
1.  <span data-ttu-id="f016e-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="f016e-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="f016e-123">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="f016e-123">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="f016e-124">Dans le volet de détails, cliquez sur l’instance d’hôte que vous souhaitez démarrer, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="f016e-124">In the details pane, right-click the host instance you want to start, and then click **Start**.</span></span>  
  
     <span data-ttu-id="f016e-125">L’état de l’instance d’hôte devient **attente de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="f016e-125">The status of the host instance changes to **Start pending**.</span></span> <span data-ttu-id="f016e-126">Une fois que l’instance d’hôte démarre, l’état passe à **en cours d’exécution**.</span><span class="sxs-lookup"><span data-stu-id="f016e-126">After the host instance initiates, the status changes to **Running**.</span></span>  
  
 <span data-ttu-id="f016e-127">Après avoir lancé une instance d'hôte, vous pouvez l'arrêter pour l'empêcher d'acheminer des messages vers la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="f016e-127">After you start a host instance, you can stop it to prevent it from routing messages to the MessageBox database.</span></span> <span data-ttu-id="f016e-128">Vous devez arrêter une instance d'hôte pour pouvoir désinstaller BizTalk Server d'un ordinateur donné.</span><span class="sxs-lookup"><span data-stu-id="f016e-128">You must stop a host instance before you can remove BizTalk Server from a given computer.</span></span> <span data-ttu-id="f016e-129">Pour plus d’informations sur l’arrêt d’une instance d’hôte, consultez [comment arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md).</span><span class="sxs-lookup"><span data-stu-id="f016e-129">For information about stopping a host instance, see [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f016e-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f016e-130">See Also</span></span>  
 <span data-ttu-id="f016e-131">[La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md) </span><span class="sxs-lookup"><span data-stu-id="f016e-131">[Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md) </span></span>  
 <span data-ttu-id="f016e-132">[Ajouter une Instance d’hôte](../core/how-to-add-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="f016e-132">[Add a Host Instance](../core/how-to-add-a-host-instance.md) </span></span>  
 <span data-ttu-id="f016e-133">[Arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="f016e-133">[Stop a Host Instance](../core/how-to-stop-a-host-instance.md) </span></span>  
 <span data-ttu-id="f016e-134">[Supprimer une Instance d’hôte](../core/how-to-delete-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="f016e-134">[Delete a Host Instance](../core/how-to-delete-a-host-instance.md) </span></span>  
 [<span data-ttu-id="f016e-135">Modifier les propriétés de l’Instance hôte</span><span class="sxs-lookup"><span data-stu-id="f016e-135">Modify Host Instance Properties</span></span>](../core/how-to-modify-host-instance-properties.md)