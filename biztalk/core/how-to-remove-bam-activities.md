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
ms.openlocfilehash: 67320d4d7d96f037e8d16132e0274b43feee8003
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-remove-bam-activities"></a><span data-ttu-id="fcf60-102">Suppression d'activités BAM</span><span class="sxs-lookup"><span data-stu-id="fcf60-102">How to Remove BAM Activities</span></span>
<span data-ttu-id="fcf60-103">Les administrateurs utilisent la **remove-activity** commande pour supprimer l’activité spécifiée à partir de la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="fcf60-103">Administrators use the **remove-activity** command to remove the specified activity from the BAM Primary Import database.</span></span>  
  
### <a name="to-remove-a-bam-activity"></a><span data-ttu-id="fcf60-104">Pour supprimer une activité BAM</span><span class="sxs-lookup"><span data-stu-id="fcf60-104">To remove a BAM activity</span></span>  
  
1.  <span data-ttu-id="fcf60-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fcf60-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="fcf60-106">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fcf60-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
3.  <span data-ttu-id="fcf60-107">Type **bm remove-activity-nom :\<nom de l’activité\>**.</span><span class="sxs-lookup"><span data-stu-id="fcf60-107">Type **bm remove-activity -Name:\<activity name\>**.</span></span>  
  
4.  <span data-ttu-id="fcf60-108">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="fcf60-108">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf60-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcf60-109">See Also</span></span>  
 <span data-ttu-id="fcf60-110">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="fcf60-110">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="fcf60-111">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="fcf60-111">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="fcf60-112">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="fcf60-112">BAM Management Utility</span></span>](../core/bam-management-utility.md)