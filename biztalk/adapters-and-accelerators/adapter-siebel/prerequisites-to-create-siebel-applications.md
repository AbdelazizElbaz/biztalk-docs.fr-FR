---
title: "Conditions préalables pour créer des applications Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c08f853-7f72-4e08-aa63-debdab68c972
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eeea15b7a05eb50b498c4c177c987f5c5c736a85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prerequisites-to-create-siebel-applications"></a><span data-ttu-id="e5e4d-102">Conditions préalables pour créer des applications Siebel</span><span class="sxs-lookup"><span data-stu-id="e5e4d-102">Prerequisites to create Siebel applications</span></span>
<span data-ttu-id="e5e4d-103">Ce que vous devez faire avant de développer des applications BizTalk à l’aide de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5e4d-103">What you must do before developing BizTalk applications using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="e5e4d-104">La rubrique répertorie également des outils de BizTalk Server qui sont utilisés pour développer des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-104">The topic also lists some BizTalk Server tools that are used to develop BizTalk applications.</span></span>  
  
## <a name="create-a-strong-named-key-file"></a><span data-ttu-id="e5e4d-105">Créer un fichier de clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="e5e4d-105">Create a strong-named key file</span></span>

<span data-ttu-id="e5e4d-106">Vous devez créer un fichier de clé de nom fort pour générer des projets dans Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5e4d-106">You must create a strong-name key file to build projects in Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="e5e4d-107">Un nom fort est constitué de l’identité du projet : son simple nom textuel, numéro de version et les informations de culture (le cas échéant) ; plus une clé publique et une signature numérique.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-107">A strong name consists of the project's identity — its simple text name, version number, and culture information (if provided); plus a public key and a digital signature.</span></span> <span data-ttu-id="e5e4d-108">Le fichier de clé de nom fort contient la clé publique et la clé privée.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-108">The strong-name key file contains the public key and the private key.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e5e4d-109">Création d’un fichier de clé de nom fort est une tâche unique.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-109">Creating a strong-name key file is a one-time task.</span></span> <span data-ttu-id="e5e4d-110">Vous pouvez utiliser la même clé pour toutes les applications BizTalk que vous développez.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-110">You can use the same key for all the BizTalk applications you develop.</span></span>  
  
### <a name="prerequisites"></a><span data-ttu-id="e5e4d-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e5e4d-111">Prerequisites</span></span>  
 <span data-ttu-id="e5e4d-112">Vous devez disposer de Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] installé sur l’ordinateur où vous souhaitez créer une clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-112">You must have Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] installed on the computer where you want to create a strong-name key.</span></span>  
  
### <a name="create-a-strong-name-key-file"></a><span data-ttu-id="e5e4d-113">Créer un fichier de clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="e5e4d-113">Create a strong-name key file</span></span>  
  
1.  <span data-ttu-id="e5e4d-114">Ouvrez l’invite de commandes développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-114">Open the developer command prompt for Visual Studio.</span></span>  
  
2.  <span data-ttu-id="e5e4d-115">À l’invite de commandes, accédez à l’emplacement où vous souhaitez créer le fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-115">At the command prompt, navigate to the location where you want to create the key file.</span></span> <span data-ttu-id="e5e4d-116">Par exemple, tapez `cd C:\Sample`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-116">For example, type `cd C:\Sample`, and then press ENTER.</span></span>  
  
3.  <span data-ttu-id="e5e4d-117">À l'invite de commandes, tapez `sn -k <key file name>.snk`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-117">At the command prompt, type `sn -k <key file name>.snk`, and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e5e4d-118">Vous devez recevoir un message à l’invite de commandes signalant que la paire de clés a été écrite dans le fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-118">You should receive a message at the command prompt stating that the key pair was written to the strong-name key file.</span></span>  
  
4.  <span data-ttu-id="e5e4d-119">À l'invite de commandes, tapez `exit`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-119">At the command prompt, type `exit`, and then press ENTER.</span></span>  
  
## <a name="learn-the-biztalk-server-tools"></a><span data-ttu-id="e5e4d-120">Découvrez les outils de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e5e4d-120">Learn the BizTalk Server tools</span></span>

<span data-ttu-id="e5e4d-121">Les rubriques sur l’utilisation de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] dans [blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md) sont écrits dans l’hypothèse que vous avez connaissance d’un nombre de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] outils.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-121">The topics on how to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in [Building blocks to create BizTalk applications with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md) are written with the assumption that you have working knowledge of a number of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools.</span></span> <span data-ttu-id="e5e4d-122">Vous utilisez les outils suivants pour développer des applications BizTalk à l’aide de la [!INCLUDE[adaptersiebel_md](../../includes/adaptersiebel-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="e5e4d-122">You use the following tools to develop BizTalk applications using the [!INCLUDE[adaptersiebel_md](../../includes/adaptersiebel-md.md)]:</span></span>  
  
-   <span data-ttu-id="e5e4d-123">Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5e4d-123">Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]</span></span> 
  
