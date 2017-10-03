---
title: Ajouter une application BizTalk Server pour Visual Studio Team Services | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2c7a1ff-0f26-45f3-9a9b-4c99a67b51a9
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: d3fc8c0253c8e2517f78c2d60fdc7c74a983bdbd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="add-a-biztalk-server-application-to-visual-studio-team-services"></a><span data-ttu-id="aabc9-102">Ajouter une application BizTalk Server pour Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="aabc9-102">Add a BizTalk Server application to Visual Studio Team Services</span></span>
<span data-ttu-id="aabc9-103">Ajouter un [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] projet VSTS pour déployer automatiquement à l’aide de l’intégration continue.</span><span class="sxs-lookup"><span data-stu-id="aabc9-103">Add a [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] project to VSTS to automatically deploy using continuous integration.</span></span>  

<span data-ttu-id="aabc9-104">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , vous pouvez déployer automatiquement vos applications pour votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements à l’aide de Visual Studio Team Services (VSTS).</span><span class="sxs-lookup"><span data-stu-id="aabc9-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, you can automatically deploy your applications to your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments using Visual Studio Team Services (VSTS).</span></span> 

<span data-ttu-id="aabc9-105">Cette rubrique fournit une vue d’ensemble et répertorie les principales étapes pour déployer votre solution à partir de Visual Studio pour votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aabc9-105">This topics provides an overview, and lists the key steps to deploy your solution from Visual Studio to your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="aabc9-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="aabc9-106">Prerequisites</span></span>
* <span data-ttu-id="aabc9-107">Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aabc9-107">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* [<span data-ttu-id="aabc9-108">Configurer VSTS pour le déploiement automatique</span><span class="sxs-lookup"><span data-stu-id="aabc9-108">Configure VSTS for automatic deployment</span></span>](../core/configure-visual-studio-team-services-to-deploy-biztalk-solutions-or-projects.md)
* <span data-ttu-id="aabc9-109">Base de connaissances et expérience avec Git et des référentiels dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aabc9-109">Knowledge and experience working with Git and repositories in Visual Studio.</span></span> <span data-ttu-id="aabc9-110">Si vous êtes débutant dépôts et le contrôle de version, il peut s’agir de bonnes ressources :</span><span class="sxs-lookup"><span data-stu-id="aabc9-110">If you're brand new to repositories and version control, these may be good resources:</span></span> 

    [<span data-ttu-id="aabc9-111">En savoir plus Git</span><span class="sxs-lookup"><span data-stu-id="aabc9-111">Learn Git</span></span>](https://www.visualstudio.com/learn-git/)  
    [<span data-ttu-id="aabc9-112">GIT et Team Services</span><span class="sxs-lookup"><span data-stu-id="aabc9-112">Git and Team Services</span></span>](https://www.visualstudio.com/docs/git/overview)
* <span data-ttu-id="aabc9-113">Base de connaissances et expérience des projets BizTalk dans[!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aabc9-113">Knowledge and experience working with BizTalk projects in [!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)]</span></span>

## <a name="add-biztalk-project-to-vsts"></a><span data-ttu-id="aabc9-114">Ajouter un projet BizTalk pour VSTS</span><span class="sxs-lookup"><span data-stu-id="aabc9-114">Add BizTalk project to VSTS</span></span>
1. <span data-ttu-id="aabc9-115">Dans **Visual Studio**, se connecter à votre **référentiel Source**, et **Clone** à votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aabc9-115">In **Visual Studio**, connect to your **Source repository**, and **Clone** it to your machine.</span></span>
2. <span data-ttu-id="aabc9-116">Ouvrez ou créez un **projet BizTalk** (.btproj).</span><span class="sxs-lookup"><span data-stu-id="aabc9-116">Open or Create a **BizTalk Project** (.btproj).</span></span>

   > [!NOTE]
   > <span data-ttu-id="aabc9-117">Vous pouvez ajouter plusieurs projets dans la même solution.</span><span class="sxs-lookup"><span data-stu-id="aabc9-117">You can add multiple project into the same solution.</span></span>
   
3. <span data-ttu-id="aabc9-118">Ajouter un nouveau **projet d’Application de BizTalk Server** (.btaproj).</span><span class="sxs-lookup"><span data-stu-id="aabc9-118">Add a new **BizTalk Server Application Project** (.btaproj).</span></span>
4. <span data-ttu-id="aabc9-119">Cliquez sur le projet dans le **l’Explorateur de solutions**, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="aabc9-119">Right-click the project in the **Solution Explorer**, and select **Properties**.</span></span>
5. <span data-ttu-id="aabc9-120">Configurer le **Version** et les propriétés de connexion pour votre **Visual Studio Team Services** compte.</span><span class="sxs-lookup"><span data-stu-id="aabc9-120">Configure the **Version** and the connection properties to your **Visual Studio Team Services** account.</span></span>

    ![Visual Studio Configuration FP1 BizTalk](../core/media/visual-studio-configuration-fp1-biztalk.png)

6. <span data-ttu-id="aabc9-122">Ajoutez tous les assemblys et les artefacts requis par votre application.</span><span class="sxs-lookup"><span data-stu-id="aabc9-122">Add all the assemblies and artifacts needed by your application.</span></span>
7. <span data-ttu-id="aabc9-123">Mise à jour la **binding.xml** fichier avec les informations de liaison correct.</span><span class="sxs-lookup"><span data-stu-id="aabc9-123">Update the **binding.xml** file with the correct binding information.</span></span>
8. <span data-ttu-id="aabc9-124">Mise à jour la **BizTalkServerInventory.json** avec tous les artefacts et le bon ordre pour les artefacts doit être installé sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aabc9-124">Update the **BizTalkServerInventory.json** with all the artifacts, and the correct order for the artifacts to be installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>
9. <span data-ttu-id="aabc9-125">Avec le bouton droit et **générer** votre solution pour vérifier les erreurs.</span><span class="sxs-lookup"><span data-stu-id="aabc9-125">Right-click and **build** your solution to check for any errors.</span></span> 
10. <span data-ttu-id="aabc9-126">Lorsque la build se termine correctement, avec le bouton droit de votre solution, puis sélectionnez **déployer**.</span><span class="sxs-lookup"><span data-stu-id="aabc9-126">When the build completes successfully, right-click your solution, and select **Deploy**.</span></span>
11. <span data-ttu-id="aabc9-127">Votre application doit déployer automatiquement sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aabc9-127">Your application should automatically deploy to your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="aabc9-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aabc9-128">See also</span></span>
[<span data-ttu-id="aabc9-129">Configurer le Pack de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="aabc9-129">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)