---
title: "Affichage des abonnés à une alerte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- alerts, listing subscribers
- managing [BAM], listing alert subscribers
- subscriptions, listing subscribers
ms.assetid: 760cc88f-896d-43a3-a4af-b2a836190276
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 909854abd251d94fa71ce963c3714f6d664153c1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-list-subscribers-to-an-alert"></a><span data-ttu-id="2bf56-102">Affichage des abonnés à une alerte</span><span class="sxs-lookup"><span data-stu-id="2bf56-102">How to List Subscribers to an Alert</span></span>
<span data-ttu-id="2bf56-103">Les administrateurs utilisent la **get-subscriptions** commande pour répertorier tous les abonnés à une alerte spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2bf56-103">Administrators use the **get-subscriptions** command to list all of the subscribers to a specified alert.</span></span>  
  
### <a name="to-list-subscribers-to-an-alert"></a><span data-ttu-id="2bf56-104">Pour afficher tous les abonnés à une alerte</span><span class="sxs-lookup"><span data-stu-id="2bf56-104">To list subscribers to an alert</span></span>  
  
1.  <span data-ttu-id="2bf56-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2bf56-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="2bf56-106">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="2bf56-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="2bf56-107">Type **bm get-subscriptions-View :\<nom de la vue\> -alerte :\<nom de l’alerte\>**.</span><span class="sxs-lookup"><span data-stu-id="2bf56-107">Type **bm get-subscriptions -View:\<view name\> -Alert:\<alert name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2bf56-108">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="2bf56-108">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="2bf56-109">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="2bf56-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf56-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bf56-110">See Also</span></span>  
 <span data-ttu-id="2bf56-111">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="2bf56-111">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="2bf56-112">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="2bf56-112">BAM Management Utility</span></span>](../core/bam-management-utility.md)