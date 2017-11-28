---
title: "Concepteur de projet : Onglet déploiement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties, Configuration database [BizTalk Server]
- Redeploy property
- configuration properties [deployment], Server property
- Server property
- configuration properties [deployment], Install to Global Assembly Cache (GAC) property
- properties, Management database
- Install to Global Assembly Cache (GAC) property
- Configuration database [BizTalk Server], properties
- Management database, properties
- Administration Group property
- configuration properties [deployment], Redeploy property
- configuration properties [deployment], Management database property
- configuration properties [deployment], Administration Group property
ms.assetid: 5b64f99c-4ec6-4ed3-8590-46420e2f75b8
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 972f3956a19d66d47238ee8170584b4faf6ba886
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="project-designer-deployment-tab"></a><span data-ttu-id="3c632-102">Concepteur de projet : onglet Déploiement</span><span class="sxs-lookup"><span data-stu-id="3c632-102">Project Designer: Deployment Tab</span></span>
<span data-ttu-id="3c632-103">Le **déploiement** onglet de propriétés du Concepteur de projets permet de configurer les attributs de déploiement pour le projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3c632-103">The **Deployment** property tab of the Project Designer allows you to configure the deployment attributes for the BizTalk project.</span></span> <span data-ttu-id="3c632-104">Vous devez configurer les deux le **Server** et **base de données de Configuration** (également appelée la base de données BizTalk Management) propriétés en tant qu’ensemble pour le déploiement réussisse.</span><span class="sxs-lookup"><span data-stu-id="3c632-104">You must configure both the **Server** and the **Configuration Database** (also known as the BizTalk Management database) properties as a set for deployment to be successful.</span></span>  
  
## <a name="application-name"></a><span data-ttu-id="3c632-105">Application Name</span><span class="sxs-lookup"><span data-stu-id="3c632-105">Application Name</span></span>  
 <span data-ttu-id="3c632-106">Indiquer l'application BizTalk dans laquelle déployer l'assembly.</span><span class="sxs-lookup"><span data-stu-id="3c632-106">Specify the BizTalk application in which to deploy the assembly.</span></span> <span data-ttu-id="3c632-107">Si ce champ est vide, le projet sera déployé dans l'application par défaut.</span><span class="sxs-lookup"><span data-stu-id="3c632-107">If this is empty, the project will be deployed into the default application.</span></span>  
  
## <a name="configuration-database"></a><span data-ttu-id="3c632-108">Base de données de configuration</span><span class="sxs-lookup"><span data-stu-id="3c632-108">Configuration Database</span></span>  
 <span data-ttu-id="3c632-109">Ce champ permet de spécifier le nom de la base de données de configuration BizTalk pour l'assembly déployé.</span><span class="sxs-lookup"><span data-stu-id="3c632-109">You use this field to specify the name of the BizTalk Configuration database for the deployed assembly.</span></span> <span data-ttu-id="3c632-110">Cela est nécessaire si vous avez configuré le projet BizTalk en tant que projet de déploiement.</span><span class="sxs-lookup"><span data-stu-id="3c632-110">This applies if you have configured the BizTalk project as a deployment project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c632-111">La base de données de configuration BizTalk est également appelée « base de données de gestion BizTalk ».</span><span class="sxs-lookup"><span data-stu-id="3c632-111">The BizTalk Configuration database is also referred to as the BizTalk Management database.</span></span>  
  
 <span data-ttu-id="3c632-112">Le nom par défaut de la base de données de configuration est BizTalkMgmtDb.</span><span class="sxs-lookup"><span data-stu-id="3c632-112">The default Configuration database name is BizTalkMgmtDb.</span></span>  
  
## <a name="server"></a><span data-ttu-id="3c632-113">Server</span><span class="sxs-lookup"><span data-stu-id="3c632-113">Server</span></span>  
 <span data-ttu-id="3c632-114">Il s'agit du nom du serveur sur lequel se trouve l'espace de stockage Configuration (également appelé base de données de gestion ou de configuration BizTalk).</span><span class="sxs-lookup"><span data-stu-id="3c632-114">This is the name of the server where the Configuration repository (also known as the BizTalk Management or Configuration database) is located.</span></span> <span data-ttu-id="3c632-115">Vous déployez le projet BizTalk sur ce serveur si vous configurez le projet BizTalk en tant que « Déploiement ».</span><span class="sxs-lookup"><span data-stu-id="3c632-115">You deploy the BizTalk project to this server if you configure the BizTalk project as "Deployment."</span></span>  
  
