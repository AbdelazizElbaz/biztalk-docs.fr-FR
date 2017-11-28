---
title: "Comment supprimer des activités BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM definitions], deleting activities
- activities [BAM], deleting
- deleting, activities [BAM]
- Remove-Activity command [BAM]
ms.assetid: 6c4643dc-84df-487d-aad0-590d1a6a5107
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09e12e893df596a92377357b7e28b6e68f04b810
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-bam-activities"></a><span data-ttu-id="eba83-102">Suppression d'activités BAM</span><span class="sxs-lookup"><span data-stu-id="eba83-102">How to Remove BAM Activities</span></span>
<span data-ttu-id="eba83-103">Les administrateurs utilisent la **remove-activity** commande pour supprimer l’activité spécifiée à partir de la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="eba83-103">Administrators use the **remove-activity** command to remove the specified activity from the BAM Primary Import database.</span></span>  
  
### <a name="to-remove-a-bam-activity"></a><span data-ttu-id="eba83-104">Pour supprimer une activité BAM</span><span class="sxs-lookup"><span data-stu-id="eba83-104">To remove a BAM activity</span></span>  
  
1.  <span data-ttu-id="eba83-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eba83-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="eba83-106">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eba83-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
3.  <span data-ttu-id="eba83-107">Type **bm remove-activity-nom :\<nom de l’activité >**.</span><span class="sxs-lookup"><span data-stu-id="eba83-107">Type **bm remove-activity -Name:\<activity name>**.</span></span>  
  
4.  <span data-ttu-id="eba83-108">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="eba83-108">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba83-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eba83-109">See Also</span></span>  
 <span data-ttu-id="eba83-110">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="eba83-110">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="eba83-111">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="eba83-111">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="eba83-112">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="eba83-112">BAM Management Utility</span></span>](../core/bam-management-utility.md)