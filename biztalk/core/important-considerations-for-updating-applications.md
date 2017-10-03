---
title: "Considérations importantes pour la mise à jour des Applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updating, applications
- applications, planning
- applications, updating
- planning, applications
- planning, updating
- updating, planning
ms.assetid: e7690bdf-943d-4bb6-b8cd-a6841b722d40
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c24528dcce390376b7ac2e47199aa5ae06d412a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="important-considerations-for-updating-applications"></a><span data-ttu-id="fab2f-102">Considérations importantes relatives à la mise à jour d'applications</span><span class="sxs-lookup"><span data-stu-id="fab2f-102">Important Considerations for Updating Applications</span></span>
<span data-ttu-id="fab2f-103">Vous trouverez ci-dessous d'importantes remarques à prendre en considération avant de mettre une application à jour, en particulier si celle-ci est exécutée dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="fab2f-103">The following are important issues to consider before updating an application, especially one that is running in a production environment.</span></span>  
  
## <a name="general-considerations"></a><span data-ttu-id="fab2f-104">Observations générales</span><span class="sxs-lookup"><span data-stu-id="fab2f-104">General considerations</span></span>  
  
-   <span data-ttu-id="fab2f-105">Les tiers et les règles sont visibles au niveau des groupes. L'ajout de tiers et de règles peut donc perturber les autres applications.</span><span class="sxs-lookup"><span data-stu-id="fab2f-105">Parties and rules are visible at a group scope, so adding additional parties and rules could disrupt other applications.</span></span>  
  
-   <span data-ttu-id="fab2f-106">Si vous annulez le déploiement d'un artefact dont dépend un autre artefact, le déploiement de l'artefact dépendant doit être annulé au préalable.</span><span class="sxs-lookup"><span data-stu-id="fab2f-106">If you are undeploying an artifact on which another artifact depends, the dependent artifact must be undeployed first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fab2f-107">La console Administration de BizTalk Server affiche un avertissement pour vous empêcher d'annuler le déploiement des artefacts dans le mauvais ordre.</span><span class="sxs-lookup"><span data-stu-id="fab2f-107">The BizTalk Server Administration console will display a warning and prevent you from undeploying artifacts in the incorrect order.</span></span>  
  
-   <span data-ttu-id="fab2f-108">Si un assembly BizTalk dans une application existante est mise à jour, vous devrez peut-être redémarrer les instances d’hôte pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="fab2f-108">If a BizTalk assembly in an existing application is updated, you may need to restart host instances for the changes to take effect.</span></span> <span data-ttu-id="fab2f-109">Le redémarrage d’une instance d’hôte arrête toutes les autres applications qui sont exécutent sur l’instance d’hôte.</span><span class="sxs-lookup"><span data-stu-id="fab2f-109">Restarting a host instance stops all other applications that are running on the host instance.</span></span>  
  
-   <span data-ttu-id="fab2f-110">Si vous utilisez Visual Studio pour déployer une application dans un environnement de production (ce que nous vous déconseillons fortement) et que l'option Redémarrer les instances d'hôte est définie sur True dans les propriétés de projet, toutes les instances d'hôte redémarreront lorsque vous déploierez l'application, y compris celles qui ne sont pas associées à l'application.</span><span class="sxs-lookup"><span data-stu-id="fab2f-110">If you use Visual Studio to deploy an application into a production environment (which we strongly recommend against doing) and the Restart Host Instances option is set to True in project properties, all host instances will restart when you deploy the application, including those that are not associated with this application.</span></span> <span data-ttu-id="fab2f-111">Ce processus interrompra toutes les autres applications exécutées sur les instances d'hôte de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fab2f-111">This will stop all other applications that are running on any host instance on the local computer.</span></span>  
  
-   <span data-ttu-id="fab2f-112">Pour mettre à jour un assembly BizTalk Server (contenant une orchestration, un schéma ou un mappage) déployé comme application BizTalk, vous pouvez effectuer l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="fab2f-112">If you want to update a BizTalk Server assembly (containing an orchestration, schema, or map) which is deployed as a BizTalk application, you can do any of the following:</span></span>  
  
    -   <span data-ttu-id="fab2f-113">Effectuez un déploiement côte à côte.</span><span class="sxs-lookup"><span data-stu-id="fab2f-113">Perform a side-by-side deployment.</span></span> <span data-ttu-id="fab2f-114">Vous pouvez généralement modifier de façon appropriée l'assembly plus récent en incrémentant sa version.</span><span class="sxs-lookup"><span data-stu-id="fab2f-114">You can appropriately modify the newer assembly typically by incrementing the version.</span></span> <span data-ttu-id="fab2f-115">Cela a pour effet d'attribuer aux deux assemblys un nom complet distinct.</span><span class="sxs-lookup"><span data-stu-id="fab2f-115">This makes both the assemblies have a distinct fully qualified assembly name.</span></span> <span data-ttu-id="fab2f-116">Pour plus d’informations, consultez [comment déployer une nouvelle Version d’une Application à exécuter de côte à côte avec une Version existante](../core/deploy-new-application-version-to-run-side-by-side-with-existing-version.md).</span><span class="sxs-lookup"><span data-stu-id="fab2f-116">For more information, see [How to Deploy a New Version of an Application to Run Side-by-side with an Existing Version](../core/deploy-new-application-version-to-run-side-by-side-with-existing-version.md).</span></span>  
  
    -   <span data-ttu-id="fab2f-117">Remplacez l'assembly BizTalk Server existant par un nouvel assembly.</span><span class="sxs-lookup"><span data-stu-id="fab2f-117">Replace the existing BizTalk Server assembly with a new assembly.</span></span> <span data-ttu-id="fab2f-118">Vous devez arrêter toutes les instances de l'hôte susceptibles de charger l'assembly obsolète, remplacer ce dernier dans le GAC, puis redémarrer les instances de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="fab2f-118">You must stop all host instances that can possibly load the out-dated assembly, replace the out-dated assembly in the GAC, and then restart the host instances.</span></span>  
  
