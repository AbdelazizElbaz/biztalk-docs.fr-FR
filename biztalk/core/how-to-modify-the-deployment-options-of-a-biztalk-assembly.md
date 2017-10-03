---
title: "Comment modifier les Options de déploiement d’un Assembly BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying, deploying
- managing [assemblies], modifying
- deploying, assemblies
- managing [assemblies], deploying
- assemblies, deploying
ms.assetid: d25e2f71-08bd-4786-ab6c-35ae4e88b8cc
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 416fc38c8768e7391659d133877b2ae59e704463
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-the-deployment-options-of-a-biztalk-assembly"></a><span data-ttu-id="0322d-102">Modification des options de déploiement d'un assembly BizTalk</span><span class="sxs-lookup"><span data-stu-id="0322d-102">How to Modify the Deployment Options of a BizTalk Assembly</span></span>
<span data-ttu-id="0322d-103">Cette rubrique explique comment modifier les options de déploiement d'un assembly BizTalk à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0322d-103">This topic describes how to use the BizTalk Server Administration console to modify the deployment options of a BizTalk assembly.</span></span>  
  
 <span data-ttu-id="0322d-104">Vous pouvez spécifier les options de déploiement suivantes :</span><span class="sxs-lookup"><span data-stu-id="0322d-104">You can specify the following deployment options:</span></span>  
  
-   <span data-ttu-id="0322d-105">**Ajouter au global assembly cache sur Ajouter une ressource (gacutil).**</span><span class="sxs-lookup"><span data-stu-id="0322d-105">**Add to the global assembly cache on add resource (gacutil).**</span></span> <span data-ttu-id="0322d-106">si vous sélectionnez cette option, l'assembly est ajouté dans le GAC sur l'ordinateur local lors de son ajout dans l'application.</span><span class="sxs-lookup"><span data-stu-id="0322d-106">When you select this option, the assembly is added to the global assembly cache (GAC) on the local computer when the assembly is added to the application.</span></span> <span data-ttu-id="0322d-107">En outre, si vous mettez ensuite à jour l’assembly (faites un clic droit et cliquez sur **Actualiser**), l’assembly est ajouté au GAC.</span><span class="sxs-lookup"><span data-stu-id="0322d-107">In addition, if you later refresh the assembly (right-click it and click **Refresh**), the assembly is added to the GAC.</span></span> <span data-ttu-id="0322d-108">La désactivation de cette option ne supprime pas l'assembly du GAC.</span><span class="sxs-lookup"><span data-stu-id="0322d-108">Clearing the check box for this option does not remove the assembly from the GAC, if it currently exists there.</span></span>  
  
-   <span data-ttu-id="0322d-109">**Ajouter au global assembly cache lors de l’importation du fichier MSI (gacutil).**</span><span class="sxs-lookup"><span data-stu-id="0322d-109">**Add to the global assembly cache on MSI file import (gacutil).**</span></span> <span data-ttu-id="0322d-110">installe l'assembly dans le GAC de l'ordinateur local lors de l'importation du fichier .msi de l'application.</span><span class="sxs-lookup"><span data-stu-id="0322d-110">Install the assembly to the GAC on the local computer when the application .msi file is imported.</span></span>  
  
-   <span data-ttu-id="0322d-111">**Ajoutez dans le global assembly cache lors de l’installation du fichier MSI (gacutil).**</span><span class="sxs-lookup"><span data-stu-id="0322d-111">**Add to the global assembly cache on MSI file install (gacutil).**</span></span> <span data-ttu-id="0322d-112">installe l'assembly dans le GAC de l'ordinateur local lorsque l'application est installée à partir du fichier .msi.</span><span class="sxs-lookup"><span data-stu-id="0322d-112">Install the assembly to the GAC on the local computer when the application is installed from the .msi file.</span></span>  
  
-   <span data-ttu-id="0322d-113">**Emplacement de destination :** chemin d’accès auquel le fichier d’assembly sera copié lorsque l’application est installée.</span><span class="sxs-lookup"><span data-stu-id="0322d-113">**Destination location:** Path to which the assembly file will be copied when the application is installed.</span></span> <span data-ttu-id="0322d-114">Si aucun chemin d'accès n'est fourni, le fichier de l'assembly n'est pas copié dans le système de fichiers local lors de l'installation.</span><span class="sxs-lookup"><span data-stu-id="0322d-114">If a path is not provided, the assembly file is not copied to the local file system on installation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0322d-115">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0322d-115">Prerequisites</span></span>  
 <span data-ttu-id="0322d-116">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0322d-116">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="0322d-117">Vous devez en outre être membre du groupe des administrateurs locaux pour sélectionner une option qui ajoute immédiatement l'assembly au GAC.</span><span class="sxs-lookup"><span data-stu-id="0322d-117">In addition, if you select an option that immediately adds the assembly to the GAC, your account must also be a member of the local Administrator's group.</span></span> <span data-ttu-id="0322d-118">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="0322d-118">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-modify-the-deployment-options-of-a-biztalk-assembly"></a><span data-ttu-id="0322d-119">Pour modifier les options de déploiement d'un assembly BizTalk</span><span class="sxs-lookup"><span data-stu-id="0322d-119">To modify the deployment options of a BizTalk assembly</span></span>  
  
1.  <span data-ttu-id="0322d-120">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="0322d-120">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0322d-121">Dans l'arborescence de la console, développez successivement Administration de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], le groupe BizTalk contenant l'assembly BizTalk pour lequel modifier les options de déploiement, puis l'application contenant l'assembly BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0322d-121">In the console tree, expand [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Administration, expand the BizTalk group containing the BizTalk assembly for which to modify deployment options, and then expand the application containing the BizTalk assembly.</span></span>  
  
3.  <span data-ttu-id="0322d-122">Cliquez sur le **ressources** dossier, cliquez sur l’assembly BizTalk, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="0322d-122">Click the **Resources** folder, right-click the BizTalk assembly, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="0322d-123">Dans **Options**, activez les cases à cocher des options de déploiement que vous souhaitez.</span><span class="sxs-lookup"><span data-stu-id="0322d-123">In **Options**, select the check boxes of the deployment options that you want.</span></span>  
  
5.  <span data-ttu-id="0322d-124">Si nécessaire, dans **l’emplacement de Destination** modifier le chemin d’accès dans lequel l’assembly sera copié lorsque l’application est installée, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0322d-124">If necessary, in **Destination location** edit the path where the assembly will be copied when the application is installed, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0322d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0322d-125">See Also</span></span>  
 [<span data-ttu-id="0322d-126">Gestion des assemblys BizTalk</span><span class="sxs-lookup"><span data-stu-id="0322d-126">Managing BizTalk Assemblies</span></span>](../core/managing-biztalk-assemblies.md)