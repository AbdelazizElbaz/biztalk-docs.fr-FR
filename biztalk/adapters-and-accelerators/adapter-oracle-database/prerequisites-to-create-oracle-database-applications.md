---
title: Conditions préalables requises pour créer des applications de base de données Oracle | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strong-name key file, creating a
ms.assetid: 7a6b2e50-8153-468c-a25e-c15612792773
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba73b79cbbb7914f53c066b474deb23ffcaa9c10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prerequisites-to-create-oracle-database-applications"></a><span data-ttu-id="945e3-102">Conditions préalables requises pour créer des applications de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="945e3-102">Prerequisites to create Oracle Database applications</span></span>
<span data-ttu-id="945e3-103">Ce que vous devez faire avant de développer des applications BizTalk à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="945e3-103">What you must do before developing BizTalk applications using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="945e3-104">La section répertorie également des outils de BizTalk Server qui sont utilisés pour développer des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="945e3-104">The section also lists some BizTalk Server tools that are used to develop BizTalk applications.</span></span>  
  
## <a name="create-a-strong-named-key-file"></a><span data-ttu-id="945e3-105">Créer un fichier de clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="945e3-105">Create a strong-named key file</span></span>

<span data-ttu-id="945e3-106">Vous devez créer un fichier de clé de nom fort pour générer des projets dans Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="945e3-106">You must create a strong-name key file to build projects in Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="945e3-107">Un nom fort est constitué de l’identité du projet : son simple nom textuel, numéro de version et les informations de culture (le cas échéant) ; plus une clé publique et une signature numérique.</span><span class="sxs-lookup"><span data-stu-id="945e3-107">A strong name consists of the project's identity — its simple text name, version number, and culture information (if provided); plus a public key and a digital signature.</span></span> <span data-ttu-id="945e3-108">Le fichier de clé de nom fort contient la clé publique et la clé privée.</span><span class="sxs-lookup"><span data-stu-id="945e3-108">The strong-name key file contains the public key and the private key.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="945e3-109">Création d’un fichier de clé de nom fort est une tâche unique.</span><span class="sxs-lookup"><span data-stu-id="945e3-109">Creating a strong-name key file is a one-time task.</span></span> <span data-ttu-id="945e3-110">Vous pouvez utiliser la même clé pour toutes les applications BizTalk que vous développez.</span><span class="sxs-lookup"><span data-stu-id="945e3-110">You can use the same key for all the BizTalk applications you develop.</span></span>  
  
### <a name="prerequisites"></a><span data-ttu-id="945e3-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="945e3-111">Prerequisites</span></span>  
 <span data-ttu-id="945e3-112">Vous devez disposer de Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] installé sur l’ordinateur où vous souhaitez créer une clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="945e3-112">You must have Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] installed on the computer where you want to create a strong-name key.</span></span>  
  
### <a name="create-a-strong-name-key-file"></a><span data-ttu-id="945e3-113">Créer un fichier de clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="945e3-113">Create a strong-name key file</span></span>  
  
1.  <span data-ttu-id="945e3-114">Ouvrez l’invite de commandes développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="945e3-114">Open the developer command prompt for Visual Studio.</span></span>  
  
2.  <span data-ttu-id="945e3-115">À l’invite de commandes, accédez à l’emplacement où vous souhaitez créer le fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="945e3-115">At the command prompt, navigate to the location where you want to create the key file.</span></span> <span data-ttu-id="945e3-116">Par exemple, tapez `cd C:\Sample`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="945e3-116">For example, type `cd C:\Sample`, and then press ENTER.</span></span>  
  
3.  <span data-ttu-id="945e3-117">À l'invite de commandes, tapez `sn -k <key file name>.snk`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="945e3-117">At the command prompt, type `sn -k <key file name>.snk`, and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="945e3-118">Vous devez recevoir un message à l’invite de commandes signalant que la paire de clés a été écrite dans le fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="945e3-118">You should receive a message at the command prompt stating that the key pair was written to the strong-name key file.</span></span>  
  
4.  <span data-ttu-id="945e3-119">À l'invite de commandes, tapez `exit`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="945e3-119">At the command prompt, type `exit`, and then press ENTER.</span></span>  
  
## <a name="learn-the-biztalk-server-tools"></a><span data-ttu-id="945e3-120">Découvrez les outils de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="945e3-120">Learn the BizTalk Server tools</span></span>

