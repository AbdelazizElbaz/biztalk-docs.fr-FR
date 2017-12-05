---
title: "Comment supprimer les abonnés d’une alerte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subscriptions, subscribers
- managing [BAM], deleting alert subscibers
- alerts, subscribers
ms.assetid: d5571863-26e3-4c1b-991f-538cd1fef347
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9122b74ecc82e32230d09e2d0e01b553aaa2bd06
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-remove-subscribers-from-an-alert"></a><span data-ttu-id="41dfa-102">Suppression d'abonnés d'une alerte</span><span class="sxs-lookup"><span data-stu-id="41dfa-102">How to Remove Subscribers from an Alert</span></span>
<span data-ttu-id="41dfa-103">Les administrateurs utilisent la **remove-subscription** commande pour supprimer l’utilisateur spécifié en tant qu’abonné à partir d’une alerte.</span><span class="sxs-lookup"><span data-stu-id="41dfa-103">Administrators use the **remove-subscription** command to remove the specified user as a subscriber from an alert.</span></span>  
  
### <a name="to-remove-subscribers-from-an-alert"></a><span data-ttu-id="41dfa-104">Pour supprimer des abonnés d'une alerte</span><span class="sxs-lookup"><span data-stu-id="41dfa-104">To remove subscribers from an alert</span></span>  
  
1.  <span data-ttu-id="41dfa-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="41dfa-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="41dfa-106">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="41dfa-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="41dfa-107">Type **bm remove-subscription-View :\<nom de la vue\> -alerte :\<nom de l’alerte\> - AccountName :\<nom de compte\>**.</span><span class="sxs-lookup"><span data-stu-id="41dfa-107">Type **bm remove-subscription -View:\<view name\> -Alert:\<alert name\> -AccountName:\<account name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41dfa-108">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="41dfa-108">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="41dfa-109">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="41dfa-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41dfa-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41dfa-110">See Also</span></span>  
 <span data-ttu-id="41dfa-111">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="41dfa-111">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="41dfa-112">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="41dfa-112">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="41dfa-113">Comment ajouter des abonnés à une alerte</span><span class="sxs-lookup"><span data-stu-id="41dfa-113">How to Add Subscribers to an Alert</span></span>](../core/how-to-add-subscribers-to-an-alert.md)