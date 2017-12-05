---
title: "Comment définir la durée dans une fenêtre RTA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], aggregations
- aggregations [BAM], time intervals
- Set-RTAWindow command [BAM]
- managing [BAM], time intervals
ms.assetid: 3042c3f5-be0f-48fb-9831-daa4868b90fe
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb8b43fc846835ab8f24f664d4af54ab99b88576
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-set-the-duration-on-an-rta-window"></a><span data-ttu-id="b3b7f-102">Définition de la durée dans une fenêtre RTA</span><span class="sxs-lookup"><span data-stu-id="b3b7f-102">How to Set the Duration on an RTA Window</span></span>
<span data-ttu-id="b3b7f-103">Les administrateurs utilisent la **set-rtawindow** commande pour définir la durée de l’agrégation en temps réel (RTA) spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b3b7f-103">Administrators use the **set-rtawindow** command to set the duration for the specified real-time aggregation (RTA).</span></span>  
  
### <a name="to-set-the-duration-on-an-aggregation"></a><span data-ttu-id="b3b7f-104">Pour définir la durée dans une agrégation</span><span class="sxs-lookup"><span data-stu-id="b3b7f-104">To set the duration on an aggregation</span></span>  
  
1.  <span data-ttu-id="b3b7f-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b3b7f-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b3b7f-106">Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="b3b7f-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="b3b7f-107">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="b3b7f-107">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="b3b7f-108">Type **bm set-rtawindow-View :\<nom de la vue\> -activité :\<nom de l’activité\> -nom :\<nom RTA\> - TimeLength :\<le nombre entier\>- TimeUnit : jour &#124; Heure &#124; Minute**.</span><span class="sxs-lookup"><span data-stu-id="b3b7f-108">Type **bm set-rtawindow -View:\<view name\> -Activity:\<activity name\> -Name:\<RTA name\> -TimeLength:\<integer number\> -TimeUnit:Day&#124;Hour&#124;Minute**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b3b7f-109">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b3b7f-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="b3b7f-110">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="b3b7f-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b7f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3b7f-111">See Also</span></span>  
 <span data-ttu-id="b3b7f-112">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="b3b7f-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="b3b7f-113">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="b3b7f-113">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="b3b7f-114">Comment obtenir la durée d’une fenêtre RTA</span><span class="sxs-lookup"><span data-stu-id="b3b7f-114">How to Get the Duration on an RTA Window</span></span>](../core/how-to-get-the-duration-on-an-rta-window.md)