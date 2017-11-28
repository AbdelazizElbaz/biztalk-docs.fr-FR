---
title: "À l’aide de l’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, about Tracking Profile Editor
- tracking profiles, prerequisites
ms.assetid: ebe9a5da-66ec-482d-8aac-892a829ca996
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0fa826ce68042336c2b6e4fb006ecb278a3f981
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-tpe"></a><span data-ttu-id="6ed2a-102">Utilisation de l'Éditeur de modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="6ed2a-102">Using the TPE</span></span>
<span data-ttu-id="6ed2a-103">Vous utilisez l'Éditeur de modèle de suivi pour mapper des orchestrations et des propriétés sur les définitions d'activité BAM.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-103">You use the Tracking Profile Editor (TPE) to map orchestrations and properties to BAM activity definitions.</span></span>  
  
 <span data-ttu-id="6ed2a-104">Les utilisateurs de l'Éditeur de modèle de suivi créent un mappage, ou modèle de suivi, entre les éléments d'une activité BAM tels que des étapes majeures et données contextuelles (parfois appelées « liste souhaitée de visibilité ») et les fichiers sources de la solution BizTalk correspondant à ces éléments.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-104">Users of the TPE create a map, or tracking profile, between items in a BAM activity such as milestones and contextual data (sometimes called the "visibility wish-list") and the BizTalk solution sources for those items.</span></span>  
  
 <span data-ttu-id="6ed2a-105">**Création d’un modèle de suivi**</span><span class="sxs-lookup"><span data-stu-id="6ed2a-105">**Creating a Tracking Profile**</span></span>  
  
 <span data-ttu-id="6ed2a-106">Prenons l'exemple d'une activité BAM comportant une étape majeure appelée « PO Received ».</span><span class="sxs-lookup"><span data-stu-id="6ed2a-106">For example, consider a BAM activity that includes a milestone called “PO Received.”</span></span> <span data-ttu-id="6ed2a-107">Pour avoir créé des processus dans d'autres outils de développement BizTalk Server, le développeur sait que ce processus inclut un port de messagerie via lequel des bons de commande sont transmis pour initier le traitement.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-107">The developer knows, from having created processes in other BizTalk Server development tools, that the actual process includes a messaging port through which purchase orders flow to initiate processing.</span></span> <span data-ttu-id="6ed2a-108">Le développeur détermine qu'il est préférable que l'étape majeure d'activité, appelée « PO Received », soit associée à une propriété de messagerie BizTalk appelée « PortEndTime » pour le port dans la solution.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-108">The developer determines that the activity milestone, called “PO Received,” is most correctly associated with a BizTalk messaging property called “PortEndTime” for the port in the solution.</span></span> <span data-ttu-id="6ed2a-109">En outre, le développeur procède à tous les mappages nécessaires pour terminer le modèle de suivi. Pour cela, il charge l'activité, sélectionne des sources d'événements et fait glisser les éléments appropriés depuis les sources d'événements dans les nœuds correspondants de la définition de l'arborescence d'activité.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-109">The developer makes this and any other mappings to complete the tracking profile by loading the activity, selecting event sources, and dragging the appropriate items from the event source and dropping them on the corresponding nodes in the activity tree definition.</span></span>  
  
 <span data-ttu-id="6ed2a-110">**Configuration requise pour la création d’un profil**</span><span class="sxs-lookup"><span data-stu-id="6ed2a-110">**Prerequisites for Creating a Profile**</span></span>  
  
 <span data-ttu-id="6ed2a-111">Il existe deux conditions préalables à la création d'un modèle de suivi :</span><span class="sxs-lookup"><span data-stu-id="6ed2a-111">There are two prerequisites for creating a tracking profile:</span></span>  
  
1.  <span data-ttu-id="6ed2a-112">Une activité BAM a été définie par l'analyste d'entreprise comme faisant partie d'un modèle d'observation global et a été déployée par l'administrateur système.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-112">A BAM activity has been defined by the business analyst, as part of an overall observation model, and has been deployed by the system administrator.</span></span>  
  
