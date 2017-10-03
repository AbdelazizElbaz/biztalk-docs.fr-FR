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
ms.openlocfilehash: 92855ecc4e4e5ad2f7932327de7da8e19a80d490
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-subscribers-from-an-alert"></a><span data-ttu-id="55820-102">Suppression d'abonnés d'une alerte</span><span class="sxs-lookup"><span data-stu-id="55820-102">How to Remove Subscribers from an Alert</span></span>
<span data-ttu-id="55820-103">Les administrateurs utilisent la **remove-subscription** commande pour supprimer l’utilisateur spécifié en tant qu’abonné à partir d’une alerte.</span><span class="sxs-lookup"><span data-stu-id="55820-103">Administrators use the **remove-subscription** command to remove the specified user as a subscriber from an alert.</span></span>  
  
### <a name="to-remove-subscribers-from-an-alert"></a><span data-ttu-id="55820-104">Pour supprimer des abonnés d'une alerte</span><span class="sxs-lookup"><span data-stu-id="55820-104">To remove subscribers from an alert</span></span>  
  
1.  <span data-ttu-id="55820-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="55820-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="55820-106">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="55820-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="55820-107">Type **bm remove-subscription-View :\<nom de la vue >-alerte :\<nom de l’alerte > - AccountName :\<nom du compte >**.</span><span class="sxs-lookup"><span data-stu-id="55820-107">Type **bm remove-subscription -View:\<view name> -Alert:\<alert name> -AccountName:\<account name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="55820-108">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="55820-108">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="55820-109">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="55820-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55820-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55820-110">See Also</span></span>  
 <span data-ttu-id="55820-111">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="55820-111">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="55820-112">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="55820-112">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="55820-113">Comment ajouter des abonnés à une alerte</span><span class="sxs-lookup"><span data-stu-id="55820-113">How to Add Subscribers to an Alert</span></span>](../core/how-to-add-subscribers-to-an-alert.md)