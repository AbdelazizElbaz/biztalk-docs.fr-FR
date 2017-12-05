---
title: "Comment obtenir la durée d’une fenêtre d’activité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], time intervals
- managing [BAM], time intervals
- Get-ActivityWindow command [BAM]
ms.assetid: d70f6767-f6f7-4ecf-ad9d-4a9d8c76edea
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37c5bb2c60133d19887e157f8e06633527e0fa11
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-get-the-duration-on-an-activity-window"></a><span data-ttu-id="123c4-102">Obtention de la durée dans une fenêtre d'activité</span><span class="sxs-lookup"><span data-stu-id="123c4-102">How to Get the Duration on an Activity Window</span></span>
<span data-ttu-id="123c4-103">Les administrateurs utilisent la **get-activitywindow** commande pour obtenir la durée de l’activité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="123c4-103">Administrators use the **get-activitywindow** command to get the duration for the specified activity.</span></span> <span data-ttu-id="123c4-104">Cette commande renvoie la valeur de la durée ainsi que son unité de mesure.</span><span class="sxs-lookup"><span data-stu-id="123c4-104">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
### <a name="to-get-the-duration-on-an-activity"></a><span data-ttu-id="123c4-105">Pour obtenir la durée d'une activité</span><span class="sxs-lookup"><span data-stu-id="123c4-105">To get the duration on an activity</span></span>  
  
1.  <span data-ttu-id="123c4-106">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="123c4-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="123c4-107">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="123c4-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="123c4-108">Tapez bm get-activitywindow-activité :\<nom de l’activité\>.</span><span class="sxs-lookup"><span data-stu-id="123c4-108">Type  bm get-activitywindow -Activity:\<activity name\>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="123c4-109">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="123c4-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="123c4-110">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="123c4-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="123c4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="123c4-111">See Also</span></span>  
 <span data-ttu-id="123c4-112">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="123c4-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="123c4-113">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="123c4-113">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="123c4-114">Comment définir la durée dans une fenêtre d’activité</span><span class="sxs-lookup"><span data-stu-id="123c4-114">How to Set the Duration on an Activity Window</span></span>](../core/how-to-set-the-duration-on-an-activity-window.md)