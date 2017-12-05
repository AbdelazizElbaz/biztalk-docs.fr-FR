---
title: Planifier le traitement par lots | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, scheduling
- scheduling batching
ms.assetid: 037626f1-1b3b-43e6-80eb-5fb900cdbd46
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 790cf5cb853da211d5e8928f398ecc1a2b3fe0ba
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="scheduling-batching"></a>Planification de traitement par lot
Vous utilisez [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Explorer de Configuration pour activer, de demande ou de mettre fin à un lot sortant. Activation d’un lot sortant comprend deux étapes : configuration temporels ou message compter les critères et avant de démarrer l’orchestration de traitement par lot sortante.  
  
 L’illustration suivante montre le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **planification par lot** onglet.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-batchsch.gif "hl7_ops_batchsch")  
  
 Utilisez les procédures suivantes pour ouvrir [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration et la planification de traitement par lot.  
  
### <a name="to-open-btahl7-configuration-explorer"></a>Pour ouvrir l’Explorateur de Configuration de BTAHL7  
  
-   Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator pour HL7**, puis cliquez sur  **BTAHL7 L’Explorateur de Configuration**.  
  
### <a name="to-schedule-message-batching"></a>Pour planifier le traitement par lots du message  
  
1.  Ouvrez l’Explorateur de Configuration de BTAHL7.  
  
2.  Dans l’Explorateur de Configuration de BTAHL7, dans le **BTAHL7 Configuration Explorer** boîte de dialogue le **Parties** , sélectionnez la partie que vous souhaitez configurer, puis, dans le **lot planification** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Heures avant tout d’abord du lot**|Tapez le nombre d’heures avant le premier traitement consiste à démarrer.|  
    |**Répétez le traitement par lots après**|Sélectionnez l'une des options suivantes :<br /><br /> -   **Heures**. Tapez le nombre d’heures de répéter le processus de traitement par lots.<br />-   **Messages**. Tapez le nombre de messages à traiter avant que le processus de traitement suivant commence.|  
    |**Contrôle de traitement par lots**|Sélectionnez l'une des options suivantes :<br /><br /> -   **Démarrer la planification**: sélectionnez cette option pour démarrer la planification par lot.<br />-   **Envoyer maintenant**: sélectionnez cette option pour démarrer le traitement est immédiatement traité.<br />-   **Arrêter planification**: sélectionnez cette option pour arrêter la planification du lot actuel.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration du traitement par lot des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/configuring-batching-acknowledgments.md)