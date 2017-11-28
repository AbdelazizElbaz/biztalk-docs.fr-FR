---
title: "Que se passe-t-il quand les artefacts sont ajoutés et supprimés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, artifacts
- artifacts, deleting
- artifacts, creating
- deleting, artifacts
ms.assetid: 811166ba-3ff4-4224-9d84-a2f4ed31bf4d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 464964714993205ef65d5a67de3399935f79320f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-happens-when-artifacts-are-added-and-removed"></a><span data-ttu-id="e6e89-102">Effets de l'ajout et de la suppression d'artefacts</span><span class="sxs-lookup"><span data-stu-id="e6e89-102">What Happens When Artifacts Are Added and Removed</span></span>
<span data-ttu-id="e6e89-103">Cette rubrique décrit les effets de l'ajout d'artefacts à une application.</span><span class="sxs-lookup"><span data-stu-id="e6e89-103">This topic describes what happens when you add artifacts to an application.</span></span> <span data-ttu-id="e6e89-104">Vous pouvez ajouter des artefacts basés sur des fichiers à une application en utilisant la console Administration de BizTalk Server ou l'outil de ligne de commande BTSTask.</span><span class="sxs-lookup"><span data-stu-id="e6e89-104">You can add file-based artifacts to an application by using the BizTalk Server Administration console or the BTSTask command-line tool.</span></span> <span data-ttu-id="e6e89-105">Les artefacts basés sur des fichiers incluent les types suivants :</span><span class="sxs-lookup"><span data-stu-id="e6e89-105">File-based artifacts include the following types:</span></span>  
  
-   <span data-ttu-id="e6e89-106">Assemblys BizTalk</span><span class="sxs-lookup"><span data-stu-id="e6e89-106">BizTalk assemblies</span></span>  
  
-   <span data-ttu-id="e6e89-107">Assemblys .NET non spécifiques à BizTalk</span><span class="sxs-lookup"><span data-stu-id="e6e89-107">.NET assemblies that are not BizTalk-specific</span></span>  
  
-   <span data-ttu-id="e6e89-108">Fichiers de liaison (.xml)</span><span class="sxs-lookup"><span data-stu-id="e6e89-108">Binding (.xml) files</span></span>  
  
-   <span data-ttu-id="e6e89-109">composants des services COM</span><span class="sxs-lookup"><span data-stu-id="e6e89-109">COM components</span></span>  
  
-   <span data-ttu-id="e6e89-110">Certificats</span><span class="sxs-lookup"><span data-stu-id="e6e89-110">Certificates</span></span>  
  
-   <span data-ttu-id="e6e89-111">Scripts de pré-traitement et de post-traitement</span><span class="sxs-lookup"><span data-stu-id="e6e89-111">Pre- and post-processing scripts</span></span>  
  
-   <span data-ttu-id="e6e89-112">Stratégies</span><span class="sxs-lookup"><span data-stu-id="e6e89-112">Policies</span></span>  
  
-   <span data-ttu-id="e6e89-113">Fichiers ad hoc, tels que les fichiers Lisezmoi</span><span class="sxs-lookup"><span data-stu-id="e6e89-113">Ad hoc files, such as Readme files</span></span>  
  
-   <span data-ttu-id="e6e89-114">Répertoires virtuels</span><span class="sxs-lookup"><span data-stu-id="e6e89-114">Virtual directories</span></span>  
  
