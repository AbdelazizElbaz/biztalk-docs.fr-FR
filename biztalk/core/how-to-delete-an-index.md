---
title: Comment supprimer un Index | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- indexes [BAM], deleting
- Get-Index command [BAM]
- aggregations [BAM], indexes
ms.assetid: 5f9c7989-3357-451f-8565-1d4b01c1d16a
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9934c333699b853a3e10a0e5ecf212acf17fa6c6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-delete-an-index"></a><span data-ttu-id="58237-102">Comment supprimer un Index</span><span class="sxs-lookup"><span data-stu-id="58237-102">How to Delete an Index</span></span>
<span data-ttu-id="58237-103">Les administrateurs utilisent la **delete-index** commande pour supprimer un index sur l’activité spécifiée aux points de contrôle spécifiés.</span><span class="sxs-lookup"><span data-stu-id="58237-103">Administrators use the **delete-index** command to delete an index on the specified activity at the specified checkpoints.</span></span>  
  
### <a name="to-delete-an-index-on-an-activity"></a><span data-ttu-id="58237-104">Pour supprimer un index sur une activité</span><span class="sxs-lookup"><span data-stu-id="58237-104">To delete an index on an activity</span></span>  
  
1.  <span data-ttu-id="58237-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="58237-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="58237-106">Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="58237-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="58237-107">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="58237-107">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="58237-108">Type **bm delete-index - IndexName :\<nom de l’index\> -activité :\<nom de l’activité\>**.</span><span class="sxs-lookup"><span data-stu-id="58237-108">Type **bm delete-index -IndexName:\<index name\> -Activity:\<activity name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="58237-109">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="58237-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="58237-110">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="58237-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58237-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58237-111">See Also</span></span>  
 <span data-ttu-id="58237-112">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="58237-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="58237-113">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="58237-113">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 <span data-ttu-id="58237-114">[Comment supprimer un Index](../core/how-to-delete-an-index.md) </span><span class="sxs-lookup"><span data-stu-id="58237-114">[How to Delete an Index](../core/how-to-delete-an-index.md) </span></span>  
 [<span data-ttu-id="58237-115">Comment obtenir la liste des index sur une agrégation</span><span class="sxs-lookup"><span data-stu-id="58237-115">How to Get a List of Indexes on an Aggregation</span></span>](../core/how-to-get-a-list-of-indexes-on-an-aggregation.md)