-   <span data-ttu-id="e5e4d-124">Explorateur BizTalk</span><span class="sxs-lookup"><span data-stu-id="e5e4d-124">BizTalk Explorer</span></span>  
  
-   <span data-ttu-id="e5e4d-125">Orchestration eesigner</span><span class="sxs-lookup"><span data-stu-id="e5e4d-125">Orchestration eesigner</span></span>  
  
-   <span data-ttu-id="e5e4d-126">Concepteur de pipeline</span><span class="sxs-lookup"><span data-stu-id="e5e4d-126">Pipeline designer</span></span>  
  
-   <span data-ttu-id="e5e4d-127">Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="e5e4d-127">BizTalk mapper</span></span>  
  
-   <span data-ttu-id="e5e4d-128">Console d’Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e5e4d-128">BizTalk Server Administration console</span></span>  
  
### <a name="prerequisites"></a><span data-ttu-id="e5e4d-129">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e5e4d-129">Prerequisites</span></span>  
 <span data-ttu-id="e5e4d-130">Vous devez installer Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] avant de pouvoir accéder le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] outils.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-130">You must install Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] before you can access the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools.</span></span>  
  
### <a name="biztalk-server-tools"></a><span data-ttu-id="e5e4d-131">Outils de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e5e4d-131">BizTalk Server Tools</span></span>  
 <span data-ttu-id="e5e4d-132">Le tableau suivant présente les rubriques de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation qui expliquent comment utiliser chacun des outils répertoriés.</span><span class="sxs-lookup"><span data-stu-id="e5e4d-132">The following table includes topics in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation that explain how to use each of the listed tools.</span></span>  
  
|<span data-ttu-id="e5e4d-133">Outil</span><span class="sxs-lookup"><span data-stu-id="e5e4d-133">Tool</span></span>|<span data-ttu-id="e5e4d-134">Rubriques de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation de base</span><span class="sxs-lookup"><span data-stu-id="e5e4d-134">Topics in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] core documentation</span></span>|  
|---|---|  
|[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]|<span data-ttu-id="e5e4d-135">-   [À l’aide de Visual Studio](../../core/using-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="e5e4d-135">-   [Using Visual Studio](../../core/using-visual-studio.md)</span></span> <br /><span data-ttu-id="e5e4d-136">-   [Utilisation des projets BizTalk](../../core/working-with-biztalk-projects.md)</span><span class="sxs-lookup"><span data-stu-id="e5e4d-136">-   [Working with BizTalk Projects](../../core/working-with-biztalk-projects.md)</span></span><br /><span data-ttu-id="e5e4d-137">-   [Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)</span><span class="sxs-lookup"><span data-stu-id="e5e4d-137">-   [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)</span></span><br /><br /> <span data-ttu-id="e5e4d-138">En savoir plus sur les solutions de Visual Studio, projets et les éléments à [Solutions et projets dans Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx).</span><span class="sxs-lookup"><span data-stu-id="e5e4d-138">Learn more about Visual Studio solutions, projects, and items at [Solutions and Projects in Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx).</span></span>|  
|<span data-ttu-id="e5e4d-139">Concepteur d'orchestration</span><span class="sxs-lookup"><span data-stu-id="e5e4d-139">Orchestration Designer</span></span>|[<span data-ttu-id="e5e4d-140">Création d’Orchestrations à l’aide du Concepteur d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="e5e4d-140">Creating Orchestrations Using Orchestration Designer</span></span>](../../core/creating-orchestrations-using-orchestration-designer.md)|  
|<span data-ttu-id="e5e4d-141">Concepteur de pipeline</span><span class="sxs-lookup"><span data-stu-id="e5e4d-141">Pipeline Designer</span></span>| [<span data-ttu-id="e5e4d-142">Création de Pipelines à l’aide du Concepteur de Pipeline</span><span class="sxs-lookup"><span data-stu-id="e5e4d-142">Creating Pipelines Using Pipeline Designer</span></span>](../../core/creating-pipelines-using-pipeline-designer.md)|  
|<span data-ttu-id="e5e4d-143">Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="e5e4d-143">BizTalk Mapper</span></span>| [<span data-ttu-id="e5e4d-144">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="e5e4d-144">Creating Maps Using BizTalk Mapper</span></span>](../../core/creating-maps-using-biztalk-mapper.md)|  
|<span data-ttu-id="e5e4d-145">Console d’Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e5e4d-145">BizTalk Server Administration console</span></span>|[<span data-ttu-id="e5e4d-146">À l’aide de la Console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e5e4d-146">Using the BizTalk Server Administration Console</span></span>](../../core/using-the-biztalk-server-administration-console.md)|  
  
## <a name="next"></a><span data-ttu-id="e5e4d-147">Suivant</span><span class="sxs-lookup"><span data-stu-id="e5e4d-147">Next</span></span>
[<span data-ttu-id="e5e4d-148">Blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="e5e4d-148">Building blocks to create BizTalk applications with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)