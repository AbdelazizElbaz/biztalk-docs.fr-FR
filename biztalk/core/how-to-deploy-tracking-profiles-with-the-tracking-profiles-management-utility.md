---
title: "Comment déployer des modèles de suivi avec le suivi des profils d’utilitaire de gestion | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking profiles, deploying
- deploying, tracking profiles
- bttdeploy.exe [BAM]
- managing [BAM], deploying tracking profiles
ms.assetid: b3023379-cae1-45fc-a773-2660d3e4abf1
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2dde3f351c583be9037127c060d02c98d12b2fcb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility"></a><span data-ttu-id="6e2ea-102">Déploiement de modèles de suivi à l'aide de l'utilitaire de gestion des modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="6e2ea-102">How to Deploy Tracking Profiles with the Tracking Profiles Management Utility</span></span>
<span data-ttu-id="6e2ea-103">Un gestionnaire des activités demande à un développeur de solutions de créer un modèle de suivi ou d'en modifier un pour mieux gérer et contrôler un processus d'entreprise spécifique à votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-103">A business manager asks a solutions developer to create a new tracking profile or modify an existing one to better manage and monitor a specific business process for your organization.</span></span>  
  
 <span data-ttu-id="6e2ea-104">Le développeur de solutions utilise l'Éditeur de modèle de suivi pour définir les données que l'analyste d'entreprise requiert.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-104">The solutions developer uses the Tracking Profile Editor (TPE) to define the data that the business analyst requires.</span></span>  
  
 <span data-ttu-id="6e2ea-105">Une fois que le développeur de solutions a créé ou modifié le modèle de suivi, un administrateur utilise l'utilitaire de ligne de commande bttdeploy.exe pour le déployer de manière à ce que les modifications prennent effet et que les données soient collectées.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-105">After a solutions developer creates or modifies the tracking profile, an administrator uses the bttdeploy.exe command line utility to deploy it so that the changes take affect and the data is collected.</span></span> <span data-ttu-id="6e2ea-106">Le développeur de solutions peut déployer des modèles de suivi avec l'Éditeur de modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-106">The solutions developer can deploy tracking profiles with the TPE.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6e2ea-107">Avant de déployer le modèle de suivi, vous devez déployer les assemblys qui lui sont associés.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-107">You must deploy the assemblies associated with the tracking profile before you deploy the tracking profile.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6e2ea-108">Vous devez disposer des privilèges d'administrateur BizTalk® pour utiliser cet outil.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-108">You must have BizTalk® Administrator privileges to use this tool.</span></span>  
  
### <a name="to-deploy-the-tracking-profile-from-the-command-line-utility"></a><span data-ttu-id="6e2ea-109">Pour déployer le modèle de suivi à partir de l'utilitaire de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="6e2ea-109">To deploy the tracking profile from the command-line utility</span></span>  
  
1.  <span data-ttu-id="6e2ea-110">À partir d’une invite de commandes, accédez au répertoire \<chemin d’installation\>\Program Files\Microsoft BizTalk Server \<version\>\Tracking\\.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-110">From a command prompt, move to the directory \<installation path\>\Program Files\Microsoft BizTalk Server \<version\>\Tracking\\.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e2ea-111">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
2.  <span data-ttu-id="6e2ea-112">Type **bttdeploy.exe \<nom du profil\>.btt**.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-112">Type **bttdeploy.exe \<profile name\>.btt**.</span></span>  
  
3.  <span data-ttu-id="6e2ea-113">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-113">Press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e2ea-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e2ea-114">See Also</span></span>  
 <span data-ttu-id="6e2ea-115">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="6e2ea-115">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="6e2ea-116">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="6e2ea-116">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="6e2ea-117">BAM (Business Activity Monitoring)</span><span class="sxs-lookup"><span data-stu-id="6e2ea-117">Business Activity Monitoring (BAM)</span></span>](../core/business-activity-monitoring-bam.md)