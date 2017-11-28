---
title: "Comment supprimer un Port d’envoi à partir d’un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send port groups, deleting send ports
- managing [send port groups], deleting send ports
- managing [send ports], deleting send ports
- deleting, send ports
- send ports, deleting from send port groups
ms.assetid: a2289bfe-5bc9-4bc7-949c-5152ffb5bc62
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d109064a1286bcd622479a4075ef2d23dc8d320c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-send-port-from-a-send-port-group"></a><span data-ttu-id="91810-102">Suppression d'un port d'envoi d'un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="91810-102">How to Remove a Send Port from a Send Port Group</span></span>
<span data-ttu-id="91810-103">La présente rubrique explique comment supprimer un port d'envoi d'un groupe de ports d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="91810-103">This topic describes how to use the BizTalk Server Administration console to remove a send port from a send port group.</span></span> <span data-ttu-id="91810-104">Lors de cette opération, le port d'envoi n'est pas supprimé de l'application ou de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="91810-104">When you do this, the send port is not deleted from the application or the BizTalk Management database.</span></span>  
  
 <span data-ttu-id="91810-105">Avant de pouvoir supprimer un port d'envoi, il doit être arrêté ou désinscrit.</span><span class="sxs-lookup"><span data-stu-id="91810-105">Before you can remove a send port, it must be in a stopped or unenlisted state.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91810-106">Afin de pouvoir acheminer des messages, un groupe de ports d'envoi doit contenir au moins un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="91810-106">To route messages, a send port group must contain at least one send port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="91810-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="91810-107">Prerequisites</span></span>  
 <span data-ttu-id="91810-108">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="91810-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="91810-109">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="91810-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-remove-a-send-port-from-a-send-port-group"></a><span data-ttu-id="91810-110">Pour supprimer un port d'envoi d’un groupe de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="91810-110">To remove a send port from a send port group</span></span>  
  
1.  <span data-ttu-id="91810-111">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="91810-111">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="91810-112">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dans laquelle supprimer un port d'envoi d'un groupe de ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="91810-112">In the console tree, expand the BizTalk group and the BizTalk application in which you want to remove a send port from a send port group.</span></span>  
  
3.  <span data-ttu-id="91810-113">Cliquez sur **groupes de ports d’envoi**, cliquez sur le groupe de ports d’envoi, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="91810-113">Click **Send Port Groups**, right-click the send port group, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="91810-114">Sous **nom**, cliquez sur le port d’envoi à supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="91810-114">Under **Name**, click the send port to remove, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91810-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91810-115">See Also</span></span>  
 <span data-ttu-id="91810-116">[Création et configuration des groupes de ports d’envoi](../core/creating-and-configuring-send-port-groups.md) </span><span class="sxs-lookup"><span data-stu-id="91810-116">[Creating and Configuring Send Port Groups](../core/creating-and-configuring-send-port-groups.md) </span></span>  
 [<span data-ttu-id="91810-117">Création et configuration des Ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="91810-117">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)