-   <span data-ttu-id="e6e89-115">Artefacts BAM</span><span class="sxs-lookup"><span data-stu-id="e6e89-115">BAM artifacts</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6e89-116">Les ports d’envoi, groupes de ports d‘envoi, emplacements de réception et ports de réception ne sont pas des artefacts basés sur un fichier et ils ne peuvent pas être ajoutés à une application.</span><span class="sxs-lookup"><span data-stu-id="e6e89-116">Send ports, send port groups, receive locations, and receive ports are not file-based artifacts and cannot be added to an application.</span></span> <span data-ttu-id="e6e89-117">Vous devez créer ces artefacts dans une application donnée.</span><span class="sxs-lookup"><span data-stu-id="e6e89-117">You must create these artifacts within a given application.</span></span> <span data-ttu-id="e6e89-118">Vous pouvez ensuite les déplacer vers une autre application, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="e6e89-118">You can then move them to a different application, if you want.</span></span> <span data-ttu-id="e6e89-119">Les orchestrations, schémas, mappages et pipelines sont tous déployés et gérés dans le cadre des assemblys dont ils font partie.</span><span class="sxs-lookup"><span data-stu-id="e6e89-119">Orchestrations, schemas, maps and pipelines are all deployed and managed as part of the assemblies that contain them.</span></span>  
  
 <span data-ttu-id="e6e89-120">Lorsque vous ajoutez un artefact à une application, l'artefact est associé à l'application dans la base de données de gestion BizTalk et les données de fichier destinées à l'artefact sont également ajoutées à la base de données de gestion.</span><span class="sxs-lookup"><span data-stu-id="e6e89-120">When you add an artifact to an application, the artifact is associated with the application in the BizTalk Management database, and file-based data for the artifact is added to the Management database as well.</span></span> <span data-ttu-id="e6e89-121">Cela vous permet de transporter facilement des applications et des artefacts d'un groupe BizTalk à un autre car vous pouvez exporter l'application et les données des artefacts dans un fichier .msi à partir de la base de données de gestion, puis les réimporter dans une base de données de gestion dans un autre groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e6e89-121">This allows you to easily transport applications and artifacts from one BizTalk group to another because you can export the application and the data for its artifacts into an .msi file from the Management database, and then import it into a Management database in a different BizTalk group.</span></span>  
  
 <span data-ttu-id="e6e89-122">Lorsque vous ajoutez un fichier de liaison à une application, vous pouvez spécifier l'environnement de déploiement cible dans lequel vous souhaitez appliquer les liaisons.</span><span class="sxs-lookup"><span data-stu-id="e6e89-122">When you add a binding file to an application, you can specify the target deployment environment in which you want the bindings to be applied.</span></span> <span data-ttu-id="e6e89-123">Contrairement à ce qui se passe lors de l'importation d'un fichier de liaison, lorsque vous ajoutez un fichier de liaison, ses liaisons ne sont pas appliquées.</span><span class="sxs-lookup"><span data-stu-id="e6e89-123">Unlike importing a binding file, when you add a binding file, its bindings are not applied.</span></span>  
  
 <span data-ttu-id="e6e89-124">Lorsque vous ajoutez un assembly BizTalk ou .NET à une application, vous pouvez spécifier à l'aide de l'option appropriée l'installation de l'assembly dans le GAC (global assembly cache).</span><span class="sxs-lookup"><span data-stu-id="e6e89-124">When you add a BizTalk assembly or a .NET assembly to an application, the assembly is added to the global assembly cache if you specify this option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e89-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6e89-125">See Also</span></span>  
 <span data-ttu-id="e6e89-126">[Que se passe-t-il pour les artefacts au cours du déploiement](../core/what-happens-to-artifacts-during-application-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="e6e89-126">[What Happens to Artifacts During Application Deployment](../core/what-happens-to-artifacts-during-application-deployment.md) </span></span>  
 <span data-ttu-id="e6e89-127">[Comment créer ou ajouter un artefact](../core/how-to-create-or-add-an-artifact.md) </span><span class="sxs-lookup"><span data-stu-id="e6e89-127">[How to Create or Add an Artifact](../core/how-to-create-or-add-an-artifact.md) </span></span>  
 <span data-ttu-id="e6e89-128">[Comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="e6e89-128">[How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md) </span></span>  
 [<span data-ttu-id="e6e89-129">Comment exporter une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="e6e89-129">How to Export a BizTalk Application</span></span>](../core/how-to-export-a-biztalk-application.md)