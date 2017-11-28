---
title: "Groupes hôtes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host groups, privileges
- Windows groups, host groups
- host groups, Windows groups
- host groups, about host groups
- host groups
ms.assetid: 0d92478b-b3a2-4c5a-925e-5495ee481e82
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d5e7782dd2e98822d6fc9e51ca08dac2d31f166
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="host-groups"></a><span data-ttu-id="7aa67-102">Groupes d'hôtes</span><span class="sxs-lookup"><span data-stu-id="7aa67-102">Host Groups</span></span>
<span data-ttu-id="7aa67-103">Le groupe d'hôtes est le groupe Windows (appelé groupe Utilisateurs d'applications BizTalk par défaut) que vous utilisez pour vos comptes avec accès aux hôtes BizTalk In-process (processus hôtes dans BizTalk Server).</span><span class="sxs-lookup"><span data-stu-id="7aa67-103">The host group is the Windows group (named the BizTalk Application Users group by default) that you use for accounts with access to the in-process BizTalk hosts (host processes in BizTalk Server).</span></span> <span data-ttu-id="7aa67-104">Il est conseillé d'utiliser un groupe d'hôtes pour chaque hôte In-process de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="7aa67-104">It is recommended that you use one host group for each in-process host in your environment.</span></span>  
  
 <span data-ttu-id="7aa67-105">Vous ne pouvez associer un ordinateur hôte à un groupe Windows (appelé un *groupe hôte*).</span><span class="sxs-lookup"><span data-stu-id="7aa67-105">You can only associate a host with one Windows group (called a *host group*).</span></span> <span data-ttu-id="7aa67-106">Ce groupe d'hôtes doit avoir une connexion et des privilèges SQL Server dans toutes les bases de données BizTalk Server appropriées.</span><span class="sxs-lookup"><span data-stu-id="7aa67-106">The host group must have a SQL Server login and privileges in all relevant BizTalk Server databases.</span></span> <span data-ttu-id="7aa67-107">Lorsque vous associez un hôte au groupe d'hôtes, vous accordez à cet hôte les privilèges du groupe.</span><span class="sxs-lookup"><span data-stu-id="7aa67-107">When you associate a host with the host group, you grant the host the privileges of the host group.</span></span>  
  
 <span data-ttu-id="7aa67-108">Si vous faites appel à l'Assistant Configuration pour créer des hôtes et que vous spécifiez un groupe Windows local qui sera utilisé pour ces hôtes, l'Assistant crée automatiquement deux groupes Windows.</span><span class="sxs-lookup"><span data-stu-id="7aa67-108">If you use the Configuration Wizard to create hosts, and you specify a local Windows group to use for hosts, the Configuration Wizard automatically creates two Windows groups.</span></span> <span data-ttu-id="7aa67-109">Par défaut, ces groupes sont appelés Utilisateurs d'applications BizTalk et Utilisateurs d'hôtes BizTalk isolés.</span><span class="sxs-lookup"><span data-stu-id="7aa67-109">The default names of these groups are the BizTalk Application Users group and the BizTalk Isolated Host Users group.</span></span>  
  
 <span data-ttu-id="7aa67-110">Lorsque vous créez une instance d'un hôte associé au groupe d'hôtes, cette instance hérite des privilèges de base de données du groupe.</span><span class="sxs-lookup"><span data-stu-id="7aa67-110">When you create a host instance of a host associated with the host group, the host instance inherits the database privileges of the host group.</span></span>  
  
 <span data-ttu-id="7aa67-111">Le groupe d'hôte est une propriété de l'objet Windows Management Instrumentation (WMI) hôte.</span><span class="sxs-lookup"><span data-stu-id="7aa67-111">The host group is a property of the host Windows Management Instrumentation (WMI) object.</span></span> <span data-ttu-id="7aa67-112">Vous pouvez changer le groupe Windows auquel un hôte appartient s'il n'existe pas d'instances de cet hôte.</span><span class="sxs-lookup"><span data-stu-id="7aa67-112">You can change the Windows group that a host belongs to if there are no host instances of the host.</span></span>  
  
 <span data-ttu-id="7aa67-113">Vous spécifiez le groupe d'hôtes auquel un hôte appartient lorsque vous créez cet hôte.</span><span class="sxs-lookup"><span data-stu-id="7aa67-113">You specify the host group a host belongs to when you create the host.</span></span> <span data-ttu-id="7aa67-114">Le fournisseur BizTalk WMI accorde à l'hôte les privilèges que le groupe d'hôtes détient (par exemple, les privilèges BizTalk Server requis pour la fonctionnalité d'exécution, y compris les connexions SQL Server et l'accès utilisateur à la base de données).</span><span class="sxs-lookup"><span data-stu-id="7aa67-114">The BizTalk WMI provider grants the privileges that the host group has (for example, the BizTalk Server privileges required for runtime functionality, including SQL Server logins and database user access) to the host.</span></span> <span data-ttu-id="7aa67-115">Vous devez spécifier le compte de service (hôte) correct lorsque vous créez une instance d'hôte afin que le fournisseur BizTalk Server WMI octroie les privilèges du groupe d'hôtes à cette instance.</span><span class="sxs-lookup"><span data-stu-id="7aa67-115">You must specify the correct service account (host) when you create a host instance, so that the BizTalk Server WMI provider grants the privileges of the host group to the host instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7aa67-116">Si vous voulez créer un groupe d'hôtes local, vous pouvez définir un groupe Windows local et assigner un utilisateur du domaine comme membre du groupe.</span><span class="sxs-lookup"><span data-stu-id="7aa67-116">If you want to create a local host group, you can create a local Windows group and assign a domain user as a member of the group.</span></span> <span data-ttu-id="7aa67-117">Si vous voulez spécifier un groupe Windows local pour l'hôte, vous pouvez utiliser le membre du groupe Windows, qu'il s'agisse d'un utilisateur du domaine ou d'un utilisateur local, comme utilisateur de connexion de l'instance d'hôte.</span><span class="sxs-lookup"><span data-stu-id="7aa67-117">If you specify a local Windows group for the Host, the Windows group member, whether it is a domain or local user, can be used as the host instance log-on user.</span></span>  
  
 <span data-ttu-id="7aa67-118">Le groupe d'hôtes requiert les privilèges suivants :</span><span class="sxs-lookup"><span data-stu-id="7aa67-118">The host group requires the following privileges:</span></span>  
  
