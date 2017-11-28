---
title: "Qu'est-ce qu'un modèle de suivi ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking profiles, about tracking profiles
- tracking profiles, Tracking Profile Editor
- Tracking Profile Editor, tracking profiles
- tracking profiles
ms.assetid: b579bdc4-7c69-4fa0-bbc1-f98170c13d4f
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da032fb6063d81cedca9f21899c5e2bbe6eca947
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-a-tracking-profile"></a><span data-ttu-id="6230b-103">Qu'est-ce qu'un modèle de suivi ?</span><span class="sxs-lookup"><span data-stu-id="6230b-103">What Is a Tracking Profile?</span></span>
<span data-ttu-id="6230b-104">Un modèle est un ensemble de caractéristiques qui définissent un processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6230b-104">A profile is a set of characteristics that define a business process.</span></span> <span data-ttu-id="6230b-105">Un modèle de suivi contient le mappage de ces caractéristiques entre une activité et des orchestrations et des ports.</span><span class="sxs-lookup"><span data-stu-id="6230b-105">A tracking profile contains the mapping of these characteristics from an activity to orchestrations and ports.</span></span> <span data-ttu-id="6230b-106">C'est un fichier dont le nom est doté de l'extension .btt.</span><span class="sxs-lookup"><span data-stu-id="6230b-106">A tracking profile is a file with a .btt file name extension.</span></span>  
  
## <a name="using-tracking-profiles-in-the-tpe"></a><span data-ttu-id="6230b-107">Utilisation de modèles de suivi dans l'Éditeur de modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="6230b-107">Using tracking profiles in the TPE</span></span>  
 <span data-ttu-id="6230b-108">Les utilisateurs de l'Éditeur de modèle de suivi créent un mappage, ou modèle de suivi, entre les éléments d'une activité BAM et les sources de solution BizTalk Server correspondant à ces éléments.</span><span class="sxs-lookup"><span data-stu-id="6230b-108">Users of the TPE create a map, or tracking profile, between items in a BAM activity and the BizTalk Server solution sources for those items.</span></span> <span data-ttu-id="6230b-109">Les activités BAM se composent des étapes majeures et des données contextuelles qui constituent la « liste souhaitée de visibilité ». Elles définissent une unité de travail dans l'activité commerciale que suit le modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="6230b-109">BAM activities consist of the milestones and contextual data that make up the "visibility wish-list" and define a unit of work in the business that the tracking profile follows.</span></span> <span data-ttu-id="6230b-110">Pour plus d’informations sur les activités, consultez [mise en œuvre les activités BAM avec les flux d’événements](../core/implementing-bam-activities-with-event-streams.md).</span><span class="sxs-lookup"><span data-stu-id="6230b-110">For more information about activities, see [Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md).</span></span>  
  
 <span data-ttu-id="6230b-111">Lorsque vous créez un modèle de suivi à l'aide de l'Éditeur de modèle de suivi, vous travaillez avec les objets suivants :</span><span class="sxs-lookup"><span data-stu-id="6230b-111">When you create a tracking profile using the TPE, you are working with the following objects:</span></span>  
  
-   <span data-ttu-id="6230b-112">Activités BAM</span><span class="sxs-lookup"><span data-stu-id="6230b-112">BAM activities</span></span>  
  
-   <span data-ttu-id="6230b-113">Orchestrations BizTalk au sein d'assemblys déployés</span><span class="sxs-lookup"><span data-stu-id="6230b-113">BizTalk orchestrations in deployed assemblies</span></span>  
  
-   <span data-ttu-id="6230b-114">Ports d'envoi et de réception</span><span class="sxs-lookup"><span data-stu-id="6230b-114">Receive and send ports</span></span>  
  
-   <span data-ttu-id="6230b-115">Schémas de message au sein d'assemblys déployés</span><span class="sxs-lookup"><span data-stu-id="6230b-115">Message schemas in deployed assemblies</span></span>  
  
-   <span data-ttu-id="6230b-116">Propriétés de contexte</span><span class="sxs-lookup"><span data-stu-id="6230b-116">Context properties</span></span>  
  
-   <span data-ttu-id="6230b-117">Base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="6230b-117">BAM Primary Import database</span></span>  
  
-   <span data-ttu-id="6230b-118">Base de données de gestion BizTalk</span><span class="sxs-lookup"><span data-stu-id="6230b-118">BizTalk Management database</span></span>  
  
