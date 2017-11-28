---
title: "État des artefacts de fichier au cours du déploiement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- artifacts, status
- deploying [artifacts], status
ms.assetid: 6d0f7336-c2cb-4aa4-9f1d-55fb85fe78bf
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1f57716741bb61c7a9f6f012aed14ec04c8e250
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="status-of-file-artifacts-during-deployment"></a><span data-ttu-id="019c3-102">État des artefacts de fichier lors du déploiement</span><span class="sxs-lookup"><span data-stu-id="019c3-102">Status of File Artifacts During Deployment</span></span>
<span data-ttu-id="019c3-103">Vous pouvez avoir besoin de savoir quels artefacts basés sur des fichiers existent sur le système de fichiers lors de l'exécution d'un script de pré-traitement ou de post-traitement.</span><span class="sxs-lookup"><span data-stu-id="019c3-103">You may need to know what file-based artifacts exist on the file system when a pre- or post-processing script executes.</span></span> <span data-ttu-id="019c3-104">Par exemple, vous pouvez vouloir l'exécution d'un script de post-traitement lors de la désinstallation et la suppression d'un certain fichier d'artefact du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="019c3-104">For example, you might want a post-processing script to run during uninstallation and delete a certain artifact file from the file system.</span></span> <span data-ttu-id="019c3-105">Les artefacts basés sur des fichiers sont des artefacts qui peuvent exister en tant que fichiers dans le système de fichiers local, en plus de leur représentation dans les bases de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="019c3-105">File-based artifacts are artifacts that can exist as files on the local file system, in addition to their representation in the BizTalk databases.</span></span> <span data-ttu-id="019c3-106">Parmi les artefacts basés sur des fichiers, il y a les composants COM, les assemblys .NET, les assemblys BizTalk, les artefacts BAM, les fichiers ad hoc, les scripts et les fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="019c3-106">Examples of file-based artifacts are COM components, .NET assemblies, BizTalk assemblies, BAM artifacts, ad hoc files, scripts, and binding files.</span></span>  
  
 <span data-ttu-id="019c3-107">Le tableau suivant récapitule l'état des fichiers d'artefact à chaque étape du processus de déploiement.</span><span class="sxs-lookup"><span data-stu-id="019c3-107">The following table summarizes the status of the artifact files at each point in the deployment process.</span></span>  
  
|<span data-ttu-id="019c3-108">Étape du processus de déploiement</span><span class="sxs-lookup"><span data-stu-id="019c3-108">Point in the Deployment Process</span></span>|<span data-ttu-id="019c3-109">État des fichiers d'artefact de l'application</span><span class="sxs-lookup"><span data-stu-id="019c3-109">Status of Application Artifact Files</span></span>|  
|-------------------------------------|------------------------------------------|  
|<span data-ttu-id="019c3-110">Avant installation</span><span class="sxs-lookup"><span data-stu-id="019c3-110">Pre-installation</span></span>|<span data-ttu-id="019c3-111">Seuls les fichiers du type System.BizTalk.File existent sur le système de fichiers local.*</span><span class="sxs-lookup"><span data-stu-id="019c3-111">Only files of the type System.BizTalk.File exist on the local file system.*</span></span>|  
|<span data-ttu-id="019c3-112">Après installation</span><span class="sxs-lookup"><span data-stu-id="019c3-112">Post-installation</span></span>|<span data-ttu-id="019c3-113">Tous les fichiers existent sur le système de fichiers local.*</span><span class="sxs-lookup"><span data-stu-id="019c3-113">All files exist on the local file system.*</span></span>|  
|<span data-ttu-id="019c3-114">Avant désinstallation</span><span class="sxs-lookup"><span data-stu-id="019c3-114">Pre-uninstallation</span></span>|<span data-ttu-id="019c3-115">Tous les fichiers existent sur le système de fichiers local.*</span><span class="sxs-lookup"><span data-stu-id="019c3-115">All files exist on the local file system.*</span></span>|  
|<span data-ttu-id="019c3-116">Après désinstallation</span><span class="sxs-lookup"><span data-stu-id="019c3-116">Post-uninstallation</span></span>|<span data-ttu-id="019c3-117">Tous les fichiers ont été supprimés du système de fichiers local.</span><span class="sxs-lookup"><span data-stu-id="019c3-117">All files have been deleted from the local file system.</span></span>|  
|<span data-ttu-id="019c3-118">Avant importation</span><span class="sxs-lookup"><span data-stu-id="019c3-118">Pre-import</span></span>|<span data-ttu-id="019c3-119">Aucun fichier n'existe sur le système de fichiers local, à moins que l'application n'ait été installée sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="019c3-119">No files exist on the local file system unless the application has been installed on the local computer.</span></span>|  
|<span data-ttu-id="019c3-120">Après importation</span><span class="sxs-lookup"><span data-stu-id="019c3-120">Post-import</span></span>|<span data-ttu-id="019c3-121">Aucun fichier n'existe sur le système de fichiers local, à moins que l'application n'ait été installée sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="019c3-121">No files exist on the local file system unless the application has been installed on the local computer.</span></span>|  
  
 <span data-ttu-id="019c3-122">\*Fichiers existent sur le système de fichiers local uniquement si un emplacement de destination valide a été spécifié lorsque le fichier a été ajouté à l’application.</span><span class="sxs-lookup"><span data-stu-id="019c3-122">\* Files exist on the local file system only if a valid destination location was specified when the file was added to the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="019c3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="019c3-123">See Also</span></span>  
 [<span data-ttu-id="019c3-124">À l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement d’Application</span><span class="sxs-lookup"><span data-stu-id="019c3-124">Using Pre- and Post-processing Scripts to Customize Application Deployment</span></span>](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)