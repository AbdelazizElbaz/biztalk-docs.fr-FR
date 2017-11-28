---
title: "L’utilisation du système de projet BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Editor, opening
- BizTalk Mapper, opening
- Orchestration Designer, opening
- Pipeline Designer, opening
ms.assetid: a28c715e-128c-463a-b421-9b3efe76a530
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e55e1280f4054c431f53aa21fa16123f11509f7b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-biztalk-project-system"></a><span data-ttu-id="031f6-102">Utilisation du système de projet BizTalk </span><span class="sxs-lookup"><span data-stu-id="031f6-102">Using the BizTalk Project System</span></span>
<span data-ttu-id="031f6-103">Le système de projet BizTalk® permet de créer, organiser et configurer des solutions BizTalk dans l'environnement Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="031f6-103">You can use the BizTalk project system to create, organize, and configure BizTalk solutions in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="031f6-104">Les rubriques et les procédures de cette section expliquent comment effectuer diverses tâches à l'aide du système de projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="031f6-104">The topics and procedures in this section describe how to perform various tasks by using the BizTalk project system.</span></span>  
  
 <span data-ttu-id="031f6-105">Les principes et procédures de gestion de projet du système de projet [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] sont identiques à ceux que vous utilisez avec d'autres projets Microsoft Build Engine (MSBuild) dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="031f6-105">The [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] project system uses the same project management principles and procedures that you use with other Microsoft Build Engine (MSBuild) projects in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="031f6-106">Cette section détaille les procédures courantes que vous serez éventuellement amené à utiliser pour créer une application s'exécutant sur Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="031f6-106">This section details common procedures that you might use when creating an application that runs on Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="031f6-107">Pour plus d’informations sur MSBuild, consultez la section de référence MSBuild dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Collection combinée à [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).</span><span class="sxs-lookup"><span data-stu-id="031f6-107">For more information about MSBuild, see the MSBuild reference section in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection at [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).</span></span>  
  
 <span data-ttu-id="031f6-108">Pour plus d’informations sur l’utilisation de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environnement, consultez « Gestion des Solutions, projets et fichiers » dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Collection combinée à [http://msdn.microsoft.com/library/wbzbtw81.aspx](http://msdn.microsoft.com/library/wbzbtw81.aspx).</span><span class="sxs-lookup"><span data-stu-id="031f6-108">For more information about using the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment, see "Managing Solutions, Projects, and Files" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection at [http://msdn.microsoft.com/library/wbzbtw81.aspx](http://msdn.microsoft.com/library/wbzbtw81.aspx).</span></span>  
  
 <span data-ttu-id="031f6-109">L’illustration suivante montre l’environnement de conception de système de projet BizTalk avec le **nouveau projet** boîte de dialogue ouverte.</span><span class="sxs-lookup"><span data-stu-id="031f6-109">The following figure shows the BizTalk project system design environment with the **New Project** dialog box open.</span></span>  
  
 <span data-ttu-id="031f6-110">![Systèmes de projet](../core/media/bts-biztalk2009-projectsystems.gif "bts_BizTalk2009_ProjectSystems")</span><span class="sxs-lookup"><span data-stu-id="031f6-110">![Project Systems](../core/media/bts-biztalk2009-projectsystems.gif "bts_BizTalk2009_ProjectSystems")</span></span>  
<span data-ttu-id="031f6-111">Représentation de l'environnement de conception du système de projet</span><span class="sxs-lookup"><span data-stu-id="031f6-111">Depicts the Project System Design Environment</span></span>  
  
### <a name="to-open-biztalk-editor"></a><span data-ttu-id="031f6-112">Pour ouvrir l'Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="031f6-112">To open BizTalk Editor</span></span>  
  
1.  <span data-ttu-id="031f6-113">Dans l'Explorateur de solutions, cliquez sur un schéma.</span><span class="sxs-lookup"><span data-stu-id="031f6-113">In Solution Explorer, click a schema.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="031f6-114">Pour ouvrir l'Éditeur BizTalk, vous devez d'abord créer un schéma ou ouvrir un schéma créé au préalable.</span><span class="sxs-lookup"><span data-stu-id="031f6-114">To open BizTalk Editor, you must first create a schema or open a previously created schema.</span></span> <span data-ttu-id="031f6-115">Pour plus d’informations sur la création d’un schéma, consultez [comment créer les schémas des Messages XML](../core/how-to-create-schemas-for-xml-messages.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-115">For information about creating a schema, see [How to Create Schemas for XML Messages](../core/how-to-create-schemas-for-xml-messages.md).</span></span> <span data-ttu-id="031f6-116">Consultez également [Ajout des éléments de projet](../core/adding-project-items.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-116">Also see [Adding Project Items](../core/adding-project-items.md).</span></span>  
  
2.  <span data-ttu-id="031f6-117">Sur le **vue** menu, cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="031f6-117">On the **View** menu, click **Open**.</span></span>  
  
     <span data-ttu-id="031f6-118">— Ou :</span><span class="sxs-lookup"><span data-stu-id="031f6-118">—Or—</span></span>  
  
     <span data-ttu-id="031f6-119">Cliquez sur le schéma, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="031f6-119">Right-click the schema, and then click **Open**.</span></span>  
  
     <span data-ttu-id="031f6-120">— Ou :</span><span class="sxs-lookup"><span data-stu-id="031f6-120">—Or—</span></span>  
  
     <span data-ttu-id="031f6-121">Double-cliquez sur le schéma.</span><span class="sxs-lookup"><span data-stu-id="031f6-121">Double-click the schema.</span></span>  
  
     <span data-ttu-id="031f6-122">Le schéma sélectionné s'ouvre dans l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="031f6-122">The selected schema opens in BizTalk Editor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="031f6-123">Si vous voulez créer un schéma, un projet doit être ouvert.</span><span class="sxs-lookup"><span data-stu-id="031f6-123">To create a schema, you must have a project open.</span></span> <span data-ttu-id="031f6-124">Pour plus d’informations sur la création d’un projet, consultez [comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-124">For information about how to create a project, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).</span></span> <span data-ttu-id="031f6-125">Pour plus d’informations sur l’ajout d’éléments à un projet, consultez [comment créer les schémas des Messages XML](../core/how-to-create-schemas-for-xml-messages.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-125">For information about adding items to a project, see [How to Create Schemas for XML Messages](../core/how-to-create-schemas-for-xml-messages.md).</span></span> <span data-ttu-id="031f6-126">Consultez également [Ajout des éléments de projet](../core/adding-project-items.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-126">Also see [Adding Project Items](../core/adding-project-items.md).</span></span>  
  
### <a name="to-open-biztalk-mapper"></a><span data-ttu-id="031f6-127">Pour ouvrir le Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="031f6-127">To open BizTalk Mapper</span></span>  
  
1.  <span data-ttu-id="031f6-128">Dans l'Explorateur de solutions, cliquez sur un mappage.</span><span class="sxs-lookup"><span data-stu-id="031f6-128">In Solution Explorer, click a map.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="031f6-129">Pour ouvrir le Mappeur BizTalk, vous devez d'abord créer un mappage ou ouvrir un mappage créé au préalable.</span><span class="sxs-lookup"><span data-stu-id="031f6-129">To open BizTalk Mapper, you must first create a map or open a previously created map.</span></span> <span data-ttu-id="031f6-130">Pour plus d’informations sur la création d’un mappage, consultez [comment créer de nouveaux mappages](../core/how-to-create-new-maps.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-130">For information about creating a map, see [How to Create New Maps](../core/how-to-create-new-maps.md).</span></span> <span data-ttu-id="031f6-131">Consultez également [Ajout des éléments de projet](../core/adding-project-items.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-131">Also see [Adding Project Items](../core/adding-project-items.md).</span></span>  
  
2.  <span data-ttu-id="031f6-132">Sur le **vue** menu, cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="031f6-132">On the **View** menu, click **Open**.</span></span>  
  
     <span data-ttu-id="031f6-133">— Ou :</span><span class="sxs-lookup"><span data-stu-id="031f6-133">—Or—</span></span>  
  
     <span data-ttu-id="031f6-134">Avec le bouton droit de la carte, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="031f6-134">Right-click the map, and then click **Open**.</span></span>  
  
     <span data-ttu-id="031f6-135">— Ou :</span><span class="sxs-lookup"><span data-stu-id="031f6-135">—Or—</span></span>  
  
     <span data-ttu-id="031f6-136">Double-cliquez sur un mappage.</span><span class="sxs-lookup"><span data-stu-id="031f6-136">Double-click a map.</span></span>  
  
     <span data-ttu-id="031f6-137">Le mappage sélectionné s'ouvre dans le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="031f6-137">The selected map opens in BizTalk Mapper.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="031f6-138">Si vous voulez créer un mappage, un projet doit être ouvert.</span><span class="sxs-lookup"><span data-stu-id="031f6-138">To create a map, you must have a project open.</span></span> <span data-ttu-id="031f6-139">Pour plus d’informations sur la création d’un projet, consultez [comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-139">For information about how to create a project, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).</span></span> <span data-ttu-id="031f6-140">Pour plus d’informations sur l’ajout d’éléments à un projet, consultez [Ajout des éléments de projet](../core/adding-project-items.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-140">For information about adding items to a project, see [Adding Project Items](../core/adding-project-items.md).</span></span> <span data-ttu-id="031f6-141">Consultez également [comment créer de nouveaux mappages](../core/how-to-create-new-maps.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-141">Also see [How to Create New Maps](../core/how-to-create-new-maps.md).</span></span>  
  
### <a name="to-open-orchestration-designer"></a><span data-ttu-id="031f6-142">Pour ouvrir le Concepteur d'orchestration</span><span class="sxs-lookup"><span data-stu-id="031f6-142">To open Orchestration Designer</span></span>  
  
1.  <span data-ttu-id="031f6-143">Dans l'Explorateur de solutions, cliquez sur une orchestration (.odx).</span><span class="sxs-lookup"><span data-stu-id="031f6-143">In Solution Explorer, click an orchestration (.odx).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="031f6-144">Pour ouvrir le Concepteur d'orchestration, vous devez d'abord créer une orchestration ou ouvrir une orchestration créée au préalable.</span><span class="sxs-lookup"><span data-stu-id="031f6-144">To open Orchestration Designer, you must first create an orchestration or open a previously created orchestration.</span></span> <span data-ttu-id="031f6-145">Pour plus d’informations sur la création d’une orchestration, consultez [dans le Concepteur d’Orchestration](../core/working-in-orchestration-designer.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-145">For information about how to create an orchestration, see [Working in Orchestration Designer](../core/working-in-orchestration-designer.md).</span></span>  
  
2.  <span data-ttu-id="031f6-146">Sur le **vue** menu, cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="031f6-146">On the **View** menu, click **Open**.</span></span>  
  
     <span data-ttu-id="031f6-147">— Ou :</span><span class="sxs-lookup"><span data-stu-id="031f6-147">—Or—</span></span>  
  
     <span data-ttu-id="031f6-148">Avec le bouton droit de l’orchestration, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="031f6-148">Right-click the orchestration, and then click **Open**.</span></span>  
  
     <span data-ttu-id="031f6-149">— Ou :</span><span class="sxs-lookup"><span data-stu-id="031f6-149">—Or—</span></span>  
  
     <span data-ttu-id="031f6-150">Double-cliquez sur l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="031f6-150">Double-click the orchestration.</span></span>  
  
     <span data-ttu-id="031f6-151">Le Concepteur d'orchestration s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="031f6-151">Orchestration Designer opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="031f6-152">Si vous voulez créer une orchestration, un projet doit être ouvert.</span><span class="sxs-lookup"><span data-stu-id="031f6-152">To create an orchestration, you must have a project open.</span></span> <span data-ttu-id="031f6-153">Pour plus d’informations sur la création d’un projet, consultez [comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-153">For information about how to create a project, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).</span></span> <span data-ttu-id="031f6-154">Pour plus d’informations sur l’ajout d’éléments à un projet, consultez [Ajout des éléments de projet](../core/adding-project-items.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-154">For information about adding items to a project, see [Adding Project Items](../core/adding-project-items.md).</span></span> <span data-ttu-id="031f6-155">Consultez également [dans le Concepteur d’Orchestration](../core/working-in-orchestration-designer.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-155">Also see [Working in Orchestration Designer](../core/working-in-orchestration-designer.md).</span></span>  
  
### <a name="to-open-pipeline-designer"></a><span data-ttu-id="031f6-156">Pour ouvrir le Concepteur de pipeline</span><span class="sxs-lookup"><span data-stu-id="031f6-156">To open Pipeline Designer</span></span>  
  
1.  <span data-ttu-id="031f6-157">Dans l'Explorateur de solutions, cliquez sur un pipeline.</span><span class="sxs-lookup"><span data-stu-id="031f6-157">In Solution Explorer, click a pipeline.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="031f6-158">Pour ouvrir le Concepteur de pipeline, vous devez d'abord créer un pipeline ou ouvrir un pipeline créé au préalable.</span><span class="sxs-lookup"><span data-stu-id="031f6-158">To open Pipeline Designer, you must first create a pipeline or open a previously created pipeline.</span></span> <span data-ttu-id="031f6-159">Pour plus d’informations sur la création d’un pipeline, consultez [comment créer un Pipeline](../core/how-to-create-a-new-pipeline.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-159">For information about how to create a pipeline, see [How to Create a New Pipeline](../core/how-to-create-a-new-pipeline.md).</span></span>  
  
2.  <span data-ttu-id="031f6-160">Sur le **vue** menu, cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="031f6-160">On the **View** menu, click **Open**.</span></span>  
  
     <span data-ttu-id="031f6-161">— Ou :</span><span class="sxs-lookup"><span data-stu-id="031f6-161">—Or—</span></span>  
  
     <span data-ttu-id="031f6-162">Le pipeline d’avec le bouton droit, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="031f6-162">Right-click the pipeline, and then click **Open**.</span></span>  
  
     <span data-ttu-id="031f6-163">— Ou :</span><span class="sxs-lookup"><span data-stu-id="031f6-163">—Or—</span></span>  
  
     <span data-ttu-id="031f6-164">Double-cliquez sur le pipeline.</span><span class="sxs-lookup"><span data-stu-id="031f6-164">Double-click the pipeline.</span></span>  
  
     <span data-ttu-id="031f6-165">Le Concepteur de pipeline s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="031f6-165">Pipeline Designer opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="031f6-166">Si vous voulez créer un pipeline, un projet doit être ouvert.</span><span class="sxs-lookup"><span data-stu-id="031f6-166">To create a pipeline, you must have a project open.</span></span> <span data-ttu-id="031f6-167">Pour plus d’informations sur la création d’un projet, consultez [comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-167">For information about how to create a project, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).</span></span> <span data-ttu-id="031f6-168">Pour plus d’informations sur l’ajout d’éléments à un projet, consultez [Ajout des éléments de projet](../core/adding-project-items.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-168">For information about adding items to a project, see [Adding Project Items](../core/adding-project-items.md).</span></span> <span data-ttu-id="031f6-169">Consultez également [dans le Concepteur d’Orchestration](../core/working-in-orchestration-designer.md).</span><span class="sxs-lookup"><span data-stu-id="031f6-169">Also see [Working in Orchestration Designer](../core/working-in-orchestration-designer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="031f6-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="031f6-170">See Also</span></span>  
 <span data-ttu-id="031f6-171">[Création d’Orchestrations à l’aide du Concepteur d’Orchestration](../core/creating-orchestrations-using-orchestration-designer.md) </span><span class="sxs-lookup"><span data-stu-id="031f6-171">[Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md) </span></span>  
 <span data-ttu-id="031f6-172">[À l’aide du Concepteur de Pipeline](../core/using-pipeline-designer.md) </span><span class="sxs-lookup"><span data-stu-id="031f6-172">[Using Pipeline Designer](../core/using-pipeline-designer.md) </span></span>  
 <span data-ttu-id="031f6-173">[Fenêtres de l’éditeur des règles d’entreprise](../core/windows-of-the-business-rule-composer.md) </span><span class="sxs-lookup"><span data-stu-id="031f6-173">[Windows of the Business Rule Composer](../core/windows-of-the-business-rule-composer.md) </span></span>  
 <span data-ttu-id="031f6-174">[À l’aide de l’Éditeur BizTalk](../core/using-biztalk-editor.md) </span><span class="sxs-lookup"><span data-stu-id="031f6-174">[Using BizTalk Editor](../core/using-biztalk-editor.md) </span></span>  
 <span data-ttu-id="031f6-175">[À l’aide du Mappeur BizTalk](../core/using-biztalk-mapper.md) </span><span class="sxs-lookup"><span data-stu-id="031f6-175">[Using BizTalk Mapper](../core/using-biztalk-mapper.md) </span></span>  
 [<span data-ttu-id="031f6-176">Outils de développement</span><span class="sxs-lookup"><span data-stu-id="031f6-176">Developer Tools</span></span>](../core/developer-tools.md)