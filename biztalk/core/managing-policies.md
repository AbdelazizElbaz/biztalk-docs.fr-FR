---
title: "Gérer les stratégies | Documents Microsoft"
description: "Liens rapides à importer, publier, ajouter, déployer, supprimer ou exporter une stratégie dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7b3bf92-8868-4c35-953f-61a7f2edff9c
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dd482c2f7a226a15fe730d2b75b470a54ff27e9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="manage-policies"></a><span data-ttu-id="4b1c2-103">Gérer les stratégies</span><span class="sxs-lookup"><span data-stu-id="4b1c2-103">Manage policies</span></span>

## <a name="overview"></a><span data-ttu-id="4b1c2-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="4b1c2-104">Overview</span></span>
<span data-ttu-id="4b1c2-105">Les rubriques de cette section fournissent des instructions sur l'utilisation de la console Administration de BizTalk ou de l'outil de ligne de commande BTSTask pour la gestion des stratégies.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-105">The topics in this section provide instructions on using the BizTalk Server Administration console or the BTSTask command-line tool to manage policies.</span></span> <span data-ttu-id="4b1c2-106">Une stratégie est un groupe de règles d’entreprises.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-106">A policy is a logical grouping of business rules.</span></span> <span data-ttu-id="4b1c2-107">Pour plus d’informations sur les stratégies, consultez [stratégies](../core/policies.md).</span><span class="sxs-lookup"><span data-stu-id="4b1c2-107">For background information on policies, see [Policies](../core/policies.md).</span></span>  
  
## <a name="import-publish-deploy-and-remove-policies"></a><span data-ttu-id="4b1c2-108">Importer, publier, déployer et supprimer des stratégies</span><span class="sxs-lookup"><span data-stu-id="4b1c2-108">Import, publish, deploy, and remove policies</span></span>
 <span data-ttu-id="4b1c2-109">Les développeurs de solutions peuvent créer et afficher des stratégies à l’aide de l’éditeur des règles d’entreprise, comme décrit dans [création des règles d’entreprise à l’aide de l’éditeur des règles d’entreprise](../core/creating-business-rules-using-the-business-rule-composer.md).</span><span class="sxs-lookup"><span data-stu-id="4b1c2-109">Solution developers can create and view policies by using the Business Rule Composer, as described in [Creating Business Rules Using the Business Rule Composer](../core/creating-business-rules-using-the-business-rule-composer.md).</span></span> <span data-ttu-id="4b1c2-110">Les développeurs et administrateurs informatiques peuvent ensuite effectuer les tâches suivantes, décrites dans les rubriques de cette section, pour déployer et gérer des stratégies dans une application et un groupe BizTalk :</span><span class="sxs-lookup"><span data-stu-id="4b1c2-110">Developers and IT administrators can then perform the following tasks, which are described in the topics in this section, to deploy and manage policies in a BizTalk group and application:</span></span>  
  
-   <span data-ttu-id="4b1c2-111">**Importer la stratégie dans un groupe BizTalk.**</span><span class="sxs-lookup"><span data-stu-id="4b1c2-111">**Import the policy into a BizTalk group.**</span></span> <span data-ttu-id="4b1c2-112">Dans ce cas, la stratégie est ajoutée à la base de données du moteur de règles pour le groupe et affiche dans la console Administration de BizTalk Server dans le \<tous les artefacts\> nœud pour le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-112">When you do this, the policy is added to the Rule Engine database for the group and displays in the BizTalk Server Administration console in the \<All Artifacts\> node for the BizTalk group.</span></span> <span data-ttu-id="4b1c2-113">Cela n'applique pas la stratégie à une application particulière.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-113">This does not put the policy into effect for any particular application.</span></span> <span data-ttu-id="4b1c2-114">Vous devez d’abord publier la stratégie, l’ajouter à une application, puis la déployer, conformément à la description figurant dans les autres rubriques de cette section.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-114">You must first publish the policy, add it to an application, and then deploy it, as described in other topics in this section.</span></span> <span data-ttu-id="4b1c2-115">La base de données du moteur de règles est une base de données qui contient toutes les stratégies d'un groupe BizTalk ?</span><span class="sxs-lookup"><span data-stu-id="4b1c2-115">The Rule Engine database is a database that contains all of the policies in a BizTalk group.</span></span>  
  
-   <span data-ttu-id="4b1c2-116">**Publier une stratégie.**</span><span class="sxs-lookup"><span data-stu-id="4b1c2-116">**Publish a policy.**</span></span> <span data-ttu-id="4b1c2-117">C’est ce qui permet à une stratégie d’être utilisé dans une application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-117">This makes it available to use in a BizTalk application.</span></span>  
  
