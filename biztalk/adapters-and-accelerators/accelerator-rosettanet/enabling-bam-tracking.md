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
# <a name="enabling-bam-tracking"></a>L’activation de suivi BAM
[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]prend en charge améliorée de suivi à l’aide de BizTalk activité BAM (Monitoring). Pour activer le suivi dans le cadre des propriétés globales de la configuration de BTARN. Après avoir activé le suivi, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] effectue le suivi de tous les messages pour tous les contrats. Par défaut, le suivi est activé.  
  
 Pour plus d’informations sur le suivi, consultez [amélioré de suivi](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md).  
  
### <a name="to-enable-or-disable-bam-tracking"></a>Pour activer ou désactiver le suivi BAM  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Cliquez sur le [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] nœud dans le volet d’étendue, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés globales** boîte de dialogue, sélectionnez **activer le suivi BAM** pour activer le suivi, ou désactivez cette option pour la désactiver.  
  
> [!IMPORTANT]
>  Chaque fois que vous modifiez l’indicateur d’activation pour activer ou désactiver le suivi, vous devez redémarrer tous les services sur lequel les processus publics et l’adaptateur HTTP sont en cours d’exécution. Cela inclut le service hôte et le service de l’hôte isolé.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer la configuration, les certificats, les bases de données et la sécurité](manage-configuration-certificates-databases-security.md)   
 [Suivi amélioré](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md)   
 [Administration de la Configuration de BTARN](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)