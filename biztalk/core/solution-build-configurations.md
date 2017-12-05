---
title: Configurations de Build de solution | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Configuration Manager
- building, solutions
- building, Configuration Manager
- solutions, deploying
- deploying, building
- solutions, developing
- solutions, build configuration
ms.assetid: 6f2cce47-388d-4c93-9146-768f53b8207e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c48791d26842b7224bb950334d6b184452a54d6
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="solution-build-configurations"></a><span data-ttu-id="eb34b-102">Configurations de version de solution</span><span class="sxs-lookup"><span data-stu-id="eb34b-102">Solution Build Configurations</span></span>
<span data-ttu-id="eb34b-103">Comme c'est le cas avec d'autres projets que vous créez dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], vous pouvez utiliser le Gestionnaire de configuration pour spécifier des configurations de version de solution.</span><span class="sxs-lookup"><span data-stu-id="eb34b-103">As with other projects that you build in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], you can use Configuration Manager to specify solution build configurations.</span></span> <span data-ttu-id="eb34b-104">Celles-ci vous permettent de déterminer les projets à inclure dans les différentes versions d'une solution et si elles seront déployées ou non.</span><span class="sxs-lookup"><span data-stu-id="eb34b-104">Solution build configurations enable you to determine which projects to include in builds of a solution and if they will be deployed.</span></span> <span data-ttu-id="eb34b-105">BizTalk Server prend en charge les deux **déboguer** et **version** configurations de build.</span><span class="sxs-lookup"><span data-stu-id="eb34b-105">BizTalk Server supports both **Debug** and **Release** build configurations.</span></span>  
  
 <span data-ttu-id="eb34b-106">Une solution de générer la configuration avec une coche dans le **générer** colonne vous permet de créer une solution et générer un assembly lorsque vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="eb34b-106">A solution build configuration with a check mark in the **Build** column enables you to build a solution and to generate an assembly when you are finished.</span></span> <span data-ttu-id="eb34b-107">Si la case à cocher correspondante est également présente dans le **déployer** colonne, puis l’application sera déployée en fonction des paramètres de déploiement dans le Concepteur de projet.</span><span class="sxs-lookup"><span data-stu-id="eb34b-107">If a check mark is also present in the **Deploy** column, then the application will be deployed based on deployment settings in the Project Designer.</span></span>  
  
 <span data-ttu-id="eb34b-108">Une référence complète à Configuration Manager et la configuration des options fournies par la boîte de dialogue zone, consultez le lien de référence suivant : [http://go.microsoft.com/fwlink/?LinkId=125365](http://go.microsoft.com/fwlink/?LinkId=125365).</span><span class="sxs-lookup"><span data-stu-id="eb34b-108">A complete reference to Configuration Manager and the configuration options provided by the dialog box can be found at the following reference link: [http://go.microsoft.com/fwlink/?LinkId=125365](http://go.microsoft.com/fwlink/?LinkId=125365).</span></span>  
  
### <a name="to-configure-build-properties-in-configuration-manager"></a><span data-ttu-id="eb34b-109">Pour configurer les propriétés de version dans Gestionnaire de configuration</span><span class="sxs-lookup"><span data-stu-id="eb34b-109">To configure build properties in Configuration Manager</span></span>  
  
1.  <span data-ttu-id="eb34b-110">Dans le menu **Générer** , cliquez sur **Gestionnaire de configurations**.</span><span class="sxs-lookup"><span data-stu-id="eb34b-110">On the **Build** menu, click **Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="eb34b-111">Dans le **Configuration Manager** boîte de dialogue, sélectionnez une des options suivantes pour configurer les propriétés de génération.</span><span class="sxs-lookup"><span data-stu-id="eb34b-111">In the **Configuration Manager** dialog box, select one of following to configure the build properties.</span></span>  
  
    |<span data-ttu-id="eb34b-112">Utiliser</span><span class="sxs-lookup"><span data-stu-id="eb34b-112">Use this</span></span>|<span data-ttu-id="eb34b-113">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="eb34b-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="eb34b-114">**Configuration**</span><span class="sxs-lookup"><span data-stu-id="eb34b-114">**Configuration**</span></span>|<span data-ttu-id="eb34b-115">Choisissez **version** ou **déboguer** configurations pour le projet.</span><span class="sxs-lookup"><span data-stu-id="eb34b-115">Choose from **Release** or **Debug** configurations for the project.</span></span> <span data-ttu-id="eb34b-116">Vous pouvez également créer une configuration ou en modifier une.</span><span class="sxs-lookup"><span data-stu-id="eb34b-116">Alternatively, create a new configuration or edit an existing one.</span></span>|  
    |<span data-ttu-id="eb34b-117">**Plateforme**</span><span class="sxs-lookup"><span data-stu-id="eb34b-117">**Platform**</span></span>|<span data-ttu-id="eb34b-118">Choisissez une plateforme pour le projet représentant l'architecture d'UC de l'assembly compilé.</span><span class="sxs-lookup"><span data-stu-id="eb34b-118">Choose a platform for the project representing the CPU architecture of the compiled assembly.</span></span> <span data-ttu-id="eb34b-119">Vous pouvez également créer une plateforme ou en modifier une.</span><span class="sxs-lookup"><span data-stu-id="eb34b-119">Alternatively, create a new platform or edit an existing one.</span></span>|  
    |<span data-ttu-id="eb34b-120">**Build**</span><span class="sxs-lookup"><span data-stu-id="eb34b-120">**Build**</span></span>|<span data-ttu-id="eb34b-121">Activez la case à cocher dans cette colonne pour qu'un projet soit généré ou regénéré en réponse à une commande de création pour la solution.</span><span class="sxs-lookup"><span data-stu-id="eb34b-121">Check the box in this column for a project to have the project built or rebuilt in response to a build command for the solution.</span></span>|  
    |<span data-ttu-id="eb34b-122">**Déployer**</span><span class="sxs-lookup"><span data-stu-id="eb34b-122">**Deploy**</span></span>|<span data-ttu-id="eb34b-123">Activez la case à cocher dans cette colonne pour qu'un projet soit déployé sur la base de paramètres de déploiement lorsqu'une commande de création est émise pour la solution ou le projet.</span><span class="sxs-lookup"><span data-stu-id="eb34b-123">Check the box in this column to have the project deployed based on deployment settings when a build command is issued for the solution or project.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb34b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb34b-124">See Also</span></span>  
 <span data-ttu-id="eb34b-125">[Comment déployer un Assembly BizTalk à partir de Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="eb34b-125">[How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md) </span></span>  
 [<span data-ttu-id="eb34b-126">Comment créer des projets BizTalk</span><span class="sxs-lookup"><span data-stu-id="eb34b-126">How to Create BizTalk Projects</span></span>](../core/how-to-create-biztalk-projects.md)