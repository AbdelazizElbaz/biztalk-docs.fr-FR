---
title: "Comment ajouter des abonnés à une alerte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subscriptions, subscribers
- subscriptions
- managing [BAM], adding alert subscribers
ms.assetid: c76a117d-4516-4f48-995c-7e018dbba755
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e86bde9f47e04c17f62c3cacff5d779cf0bed56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-subscribers-to-an-alert"></a><span data-ttu-id="eb9f6-102">Ajout d'abonnés à une alerte</span><span class="sxs-lookup"><span data-stu-id="eb9f6-102">How to Add Subscribers to an Alert</span></span>
<span data-ttu-id="eb9f6-103">Les administrateurs utilisent la **-ajouter un abonnement** commande pour ajouter un abonné à une alerte spécifiée.</span><span class="sxs-lookup"><span data-stu-id="eb9f6-103">Administrators use the **add-subscription** command to add a subscriber to a specified alert.</span></span>  
  
### <a name="to-add-subscribers-to-an-alert"></a><span data-ttu-id="eb9f6-104">Pour ajouter des abonnés à une alerte</span><span class="sxs-lookup"><span data-stu-id="eb9f6-104">To add subscribers to an alert</span></span>  
  
1.  <span data-ttu-id="eb9f6-105">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eb9f6-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="eb9f6-106">Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="eb9f6-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="eb9f6-107">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="eb9f6-107">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="eb9f6-108">Tapez `bm add-subscription -View:<view name> -Alert:<alert name> -AccountName:<account name> -Type: [ File | Email ][ -Email:<e-mail address> ]`.</span><span class="sxs-lookup"><span data-stu-id="eb9f6-108">Type `bm add-subscription -View:<view name> -Alert:<alert name> -AccountName:<account name> -Type: [ File | Email ][ -Email:<e-mail address> ]`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb9f6-109">*Type* spécifie la méthode de remise BAM utilise pour remettre l’alerte.</span><span class="sxs-lookup"><span data-stu-id="eb9f6-109">*Type* specifies the delivery method which BAM uses to deliver the alert.</span></span> <span data-ttu-id="eb9f6-110">Si vous indiquez un type de remise par messagerie, vous devez fournir une adresse de messagerie à laquelle l'alerte sera envoyée.</span><span class="sxs-lookup"><span data-stu-id="eb9f6-110">If you specify a delivery type of e-mail you must supply an e-mail address to which the alert is delivered.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb9f6-111">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="eb9f6-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="eb9f6-112">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="eb9f6-112">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb9f6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb9f6-113">See Also</span></span>  
 <span data-ttu-id="eb9f6-114">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="eb9f6-114">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="eb9f6-115">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="eb9f6-115">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="eb9f6-116">Comment supprimer les abonnés d’une alerte</span><span class="sxs-lookup"><span data-stu-id="eb9f6-116">How to Remove Subscribers from an Alert</span></span>](../core/how-to-remove-subscribers-from-an-alert.md)