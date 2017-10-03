---
title: "La désactivation de suivi BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, disabling BAM tracking
- BAM tracking
ms.assetid: ea5fef0e-7a96-46f5-81d8-9b1d8a5d24d2
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4e734bd31147ecacc8bbbe98d98297edfb4f0de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="disabling-bam-tracking"></a>La désactivation de suivi BAM
Par défaut, le suivi BAM est activé pour le rapprochement de réponse de FIN. Vous pouvez le désactiver comme suit.  
  
### <a name="to-disable-bam-tracking-for-frr"></a>Pour désactiver le suivi pour FRR BAM  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **regedit**, puis cliquez sur **OK**.  
  
2.  Dans le volet gauche de l’Éditeur du Registre, déplacez à mon ordinateur/HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/BizTalk Accelerator pour SWIFT/FRR.  
  
    > [!IMPORTANT]
    >  Cette entrée de Registre doit être modifiée sur chaque ordinateur rapprochement de réponse de FIN est en cours d’exécution.  
  
3.  Dans le volet droit de l’Éditeur du Registre, double-cliquez sur **BAMTrackingEnabled**.  
  
4.  Dans le **modifier la valeur DWORD** boîte de dialogue le **données de la valeur** , tapez **0** pour désactiver le suivi BAM.  
  
5.  Cliquez sur **OK**.