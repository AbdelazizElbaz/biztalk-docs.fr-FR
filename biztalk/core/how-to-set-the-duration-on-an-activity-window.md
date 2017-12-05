---
title: "Comment définir la durée dans une fenêtre d’activité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Set-ActivityWindow command [BAM]
- activities [BAM], time intervals
- managing [BAM], time intervals
ms.assetid: e39c315e-f215-4f81-9774-cf7aedf6ba33
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66ef0c7200c69cd69a72a5743ca8f14a8950b17d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-set-the-duration-on-an-activity-window"></a><span data-ttu-id="a6bbd-102">Définition de la durée dans une fenêtre d'activité</span><span class="sxs-lookup"><span data-stu-id="a6bbd-102">How to Set the Duration on an Activity Window</span></span>
<span data-ttu-id="a6bbd-103">Les administrateurs utilisent la **set-activitywindow** commande pour définir la durée de l’activité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a6bbd-103">Administrators use the **set-activitywindow** command to set the duration for the specified activity.</span></span>  
  
### <a name="to-set-the-duration-on-an-activity"></a><span data-ttu-id="a6bbd-104">Pour définir la durée dans une activité</span><span class="sxs-lookup"><span data-stu-id="a6bbd-104">To set the duration on an activity</span></span>  
  
1.  <span data-ttu-id="a6bbd-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a6bbd-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="a6bbd-106">Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="a6bbd-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="a6bbd-107">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="a6bbd-107">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="a6bbd-108">Type **bm set-activitywindow-activité :\<nom de l’activité\> - TimeLength :\<nombre entier\> - TimeUnit : mois &#124; jour &#124; Heure &#124; Minute**.</span><span class="sxs-lookup"><span data-stu-id="a6bbd-108">Type **bm set-activitywindow -Activity:\<activity name\> -TimeLength:\<integer number\> -TimeUnit:Month&#124;Day&#124;Hour&#124;Minute**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6bbd-109">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a6bbd-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="a6bbd-110">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="a6bbd-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6bbd-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6bbd-111">See Also</span></span>  
 <span data-ttu-id="a6bbd-112">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="a6bbd-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="a6bbd-113">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="a6bbd-113">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="a6bbd-114">Comment obtenir la durée d’une fenêtre d’activité</span><span class="sxs-lookup"><span data-stu-id="a6bbd-114">How to Get the Duration on an Activity Window</span></span>](../core/how-to-get-the-duration-on-an-activity-window.md)