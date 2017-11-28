---
title: "Comment supprimer un mappage à partir d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, maps
- deleting, maps
- managing [maps], deleting
- managing [maps], applications
ms.assetid: 27d9bb08-36f0-46ff-ae9a-2247be6e3f96
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8b264809306e2cda40cc44be1287b6c2426fb43
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-map-from-an-application"></a><span data-ttu-id="3d6a7-102">Suppression d'un mappage d'une application</span><span class="sxs-lookup"><span data-stu-id="3d6a7-102">How to Remove a Map from an Application</span></span>
<span data-ttu-id="3d6a7-103">Cette rubrique décrit comment supprimer un mappage d'une application BizTalk à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3d6a7-103">This topic describes how to use the BizTalk Server Administration console to remove a map from a BizTalk application.</span></span> <span data-ttu-id="3d6a7-104">Il peut être utile de supprimer un mappage après avoir déployé une nouvelle version du mappage.</span><span class="sxs-lookup"><span data-stu-id="3d6a7-104">You might want to remove a map after deploying a new version of the map.</span></span> <span data-ttu-id="3d6a7-105">Pour plus d’informations et des considérations importantes pour la mise à jour des artefacts de l’application, consultez [mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md).</span><span class="sxs-lookup"><span data-stu-id="3d6a7-105">For more information and important considerations for updating application artifacts, see [Updating BizTalk Applications](../core/updating-biztalk-applications.md).</span></span>  
  
 <span data-ttu-id="3d6a7-106">Lorsque vous supprimez un mappage, voici ce qui se produit :</span><span class="sxs-lookup"><span data-stu-id="3d6a7-106">When you remove a map, the following occurs:</span></span>  
  
-   <span data-ttu-id="3d6a7-107">le mappage est supprimé de la base de données de gestion BizTalk ;</span><span class="sxs-lookup"><span data-stu-id="3d6a7-107">The map is deleted from the BizTalk Management database.</span></span>  
  
-   <span data-ttu-id="3d6a7-108">l'assembly BizTalk qui contient le mappage est supprimé de la base de données de gestion BizTalk, mais pas du système de fichiers local ou du Global Assembly Cache (GAC), s'il existe dans ces emplacements ;</span><span class="sxs-lookup"><span data-stu-id="3d6a7-108">The BizTalk assembly that contains the map is deleted from the BizTalk Management database, but is not removed from the local file system or the global assembly cache (GAC), if it exists in these locations.</span></span>  
  
-   <span data-ttu-id="3d6a7-109">par conséquent, tous les artefacts contenus dans l'assembly sont également supprimés de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3d6a7-109">As a consequence of the BizTalk assembly being deleted, all artifacts contained in the assembly are removed deleted the BizTalk Management database as well.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3d6a7-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3d6a7-110">Prerequisites</span></span>  
 <span data-ttu-id="3d6a7-111">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3d6a7-111">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="3d6a7-112">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="3d6a7-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-remove-a-map"></a><span data-ttu-id="3d6a7-113">Pour supprimer un mappage</span><span class="sxs-lookup"><span data-stu-id="3d6a7-113">To remove a map</span></span>  
  
1.  <span data-ttu-id="3d6a7-114">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="3d6a7-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="3d6a7-115">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant le mappage à supprimer, puis développez l’application contenant le mappage.</span><span class="sxs-lookup"><span data-stu-id="3d6a7-115">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the map to remove, and then expand the application containing the map.</span></span>  
  
3.  <span data-ttu-id="3d6a7-116">Cliquez sur le **cartes** dossier, avec le bouton droit de la carte, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="3d6a7-116">Click the **Maps** folder, right-click the map, and then click **Remove**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d6a7-117">Pour supprimer plusieurs mappages, maintenez la touche MAJ enfoncée, cliquez sur chaque carte à supprimer, cliquez sur un des mappages, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="3d6a7-117">To remove multiple maps, hold down the shift key, click each map to remove, right-click one of the maps, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d6a7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d6a7-118">See Also</span></span>  
 <span data-ttu-id="3d6a7-119">[La gestion des mappages](../core/managing-maps.md) </span><span class="sxs-lookup"><span data-stu-id="3d6a7-119">[Managing Maps](../core/managing-maps.md) </span></span>  
 <span data-ttu-id="3d6a7-120">[Comment supprimer un Assembly BizTalk à partir d’une Application](../core/how-to-remove-a-biztalk-assembly-from-an-application.md) </span><span class="sxs-lookup"><span data-stu-id="3d6a7-120">[How to Remove a BizTalk Assembly from an Application](../core/how-to-remove-a-biztalk-assembly-from-an-application.md) </span></span>  
 [<span data-ttu-id="3d6a7-121">Annulation du déploiement des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="3d6a7-121">Undeploying BizTalk Applications</span></span>](../core/undeploying-biztalk-applications.md)