-   <span data-ttu-id="fab2f-119">Si vous déployez une toute nouvelle application en remplacement de l'application existante, vous devez corriger toutes les références entre les autres applications et l'application que vous remplacez.</span><span class="sxs-lookup"><span data-stu-id="fab2f-119">If you deploy an entirely new application to replace an existing application, you must correct any references between other applications and the application that you are replacing.</span></span>  
  
## <a name="considerations-for-updating-schemas"></a><span data-ttu-id="fab2f-120">Observations concernant la mise à jour des schémas</span><span class="sxs-lookup"><span data-stu-id="fab2f-120">Considerations for updating schemas</span></span>  
  
-   <span data-ttu-id="fab2f-121">Si vous ajoutez un assembly à une application qui comprend un nouveau schéma avec le même type de message en tant qu’un schéma existant dans le groupe BizTalk, le schéma avec le numéro de version le plus élevé sera utilisé lors de la résolution de schéma se produit dans les pipelines.</span><span class="sxs-lookup"><span data-stu-id="fab2f-121">If you add an assembly to an application that includes a new schema with the same message type as an existing schema in the BizTalk group, the schema with the highest version number will be used when schema resolution occurs in pipelines.</span></span> <span data-ttu-id="fab2f-122">En outre, si un type de message fait référence à plusieurs types .NET, cette ambiguïté peut entraîner d’échec d’exécution du pipeline.</span><span class="sxs-lookup"><span data-stu-id="fab2f-122">In addition, if one message type refers to more than one .NET type, this ambiguity may cause pipeline execution failure.</span></span> <span data-ttu-id="fab2f-123">En effet, la recherche de schémas utilise le type de message, l'espace de noms cible et le nom de la racine de l'instance.</span><span class="sxs-lookup"><span data-stu-id="fab2f-123">This is because schema lookup uses message type, the target namespace, and root name of the instance.</span></span> <span data-ttu-id="fab2f-124">Ceci peut se produire pour les pipelines des applications qui utilisent un schéma possédant le même type de message que le nouveau schéma.</span><span class="sxs-lookup"><span data-stu-id="fab2f-124">This can occur for pipelines in any application that uses a schema with the same message type as the new schema.</span></span> <span data-ttu-id="fab2f-125">Pour plus d’informations sur la résolution de schéma, consultez [résolution de schéma dans les composants de Pipeline](../core/schema-resolution-in-pipeline-components.md).</span><span class="sxs-lookup"><span data-stu-id="fab2f-125">For more information about schema resolution, see [Schema Resolution in Pipeline Components](../core/schema-resolution-in-pipeline-components.md).</span></span>  
  
-   <span data-ttu-id="fab2f-126">Lorsque vous mettez un schéma à jour, vous devez également mettre à jour les mappages qui font référence au schéma (ou créer de nouveaux mappages), ainsi que les orchestrations reposant sur ce schéma.</span><span class="sxs-lookup"><span data-stu-id="fab2f-126">When you update a schema, you must also update the maps that reference the schema (or create new maps) as well as any orchestrations that rely on the schema.</span></span>  
  
-   <span data-ttu-id="fab2f-127">Si vous incrémentez la version d'un schéma, vous devez mettre à jour la référence à ce schéma pour toutes les instances et composants de pipeline qui l'utilisent.</span><span class="sxs-lookup"><span data-stu-id="fab2f-127">If you increment a schema version, you should update the reference to the schema for any pipeline instances and pipeline components that use it.</span></span>  
  
-   <span data-ttu-id="fab2f-128">L'annulation du déploiement d'un schéma entraîne l'activation de la version précédente de ce schéma, si tant est qu'elle soit disponible.</span><span class="sxs-lookup"><span data-stu-id="fab2f-128">Undeploying a schema causes the previous version of the schema, if available, to become active.</span></span>  
  
## <a name="considerations-for-updating-policies"></a><span data-ttu-id="fab2f-129">Observations concernant la mise à jour des stratégies</span><span class="sxs-lookup"><span data-stu-id="fab2f-129">Considerations for updating policies</span></span>  
  
-   <span data-ttu-id="fab2f-130">La version la plus élevée d'une stratégie déployée est utilisée par le moteur d'exécution BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fab2f-130">The highest version of a policy that is in a deployed state is used by the BizTalk Server runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fab2f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fab2f-131">See Also</span></span>  
 [<span data-ttu-id="fab2f-132">Mise à jour des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="fab2f-132">Updating BizTalk Applications</span></span>](../core/updating-biztalk-applications.md)