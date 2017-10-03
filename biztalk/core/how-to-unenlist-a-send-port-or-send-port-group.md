---
title: "Comment désinscrire un Port d’envoi ou un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unenlisting, send port groups
- send port groups, unenlisting
- managing [send ports], unenlisting
- managing [send port groups], unenlisting
- unenlisting, send ports
- send ports, unenlisting
ms.assetid: 3185adad-2efa-4abd-a532-77ae6c7b4c1d
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac2599ae3d06a75506de244a4f996a9e77cef6ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-unenlist-a-send-port-or-send-port-group"></a><span data-ttu-id="48ed8-102">Désinscription d'un port d'envoi ou d'un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="48ed8-102">How to Unenlist a Send Port or Send Port Group</span></span>
<span data-ttu-id="48ed8-103">La présente rubrique explique comment désinscrire un port d'envoi ou un groupe de ports d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="48ed8-103">This topic describes how to use the BizTalk Server Administration console to unenlist a send port or send port group.</span></span> <span data-ttu-id="48ed8-104">Désinscrire un port d'envoi ou un groupe de ports d'envoi permet de supprimer tous les abonnements associés à ces éléments.</span><span class="sxs-lookup"><span data-stu-id="48ed8-104">Unenlisting a send port or send port group eliminates all subscriptions associated with that send port or send port group.</span></span> <span data-ttu-id="48ed8-105">Vous pouvez désinscrire les ports d'envoi ou les groupes de ports d'envoi en cours d'exécution ou arrêtés.</span><span class="sxs-lookup"><span data-stu-id="48ed8-105">You can unenlist both running and stopped send ports or send port groups.</span></span> <span data-ttu-id="48ed8-106">La désinscription d'un port d'envoi ou d'un groupe de ports d'envoi arrête automatiquement ce dernier.</span><span class="sxs-lookup"><span data-stu-id="48ed8-106">Unenlisting a send port or send port group automatically stops it.</span></span>  
  
 <span data-ttu-id="48ed8-107">Vous pouvez par exemple vouloir désinscrire un port d'envoi ou un groupe de ports d'envoi pour modifier ses liaisons, ou encore pour les supprimer de l'environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="48ed8-107">For example, you may want to unenlist a send port or send port group to edit its bindings, or if you want to remove the send port or send port group from the BizTalk Server environment.</span></span>  
  
 <span data-ttu-id="48ed8-108">Vous ne pouvez pas désinscrire le dernier port d'envoi inscrit d'un groupe de ports d'envoi inscrit ou en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="48ed8-108">You cannot unenlist the last enlisted send port within a send port group that is enlisted or running.</span></span> <span data-ttu-id="48ed8-109">Le fait de désinscrire un groupe de ports d'envoi ne modifie pas l'état des ports d'envoi qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="48ed8-109">Unenlisting a send port group does not change the state of any send ports that it contains.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="48ed8-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="48ed8-110">Prerequisites</span></span>  
 <span data-ttu-id="48ed8-111">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="48ed8-111">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="48ed8-112">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="48ed8-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-unenlist-a-send-port-or-send-port-group"></a><span data-ttu-id="48ed8-113">Pour désinscrire un port d'envoi ou un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="48ed8-113">To unenlist a send port or send port group</span></span>  
  
1.  <span data-ttu-id="48ed8-114">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="48ed8-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="48ed8-115">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le port d’envoi ou un groupe de ports d’envoi que vous souhaitez Annuler l’inscription.</span><span class="sxs-lookup"><span data-stu-id="48ed8-115">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to unenlist.</span></span>  
  
3.  <span data-ttu-id="48ed8-116">Cliquez sur **Ports d’envoi** ou **groupes de ports d’envoi**, cliquez sur le port d’envoi ou un groupe de ports d’envoi, puis cliquez sur **désinscrire**.</span><span class="sxs-lookup"><span data-stu-id="48ed8-116">Click **Send Ports** or **Send Port Groups**, right-click the send port or send port group, and then click **Unenlist**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ed8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48ed8-117">See Also</span></span>  
 [<span data-ttu-id="48ed8-118">La gestion des Ports d’envoi et groupes de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="48ed8-118">Managing Send Ports and Send Port Groups</span></span>](../core/managing-send-ports-and-send-port-groups.md)