-   <span data-ttu-id="7aa67-119">Il doit être membre du rôle SQL Server BTS_HOST_USERS dans les bases de données suivantes :</span><span class="sxs-lookup"><span data-stu-id="7aa67-119">It must be a member of the BTS_HOST_USERS SQL Server role in the following databases:</span></span>  
  
    -   <span data-ttu-id="7aa67-120">Base de données de gestion BizTalk (également appelée Base de données de configuration dans [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)])</span><span class="sxs-lookup"><span data-stu-id="7aa67-120">BizTalk Management (known as the Configuration database in [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)])</span></span>  
  
    -   <span data-ttu-id="7aa67-121">MessageBox</span><span class="sxs-lookup"><span data-stu-id="7aa67-121">MessageBox</span></span>  
  
    -   <span data-ttu-id="7aa67-122">Moteur de règles</span><span class="sxs-lookup"><span data-stu-id="7aa67-122">Rule Engine</span></span>  
  
    -   <span data-ttu-id="7aa67-123">Suivi</span><span class="sxs-lookup"><span data-stu-id="7aa67-123">Tracking</span></span>  
  
    -   <span data-ttu-id="7aa67-124">Importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="7aa67-124">BAM Primary Import</span></span>  
  
-   <span data-ttu-id="7aa67-125">Il doit être un membre de la BTS_\<nom de l’hôte in-process > rôle de SQL Server _USERS pour la base de données MessageBox</span><span class="sxs-lookup"><span data-stu-id="7aa67-125">It must be a member of the BTS_\<in-process host name>_USERS SQL Server role for the MessageBox database</span></span>  
  
-   <span data-ttu-id="7aa67-126">Il doit être membre du rôle SQL Server BAM_EVENT_WRITER dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="7aa67-126">It must be a member of the BAM_EVENT_WRITER SQL Server role in the BAM Primary Import database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7aa67-127">Si vous désignez un hôte comme hôte de suivi, l'Administration de BizTalk Server supprime automatiquement le groupe d'hôtes BizTalk des rôles SQL Server pour la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7aa67-127">If you designate a host as a tracking host, BizTalk Server Administration automatically removes the BizTalk Host group from the SQL Server roles for the Tracking database.</span></span> <span data-ttu-id="7aa67-128">Vous devez supprimer manuellement le groupe d'hôtes BizTalk dans les rôles SQL Server pour la base de données de gestion BizTalk et la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="7aa67-128">You must manually remove the BizTalk Host group from the SQL Server roles for the BizTalk Management database and the MessageBox database.</span></span> <span data-ttu-id="7aa67-129">Pour plus d’informations sur la désignation d’un ordinateur hôte comme hôte de suivi, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).</span><span class="sxs-lookup"><span data-stu-id="7aa67-129">For information about designating a host as a tracking host, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aa67-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7aa67-130">See Also</span></span>  
 [<span data-ttu-id="7aa67-131">Entités</span><span class="sxs-lookup"><span data-stu-id="7aa67-131">Entities</span></span>](../core/entities.md)