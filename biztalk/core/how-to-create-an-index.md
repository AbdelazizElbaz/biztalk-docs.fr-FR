---
title: "Comment créer un Index | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Create-Index command [BAM]
- indexes [BAM], creating
- indexes [BAM], aggregations
- creating, indexes [BAM]
- aggregations [BAM], indexes
ms.assetid: 456d94e6-2e84-4d12-ad38-49f9eeb103f3
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61c0393beae4883359d71915543b629e41c5f6ec
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-an-index"></a><span data-ttu-id="2532e-102">Création d'un index</span><span class="sxs-lookup"><span data-stu-id="2532e-102">How to Create an Index</span></span>
<span data-ttu-id="2532e-103">Les administrateurs utilisent la **index créer** commande pour créer un index sur l’activité spécifiée aux points de contrôle spécifiés.</span><span class="sxs-lookup"><span data-stu-id="2532e-103">Administrators use the **create-index** command to create an index on the specified activity at the specified checkpoints.</span></span>  
  
### <a name="to-create-an-index-on-an-activity"></a><span data-ttu-id="2532e-104">Pour créer un index sur une activité</span><span class="sxs-lookup"><span data-stu-id="2532e-104">To create an index on an activity</span></span>  
  
1.  <span data-ttu-id="2532e-105">À partir d’une invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]de suivi.</span><span class="sxs-lookup"><span data-stu-id="2532e-105">From a command prompt, browse to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
2.  <span data-ttu-id="2532e-106">Type **bm create-index - IndexName :\<nom de l’index\> -activité :\<nom de l’activité\> -point de contrôle :\<point de contrôle 1\>**.</span><span class="sxs-lookup"><span data-stu-id="2532e-106">Type **bm create-index -IndexName:\<index name\> -Activity:\<activity name\> -Checkpoint:\<checkpoint1\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2532e-107">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="2532e-107">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
3.  <span data-ttu-id="2532e-108">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="2532e-108">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2532e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2532e-109">See Also</span></span>  
 <span data-ttu-id="2532e-110">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="2532e-110">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="2532e-111">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="2532e-111">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 <span data-ttu-id="2532e-112">[Comment supprimer un Index](../core/how-to-delete-an-index.md) </span><span class="sxs-lookup"><span data-stu-id="2532e-112">[How to Delete an Index](../core/how-to-delete-an-index.md) </span></span>  
 [<span data-ttu-id="2532e-113">Comment obtenir la liste des index sur une agrégation</span><span class="sxs-lookup"><span data-stu-id="2532e-113">How to Get a List of Indexes on an Aggregation</span></span>](../core/how-to-get-a-list-of-indexes-on-an-aggregation.md)