-   <span data-ttu-id="4b1c2-118">**Ajoutez une stratégie à une application BizTalk.**</span><span class="sxs-lookup"><span data-stu-id="4b1c2-118">**Add a policy to a BizTalk application.**</span></span> <span data-ttu-id="4b1c2-119">Cela permet à une application d’utiliser la stratégie, mais n’applique pas la stratégie.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-119">This allows the application to use the policy, but does not put the policy into effect.</span></span> <span data-ttu-id="4b1c2-120">La stratégie est appliquée lorsqu’elle est déployée.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-120">The policy takes effect when it is deployed.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4b1c2-121">Si une stratégie est partagée entre plusieurs applications, vous devez créer une application distincte qui la contiendra, puis créer des références des applications qui l'utiliseront vers cette application.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-121">If a policy is shared across two or more applications, you should create a separate application to contain the policy and then create references from the applications that use the policy to the application containing the policy.</span></span> <span data-ttu-id="4b1c2-122">En effet, si vous arrêtez une application contenant une stratégie, le déploiement de celle-ci est automatiquement annulé et elle ne fonctionne plus pour aucune des applications qui l'utilisent.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-122">This is because if you stop an application that contains a policy, the policy is automatically undeployed and no longer functions for any of the applications that use it.</span></span>  
  
-   <span data-ttu-id="4b1c2-123">**Déployer une stratégie.**</span><span class="sxs-lookup"><span data-stu-id="4b1c2-123">**Deploy a policy.**</span></span> <span data-ttu-id="4b1c2-124">Cette opération permet d’exécuter la stratégie.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-124">Doing this puts it into operation.</span></span> <span data-ttu-id="4b1c2-125">(Cette opération est semblable à celle qui permet de démarrer une orchestration.) Vous pouvez déployer et annuler le déploiement d'une stratégie manuellement.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-125">(This is similar to starting an orchestration.) You can deploy and undeploy a policy manually.</span></span> <span data-ttu-id="4b1c2-126">Par ailleurs, le démarrage d'une application déploie automatiquement les stratégies qu'elle contient, et son arrêt annule automatiquement le déploiement de ses stratégies.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-126">In addition, when an application is started, its policies are automatically deployed, and when an application is stopped, its policies are automatically undeployed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4b1c2-127">Une fois qu’une stratégie est déployée, elle ne peut plus être modifiée.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-127">Once a policy is deployed, it can no longer be modified.</span></span> <span data-ttu-id="4b1c2-128">Si vous voulez modifier une stratégie déployée, vous devez soit annuler son déploiement, soit la recréer à l'aide de l’éditeur de règles d’entreprise et lui donner un nouveau numéro de version.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-128">If you want to modify a deployed policy, you must either undeploy it, or recreate it by using the Business Rule Composer and give it a new version number.</span></span>  
  
-   <span data-ttu-id="4b1c2-129">**Supprimer une stratégie à partir d’une application BizTalk et le groupe BizTalk.**</span><span class="sxs-lookup"><span data-stu-id="4b1c2-129">**Remove a policy from a BizTalk application and the BizTalk group.**</span></span> <span data-ttu-id="4b1c2-130">Cette opération annule le déploiement de la stratégie et supprime également cette dernière de l'application, ainsi que de la base de données du moteur de règles pour ce groupe.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-130">This undeploys the policy and removes it from the application as well as the Rule Engine database for the group.</span></span>  
  
-   <span data-ttu-id="4b1c2-131">**Exporter la stratégie.**</span><span class="sxs-lookup"><span data-stu-id="4b1c2-131">**Export the policy.**</span></span> <span data-ttu-id="4b1c2-132">Vous pouvez ensuite l’importer dans un groupe BizTalk différent pour l’y utiliser.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-132">You can then import it into a different BizTalk group to use there.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b1c2-133">Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="4b1c2-133">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="4b1c2-134">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="4b1c2-134">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="4b1c2-135">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="4b1c2-135">Next steps</span></span>
  
-   [<span data-ttu-id="4b1c2-136">Importer une stratégie</span><span class="sxs-lookup"><span data-stu-id="4b1c2-136">Import a Policy</span></span>](../core/how-to-import-a-policy.md)  
  
-   [<span data-ttu-id="4b1c2-137">Publier une stratégie</span><span class="sxs-lookup"><span data-stu-id="4b1c2-137">Publish a Policy</span></span>](../core/how-to-publish-a-policy.md)  
  
-   [<span data-ttu-id="4b1c2-138">Ajouter une stratégie à une application</span><span class="sxs-lookup"><span data-stu-id="4b1c2-138">Add a Policy to an Application</span></span>](../core/how-to-add-a-policy-to-an-application.md)  
  
-   [<span data-ttu-id="4b1c2-139">Déployer une stratégie ou annuler son déploiement</span><span class="sxs-lookup"><span data-stu-id="4b1c2-139">Deploy or Undeploy a Policy</span></span>](../core/how-to-deploy-or-undeploy-a-policy.md)  
  
-   [<span data-ttu-id="4b1c2-140">Configurer le suivi d’une stratégie</span><span class="sxs-lookup"><span data-stu-id="4b1c2-140">Configure Tracking for a Policy</span></span>](../core/how-to-configure-tracking-for-a-policy.md)  
  
-   [<span data-ttu-id="4b1c2-141">Supprimer une stratégie d’une application et du groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="4b1c2-141">Remove a Policy from an Application and the BizTalk Group</span></span>](../core/how-to-remove-a-policy-from-an-application-and-the-biztalk-group.md)  
  
-   [<span data-ttu-id="4b1c2-142">Exporter une stratégie</span><span class="sxs-lookup"><span data-stu-id="4b1c2-142">Export a Policy</span></span>](../core/how-to-export-a-policy.md)