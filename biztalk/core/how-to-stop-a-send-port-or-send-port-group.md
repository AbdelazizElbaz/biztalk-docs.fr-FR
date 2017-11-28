---
title: "Comment arrêter un Port d’envoi ou un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [send ports], stopping
- managing [send port groups], stopping
- stopping, send ports
- send port groups, stopping
- stopping, send port groups
- send ports, stopping
ms.assetid: a7a5eab3-34fe-4417-900a-c37ec16ec009
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94ac3391a7a14955198f7e7635765665d48af1ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-stop-a-send-port-or-send-port-group"></a><span data-ttu-id="da84f-102">Arrêt d'un port d'envoi ou d'un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="da84f-102">How to Stop a Send Port or Send Port Group</span></span>
<span data-ttu-id="da84f-103">La présente rubrique explique comment arrêter un port d'envoi ou un groupe de ports d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="da84f-103">This topic describes how to use the BizTalk Server Administration console to stop a send port or send port group.</span></span> <span data-ttu-id="da84f-104">Lorsque vous arrêtez un port d'envoi ou un groupe de ports d'envoi, il ne peut plus traiter de messages.</span><span class="sxs-lookup"><span data-stu-id="da84f-104">When you stop a send port or send port group, it no longer processes messages.</span></span> <span data-ttu-id="da84f-105">BizTalk Server suspend tous les messages d'activation qu'il envoie vers un port d'envoi ou un groupe de ports d'envoi arrêté.</span><span class="sxs-lookup"><span data-stu-id="da84f-105">BizTalk Server suspends all activation messages to a stopped send port or send port group.</span></span> <span data-ttu-id="da84f-106">Le fait d'arrêter un groupe de ports d'envoi n'affecte pas l'état des ports d'envoi qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="da84f-106">Stopping a send port group does not affect the state of any send ports that it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da84f-107">Par défaut, le démarrage d'une application BizTalk entraîne le démarrage de tous les artefacts que cette application contient.</span><span class="sxs-lookup"><span data-stu-id="da84f-107">By default, starting a BizTalk application starts all of the artifacts that it contains.</span></span> <span data-ttu-id="da84f-108">Pour plus d’informations, consultez [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="da84f-108">For more information, see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="da84f-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="da84f-109">Prerequisites</span></span>  
 <span data-ttu-id="da84f-110">Pour exécuter la procédure dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe opérateurs BizTalk Server ou du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="da84f-110">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Operators group or the BizTalk Server Administrators group.</span></span> <span data-ttu-id="da84f-111">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="da84f-111">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-stop-a-send-port-or-send-port-group"></a><span data-ttu-id="da84f-112">Pour arrêter un port d'envoi ou un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="da84f-112">To stop a send port or send port group</span></span>  
  
1.  <span data-ttu-id="da84f-113">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="da84f-113">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="da84f-114">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le port d’envoi ou un groupe de ports d’envoi que vous souhaitez arrêter.</span><span class="sxs-lookup"><span data-stu-id="da84f-114">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to stop.</span></span>  
  
3.  <span data-ttu-id="da84f-115">Cliquez sur **Ports d’envoi** ou **groupes de ports d’envoi**, cliquez sur le port d’envoi ou un port d’envoi, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="da84f-115">Click **Send Ports** or **Send Port Groups**, right-click the send port or send port, and then click **Stop**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da84f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da84f-116">See Also</span></span>  
 [<span data-ttu-id="da84f-117">La gestion des Ports d’envoi et groupes de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="da84f-117">Managing Send Ports and Send Port Groups</span></span>](../core/managing-send-ports-and-send-port-groups.md)