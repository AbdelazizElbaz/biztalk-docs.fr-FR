---
title: "Comment obtenir la durée d’une fenêtre RTA | Documents Microsoft"
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
- managing [BAM], time intervals
- Get-RTAWindow command [BAM]
ms.assetid: 4e7ad0fd-e7ed-47f7-9435-ef01bbe17afa
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bb930c3e9d252a23653f0464e1adaa1e18b4f45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-get-the-duration-on-an-rta-window"></a><span data-ttu-id="7154c-102">Obtention de la durée dans une fenêtre RTA</span><span class="sxs-lookup"><span data-stu-id="7154c-102">How to Get the Duration on an RTA Window</span></span>
<span data-ttu-id="7154c-103">Les administrateurs utilisent la **get-rtawindow** commande pour obtenir la durée de l’agrégation en temps réel (RTA) spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7154c-103">Administrators use the **get-rtawindow** command to get the duration for the specified real-time aggregation (RTA).</span></span> <span data-ttu-id="7154c-104">Cette commande renvoie la valeur de la durée ainsi que son unité de mesure.</span><span class="sxs-lookup"><span data-stu-id="7154c-104">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
### <a name="to-get-the-duration-on-an-aggregation"></a><span data-ttu-id="7154c-105">Pour obtenir la durée dans une agrégation</span><span class="sxs-lookup"><span data-stu-id="7154c-105">To get the duration on an aggregation</span></span>  
  
1.  <span data-ttu-id="7154c-106">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7154c-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="7154c-107">Accédez au dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="7154c-107">Navigate to the folder [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="7154c-108">Type **bm get-rtawindow-View :\<nom de la vue >-activité :\<nom de l’activité > -Rta :\<nom RTA >**.</span><span class="sxs-lookup"><span data-stu-id="7154c-108">Type **bm get-rtawindow -View:\<view name> -Activity:\<activity name> -Rta:\<RTA name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7154c-109">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="7154c-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="7154c-110">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="7154c-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7154c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7154c-111">See Also</span></span>  
 <span data-ttu-id="7154c-112">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="7154c-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="7154c-113">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="7154c-113">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="7154c-114">Comment définir la durée dans une fenêtre RTA</span><span class="sxs-lookup"><span data-stu-id="7154c-114">How to Set the Duration on an RTA Window</span></span>](../core/how-to-set-the-duration-on-an-rta-window.md)