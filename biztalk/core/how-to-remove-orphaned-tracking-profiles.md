---
title: Comment supprimer des profils de suivi orphelins | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, tracking profiles
- tracking profiles, orphans
- tracking profiles, activities
- tracking profiles, deleting
- activities, tracking profiles
ms.assetid: e8923dab-5d02-41a3-840b-104b20624e6c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33ddea8751a017db21306c06cdcca5929de641ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-orphaned-tracking-profiles"></a><span data-ttu-id="85943-102">Suppression de modèles de suivi orphelins</span><span class="sxs-lookup"><span data-stu-id="85943-102">How to Remove Orphaned Tracking Profiles</span></span>
<span data-ttu-id="85943-103">Les modèles de suivi sont associés à une activité.</span><span class="sxs-lookup"><span data-stu-id="85943-103">Tracking profiles are associated with an activity.</span></span> <span data-ttu-id="85943-104">Lorsque le déploiement d'une activité est annulé, les modèles de suivi associés peuvent devenir orphelins, c'est-à-dire qu'ils ne sont plus associés à une activité.</span><span class="sxs-lookup"><span data-stu-id="85943-104">If an activity is undeployed, the associated tracking profiles can become orphaned, which means they are no longer associated with an activity.</span></span> <span data-ttu-id="85943-105">Vous pouvez utiliser la procédure suivante pour supprimer les modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="85943-105">You can use the following procedure to remove the tracking profile.</span></span>  
  
### <a name="to-remove-an-orphaned-tracking-profile"></a><span data-ttu-id="85943-106">Pour supprimer un modèle de suivi orphelin</span><span class="sxs-lookup"><span data-stu-id="85943-106">To remove an orphaned tracking profile</span></span>  
  
1.  <span data-ttu-id="85943-107">Redéployez la définition BAM.</span><span class="sxs-lookup"><span data-stu-id="85943-107">Redeploy the BAM definition.</span></span> <span data-ttu-id="85943-108">Pour plus d’informations sur le déploiement de définitions BAM, consultez [comment déployer des définitions BAM](../core/how-to-deploy-bam-definitions.md).</span><span class="sxs-lookup"><span data-stu-id="85943-108">For information about deploying BAM definitions, see [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md).</span></span>  
  
2.  <span data-ttu-id="85943-109">Utilisez l'Éditeur de modèle de suivi pour supprimer le modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="85943-109">Use the Tracking Profile Editor (TPE) to remove the tracking profile.</span></span> <span data-ttu-id="85943-110">Pour plus d’informations sur la suppression des profils de suivi, consultez [comment appliquer et supprimer un profil de suivi](../core/how-to-apply-and-remove-a-tracking-profile.md).</span><span class="sxs-lookup"><span data-stu-id="85943-110">For information about removing tracking profiles, see [How to Apply and Remove a Tracking Profile](../core/how-to-apply-and-remove-a-tracking-profile.md).</span></span>  
  
3.  <span data-ttu-id="85943-111">Annulez le déploiement de la définition BAM.</span><span class="sxs-lookup"><span data-stu-id="85943-111">Undeploy the BAM definition.</span></span> <span data-ttu-id="85943-112">Pour plus d’informations sur la suppression de définitions BAM, consultez [comment supprimer des définitions BAM](../core/how-to-remove-bam-definitions.md).</span><span class="sxs-lookup"><span data-stu-id="85943-112">For information about removing BAM definitions, see [How to Remove BAM Definitions](../core/how-to-remove-bam-definitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85943-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85943-113">See Also</span></span>  
 <span data-ttu-id="85943-114">[Éditeur de modèle de suivi](../core/tracking-profile-editor.md) </span><span class="sxs-lookup"><span data-stu-id="85943-114">[Tracking Profile Editor](../core/tracking-profile-editor.md) </span></span>  
 [<span data-ttu-id="85943-115">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="85943-115">BAM Management Utility</span></span>](../core/bam-management-utility.md)