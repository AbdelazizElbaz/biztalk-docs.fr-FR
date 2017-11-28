---
title: "Comment désinscrire une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, unenlisting
- enlisting, unenlisting
- managing [orchestrations], unenlisting
- unenlisting, orchestrations
ms.assetid: 038ed7bb-615c-4e4e-a5bb-79de2626de77
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c55f0f7daee927e90e514cb7b566b058cee8044a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-unenlist-an-orchestration"></a><span data-ttu-id="77f19-102">Annulation de l'inscription d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="77f19-102">How to Unenlist an Orchestration</span></span>
<span data-ttu-id="77f19-103">Cette rubrique explique comment annuler l'inscription d'une orchestration à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="77f19-103">This topic describes how to unenlist an orchestration by using the BizTalk Server Administration console.</span></span> <span data-ttu-id="77f19-104">La désinscription d'une orchestration entraîne sa suppression de l'hôte,</span><span class="sxs-lookup"><span data-stu-id="77f19-104">Unenlisting an orchestration removes it from the host.</span></span> <span data-ttu-id="77f19-105">et supprime l'abonnement de sorte que l'orchestration ne peut plus traiter de messages.</span><span class="sxs-lookup"><span data-stu-id="77f19-105">This removes the subscription so that the orchestration no longer processes messages.</span></span> <span data-ttu-id="77f19-106">Vous devez annuler l'inscription d'une orchestration avant de pouvoir modifier ses liaisons.</span><span class="sxs-lookup"><span data-stu-id="77f19-106">You must unenlist an orchestration before you can edit its bindings.</span></span>  
  
 <span data-ttu-id="77f19-107">Avant d’annuler l’inscription d’une orchestration, vous devez arrêter toutes les instances en cours d’exécution, comme décrit dans [comment suspendre, reprendre et arrêter les Instances d’Orchestration](../core/how-to-suspend-resume-and-terminate-orchestration-instances.md).</span><span class="sxs-lookup"><span data-stu-id="77f19-107">Before you can unenlist an orchestration, you must terminate any running instances, as described in [How to Suspend, Resume, and Terminate Orchestration Instances](../core/how-to-suspend-resume-and-terminate-orchestration-instances.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77f19-108">Le développeur peut désinscrire une orchestration au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="77f19-108">The application developer can unenlist an orchestration during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="77f19-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="77f19-109">Prerequisites</span></span>  
 <span data-ttu-id="77f19-110">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="77f19-110">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="77f19-111">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="77f19-111">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-unenlist-an-orchestration"></a><span data-ttu-id="77f19-112">Pour désinscrire une orchestration</span><span class="sxs-lookup"><span data-stu-id="77f19-112">To unenlist an orchestration</span></span>  
  
1.  <span data-ttu-id="77f19-113">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="77f19-113">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="77f19-114">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration que vous souhaitez annuler l’inscription.</span><span class="sxs-lookup"><span data-stu-id="77f19-114">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to unenlist.</span></span>  
  
3.  <span data-ttu-id="77f19-115">Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration à désinscrire, puis cliquez sur **désinscrire**.</span><span class="sxs-lookup"><span data-stu-id="77f19-115">Click **Orchestrations**, right-click the orchestration to unenlist, and then click **Unenlist**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="77f19-116">Pour désinscrire plusieurs orchestrations à la fois, maintenez la touche MAJ enfoncée et sélectionnez les orchestrations à désinscrire, cliquez sur une orchestration, puis cliquez sur **désinscrire**.</span><span class="sxs-lookup"><span data-stu-id="77f19-116">To unenlist multiple orchestrations at once, hold down the shift key and select each orchestration to unenlist, right-click an orchestration, and then click **Unenlist**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f19-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77f19-117">See Also</span></span>  
 <span data-ttu-id="77f19-118">[La gestion des Orchestrations](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="77f19-118">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="77f19-119">[Comment inscrire une Orchestration](../core/how-to-enlist-an-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="77f19-119">[How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md) </span></span>  
 [<span data-ttu-id="77f19-120">Déploiement et gestion des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="77f19-120">Deploying and Managing BizTalk Applications</span></span>](../core/deploying-and-managing-biztalk-applications.md)