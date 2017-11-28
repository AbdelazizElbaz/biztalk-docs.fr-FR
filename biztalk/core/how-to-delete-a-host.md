---
title: "Suppression d’un hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3df8719-27cb-4010-82e3-68226ab74b17
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fd5f54fa84ddb521444cfb3f2351a8062c4de00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delete-a-host"></a><span data-ttu-id="0bcc0-102">Suppression d’un hôte</span><span class="sxs-lookup"><span data-stu-id="0bcc0-102">Delete a Host</span></span>
<span data-ttu-id="0bcc0-103">Vous ne pouvez supprimer un hôte que dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="0bcc0-103">You can delete a host only in the following circumstances:</span></span>  
  
-   <span data-ttu-id="0bcc0-104">Il ne s'agit pas de l'hôte par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bcc0-104">It is not the default host.</span></span>  
  
-   <span data-ttu-id="0bcc0-105">Cet hôte n'est pas seul à effectuer le suivi des hôtes.</span><span class="sxs-lookup"><span data-stu-id="0bcc0-105">It is not the only host that is performing host tracking.</span></span>  
  
-   <span data-ttu-id="0bcc0-106">Il n'héberge pas de gestionnaires d'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="0bcc0-106">It is not hosting any adapter handlers.</span></span>  
  
-   <span data-ttu-id="0bcc0-107">Aucune orchestration n'est inscrite pour cet hôte.</span><span class="sxs-lookup"><span data-stu-id="0bcc0-107">It has no enlisted orchestrations.</span></span>  
  
-   <span data-ttu-id="0bcc0-108">Aucune instance de l'hôte n'est lancée.</span><span class="sxs-lookup"><span data-stu-id="0bcc0-108">There are no started instances of the host.</span></span>  
  
-   <span data-ttu-id="0bcc0-109">Si l'hôte n'est pas mis en cluster.</span><span class="sxs-lookup"><span data-stu-id="0bcc0-109">If the host is not clustered.</span></span>  
  
 <span data-ttu-id="0bcc0-110">Pour plus d’informations sur les ordinateurs hôtes, consultez [hôtes](../core/hosts.md).</span><span class="sxs-lookup"><span data-stu-id="0bcc0-110">For more information about hosts, see [Hosts](../core/hosts.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0bcc0-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0bcc0-111">Prerequisites</span></span>  
 <span data-ttu-id="0bcc0-112">Vous devez disposer des droits d'utilisateur suivants pour créer ou supprimer des hôtes et pour modifier leurs propriétés :</span><span class="sxs-lookup"><span data-stu-id="0bcc0-112">You must have the following user rights to create hosts, modify host properties, and delete hosts:</span></span>  
  
-   <span data-ttu-id="0bcc0-113">Vous devez être membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0bcc0-113">You must be a member of the BizTalk Server Administrators group.</span></span>  
  
-   <span data-ttu-id="0bcc0-114">Les droits suivants sont requis dans SQL Server :</span><span class="sxs-lookup"><span data-stu-id="0bcc0-114">You must have the following rights in SQL Server:</span></span>  
  
    -   <span data-ttu-id="0bcc0-115">Vous devez être soit un administrateur SQL Server, soit un membre des rôles de base de données SQL Server db_owner ou db_securityadmin dans la base de données des suivis BizTalk (BizTalk DTADb), dans les bases de données MessageBox (BizTalkMsgBoxDb) et dans la base de données d'importation principale BAM (BAMPrimaryImport).</span><span class="sxs-lookup"><span data-stu-id="0bcc0-115">You must be either a SQL Server administrator, or a member of the db_owner or db_securityadmin SQL Server database roles in the BizTalk Tracking database (BizTalk DTADb), MessageBox databases (BizTalkMsgBoxDb), and the BAM Primary Import database (BAMPrimaryImport).</span></span>  
  
    -   <span data-ttu-id="0bcc0-116">Vous devez être membre du rôle SQL Server sysadmin sur tous les ordinateurs où résident des bases de données MessageBox, ou membre du rôle SQL Server db_owner ou db_ddladmin pour toutes les bases de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="0bcc0-116">You must be a member of the sysadmin SQL Server role on all the computers where there are MessageBox databases, or a member of the db_owner or db_ddladmin SQL Server role for all the MessageBox databases.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="0bcc0-117">Étapes</span><span class="sxs-lookup"><span data-stu-id="0bcc0-117">Steps</span></span> 
  
1.  <span data-ttu-id="0bcc0-118">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="0bcc0-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0bcc0-119">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **hôtes**.</span><span class="sxs-lookup"><span data-stu-id="0bcc0-119">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Hosts**.</span></span>  
  
3.  <span data-ttu-id="0bcc0-120">Dans le volet de détails, cliquez sur l’hôte que vous souhaitez supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="0bcc0-120">In the details pane, right-click the host you want to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="0bcc0-121">Dans le **confirmer la suppression hôte** boîte de dialogue, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="0bcc0-121">In the **Confirm host delete** dialog box, click **Yes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bcc0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bcc0-122">See Also</span></span>  
-  [<span data-ttu-id="0bcc0-123">Gestion des hôtes et des instances d’hôte BizTalk</span><span class="sxs-lookup"><span data-stu-id="0bcc0-123">Managing BizTalk Hosts and Host Instances</span></span>](../core/managing-biztalk-hosts-and-host-instances.md)   
-  [<span data-ttu-id="0bcc0-124">Comment créer un nouvel hôte</span><span class="sxs-lookup"><span data-stu-id="0bcc0-124">How to Create a New Host</span></span>](../core/how-to-create-a-new-host.md)   
-  [<span data-ttu-id="0bcc0-125">Comment modifier les propriétés de l’hôte</span><span class="sxs-lookup"><span data-stu-id="0bcc0-125">How to Modify Host Properties</span></span>](../core/how-to-modify-host-properties.md)   
-  <span data-ttu-id="0bcc0-126">**MSBTS_Host (WMI)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="0bcc0-126">**MSBTS_Host (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>