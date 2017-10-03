---
title: "L’activation du suivi de l’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM tracking, enabling
- BAM tracking, disabling
ms.assetid: 3fee3315-fba7-4eea-89f3-6a061b450bb8
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90fae70edf7f748de3790aeaa9e13e3381c44c48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-bam-tracking"></a><span data-ttu-id="e4cf0-102">L’activation de suivi BAM</span><span class="sxs-lookup"><span data-stu-id="e4cf0-102">Enabling BAM Tracking</span></span>
[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]<span data-ttu-id="e4cf0-103">prend en charge améliorée de suivi à l’aide de BizTalk activité BAM (Monitoring).</span><span class="sxs-lookup"><span data-stu-id="e4cf0-103"> supports enhanced tracking using BizTalk Activity Monitoring (BAM).</span></span> <span data-ttu-id="e4cf0-104">Pour activer le suivi dans le cadre des propriétés globales de la configuration de BTARN.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-104">You enable tracking as part of the global properties of the BTARN configuration.</span></span> <span data-ttu-id="e4cf0-105">Après avoir activé le suivi, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] effectue le suivi de tous les messages pour tous les contrats.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-105">After you enable tracking, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] tracks all messages for all agreements.</span></span> <span data-ttu-id="e4cf0-106">Par défaut, le suivi est activé.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-106">By default, tracking is enabled.</span></span>  
  
 <span data-ttu-id="e4cf0-107">Pour plus d’informations sur le suivi, consultez [amélioré de suivi](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="e4cf0-107">For more information about tracking, see [Enhanced Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md).</span></span>  
  
### <a name="to-enable-or-disable-bam-tracking"></a><span data-ttu-id="e4cf0-108">Pour activer ou désactiver le suivi BAM</span><span class="sxs-lookup"><span data-stu-id="e4cf0-108">To enable or disable BAM tracking</span></span>  
  
1.  <span data-ttu-id="e4cf0-109">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-109">Click **Start**, point to **Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
2.  <span data-ttu-id="e4cf0-110">Cliquez sur le [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] nœud dans le volet d’étendue, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-110">Right-click the [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] node in the scope pane, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="e4cf0-111">Dans le **propriétés globales** boîte de dialogue, sélectionnez **activer le suivi BAM** pour activer le suivi, ou désactivez cette option pour la désactiver.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-111">In the **Global Properties** dialog box, select **Enable BAM Tracking** to enable tracking, or clear this option to disable it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e4cf0-112">Chaque fois que vous modifiez l’indicateur d’activation pour activer ou désactiver le suivi, vous devez redémarrer tous les services sur lequel les processus publics et l’adaptateur HTTP sont en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-112">Whenever you change the enable flag to enable or disable tracking, you have to restart all services on which the public processes and the HTTP adapter are running.</span></span> <span data-ttu-id="e4cf0-113">Cela inclut le service hôte et le service de l’hôte isolé.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-113">This includes the host service and the isolated host service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4cf0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4cf0-114">See Also</span></span>  
 <span data-ttu-id="e4cf0-115">[Gérer la configuration, les certificats, les bases de données et la sécurité](manage-configuration-certificates-databases-security.md) </span><span class="sxs-lookup"><span data-stu-id="e4cf0-115">[Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md) </span></span>  
 <span data-ttu-id="e4cf0-116">[Suivi amélioré](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md) </span><span class="sxs-lookup"><span data-stu-id="e4cf0-116">[Enhanced Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md) </span></span>  
 [<span data-ttu-id="e4cf0-117">Administration de la Configuration de BTARN</span><span class="sxs-lookup"><span data-stu-id="e4cf0-117">Administering the BTARN Configuration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)