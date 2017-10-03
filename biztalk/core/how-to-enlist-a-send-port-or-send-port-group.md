---
title: "L’inscription d’un Port d’envoi ou un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enlisting, send port groups
- enlisting, send ports
- send port groups, enlisting
- send ports, enlisting
- managing [send ports], enlisting
- managing [send port groups], enlisting
ms.assetid: d4298b8e-7dc7-4382-af86-c4db0982b7e0
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb42a4ceaa88ca3d04b5dfb6d6d3afc11847421a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enlist-a-send-port-or-send-port-group"></a><span data-ttu-id="79602-102">Inscription d'un port d'envoi ou d'un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="79602-102">How to Enlist a Send Port or Send Port Group</span></span>
<span data-ttu-id="79602-103">La présente rubrique explique comment inscrire un port d'envoi ou un groupe de ports d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="79602-103">This topic describes how to use the BizTalk Server Administration console to enlist a send port or send port group.</span></span> <span data-ttu-id="79602-104">L'inscription d'un port d'envoi ou d'un groupe de ports d'envoi associe le port ou le groupe à un hôte BizTalk et crée les abonnements correspondants.</span><span class="sxs-lookup"><span data-stu-id="79602-104">Enlisting a send port or send port group associates the send port or send port group with a BizTalk host and creates the subscriptions for the send port or send port group.</span></span> <span data-ttu-id="79602-105">Si un groupe de ports d'envoi ne contient pas de port d'envoi, le fait d'inscrire ce groupe n'entraîne pas la création d'abonnements.</span><span class="sxs-lookup"><span data-stu-id="79602-105">If a send port group does not contain a send port, enlisting the send port group does not create any subscriptions.</span></span> <span data-ttu-id="79602-106">De plus, le fait d'inscrire un groupe de ports d'envoi ne modifie pas l'état des ports d'envoi qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="79602-106">In addition, enlisting a send port group does not change the state of any send ports that it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79602-107">Le démarrage d'un port d'envoi ou d'un groupe de ports d'envoi entraîne automatiquement son inscription.</span><span class="sxs-lookup"><span data-stu-id="79602-107">Starting a send port or send port group also automatically enlists it.</span></span> <span data-ttu-id="79602-108">Par défaut, le démarrage d'une application entraîne l'inscription et le démarrage de tous ses artefacts.</span><span class="sxs-lookup"><span data-stu-id="79602-108">In addition, by default starting an application enlists and starts all of its artifacts.</span></span> <span data-ttu-id="79602-109">Pour plus d’informations, consultez [comment démarrer un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-start-a-send-port-or-send-port-group.md).</span><span class="sxs-lookup"><span data-stu-id="79602-109">For more information, see [How to Start a Send Port or Send Port Group](../core/how-to-start-a-send-port-or-send-port-group.md).</span></span> <span data-ttu-id="79602-110">Consultez également [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="79602-110">Also see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="79602-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="79602-111">Prerequisites</span></span>  
 <span data-ttu-id="79602-112">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="79602-112">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="79602-113">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="79602-113">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-enlist-a-send-port-or-send-port-group"></a><span data-ttu-id="79602-114">Pour inscrire un port d'envoi ou un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="79602-114">To enlist a send port or send port group</span></span>  
  
1.  <span data-ttu-id="79602-115">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="79602-115">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="79602-116">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le port d’envoi ou un groupe de ports d’envoi que vous souhaitez s’inscrire.</span><span class="sxs-lookup"><span data-stu-id="79602-116">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to enlist.</span></span>  
  
3.  <span data-ttu-id="79602-117">Cliquez sur **Ports d’envoi** ou **groupes de ports d’envoi**, cliquez sur le port d’envoi ou un groupe de ports d’envoi, puis cliquez sur **Enlist**.</span><span class="sxs-lookup"><span data-stu-id="79602-117">Click **Send Ports** or **Send Port Groups**, right-click the send port or send port group, and then click **Enlist**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79602-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79602-118">See Also</span></span>  
 [<span data-ttu-id="79602-119">La gestion des Ports d’envoi et groupes de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="79602-119">Managing Send Ports and Send Port Groups</span></span>](../core/managing-send-ports-and-send-port-groups.md)