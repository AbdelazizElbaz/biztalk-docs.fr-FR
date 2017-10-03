---
title: "Comment supprimer un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send port groups, deleting
- managing [send port groups], deleting
- deleting, send port groups
ms.assetid: 90c01e58-d35c-4cb2-ac6d-92199199fb42
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86ddecbe657b8ea52a47133c5237bbad6a10b2f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-a-send-port-group"></a><span data-ttu-id="7ae57-102">Suppression d'un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="7ae57-102">How to Delete a Send Port Group</span></span>
<span data-ttu-id="7ae57-103">La présente rubrique explique comment supprimer un groupe de ports d'envoi d'une application BizTalk à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7ae57-103">This topic describes how use the BizTalk Server Administration console to delete a send port group from a BizTalk application.</span></span> <span data-ttu-id="7ae57-104">Lors de cette opération, le groupe de ports d'envoi est également supprimé de la base de données de gestion BizTalk associée au groupe.</span><span class="sxs-lookup"><span data-stu-id="7ae57-104">When you do this, the send port group is also deleted from the BizTalk Management database for the group.</span></span> <span data-ttu-id="7ae57-105">Supprimer un groupe de ports d'envoi ne supprime aucun des ports d'envoi qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="7ae57-105">Deleting a send port group does not delete any send ports that it contains.</span></span>  
  
 <span data-ttu-id="7ae57-106">Vous ne pouvez supprimer un groupe de ports d'envoi que s'il remplit les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="7ae57-106">You can delete a send port group only if it meets the following conditions:</span></span>  
  
-   <span data-ttu-id="7ae57-107">Le groupe de ports d'envoi n'est lié à aucune orchestration.</span><span class="sxs-lookup"><span data-stu-id="7ae57-107">An orchestration is not bound to the send port group.</span></span> <span data-ttu-id="7ae57-108">Si c’est le cas, vous pouvez supprimer la liaison en suivant les instructions de [comment annuler une Orchestration](../core/how-to-unbind-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="7ae57-108">If this is the case, you can remove the binding by following the instructions in [How to Unbind an Orchestration](../core/how-to-unbind-an-orchestration.md).</span></span>  
  
-   <span data-ttu-id="7ae57-109">Le groupe de ports d'envoi est arrêté et désinscrit.</span><span class="sxs-lookup"><span data-stu-id="7ae57-109">The send port group is both stopped and unenlisted.</span></span> <span data-ttu-id="7ae57-110">Pour obtenir des instructions sur l’arrêt et Désinscription d’un port d’envoi, consultez [comment désinscrire un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-unenlist-a-send-port-or-send-port-group.md) et [comment arrêter un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-stop-a-send-port-or-send-port-group.md).</span><span class="sxs-lookup"><span data-stu-id="7ae57-110">For instructions on stopping and unenlisting a send port, see [How to Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md) and [How to Stop a Send Port or Send Port Group](../core/how-to-stop-a-send-port-or-send-port-group.md).</span></span>  
  
-   <span data-ttu-id="7ae57-111">Le groupe de ports d'envoi n'est pas référencé par un tiers.</span><span class="sxs-lookup"><span data-stu-id="7ae57-111">The send port group is not referenced by a party.</span></span> <span data-ttu-id="7ae57-112">Pour obtenir des instructions sur la suppression d’une référence à un groupe de ports d’envoi d’un tiers, consultez [comment afficher ou modifier un tiers](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca).</span><span class="sxs-lookup"><span data-stu-id="7ae57-112">For instructions on removing a reference to a send port group from a party, see [How to View or Edit a Party](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7ae57-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7ae57-113">Prerequisites</span></span>  
 <span data-ttu-id="7ae57-114">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7ae57-114">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="7ae57-115">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="7ae57-115">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-delete-a-send-port-group"></a><span data-ttu-id="7ae57-116">Pour supprimer un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="7ae57-116">To delete a send port group</span></span>  
  
1.  <span data-ttu-id="7ae57-117">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="7ae57-117">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7ae57-118">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, **Applications**, puis développez l’application contenant le groupe de ports d’envoi que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="7ae57-118">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the send port group that you want to delete.</span></span>  
  
3.  <span data-ttu-id="7ae57-119">Cliquez sur **groupes de ports d’envoi**, cliquez sur le groupe de ports d’envoi, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="7ae57-119">Click **Send Port Groups**, right-click the send port group, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae57-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ae57-120">See Also</span></span>  
 [<span data-ttu-id="7ae57-121">Création et configuration des groupes de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="7ae57-121">Creating and Configuring Send Port Groups</span></span>](../core/creating-and-configuring-send-port-groups.md)