## <a name="redeploy"></a><span data-ttu-id="3c632-116">Redéployer</span><span class="sxs-lookup"><span data-stu-id="3c632-116">Redeploy</span></span>  
 <span data-ttu-id="3c632-117">Vous utilisez la **redéployer** propriété pour déterminer s’il faut supprimer la configuration existante et recréez la configuration de chaque fois que vous déployez l’assembly.</span><span class="sxs-lookup"><span data-stu-id="3c632-117">You use the **Redeploy** property to determine whether to delete the existing configuration and re-create the configuration each time you deploy the assembly.</span></span> <span data-ttu-id="3c632-118">La valeur par défaut est `True`.</span><span class="sxs-lookup"><span data-stu-id="3c632-118">The default value is `True`.</span></span>  
  
## <a name="install-to-global-assembly-cache"></a><span data-ttu-id="3c632-119">Installer dans le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="3c632-119">Install to Global Assembly Cache</span></span>  
 <span data-ttu-id="3c632-120">Vous utilisez la **installer dans le Global Assembly Cache** propriété pour indiquer si [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] doit installer l’assembly BizTalk dans le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="3c632-120">You use the **Install to Global Assembly Cache** property to indicate if [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] needs to install the BizTalk assembly to the global assembly cache (GAC).</span></span>  
  
## <a name="restart-host-instances"></a><span data-ttu-id="3c632-121">Redémarrer les instances d'hôte</span><span class="sxs-lookup"><span data-stu-id="3c632-121">Restart Host Instances</span></span>  
 <span data-ttu-id="3c632-122">Si vous définissez **redémarrer les Instances d’hôte** à **True**, les instances d’hôte sur l’ordinateur local seront redémarrés une fois le projet est déployé par [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c632-122">If you set **Restart Host Instances** to **True**, the host instances on the local computer will be restarted when the project is deployed by [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="3c632-123">Ceci est utile lors du cycle de développement lorsque vous effectuez des modifications et de fréquents redéploiements ; vous n'aurez pas à redémarrer manuellement les instances d'hôte associées.</span><span class="sxs-lookup"><span data-stu-id="3c632-123">This is useful during the development cycle when you are making changes and frequently redeploying; you will not have to manually restart related host instances.</span></span>  
  
 <span data-ttu-id="3c632-124">Si vous ne redémarrez pas les instances d'hôte associées, vos dernières modifications risquent de ne pas être reflétées dans votre application BizTalk car l'ancienne version risque d'être toujours en mémoire cache.</span><span class="sxs-lookup"><span data-stu-id="3c632-124">If you do not restart related host instances, your latest changes may not be reflected in your BizTalk application because the old version may still be cached.</span></span> <span data-ttu-id="3c632-125">Le redémarrage des instances d'hôte purge les assemblys mis en cache.</span><span class="sxs-lookup"><span data-stu-id="3c632-125">Restarting the host instance purges cached assemblies.</span></span>  
  
## <a name="enable-unit-testing"></a><span data-ttu-id="3c632-126">Activer les tests unitaires</span><span class="sxs-lookup"><span data-stu-id="3c632-126">Enable Unit Testing</span></span>  
 <span data-ttu-id="3c632-127">Spécifie s'il faut activer les tests unitaires pour le projet.</span><span class="sxs-lookup"><span data-stu-id="3c632-127">Specified whether to enable unit testing for the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c632-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c632-128">See Also</span></span>  
 <span data-ttu-id="3c632-129">[Comment déployer un Assembly BizTalk à partir de Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="3c632-129">[How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md) </span></span>  
 [<span data-ttu-id="3c632-130">Fenêtre des propriétés de projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="3c632-130">BizTalk Project Properties Window</span></span>](../core/biztalk-project-properties-window.md)