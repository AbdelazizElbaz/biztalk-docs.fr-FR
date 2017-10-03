---
title: "Comment supprimer un serveur d’un groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups, servers
- managing [groups], deleting servers
- servers, deleting
- deleting, groups
- servers
- managing [servers], deleting from groups
- groups, deleting
- servers, groups
- deleting, servers
ms.assetid: 85596e18-fa17-4f44-bc20-2e4cb578e109
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b69eb694da320e598c7d0cfe5a03d58e0a723a8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-server-from-a-group"></a><span data-ttu-id="d7b85-102">Suppression d'un serveur d'un groupe</span><span class="sxs-lookup"><span data-stu-id="d7b85-102">How to Remove a Server from a Group</span></span>
<span data-ttu-id="d7b85-103">Un serveur peut uniquement être associé à un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d7b85-103">A server can only be associated with one BizTalk group.</span></span> <span data-ttu-id="d7b85-104">Si un serveur appartient déjà à un autre groupe, vous devez le supprimer de son groupe actuel avant de l'ajouter à un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="d7b85-104">If a server already belongs to another group, you must first remove that server from its current group before you can add it to a new group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d7b85-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d7b85-105">Prerequisites</span></span>  
 <span data-ttu-id="d7b85-106">Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="d7b85-106">To perform this procedure, you must be logged on as a member of the Windows Administrators group.</span></span>  
  
### <a name="to-remove-a-server-from-a-group"></a><span data-ttu-id="d7b85-107">Pour supprimer un serveur d'un groupe</span><span class="sxs-lookup"><span data-stu-id="d7b85-107">To remove a server from a group</span></span>  
  
1.  <span data-ttu-id="d7b85-108">Sur l’ordinateur que vous souhaitez supprimer d’un groupe BizTalk Server, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **deConfigurationdeBizTalkServer**.</span><span class="sxs-lookup"><span data-stu-id="d7b85-108">On the computer that you want to remove from a BizTalk Server group, click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
2.  <span data-ttu-id="d7b85-109">Dans la barre de menus, cliquez sur **annuler la configuration des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="d7b85-109">On the menu bar, click **Unconfigure Features**.</span></span>  
  
3.  <span data-ttu-id="d7b85-110">Dans le **annuler la configuration des fonctionnalités** boîte de dialogue, sélectionnez **groupe**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d7b85-110">In the **Unconfigure Features** dialog box, select **Group**, and then click **OK**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="d7b85-111">L'annulation de la configuration d'un groupe annule également la configuration de tous les composants dépendants déjà configurés sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d7b85-111">Unconfiguring a group will also unconfigure all dependent features that are already configured on that computer.</span></span>  
  
4.  <span data-ttu-id="d7b85-112">Cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="d7b85-112">Click **Yes**.</span></span>  
  
5.  <span data-ttu-id="d7b85-113">Dans l’Assistant Configuration de Microsoft BizTalk Server, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="d7b85-113">In the Microsoft BizTalk Server Configuration Wizard, click **Next**.</span></span>  
  
     <span data-ttu-id="d7b85-114">La configuration du groupe et de ses composants dépendants est annulée.</span><span class="sxs-lookup"><span data-stu-id="d7b85-114">The Group and its dependent features are unconfigured.</span></span>  
  
6.  <span data-ttu-id="d7b85-115">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="d7b85-115">Click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7b85-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7b85-116">See Also</span></span>  
 <span data-ttu-id="d7b85-117">[Gestion des groupes](../core/managing-groups.md) </span><span class="sxs-lookup"><span data-stu-id="d7b85-117">[Managing Groups](../core/managing-groups.md) </span></span>  
 <span data-ttu-id="d7b85-118">[Groupes BizTalk](../core/biztalk-groups.md) </span><span class="sxs-lookup"><span data-stu-id="d7b85-118">[BizTalk Groups](../core/biztalk-groups.md) </span></span>  
 <span data-ttu-id="d7b85-119">[Comment ajouter un serveur à un groupe](../core/how-to-add-a-server-to-a-group.md) </span><span class="sxs-lookup"><span data-stu-id="d7b85-119">[How to Add a Server to a Group](../core/how-to-add-a-server-to-a-group.md) </span></span>  
 <span data-ttu-id="d7b85-120">[Comment déplacer un serveur à partir d’un groupe à un autre](../core/how-to-move-a-server-from-one-group-to-another.md) </span><span class="sxs-lookup"><span data-stu-id="d7b85-120">[How to Move a Server from One Group to Another](../core/how-to-move-a-server-from-one-group-to-another.md) </span></span>  
 <span data-ttu-id="d7b85-121">[Comment modifier les propriétés du groupe](../core/how-to-modify-group-properties.md) </span><span class="sxs-lookup"><span data-stu-id="d7b85-121">[How to Modify Group Properties](../core/how-to-modify-group-properties.md) </span></span>  
 [<span data-ttu-id="d7b85-122">Gestion des serveurs</span><span class="sxs-lookup"><span data-stu-id="d7b85-122">Managing Servers</span></span>](../core/managing-servers.md)