---
title: "Configuration de BTARN envoi et de Pipelines de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines, modifying
- modifying, send pipelines
- receive pipelines, modifying
- modifying, receive pipelines
ms.assetid: 00960de0-3763-40aa-9e4b-1fedc7f1eea6
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47f2f12629965c3b01df8cc2f2fd7b1a7ea58a47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-btarn-send-and-receive-pipelines"></a><span data-ttu-id="7d4fb-102">Configuration de BTARN envoi et de Pipelines de réception</span><span class="sxs-lookup"><span data-stu-id="7d4fb-102">Setting BTARN Send and Receive Pipelines</span></span>
<span data-ttu-id="7d4fb-103">Par défaut, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] utilise la norme [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline d’envoi (Microsoft.Solutions.BTARN.Pipelines.Send) et la norme [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] (Microsoft.Solutions.BTARN.Pipelines.Receive) de pipeline de réception lorsque vous créez ports d’envoi partenaire.</span><span class="sxs-lookup"><span data-stu-id="7d4fb-103">By default, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses the standard [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] send pipeline (Microsoft.Solutions.BTARN.Pipelines.Send) and the standard [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receive pipeline (Microsoft.Solutions.BTARN.Pipelines.Receive) when you create partner send ports.</span></span> <span data-ttu-id="7d4fb-104">Toutefois, vous pouvez modifier le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration à utiliser un pipeline BizTalk existant ou un pipeline personnalisé que vous avez créés.</span><span class="sxs-lookup"><span data-stu-id="7d4fb-104">However, you can change the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration to use an existing BizTalk pipeline or a custom pipeline that you have created.</span></span> <span data-ttu-id="7d4fb-105">Utiliser des accords de partenariat commercial, tous les partenaires et aux organisations de base, le même pipeline d’envoi et le même pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="7d4fb-105">All trading partner agreements, and all partners and home organizations, use the same send pipeline and the same receive pipeline.</span></span>  
  
 <span data-ttu-id="7d4fb-106">Lorsque vous créez un partenaire, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] crée deux ports d’envoi pour ce partenaire à utiliser une asynchrone et synchrone : \< *nom du partenaire*>. Port d’envoi asynchrone et \< *nom du partenaire*>. Port d’envoi de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="7d4fb-106">When you first create a partner, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] creates two send ports for that partner to use, one asynchronous and one synchronous: \<*partner name*>.Async send port and \<*partner name*>.Sync send port.</span></span> <span data-ttu-id="7d4fb-107">Ces par défaut des ports d’envoi à la norme [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] envoyer le pipeline et le port d’envoi de synchronisation reçoivent des valeurs par défaut du pipeline à la norme [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="7d4fb-107">These send ports default to the standard [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] send pipeline, and the sync send port receive pipeline defaults to the standard [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receive pipeline.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d4fb-108">Modification de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] de pipeline dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion peut réinitialiser les propriétés que vous avez modifiée directement dans l’Explorateur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7d4fb-108">Changing the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console might reset properties that you changed directly in BizTalk Explorer.</span></span>  
  
### <a name="to-change-the-send-or-receive-pipeline-that-btarn-uses"></a><span data-ttu-id="7d4fb-109">Pour modifier l’envoi ou le pipeline de réception qui utilise de BTARN</span><span class="sxs-lookup"><span data-stu-id="7d4fb-109">To change the send or receive pipeline that BTARN uses</span></span>  
  
1.  <span data-ttu-id="7d4fb-110">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.</span><span class="sxs-lookup"><span data-stu-id="7d4fb-110">Click **Start**, point to **Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
2.  <span data-ttu-id="7d4fb-111">Dans la Console de gestion BTARN, cliquez sur le [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] nœud, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7d4fb-111">In the BTARN Management Console, right-click the [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] node, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="7d4fb-112">Dans la boîte de dialogue Propriétés globales, sélectionnez un autre pipeline à partir de la liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d4fb-112">In the Global Properties dialog box, select a different pipeline from the drop-down list, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="7d4fb-113">Dans le **Instances d’hôte** nœud sous la [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration** nœud, arrêtez et redémarrez l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="7d4fb-113">In the **Host Instances** node under the [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**Administration** node, stop and then restart the host.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7d4fb-114">Les modifications apportées aux pipelines prendront effet que si vous redémarrez le serveur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7d4fb-114">The changes to the pipelines will only take effect if you restart the BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d4fb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d4fb-115">See Also</span></span>  
 <span data-ttu-id="7d4fb-116">[Gérer la configuration, les certificats, les bases de données et la sécurité](manage-configuration-certificates-databases-security.md) </span><span class="sxs-lookup"><span data-stu-id="7d4fb-116">[Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md) </span></span>  
 [<span data-ttu-id="7d4fb-117">L’activation de suivi BAM</span><span class="sxs-lookup"><span data-stu-id="7d4fb-117">Enabling BAM Tracking</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/enabling-bam-tracking.md)