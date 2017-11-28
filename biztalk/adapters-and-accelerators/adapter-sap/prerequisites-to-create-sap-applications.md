---
title: "Conditions préalables pour créer des applications SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51ae9569-4081-4142-9ee2-8ae0069e9d90
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b7cddc252868bf47ace0d73e81ddb1c7721bf8a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prerequisites-to-create-sap-applications"></a><span data-ttu-id="8eb45-102">Conditions préalables pour créer des applications SAP</span><span class="sxs-lookup"><span data-stu-id="8eb45-102">Prerequisites to create SAP applications</span></span>
<span data-ttu-id="8eb45-103">Cette section fournit des informations sur les tâches que vous devez effectuer avant de développer des applications BizTalk à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8eb45-103">This section provides information about tasks that you must perform before developing BizTalk applications using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="8eb45-104">La section répertorie également des outils de BizTalk Server qui sont utilisés pour développer des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8eb45-104">The section also lists some BizTalk Server tools that are used to develop BizTalk applications.</span></span>  
  
## <a name="create-a-strong-name-key-file"></a><span data-ttu-id="8eb45-105">Créer un fichier de clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="8eb45-105">Create a strong-name key file</span></span>

<span data-ttu-id="8eb45-106">Vous devez créer un fichier de clé de nom fort pour générer des projets dans Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8eb45-106">You must create a strong-name key file to build projects in Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="8eb45-107">Un nom fort est constitué de l’identité du projet : son simple nom textuel, numéro de version et des informations de culture (le cas échéant), ainsi qu’une clé publique et une signature numérique.</span><span class="sxs-lookup"><span data-stu-id="8eb45-107">A strong name consists of the project's identity—its simple text name, version number, and culture information (if provided)—plus a public key and a digital signature.</span></span> <span data-ttu-id="8eb45-108">Le fichier de clé de nom fort contient la clé publique et la clé privée.</span><span class="sxs-lookup"><span data-stu-id="8eb45-108">The strong-name key file contains the public key and the private key.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8eb45-109">Création d’un fichier de clé de nom fort est une tâche unique.</span><span class="sxs-lookup"><span data-stu-id="8eb45-109">Creating a strong-name key file is a one-time task.</span></span> <span data-ttu-id="8eb45-110">Vous pouvez utiliser la même clé pour toutes les applications BizTalk que vous développez.</span><span class="sxs-lookup"><span data-stu-id="8eb45-110">You can use the same key for all the BizTalk applications you develop.</span></span>  
  
1.  <span data-ttu-id="8eb45-111">Ouvrez l’invite de commandes développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8eb45-111">Open the developer command prompt for Visual Studio.</span></span>  
  
2.  <span data-ttu-id="8eb45-112">À l’invite de commandes, accédez à l’emplacement où vous souhaitez créer le fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="8eb45-112">At the command prompt navigate to the location where you want to create the key file.</span></span> <span data-ttu-id="8eb45-113">Par exemple, tapez **cd C:\Sample**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8eb45-113">For example, type **cd C:\Sample**,and then press ENTER.</span></span>  
  
3.  <span data-ttu-id="8eb45-114">À l'invite de commandes, tapez `sn -k <key file name\>.snk`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8eb45-114">At the command prompt, type `sn -k <key file name\>.snk`, and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8eb45-115">Vous devez recevoir un message à l’invite de commandes signalant que la paire de clés a été écrite dans le fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="8eb45-115">You should receive a message at the command prompt stating that the key pair was written to the strong-name key file.</span></span>  
  
4.  <span data-ttu-id="8eb45-116">À l’invite de commandes, tapez **quitter**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8eb45-116">At the command prompt, type **exit**, and then press ENTER.</span></span>  

## <a name="learn-the-biztalk-server-tools"></a><span data-ttu-id="8eb45-117">Découvrez les outils de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8eb45-117">Learn the BizTalk Server tools</span></span>

<span data-ttu-id="8eb45-118">Les rubriques sur l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans [BizTalk de développer des applications](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md) supposent que vous avez connaissance d’un nombre d’outils de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8eb45-118">The topics on how to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in [Develop BizTalk applications](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md) assume that you have working knowledge of a number of BizTalk Server tools.</span></span> <span data-ttu-id="8eb45-119">Vous allez utiliser les outils suivants pour développer des applications BizTalk à l’aide de [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="8eb45-119">You will use the following tools to develop BizTalk applications using [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:</span></span>  
  
-   <span data-ttu-id="8eb45-120">Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eb45-120">Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]</span></span> 
  
-   <span data-ttu-id="8eb45-121">Orchestration eesigner</span><span class="sxs-lookup"><span data-stu-id="8eb45-121">Orchestration eesigner</span></span>  
  
