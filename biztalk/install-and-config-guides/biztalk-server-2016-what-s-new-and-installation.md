---
title: "BizTalk Server 2016 : Quelles sont les nouveautés et Installation | Documents Microsoft"
description: "Introduction aux nouveautés et lors de l’installation et la mise à niveau vers BizTalk Server 2016"
ms.custom: 
ms.prod: biztalk-server
ms.date: 08/10/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 229043b3-b1a4-47e9-9c0e-1fba5ec5b417
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 212eee411c78bacd3d46ca66762fc8fc0f25fa05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-2016-whats-new-and-installation"></a><span data-ttu-id="4fb3f-103">BizTalk Server 2016 : Nouveautés et installation</span><span class="sxs-lookup"><span data-stu-id="4fb3f-103">BizTalk Server 2016: What's New, and Installation</span></span>

## <a name="get-started-with-biztalk-server-2016"></a><span data-ttu-id="4fb3f-104">Bien démarrer avec BizTalk Server 2016</span><span class="sxs-lookup"><span data-stu-id="4fb3f-104">Get started with BizTalk Server 2016</span></span>

[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]<span data-ttu-id="4fb3f-105"> est la dernière version locale.</span><span class="sxs-lookup"><span data-stu-id="4fb3f-105"> is the latest on-premises release.</span></span> <span data-ttu-id="4fb3f-106">Elle offre une intégration plus étroite avec Azure à l’aide du nouvel adaptateur Logic Apps et vous permet de vous connecter aux ressources Azure à l’aide des adaptateurs WCF-SQL et de fichier.</span><span class="sxs-lookup"><span data-stu-id="4fb3f-106">With this new version, you can expect closer integration with Azure using the new Logic Apps adapter, and connect to Azure resources using the File and WCF-SQL adapters.</span></span> 

<span data-ttu-id="4fb3f-107">L’un des plus grands changements est la prise en charge des groupes de disponibilité AlwaysOn SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="4fb3f-107">One of the biggest changes is support for SQL Server 2016 AlwaysOn Availability Groups (AG).</span></span> <span data-ttu-id="4fb3f-108">Cette prise en charge couvre l’utilisation de BizTalk Server sur site et l’utilisation des machines virtuelles Azure BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="4fb3f-108">This support covers using BizTalk Server on-premises, and using BizTalk Server Azure virtual machines.</span></span> <span data-ttu-id="4fb3f-109">Grâce à la fonctionnalité AlwaysOn, vous pouvez désormais disposer d’une solution hautement disponible à l’aide des machines virtuelles Azure.</span><span class="sxs-lookup"><span data-stu-id="4fb3f-109">With AlwaysOn, you can now have a highly-available solution using Azure virtual machines.</span></span>

<span data-ttu-id="4fb3f-110">Des mises à jour ont également été publiées pour la prise en charge SHA-2, les options de liaison d’importation et d’exportation pour les tiers, les améliorations de la console Administration, et plus encore.</span><span class="sxs-lookup"><span data-stu-id="4fb3f-110">There have also been updates to SHA-2 support, import and export binding options for parties, Administration console improvements, and much much more.</span></span> 

<span data-ttu-id="4fb3f-111">Dans cet ensemble de rubriques [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], nous nous concentrons sur la documentation spécifique à [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], notamment ses nouveautés et son installation.</span><span class="sxs-lookup"><span data-stu-id="4fb3f-111">In this [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] set of topics, we focus on the specific documentation for [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], including what's changed, and the installation.</span></span> <span data-ttu-id="4fb3f-112">Par conséquent, si vous souhaitez en savoir plus sur la haute disponibilité, l’analyse de l’environnement BizTalk et plus encore, reportez-vous à la [documentation principale de BizTalk Server](../core/biztalk-server-core-documentation.md).</span><span class="sxs-lookup"><span data-stu-id="4fb3f-112">So, if you want to read about high availability, monitoring your BIzTalk environment, and more, then go to the [BizTalk Server core documentation](../core/biztalk-server-core-documentation.md).</span></span> <span data-ttu-id="4fb3f-113">Si vous souhaitez configurer BizTalk Server, consultez [Configuration de BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="4fb3f-113">If you want to configure BizTalk Server, then go [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).</span></span> <span data-ttu-id="4fb3f-114">Si vous souhaitez en savoir plus sur les nouveautés et installer [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], commencez par consulter les liens suivants :</span><span class="sxs-lookup"><span data-stu-id="4fb3f-114">If you want to read about what's new, and install [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], then get started with the following links:</span></span>  

