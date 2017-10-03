---
title: "Comment démarrer un Port d’envoi ou un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- starting, send port groups
- starting, send ports
- managing [send port groups], starting
- managing [send ports], starting
- send port groups, starting
- send ports, starting
ms.assetid: f17c0b7c-cad7-4c5e-a08c-3ebf838faa54
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 558a9b8444a38607f18757ff09196e44a3ae0b71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-start-a-send-port-or-send-port-group"></a><span data-ttu-id="ab041-102">Démarrage d'un port d'envoi ou d'un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="ab041-102">How to Start a Send Port or Send Port Group</span></span>
<span data-ttu-id="ab041-103">La présente rubrique explique comment démarrer un port d'envoi ou un groupe de ports d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ab041-103">This topic describes how to use the BizTalk Server Administration console to start a send port or send port group.</span></span> <span data-ttu-id="ab041-104">Vous devez démarrer un port d'envoi ou un groupe de ports d'envoi pour qu'il puisse traiter les messages.</span><span class="sxs-lookup"><span data-stu-id="ab041-104">You must start a send port or send port group before it can process messages.</span></span> <span data-ttu-id="ab041-105">Si vous démarrez un port d'envoi ou un groupe de ports d'envoi désinscrit, BizTalk inscrit le port d'envoi ou le groupe de ports d'envoi avant de le démarrer.</span><span class="sxs-lookup"><span data-stu-id="ab041-105">If you start an unenlisted send port or send port group, BizTalk enlists the send port or send port group before starting it.</span></span> <span data-ttu-id="ab041-106">Un groupe de ports d'envoi doit contenir au moins un port d'envoi à l'état Inscrit pour que vous puissiez démarrer le groupe de ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="ab041-106">A send port group must contain at least one send port in an enlisted state before you can start the send port group.</span></span> <span data-ttu-id="ab041-107">Le démarrage et l'arrêt d'un groupe de ports d'envoi n'affectent pas l'état des ports d'envoi qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="ab041-107">Starting and stopping a send port group does not affect the state of any send ports that it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab041-108">Par défaut, le démarrage d'une application BizTalk entraîne le démarrage de tous les artefacts que cette application contient.</span><span class="sxs-lookup"><span data-stu-id="ab041-108">By default, starting a BizTalk application starts all of the artifacts that it contains.</span></span> <span data-ttu-id="ab041-109">Pour plus d’informations, consultez [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="ab041-109">For more information, see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ab041-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ab041-110">Prerequisites</span></span>  
 <span data-ttu-id="ab041-111">Pour exécuter la procédure décrite dans cette rubrique, vous devez avoir ouvert une session en tant que membre du groupe des opérateurs de BizTalk Server ou du groupe d'administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ab041-111">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Operators group or the BizTalk Server Administrators group.</span></span> <span data-ttu-id="ab041-112">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="ab041-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-start-a-send-port-or-send-port-group"></a><span data-ttu-id="ab041-113">Pour démarrer un port d'envoi ou un groupe de ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="ab041-113">To start a send port or send port group</span></span>  
  
1.  <span data-ttu-id="ab041-114">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="ab041-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ab041-115">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le port d’envoi ou un groupe de ports d’envoi que vous souhaitez Démarrer.</span><span class="sxs-lookup"><span data-stu-id="ab041-115">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to start.</span></span>  
  
3.  <span data-ttu-id="ab041-116">Cliquez sur **Ports d’envoi** ou **groupes de ports d’envoi**, cliquez sur le port d’envoi ou un groupe de ports d’envoi, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="ab041-116">Click **Send Ports** or **Send Port Groups**, right-click the send port or send port group, and then click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab041-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab041-117">See Also</span></span>  
 [<span data-ttu-id="ab041-118">La gestion des Ports d’envoi et groupes de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="ab041-118">Managing Send Ports and Send Port Groups</span></span>](../core/managing-send-ports-and-send-port-groups.md)