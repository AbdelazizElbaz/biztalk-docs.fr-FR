---
title: "Activer ou désactiver le suivi BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Message Repair and New Submission, BAM tracking
- BAM tracking
ms.assetid: 07896fab-88a0-4759-8547-16edcd1eebc0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1132c41e9a017e42139d988d1588f79d7d3afaa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-or-disabling-bam-tracking"></a><span data-ttu-id="38d57-102">Activer ou désactiver le suivi BAM</span><span class="sxs-lookup"><span data-stu-id="38d57-102">Enabling or Disabling BAM Tracking</span></span>
<span data-ttu-id="38d57-103">Vous pouvez activer ou désactiver le suivi à tout moment, même si le processus de réparation de Message et nouvelle Transmission a des transactions dans le processus BAM.</span><span class="sxs-lookup"><span data-stu-id="38d57-103">You can enable or disable BAM tracking at any point, even while the Message Repair and New Transmission process has transactions in process.</span></span> <span data-ttu-id="38d57-104">Toutefois, si vous désactivez le suivi BAM tandis que les transactions sont en cours, les données BAM peuvent être incomplètes pour ces transactions.</span><span class="sxs-lookup"><span data-stu-id="38d57-104">However, if you disable BAM tracking while transactions are in process, the BAM data may be incomplete for those transactions.</span></span> <span data-ttu-id="38d57-105">Si cela se produit, la table d’historique contient toujours des données précises pour toutes les instances.</span><span class="sxs-lookup"><span data-stu-id="38d57-105">If this occurs, the history table will still contain accurate data for all instances.</span></span>  
  
 <span data-ttu-id="38d57-106">Pour plus d’informations sur l’activation ou la désactivation de suivi dans le cadre du processus de configuration d’A4SWIFT composant BAM, consultez [définition des propriétés A4SWIFT](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md).</span><span class="sxs-lookup"><span data-stu-id="38d57-106">For information about enabling or disabling BAM tracking as part of the A4SWIFT component configuration process, see [Setting A4SWIFT Properties](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md).</span></span>  
  
### <a name="to-enable-or-disable-bam-tracking"></a><span data-ttu-id="38d57-107">Pour activer ou désactiver le suivi BAM</span><span class="sxs-lookup"><span data-stu-id="38d57-107">To enable or disable BAM Tracking</span></span>  
  
1.  <span data-ttu-id="38d57-108">Dans le Client Web du profil, cliquez sur **BizTalk Accelerator pour SWIFT** dans l’arborescence de la console, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="38d57-108">In the Profile Web Client, right-click **BizTalk Accelerator for SWIFT** in the console tree, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="38d57-109">Dans la boîte de dialogue Propriétés globales, désactiver le suivi BAM, en désactivant **activer le suivi BAM**, ou activer le suivi en la sélectionnant BAM.</span><span class="sxs-lookup"><span data-stu-id="38d57-109">In the Global Properties dialog box, disable BAM tracking by deselecting **Enable BAM Tracking**, or enable BAM tracking by selecting it.</span></span>  
  
3.  <span data-ttu-id="38d57-110">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="38d57-110">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="38d57-111">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, **groupe BizTalk**, puis **paramètres de plateforme**.</span><span class="sxs-lookup"><span data-stu-id="38d57-111">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, and then **Platform Settings**.</span></span> <span data-ttu-id="38d57-112">Cliquez sur **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="38d57-112">Click **Host Instances**.</span></span>  
  
5.  <span data-ttu-id="38d57-113">Dans le volet de détails, cliquez sur l’instance d’hôte, puis cliquez sur **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="38d57-113">In the details pane, right-click the host instance , and then click **Restart**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d57-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38d57-114">See Also</span></span>  
 [<span data-ttu-id="38d57-115">Définition des propriétés A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="38d57-115">Setting A4SWIFT Properties</span></span>](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md)