2.  <span data-ttu-id="6ed2a-113">Une solution BizTalk (incluant des orchestrations, des schémas, un mappage et des pipelines) a été correctement déployée dans l'environnement cible.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-113">A BizTalk solution (including orchestrations, schemas, map, and pipelines) has been successfully deployed in the target environment.</span></span>  
  
 <span data-ttu-id="6ed2a-114">Ces conditions préalables sont nécessaires puisque après son installation, l'Éditeur de modèle de suivi n'est plus renseigné avec des données pouvant être extraites depuis les bases de données.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-114">These prerequisites are necessary since after installation the TPE is not populated with any data to retrieve from the databases.</span></span>  
  
 <span data-ttu-id="6ed2a-115">**Création d’un profil pour des Solutions BAM personnalisées**</span><span class="sxs-lookup"><span data-stu-id="6ed2a-115">**Creating a Profile for Customized BAM Solutions**</span></span>  
  
 <span data-ttu-id="6ed2a-116">Les modèles de suivi s'appliquent uniquement aux composants d'exécution possédant un intercepteur.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-116">Tracking profiles are only relevant to run-times that have an interceptor.</span></span> <span data-ttu-id="6ed2a-117">Pour les solutions BAM constituées de code personnalisé utilisant les API de l'analyse BAM, il n'existe pas d'intercepteur d'exécution BAM associé et l'envoi des données vers l'analyse BAM peut se faire de deux façons uniquement :</span><span class="sxs-lookup"><span data-stu-id="6ed2a-117">For BAM solutions that consist of custom code using the BAM APIs, there is no associated BAM run-time interceptor, and sending data to BAM can be done in only one of two ways:</span></span>  
  
-   <span data-ttu-id="6ed2a-118">Directement par le biais des API de l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-118">Directly through the BAM APIs.</span></span> <span data-ttu-id="6ed2a-119">Grâce aux API, les développeurs peuvent explicitement envoyer des données d'événement à l'infrastructure BAM.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-119">Using the APIs developers can explicitly send event data to the BAM infrastructure.</span></span> <span data-ttu-id="6ed2a-120">Pour plus d’informations sur l’utilisation de l’API BAM, consultez [mise en œuvre les activités BAM avec les flux d’événements](../core/implementing-bam-activities-with-event-streams.md).</span><span class="sxs-lookup"><span data-stu-id="6ed2a-120">For more information about using the BAM APIs, see [Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md).</span></span>  
  
-   <span data-ttu-id="6ed2a-121">Indirectement, par l'intermédiaire des propriétés de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ed2a-121">Indirectly, through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] properties.</span></span> <span data-ttu-id="6ed2a-122">Dans le cas où le code personnalisé est exécuté à l'intérieur d'un contexte d'exécution ne disposant pas d'une technologie d'interception associée, telle qu'un pipeline personnalisé ou des formes d'expression/action pour l'invocation d'un assembly personnalisé, vous pouvez utiliser les API de l'analyse BAM selon les indications ci-dessus ou mettre en œuvre les techniques traditionnelles de promotion des données.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-122">In the case where the custom code is executing inside some run-time context that does have an associated interception technology, such as a custom pipeline - or expression/action shapes in invoking a custom assembly, You can use the BAM APIs as noted above or use traditional data promotion techniques.</span></span> <span data-ttu-id="6ed2a-123">En promouvant les propriétés, vous les rendez accessibles à l'Éditeur de modèle de suivi. De plus, l'association des données d'événement à un élément d'activité BAM peut ensuite être réalisée dans l'Éditeur de modèle de suivi à l'aide de la propriété de contexte appropriée.</span><span class="sxs-lookup"><span data-stu-id="6ed2a-123">By promoting the properties you make them accessible to the TPE and the association of that event data to a BAM activity item can then be made in the TPE using the correct context property.</span></span> <span data-ttu-id="6ed2a-124">Pour plus d’informations sur la promotion des propriétés, consultez [promotion des propriétés](../core/promoting-properties.md).</span><span class="sxs-lookup"><span data-stu-id="6ed2a-124">For more information about promoting properties, see [Promoting Properties](../core/promoting-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ed2a-125">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6ed2a-125">In This Section</span></span>  
  
-   [<span data-ttu-id="6ed2a-126">Création de modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="6ed2a-126">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)  
  
-   [<span data-ttu-id="6ed2a-127">Comment supprimer des profils de suivi orphelins</span><span class="sxs-lookup"><span data-stu-id="6ed2a-127">How to Remove Orphaned Tracking Profiles</span></span>](../core/how-to-remove-orphaned-tracking-profiles.md)  
  
-   [<span data-ttu-id="6ed2a-128">À l’aide de plusieurs Continuations</span><span class="sxs-lookup"><span data-stu-id="6ed2a-128">Using Multiple Continuations</span></span>](../core/using-multiple-continuations.md)