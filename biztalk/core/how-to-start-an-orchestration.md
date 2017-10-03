---
title: "Comment démarrer une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], starting
- starting, orchestrations
- orchestrations, starting
ms.assetid: 83411279-ee6f-4d68-aa3b-b5cd5e106088
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e277c078a36129a125937114ee9287a1e97999b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-start-an-orchestration"></a><span data-ttu-id="0d108-102">Démarrage d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="0d108-102">How to Start an Orchestration</span></span>
<span data-ttu-id="0d108-103">Cette rubrique explique comment démarrer une orchestration à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0d108-103">This topic describes how to use the BizTalk Server Administration console to start an orchestration.</span></span> <span data-ttu-id="0d108-104">Lorsque vous démarrez une orchestration, elle commence à traiter les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="0d108-104">When you start an orchestration, it begins processing incoming messages.</span></span>  
  
 <span data-ttu-id="0d108-105">Lorsque vous démarrez une orchestration, gardez les points importants suivants à l'esprit :</span><span class="sxs-lookup"><span data-stu-id="0d108-105">When starting and orchestration, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="0d108-106">Avant de démarrer une orchestration, celle-ci doit être inscrite, avec tous les ports d'envoi et les groupes de ports d'envoi qui lui sont associés.</span><span class="sxs-lookup"><span data-stu-id="0d108-106">Before you can start the orchestration, it must be enlisted, along with all of the send ports and send port groups associated with it.</span></span> <span data-ttu-id="0d108-107">Pour obtenir des instructions, consultez [comment inscrire une Orchestration](../core/how-to-enlist-an-orchestration.md) et [l’inscription d’un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-enlist-a-send-port-or-send-port-group.md).</span><span class="sxs-lookup"><span data-stu-id="0d108-107">For instructions, see [How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md) and [How to Enlist a Send Port or Send Port Group](../core/how-to-enlist-a-send-port-or-send-port-group.md).</span></span>  
  
-   <span data-ttu-id="0d108-108">Le démarrage d'une orchestration ne démarre pas automatiquement les ports d'envoi associés.</span><span class="sxs-lookup"><span data-stu-id="0d108-108">Starting an orchestration does not automatically start any associated send ports.</span></span> <span data-ttu-id="0d108-109">Vous devez les démarrer séparément, comme décrit dans [comment démarrer un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-start-a-send-port-or-send-port-group.md).</span><span class="sxs-lookup"><span data-stu-id="0d108-109">You must start them separately, as described in [How to Start a Send Port or Send Port Group](../core/how-to-start-a-send-port-or-send-port-group.md).</span></span>  
  
-   <span data-ttu-id="0d108-110">Si vous inscrivez les ports d'envoi et/ou les groupes de ports d'envoi associés à cette orchestration sans les démarrer, BizTalk Server place tout message destiné à ces ports ou groupes de ports dans la file d'attente des messages interrompus de l'hôte sur lequel ces ports ont été inscrits.</span><span class="sxs-lookup"><span data-stu-id="0d108-110">If you enlist the send ports and/or send port groups associated with this orchestration, but do not start them, BizTalk Server places any messages sent to this send port or send port group in the suspended queue of the host where you enlisted the send port or send port group.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d108-111">Le développeur peut démarrer une orchestration pour tester sa fonctionnalité au cours du processus de développement à l’aide de la procédure dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0d108-111">The application developer can start an orchestration to test its functionality during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0d108-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0d108-112">Prerequisites</span></span>  
 <span data-ttu-id="0d108-113">Pour exécuter la procédure décrite dans cette rubrique, vous devez avoir ouvert une session en tant que membre du groupe des opérateurs de BizTalk Server ou du groupe d'administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0d108-113">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Operators group or the BizTalk Server Administrators group.</span></span> <span data-ttu-id="0d108-114">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="0d108-114">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-start-an-orchestration"></a><span data-ttu-id="0d108-115">Pour démarrer une orchestration</span><span class="sxs-lookup"><span data-stu-id="0d108-115">To start an orchestration</span></span>  
  
1.  <span data-ttu-id="0d108-116">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="0d108-116">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0d108-117">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration que vous souhaitez démarrer.</span><span class="sxs-lookup"><span data-stu-id="0d108-117">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to start.</span></span>  
  
3.  <span data-ttu-id="0d108-118">Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="0d108-118">Click **Orchestrations**, right-click the orchestration, and then click **Start**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0d108-119">Si vous n'avez pas inscrit le port d'envoi et les groupes de ports d'envoi associés préalablement au démarrage de l'orchestration, un message d'erreur s'affiche.</span><span class="sxs-lookup"><span data-stu-id="0d108-119">If you did not first enlist the associated send port and send port groups before starting the orchestration, you will see an error message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0d108-120">Pour démarrer plusieurs orchestrations à la fois, maintenez la touche MAJ enfoncée et sélectionnez chaque orchestration, avec le bouton droit une orchestration, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="0d108-120">To start multiple orchestrations at once, hold down the shift key and select each orchestration, right-click an orchestration, and then click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d108-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d108-121">See Also</span></span>  
 <span data-ttu-id="0d108-122">[La gestion des Orchestrations](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="0d108-122">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="0d108-123">[Comment arrêter une Orchestration](../core/how-to-stop-an-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="0d108-123">[How to Stop an Orchestration](../core/how-to-stop-an-orchestration.md) </span></span>  
 [<span data-ttu-id="0d108-124">Comment démarrer et arrêter une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="0d108-124">How to Start and Stop a BizTalk Application</span></span>](../core/how-to-start-and-stop-a-biztalk-application.md)