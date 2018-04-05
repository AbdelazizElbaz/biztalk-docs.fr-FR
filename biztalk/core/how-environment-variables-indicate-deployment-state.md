---
title: Comment les Variables d’environnement indiquent état du déploiement | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts, variables
ms.assetid: 022b782b-008d-41a7-9880-d1c4e5e4015e
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 041e77eadb7c1b62e3441ee3b3c138203299f3a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-environment-variables-indicate-deployment-state"></a><span data-ttu-id="8731d-102">Indication de l'état du déploiement par les variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="8731d-102">How Environment Variables Indicate Deployment State</span></span>
<span data-ttu-id="8731d-103">Une fois appelé, un script de pré-traitement ou de post-traitement détermine l'état du déploiement dans lequel il est exécuté (installation, importation, suppression, désinstallation, annulation de l'importation ou de l'installation) en vérifiant les variables d'environnement BTAD_ChangeRequestAction, BTAD_InstallMode et BTAD_HostClass.</span><span class="sxs-lookup"><span data-stu-id="8731d-103">Once invoked, a pre- or post-processing script can determine in which deployment state (install, import, delete, uninstall, import rollback, or install rollback) it is running by checking the environment variables BTAD_ChangeRequestAction, BTAD_InstallMode and BTAD_HostClass.</span></span>  
  
 <span data-ttu-id="8731d-104">Le tableau suivant décrit les combinaisons des trois variables qui indiquent des états de déploiement différents.</span><span class="sxs-lookup"><span data-stu-id="8731d-104">The following table describes the combinations of the three variables that indicate the different deployment states.</span></span>  
  
|<span data-ttu-id="8731d-105">État du déploiement</span><span class="sxs-lookup"><span data-stu-id="8731d-105">Deployment State</span></span>|<span data-ttu-id="8731d-106">Valeurs attendues</span><span class="sxs-lookup"><span data-stu-id="8731d-106">Expected Values</span></span>|  
|----------------------|---------------------|  
||<span data-ttu-id="8731d-107">BTAD_ChangeRequestAction</span><span class="sxs-lookup"><span data-stu-id="8731d-107">BTAD_ChangeRequestAction</span></span>|<span data-ttu-id="8731d-108">BTAD_InstallMode</span><span class="sxs-lookup"><span data-stu-id="8731d-108">BTAD_InstallMode</span></span>|<span data-ttu-id="8731d-109">BTAD_HostClass</span><span class="sxs-lookup"><span data-stu-id="8731d-109">BTAD_HostClass</span></span>|  
|<span data-ttu-id="8731d-110">Importation sans indicateur de remplacement</span><span class="sxs-lookup"><span data-stu-id="8731d-110">Import without overwrite flag</span></span>|<span data-ttu-id="8731d-111">Créer</span><span class="sxs-lookup"><span data-stu-id="8731d-111">Create</span></span>|<span data-ttu-id="8731d-112">Importer</span><span class="sxs-lookup"><span data-stu-id="8731d-112">Import</span></span>|<span data-ttu-id="8731d-113">ConfigurationDb</span><span class="sxs-lookup"><span data-stu-id="8731d-113">ConfigurationDb</span></span>|  
|<span data-ttu-id="8731d-114">Importation avec indicateur de remplacement</span><span class="sxs-lookup"><span data-stu-id="8731d-114">Import with overwrite flag</span></span>|<span data-ttu-id="8731d-115">Update</span><span class="sxs-lookup"><span data-stu-id="8731d-115">Update</span></span>|<span data-ttu-id="8731d-116">Importer</span><span class="sxs-lookup"><span data-stu-id="8731d-116">Import</span></span>|<span data-ttu-id="8731d-117">ConfigurationDb</span><span class="sxs-lookup"><span data-stu-id="8731d-117">ConfigurationDb</span></span>|  
|<span data-ttu-id="8731d-118">Install</span><span class="sxs-lookup"><span data-stu-id="8731d-118">Install</span></span>|<span data-ttu-id="8731d-119">Update</span><span class="sxs-lookup"><span data-stu-id="8731d-119">Update</span></span>|<span data-ttu-id="8731d-120">Install</span><span class="sxs-lookup"><span data-stu-id="8731d-120">Install</span></span>|<span data-ttu-id="8731d-121">BizTalkHostInstance</span><span class="sxs-lookup"><span data-stu-id="8731d-121">BizTalkHostInstance</span></span>|  
|<span data-ttu-id="8731d-122">Désinstaller</span><span class="sxs-lookup"><span data-stu-id="8731d-122">Uninstall</span></span>|<span data-ttu-id="8731d-123">DELETE</span><span class="sxs-lookup"><span data-stu-id="8731d-123">Delete</span></span>|<span data-ttu-id="8731d-124">Désinstaller</span><span class="sxs-lookup"><span data-stu-id="8731d-124">Uninstall</span></span>|<span data-ttu-id="8731d-125">BizTalkHostInstance</span><span class="sxs-lookup"><span data-stu-id="8731d-125">BizTalkHostInstance</span></span>|  
|<span data-ttu-id="8731d-126">Annulation d'importation</span><span class="sxs-lookup"><span data-stu-id="8731d-126">Import rollback</span></span>|<span data-ttu-id="8731d-127">DELETE</span><span class="sxs-lookup"><span data-stu-id="8731d-127">Delete</span></span>|<span data-ttu-id="8731d-128">Importer</span><span class="sxs-lookup"><span data-stu-id="8731d-128">Import</span></span>|<span data-ttu-id="8731d-129">ConfigurationDb</span><span class="sxs-lookup"><span data-stu-id="8731d-129">ConfigurationDb</span></span>|  
|<span data-ttu-id="8731d-130">Annulation d'installation</span><span class="sxs-lookup"><span data-stu-id="8731d-130">Install rollback</span></span>|<span data-ttu-id="8731d-131">DELETE</span><span class="sxs-lookup"><span data-stu-id="8731d-131">Delete</span></span>|<span data-ttu-id="8731d-132">Install</span><span class="sxs-lookup"><span data-stu-id="8731d-132">Install</span></span>|<span data-ttu-id="8731d-133">BizTalkHostInstance</span><span class="sxs-lookup"><span data-stu-id="8731d-133">BizTalkHostInstance</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8731d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8731d-134">See Also</span></span>  
 <span data-ttu-id="8731d-135">[À l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement d’Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="8731d-135">[Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md) </span></span>  
 <span data-ttu-id="8731d-136">[BTAD_ChangeRequestAction](../core/btad-changerequestaction.md) </span><span class="sxs-lookup"><span data-stu-id="8731d-136">[BTAD_ChangeRequestAction](../core/btad-changerequestaction.md) </span></span>  
 <span data-ttu-id="8731d-137">[BTAD_InstallMode](../core/btad-installmode.md) </span><span class="sxs-lookup"><span data-stu-id="8731d-137">[BTAD_InstallMode](../core/btad-installmode.md) </span></span>  
 [<span data-ttu-id="8731d-138">BTAD_HostClass</span><span class="sxs-lookup"><span data-stu-id="8731d-138">BTAD_HostClass</span></span>](../core/btad-hostclass.md)