* [<span data-ttu-id="4fb3f-115">Nouveautés</span><span class="sxs-lookup"><span data-stu-id="4fb3f-115">What's New</span></span>](../install-and-config-guides/what-s-new-in-biztalk-server-2016.md)  
* [<span data-ttu-id="4fb3f-116">Configuration matérielle et logicielle requise</span><span class="sxs-lookup"><span data-stu-id="4fb3f-116">Hardware and Software Requirements</span></span>](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)  
* [<span data-ttu-id="4fb3f-117">Prérequis d’installation et de configuration</span><span class="sxs-lookup"><span data-stu-id="4fb3f-117">Set up and install prerequisites</span></span>](../install-and-config-guides/set-up-and-install-prerequisites-for-biztalk-server-2016.md)  
* [<span data-ttu-id="4fb3f-118">Installer BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4fb3f-118">Install BizTalk Server</span></span>](../install-and-config-guides/install-biztalk-server-2016.md)
* [<span data-ttu-id="4fb3f-119">Mettre à niveau BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4fb3f-119">Upgrade BizTalk Server</span></span>](../install-and-config-guides/upgrade-to-biztalk-server-2016.md)
  
## <a name="more-good-stuff"></a><span data-ttu-id="4fb3f-120">Autre contenu intéressant</span><span class="sxs-lookup"><span data-stu-id="4fb3f-120">More good stuff</span></span>
[<span data-ttu-id="4fb3f-121">Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4fb3f-121">Configure BizTalk Server</span></span>](../install-and-config-guides/configure-biztalk-server.md)

[<span data-ttu-id="4fb3f-122">Configuration de BizTalk Server dans un cluster</span><span class="sxs-lookup"><span data-stu-id="4fb3f-122">Configure BizTalk Server in a Cluster</span></span>](../install-and-config-guides/configure-biztalk-server-in-a-cluster.md)

[<span data-ttu-id="4fb3f-123">Étapes d’optimisation de l’environnement après configuration</span><span class="sxs-lookup"><span data-stu-id="4fb3f-123">Post-configuration steps to optimize your environment</span></span>](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)

[<span data-ttu-id="4fb3f-124">Importation et exportation de la configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4fb3f-124">Import and Export BizTalk Server Configuration</span></span>](../install-and-config-guides/import-and-export-biztalk-server-configuration.md)

[<span data-ttu-id="4fb3f-125">Consolidation des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4fb3f-125">Consolidate the BizTalk Server Databases</span></span>](../install-and-config-guides/consolidate-the-biztalk-server-databases2.md)

[<span data-ttu-id="4fb3f-126">Utilisation de Configuration Framework</span><span class="sxs-lookup"><span data-stu-id="4fb3f-126">Working with the Configuration Framework</span></span>](../install-and-config-guides/working-with-the-configuration-framework.md)

[<span data-ttu-id="4fb3f-127">Sécurisation d’un déploiement BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4fb3f-127">Securing Your BizTalk Server Deployment</span></span>](../install-and-config-guides/securing-your-biztalk-server-deployment.md)

[<span data-ttu-id="4fb3f-128">Désinstallation et annulation de la configuration de BizTalk Server pour le supprimer</span><span class="sxs-lookup"><span data-stu-id="4fb3f-128">Uninstall and unconfigure BizTalk Server to remove it</span></span>](../install-and-config-guides/uninstall-and-unconfigure-biztalk-server-to-remove-it.md)