<span data-ttu-id="945e3-121">Les rubriques sur l’utilisation de la [!INCLUDE[adapteroracle_short_md](../../includes/adapteroracle-short-md.md)] dans [blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) sont écrits dans l’hypothèse que vous avez connaissance d’un nombre de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] outils.</span><span class="sxs-lookup"><span data-stu-id="945e3-121">The topics on how to use the [!INCLUDE[adapteroracle_short_md](../../includes/adapteroracle-short-md.md)] in [Building Blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) are written with the assumption that you have working knowledge of a number of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools.</span></span> <span data-ttu-id="945e3-122">Vous utilisez les outils suivants pour développer des applications BizTalk à l’aide de la [!INCLUDE[adapteroracle_md](../../includes/adapteroracle-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="945e3-122">You use the following tools to develop BizTalk applications using the [!INCLUDE[adapteroracle_md](../../includes/adapteroracle-md.md)]:</span></span>  
  
-   <span data-ttu-id="945e3-123">Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="945e3-123">Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]</span></span> 
  
-   <span data-ttu-id="945e3-124">Explorateur BizTalk</span><span class="sxs-lookup"><span data-stu-id="945e3-124">BizTalk Explorer</span></span>  
  
-   <span data-ttu-id="945e3-125">Orchestration eesigner</span><span class="sxs-lookup"><span data-stu-id="945e3-125">Orchestration eesigner</span></span>  
  
-   <span data-ttu-id="945e3-126">Concepteur de pipeline</span><span class="sxs-lookup"><span data-stu-id="945e3-126">Pipeline designer</span></span>  
  
-   <span data-ttu-id="945e3-127">Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="945e3-127">BizTalk mapper</span></span>  
  
-   <span data-ttu-id="945e3-128">Console d’Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="945e3-128">BizTalk Server Administration console</span></span>  
  
### <a name="prerequisites"></a><span data-ttu-id="945e3-129">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="945e3-129">Prerequisites</span></span>  
 <span data-ttu-id="945e3-130">Vous devez installer Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] avant de pouvoir accéder le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] outils.</span><span class="sxs-lookup"><span data-stu-id="945e3-130">You must install Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] before you can access the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools.</span></span>  
  
### <a name="biztalk-server-tools"></a><span data-ttu-id="945e3-131">Outils de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="945e3-131">BizTalk Server Tools</span></span>  
 <span data-ttu-id="945e3-132">Le tableau suivant présente les rubriques de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation qui expliquent comment utiliser chacun des outils répertoriés.</span><span class="sxs-lookup"><span data-stu-id="945e3-132">The following table includes topics in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation that explain how to use each of the listed tools.</span></span>  
  
|<span data-ttu-id="945e3-133">Outil</span><span class="sxs-lookup"><span data-stu-id="945e3-133">Tool</span></span>|<span data-ttu-id="945e3-134">Rubriques de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation de base</span><span class="sxs-lookup"><span data-stu-id="945e3-134">Topics in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] core documentation</span></span>|  
|---|---|  
|[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]|<span data-ttu-id="945e3-135">-   [À l’aide de Visual Studio](../../core/using-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="945e3-135">-   [Using Visual Studio](../../core/using-visual-studio.md)</span></span> <br /><span data-ttu-id="945e3-136">-   [Utilisation des projets BizTalk](../../core/working-with-biztalk-projects.md)</span><span class="sxs-lookup"><span data-stu-id="945e3-136">-   [Working with BizTalk Projects](../../core/working-with-biztalk-projects.md)</span></span><br /><span data-ttu-id="945e3-137">-   [Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)</span><span class="sxs-lookup"><span data-stu-id="945e3-137">-   [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)</span></span><br /><br /> <span data-ttu-id="945e3-138">En savoir plus sur les solutions de Visual Studio, projets et les éléments à [Solutions et projets dans Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx).</span><span class="sxs-lookup"><span data-stu-id="945e3-138">Learn more about Visual Studio solutions, projects, and items at [Solutions and Projects in Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx).</span></span>|  
|<span data-ttu-id="945e3-139">Concepteur d'orchestration</span><span class="sxs-lookup"><span data-stu-id="945e3-139">Orchestration Designer</span></span>|[<span data-ttu-id="945e3-140">Création d’orchestrations à l’aide du Concepteur d’orchestration</span><span class="sxs-lookup"><span data-stu-id="945e3-140">Creating orchestrations using orchestration designer</span></span>](../../core/creating-orchestrations-using-orchestration-designer.md)|  
|<span data-ttu-id="945e3-141">Concepteur de pipeline</span><span class="sxs-lookup"><span data-stu-id="945e3-141">Pipeline Designer</span></span>| [<span data-ttu-id="945e3-142">Création de pipelines à l’aide du Concepteur de pipeline</span><span class="sxs-lookup"><span data-stu-id="945e3-142">Creating pipelines using pipeline designer</span></span>](../../core/creating-pipelines-using-pipeline-designer.md)|  
|<span data-ttu-id="945e3-143">Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="945e3-143">BizTalk Mapper</span></span>| [<span data-ttu-id="945e3-144">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="945e3-144">Creating maps using BizTalk mapper</span></span>](../../core/creating-maps-using-biztalk-mapper.md)|  
|<span data-ttu-id="945e3-145">Console d’Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="945e3-145">BizTalk Server Administration console</span></span>|[<span data-ttu-id="945e3-146">Utilisation de la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="945e3-146">Using the BizTalk Server Administration console</span></span>](../../core/using-the-biztalk-server-administration-console.md)|  
  
## <a name="next"></a><span data-ttu-id="945e3-147">Suivant</span><span class="sxs-lookup"><span data-stu-id="945e3-147">Next</span></span>
[<span data-ttu-id="945e3-148">Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="945e3-148">Building Blocks to develop BizTalk Applications with Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)