---
title: "Gérer les ressources | Documents Microsoft"
description: Utilisez btstask ou la console Administration de BizTalk pour travailler avec les assemblys, les scripts, les certificats, les fichiers de liaison et plus dans BizTalk Server
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b478ef2e-1363-4c2c-a4b7-6a582a6b33a5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07248c1689adf6b6474fd8e1f3e01f2d660becdc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-resources"></a><span data-ttu-id="085fa-103">Gérer les ressources</span><span class="sxs-lookup"><span data-stu-id="085fa-103">Manage Resources</span></span>

## <a name="overview"></a><span data-ttu-id="085fa-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="085fa-104">Overview</span></span>
<span data-ttu-id="085fa-105">Cette rubrique fournit des instructions sur l'utilisation de la console Administration de BizTalk Server ou de l'outil de ligne de commande BTSTask afin de gérer les ressources BizTalk Server une fois celles-ci déployées dans un groupe.</span><span class="sxs-lookup"><span data-stu-id="085fa-105">The topics in this section provide instructions on how to use the BizTalk Server Administration console or the BTSTask command-line tool to manage BizTalk Server resources after they have been deployed into a BizTalk group.</span></span> <span data-ttu-id="085fa-106">Les ressources incluent des artefacts de types suivants :</span><span class="sxs-lookup"><span data-stu-id="085fa-106">Resources include the following types of artifacts:</span></span>  
  
-   <span data-ttu-id="085fa-107">Assemblys BizTalk</span><span class="sxs-lookup"><span data-stu-id="085fa-107">BizTalk Assemblies</span></span>  
  
-   <span data-ttu-id="085fa-108">Scripts de pré-traitement et de post-traitement</span><span class="sxs-lookup"><span data-stu-id="085fa-108">Pre- and post-processing scripts</span></span>  
  
-   <span data-ttu-id="085fa-109">assemblys .NET</span><span class="sxs-lookup"><span data-stu-id="085fa-109">.NET assemblies</span></span>  
  
-   <span data-ttu-id="085fa-110">composants des services COM</span><span class="sxs-lookup"><span data-stu-id="085fa-110">COM components</span></span>  
  
-   <span data-ttu-id="085fa-111">Certificats</span><span class="sxs-lookup"><span data-stu-id="085fa-111">Certificates</span></span>  
  
-   <span data-ttu-id="085fa-112">Fichiers ad hoc</span><span class="sxs-lookup"><span data-stu-id="085fa-112">Ad hoc files</span></span>  
  
-   <span data-ttu-id="085fa-113">définitions BAM</span><span class="sxs-lookup"><span data-stu-id="085fa-113">BAM definitions</span></span>  
  
-   <span data-ttu-id="085fa-114">Fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="085fa-114">Binding files</span></span>  
  
-   <span data-ttu-id="085fa-115">Répertoires virtuels</span><span class="sxs-lookup"><span data-stu-id="085fa-115">Virtual directories</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="085fa-116">Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="085fa-116">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="085fa-117">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="085fa-117">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
> [!NOTE]
>  <span data-ttu-id="085fa-118">N'ajoutez jamais plusieurs ressources portant le même nom à un groupe BizTalk, quel que soit le cas.</span><span class="sxs-lookup"><span data-stu-id="085fa-118">Do not add multiple resources with the same name, regardless of case, to a BizTalk Server group.</span></span> <span data-ttu-id="085fa-119">La gestion de ressources multiples portant le même nom dans un groupe BizTalk Server n'est pas prise en charge, même lorsque la base de données de gestion BizTalk est hébergée sur un serveur SQL configuré pour utiliser les classements binaires et prenant en charge le respect de la casse.</span><span class="sxs-lookup"><span data-stu-id="085fa-119">Adding multiple resources with the same name to a BizTalk Server group is not supported, even when the BizTalk Server management database is housed on a SQL Server that is configured to use binary collation and supports case sensitivity.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="085fa-120">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="085fa-120">Next steps</span></span>
  
-   [<span data-ttu-id="085fa-121">Gestion des assemblys BizTalk</span><span class="sxs-lookup"><span data-stu-id="085fa-121">Managing BizTalk Assemblies</span></span>](../core/managing-biztalk-assemblies.md)  
  
-   [<span data-ttu-id="085fa-122">Gestion des Scripts de pré-traitement et post-traitement</span><span class="sxs-lookup"><span data-stu-id="085fa-122">Managing Pre- and Post-processing Scripts</span></span>](../core/managing-pre-and-post-processing-scripts.md)  
  
-   [<span data-ttu-id="085fa-123">La gestion des assemblys .NET, certificats et autres ressources</span><span class="sxs-lookup"><span data-stu-id="085fa-123">Managing .NET Assemblies, Certificates, and Other Resources</span></span>](../core/managing-net-assemblies-certificates-and-other-resources.md)  
  
-   [<span data-ttu-id="085fa-124">Actualisation d’une ressource</span><span class="sxs-lookup"><span data-stu-id="085fa-124">Refresh a Resource</span></span>](../core/how-to-refresh-a-resource.md)