-   <span data-ttu-id="8eb45-122">Concepteur de pipeline</span><span class="sxs-lookup"><span data-stu-id="8eb45-122">Pipeline designer</span></span>  
  
-   <span data-ttu-id="8eb45-123">Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="8eb45-123">BizTalk mapper</span></span>  
  
-   <span data-ttu-id="8eb45-124">la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] ;</span><span class="sxs-lookup"><span data-stu-id="8eb45-124">[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console</span></span>  

  
### <a name="prerequisites"></a><span data-ttu-id="8eb45-125">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8eb45-125">Prerequisites</span></span>  
 <span data-ttu-id="8eb45-126">Vous devez installer [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] avant de pouvoir accéder aux outils [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8eb45-126">You must install [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] before you can access the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools.</span></span>  
  
### <a name="biztalk-server-tools"></a><span data-ttu-id="8eb45-127">Outils de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8eb45-127">BizTalk Server Tools</span></span>  
 <span data-ttu-id="8eb45-128">Le tableau suivant présente les rubriques de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation qui expliquent comment utiliser chacun des outils répertoriés.</span><span class="sxs-lookup"><span data-stu-id="8eb45-128">The following table includes topics in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation that explain how to use each of the listed tools.</span></span>  

|<span data-ttu-id="8eb45-129">Outil</span><span class="sxs-lookup"><span data-stu-id="8eb45-129">Tool</span></span>|<span data-ttu-id="8eb45-130">Rubriques de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation de base</span><span class="sxs-lookup"><span data-stu-id="8eb45-130">Topics in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] core documentation</span></span>|  
|---|---|  
|[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]|<span data-ttu-id="8eb45-131">-   [À l’aide de Visual Studio](../../core/using-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="8eb45-131">-   [Using Visual Studio](../../core/using-visual-studio.md)</span></span> <br /><span data-ttu-id="8eb45-132">-   [Utilisation des projets BizTalk](../../core/working-with-biztalk-projects.md)</span><span class="sxs-lookup"><span data-stu-id="8eb45-132">-   [Working with BizTalk Projects](../../core/working-with-biztalk-projects.md)</span></span><br /><span data-ttu-id="8eb45-133">-   [Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)</span><span class="sxs-lookup"><span data-stu-id="8eb45-133">-   [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)</span></span><br /><br /> <span data-ttu-id="8eb45-134">En savoir plus sur les solutions de Visual Studio, projets et les éléments à [Solutions et projets dans Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx).</span><span class="sxs-lookup"><span data-stu-id="8eb45-134">Learn more about Visual Studio solutions, projects, and items at [Solutions and Projects in Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx).</span></span>|  
|<span data-ttu-id="8eb45-135">Concepteur d'orchestration</span><span class="sxs-lookup"><span data-stu-id="8eb45-135">Orchestration Designer</span></span>|[<span data-ttu-id="8eb45-136">Création d’orchestrations à l’aide du Concepteur d’orchestration</span><span class="sxs-lookup"><span data-stu-id="8eb45-136">Creating orchestrations using orchestration designer</span></span>](../../core/creating-orchestrations-using-orchestration-designer.md)|  
|<span data-ttu-id="8eb45-137">Concepteur de pipeline</span><span class="sxs-lookup"><span data-stu-id="8eb45-137">Pipeline Designer</span></span>| [<span data-ttu-id="8eb45-138">Création de pipelines à l’aide du Concepteur de pipeline</span><span class="sxs-lookup"><span data-stu-id="8eb45-138">Creating pipelines using pipeline designer</span></span>](../../core/creating-pipelines-using-pipeline-designer.md)|  
|<span data-ttu-id="8eb45-139">Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="8eb45-139">BizTalk Mapper</span></span>| [<span data-ttu-id="8eb45-140">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="8eb45-140">Creating maps using BizTalk mapper</span></span>](../../core/creating-maps-using-biztalk-mapper.md)|  
|<span data-ttu-id="8eb45-141">Console d’Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8eb45-141">BizTalk Server Administration console</span></span>|[<span data-ttu-id="8eb45-142">Utilisation de la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8eb45-142">Using the BizTalk Server Administration console</span></span>](../../core/using-the-biztalk-server-administration-console.md)|  

## <a name="next"></a><span data-ttu-id="8eb45-143">Suivant</span><span class="sxs-lookup"><span data-stu-id="8eb45-143">Next</span></span>
[<span data-ttu-id="8eb45-144">Blocs de construction pour créer des applications SAP</span><span class="sxs-lookup"><span data-stu-id="8eb45-144">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)