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
ms.openlocfilehash: a6f5e996b7046e94c90df0269381391a3aed3084
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="setting-btarn-send-and-receive-pipelines"></a>Configuration de BTARN envoi et de Pipelines de réception
Par défaut, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] utilise la norme [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline d’envoi (Microsoft.Solutions.BTARN.Pipelines.Send) et la norme [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] (Microsoft.Solutions.BTARN.Pipelines.Receive) de pipeline de réception lorsque vous créez ports d’envoi partenaire. Toutefois, vous pouvez modifier le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration à utiliser un pipeline BizTalk existant ou un pipeline personnalisé que vous avez créés. Utiliser des accords de partenariat commercial, tous les partenaires et aux organisations de base, le même pipeline d’envoi et le même pipeline de réception.  
  
 Lorsque vous créez un partenaire, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] crée deux ports d’envoi pour ce partenaire à utiliser une asynchrone et synchrone : \< *nom du partenaire*\>. Port d’envoi asynchrone et \< *nom du partenaire*\>. Port d’envoi de synchronisation. Ces par défaut des ports d’envoi à la norme [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] envoyer le pipeline et le port d’envoi de synchronisation reçoivent des valeurs par défaut du pipeline à la norme [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline de réception.  
  
> [!NOTE]
>  Modification de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] de pipeline dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion peut réinitialiser les propriétés que vous avez modifiée directement dans l’Explorateur BizTalk.  
  
### <a name="to-change-the-send-or-receive-pipeline-that-btarn-uses"></a>Pour modifier l’envoi ou le pipeline de réception qui utilise de BTARN  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Dans la Console de gestion BTARN, cliquez sur le [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] nœud, puis cliquez sur **propriétés**.  
  
3.  Dans la boîte de dialogue Propriétés globales, sélectionnez un autre pipeline à partir de la liste déroulante, puis cliquez sur **OK**.  
  
4.  Dans le **Instances d’hôte** nœud sous la [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration** nœud, arrêtez et redémarrez l’ordinateur hôte.  
  
    > [!NOTE]
    >  Les modifications apportées aux pipelines prendront effet que si vous redémarrez le serveur BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer la configuration, les certificats, les bases de données et la sécurité](manage-configuration-certificates-databases-security.md)   
 [Activation du suivi BAM](../../adapters-and-accelerators/accelerator-rosettanet/enabling-bam-tracking.md)