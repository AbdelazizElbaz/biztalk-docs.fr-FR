---
title: Comment inscrire une Orchestration | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], enlisting
- orchestrations, enlisting
- enlisting, orchestrations
ms.assetid: b21a398b-8c9a-42ae-aac0-de35dbfd8176
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f58cb697e270052f8f42229997b1125e808816b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enlist-an-orchestration"></a><span data-ttu-id="cd0b0-102">Inscription d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="cd0b0-102">How to Enlist an Orchestration</span></span>
<span data-ttu-id="cd0b0-103">Cette rubrique explique comment inscrire une orchestration dans un hôte à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-103">This topic describes how to use the BizTalk Server Administration console to enlist an orchestration into a host.</span></span> <span data-ttu-id="cd0b0-104">L'orchestration doit être inscrite pour pouvoir être démarrée.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-104">The orchestration must be enlisted before you can start it.</span></span>  
  
 <span data-ttu-id="cd0b0-105">Lorsque vous inscrivez une orchestration, gardez les points suivants à l'esprit :</span><span class="sxs-lookup"><span data-stu-id="cd0b0-105">When enlisting an orchestration, bear in mind the following points:</span></span>  
  
-   <span data-ttu-id="cd0b0-106">**L’orchestration doit être liée avant de pouvoir l’inscrire.**</span><span class="sxs-lookup"><span data-stu-id="cd0b0-106">**The orchestration must be bound before you can enlist it.**</span></span> <span data-ttu-id="cd0b0-107">Pour obtenir des instructions sur la configuration des liaisons pour les orchestrations, consultez [comment configurer les liaisons d’une Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="cd0b0-107">For instructions on configuring bindings for orchestrations, see [How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).</span></span>  
  
-   <span data-ttu-id="cd0b0-108">**Les abonnements sont créés automatiquement.**</span><span class="sxs-lookup"><span data-stu-id="cd0b0-108">**Subscriptions are automatically created.**</span></span> <span data-ttu-id="cd0b0-109">Le processus d'inscription de l'orchestration crée les abonnements nécessaires dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-109">The orchestration enlistment process creates the necessary subscriptions in the MessageBox database.</span></span>  
  
-   <span data-ttu-id="cd0b0-110">**Vous devez installer l’application.**</span><span class="sxs-lookup"><span data-stu-id="cd0b0-110">**You must install the application.**</span></span> <span data-ttu-id="cd0b0-111">Vous devez installer l'application contenant l'orchestration sur tous les ordinateurs sur lesquels l'orchestration sera exécutée.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-111">You must install the application containing the orchestration on all of computers where the orchestration will run.</span></span> <span data-ttu-id="cd0b0-112">Pour plus d’informations, consultez [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="cd0b0-112">For more information, see [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="cd0b0-113">**Une orchestration d’appel doit être liée au même hôte que l’orchestration appelée.**</span><span class="sxs-lookup"><span data-stu-id="cd0b0-113">**A calling orchestration must be bound to the same host as the called orchestration.**</span></span> <span data-ttu-id="cd0b0-114">Toute orchestration appelée par une autre orchestration doit être liée au même hôte que cette dernière.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-114">Any orchestration that is called by another orchestration must be bound to the same host as the calling orchestration.</span></span>  
  
-   <span data-ttu-id="cd0b0-115">**Vous devez également inscrire les orchestrations dépendantes.**</span><span class="sxs-lookup"><span data-stu-id="cd0b0-115">**You should also enlist dependent orchestrations.**</span></span> <span data-ttu-id="cd0b0-116">Si vous inscrivez une orchestration sans inscrire ses orchestrations dépendantes, ces dernières ne disposeront pas d'abonnements.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-116">If you enlist an orchestration but do not enlist any dependent orchestrations, the dependent orchestrations will not have any subscriptions.</span></span> <span data-ttu-id="cd0b0-117">Or, une orchestration dépendante sans abonnements peut entraîner la suppression ou la suspension des messages, ces derniers n'étant associés à aucun abonnement.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-117">A dependent orchestration without subscriptions may drop or suspend messages because there is no subscription for the messages to match.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd0b0-118">Le développeur peut inscrire une orchestration afin de tester sa fonctionnalité au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-118">The application developer can enlist an orchestration to test its functionality during the development process  by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cd0b0-119">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="cd0b0-119">Prerequisites</span></span>  
 <span data-ttu-id="cd0b0-120">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-120">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="cd0b0-121">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="cd0b0-121">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-enlist-an-orchestration"></a><span data-ttu-id="cd0b0-122">Pour inscrire une orchestration</span><span class="sxs-lookup"><span data-stu-id="cd0b0-122">To enlist an orchestration</span></span>  
  
1.  <span data-ttu-id="cd0b0-123">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-123">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="cd0b0-124">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration que vous souhaitez inscrire.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-124">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to enlist.</span></span>  
  
3.  <span data-ttu-id="cd0b0-125">Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration à inscrire, puis cliquez sur **Enlist**.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-125">Click **Orchestrations**, right-click the orchestration to enlist, and then click **Enlist**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd0b0-126">Pour inscrire plusieurs orchestrations à la fois, maintenez la touche MAJ enfoncée et sélectionnez les orchestrations à inscrire, cliquez sur une orchestration, puis cliquez sur **Enlist**.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-126">To enlist multiple orchestrations at once, hold down the shift key and select each orchestration to enlist, right-click an orchestration, and then click **Enlist**.</span></span>  
  
     <span data-ttu-id="cd0b0-127">L'orchestration est inscrite et les abonnements appropriés sont créés.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-127">The orchestration is enlisted and the appropriate subscriptions are created.</span></span> <span data-ttu-id="cd0b0-128">L'état de l'orchestration est « Arrêté ».</span><span class="sxs-lookup"><span data-stu-id="cd0b0-128">The orchestration is in the stopped state.</span></span> <span data-ttu-id="cd0b0-129">Pour démarrer le traitement des messages entrants, vous devez explicitement démarrer l’orchestration en cliquant dessus **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="cd0b0-129">To start processing incoming messages, you must explicitly start the orchestration by right-clicking it and clicking **Start**.</span></span> <span data-ttu-id="cd0b0-130">Pour plus d’informations, consultez [comment démarrer une Orchestration](../core/how-to-start-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="cd0b0-130">For more information, see [How to Start an Orchestration](../core/how-to-start-an-orchestration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd0b0-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd0b0-131">See Also</span></span>  
 <span data-ttu-id="cd0b0-132">[La gestion des Orchestrations](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="cd0b0-132">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 [<span data-ttu-id="cd0b0-133">Comment désinscrire une Orchestration</span><span class="sxs-lookup"><span data-stu-id="cd0b0-133">How to Unenlist an Orchestration</span></span>](../core/how-to-unenlist-an-orchestration.md)