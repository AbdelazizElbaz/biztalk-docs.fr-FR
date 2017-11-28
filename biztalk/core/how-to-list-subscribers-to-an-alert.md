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
ms.openlocfilehash: d62f962847cf0e48929e11040bf1de226d567b6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-subscribers-to-an-alert"></a><span data-ttu-id="0867d-102">Affichage des abonnés à une alerte</span><span class="sxs-lookup"><span data-stu-id="0867d-102">How to List Subscribers to an Alert</span></span>
<span data-ttu-id="0867d-103">Les administrateurs utilisent la **get-subscriptions** commande pour répertorier tous les abonnés à une alerte spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0867d-103">Administrators use the **get-subscriptions** command to list all of the subscribers to a specified alert.</span></span>  
  
### <a name="to-list-subscribers-to-an-alert"></a><span data-ttu-id="0867d-104">Pour afficher tous les abonnés à une alerte</span><span class="sxs-lookup"><span data-stu-id="0867d-104">To list subscribers to an alert</span></span>  
  
1.  <span data-ttu-id="0867d-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0867d-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="0867d-106">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="0867d-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="0867d-107">Type **bm get-subscriptions-View :\<nom de la vue >-Alert :\<nom de l’alerte >**.</span><span class="sxs-lookup"><span data-stu-id="0867d-107">Type **bm get-subscriptions -View:\<view name> -Alert:\<alert name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0867d-108">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="0867d-108">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="0867d-109">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="0867d-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0867d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0867d-110">See Also</span></span>  
 <span data-ttu-id="0867d-111">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="0867d-111">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="0867d-112">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="0867d-112">BAM Management Utility</span></span>](../core/bam-management-utility.md)