-   <span data-ttu-id="6230b-119">Base de données des suivis BizTalk</span><span class="sxs-lookup"><span data-stu-id="6230b-119">BizTalk Tracking database</span></span>  
  
 <span data-ttu-id="6230b-120">Pour définir l'extraction de données issues d'une orchestration, vous devez déplacer les éléments de schémas de message, de formes d'orchestration et de propriétés de contexte et les déposer dans les étapes majeures commerciales (événements) et les dossiers des éléments de données correspondants.</span><span class="sxs-lookup"><span data-stu-id="6230b-120">You define the data extraction from an orchestration by dropping items from message schemas, orchestration shapes, and context properties into business milestone (event) and data item folders.</span></span>  
  
 <span data-ttu-id="6230b-121">Prenez par exemple une activité BAM comportant une étape majeure appelée PO Received et dotée d'un port de messagerie qu'un flux de bons de commande traverse dans le but d'initier le traitement.</span><span class="sxs-lookup"><span data-stu-id="6230b-121">For example, consider a BAM activity that includes a milestone called PO Received and has a Messaging port through which purchase orders flow to initiate processing.</span></span> <span data-ttu-id="6230b-122">Dans leur solution, les développeurs peuvent associer pour le port l'étape majeure `PO Received` à une propriété de la messagerie BizTalk appelée `PortEndTime`.</span><span class="sxs-lookup"><span data-stu-id="6230b-122">Developers can associate the `PO Received` milestone with a BizTalk Messaging property called `PortEndTime` for the port in their solution.</span></span> <span data-ttu-id="6230b-123">Sémantiquement, cela indique que le bon de commande est reçu correctement une fois que le port de réception termine son action et renseigne la propriété `PortEndTime`.</span><span class="sxs-lookup"><span data-stu-id="6230b-123">Semantically, this indicates that the PO is successfully received once the receive port concludes its action and populates the `PortEndTime` property.</span></span> <span data-ttu-id="6230b-124">Le développeur accomplit cette opération et tout autre mappage afin d'achever le modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="6230b-124">The developer makes this and any other mappings to complete the tracking profile.</span></span> <span data-ttu-id="6230b-125">Tous les éléments de l'activité sont mappés s'ils ont une source de BizTalk Server ou ne le sont pas, afin d'être renseignés par des appels API directement, si la source des données ou de l'événement appartient à un processus extérieur à l'environnement d'exécution de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="6230b-125">All items in the activity are mapped if they have a BizTalk Server source, or are left unmapped to be populated by API calls directly if the source of the data or event is from a process outside of BizTalk Server’s run-time environment.</span></span>  
  
 <span data-ttu-id="6230b-126">Si chaque volet ou vue de l'Éditeur de modèle de suivi a une unique fonction, l'ensemble des vues et des dossiers possèdent des fonctionnalités de navigation similaires pour vous aider à trouver et manipuler les informations plus facilement.</span><span class="sxs-lookup"><span data-stu-id="6230b-126">Although each pane or view in the TPE has a unique function, all the views and folders have similar navigational features to help you find and manipulate information.</span></span>  
  
## <a name="who-uses-tracking-profiles-and-the-tpe"></a><span data-ttu-id="6230b-127">Qui utilise les modèles de suivi et l'Éditeur de modèle de suivi ?</span><span class="sxs-lookup"><span data-stu-id="6230b-127">Who uses tracking profiles and the TPE?</span></span>  
 <span data-ttu-id="6230b-128">Les utilisateurs participant au développement de l'intégration d'entreprise utilisent des modèles de suivi et l'Éditeur de modèle de suivi pour mapper des sources d'événements à des activités cibles BAM.</span><span class="sxs-lookup"><span data-stu-id="6230b-128">Users involved with enterprise integration development use tracking profiles and the TPE to map BizTalk Server event sources to BAM target activities.</span></span> <span data-ttu-id="6230b-129">Le fichier .btt en résultant est remis à l'implémentation informatique en vue de son déploiement.</span><span class="sxs-lookup"><span data-stu-id="6230b-129">The resulting .btt file is handed off to IT Implementation for deployment.</span></span>  
  
 <span data-ttu-id="6230b-130">Les utilisateurs de l'implémentation informatique appliquent généralement les modèles de suivi à l'aide d'outils de ligne de commande (BTTDeploy).</span><span class="sxs-lookup"><span data-stu-id="6230b-130">IT Implementation users will typically apply tracking profiles using command-line tools (BTTDeploy).</span></span> <span data-ttu-id="6230b-131">Ils peuvent également utiliser directement l'Éditeur de modèle de suivi à cette fin.</span><span class="sxs-lookup"><span data-stu-id="6230b-131">The IT user can also use the TPE directly to apply the tracking profile.</span></span>  
  
 <span data-ttu-id="6230b-132">Les utilisateurs du back office sont susceptibles d'être chargés, de façon planifiée, de la mise à jour périodique des modèles de suivi (ainsi que de toute opération requise sur les bases de données, la sauvegarde et la restauration par exemple), en particulier à la suite de changements dans les spécifications commerciales.</span><span class="sxs-lookup"><span data-stu-id="6230b-132">Users in IT Operations may be responsible for periodic updates to tracking profiles on a scheduled basis (including any database operations required, such as backup and restore), especially as a result of changes in business requirements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6230b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6230b-133">See Also</span></span>  
 [<span data-ttu-id="6230b-134">Éditeur de modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="6230b-134">Tracking Profile Editor</span></span>](../core/tracking-profile-editor.md)