---
title: "Définir le délai d’expiration de délai FRR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FIN Response Reconciliation, configuring delay time-out
ms.assetid: 62209bf6-56c8-483a-96d5-328bffc8b680
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbf4c08984876627c0f11f935b0be3e32769b5f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-the-frr-delay-time-out"></a>Définir le délai d’expiration du délai FRR
Vous devez configurer l’orchestration FRR expire après une durée, donc il n’attendra pas la réponse FNN indéfiniment. Si la durée du délai d’attente expire, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] publie les messages expiré à un gestionnaire de délai d’attente personnalisée.  
  
### <a name="to-set-the-frr-delay-time-out"></a>Pour définir le délai d’expiration du délai FRR  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **regedit**, puis cliquez sur **OK**.  
  
2.  Dans le volet gauche de l’Éditeur du Registre, déplacez à mon ordinateur/HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/BizTalk Accelerator pour SWIFT/FRR.  
  
    > [!IMPORTANT]
    >  Le rôle sera ajouté à la position dans le flux de travail qui est défini dans le nœud rôles. Pour modifier cet emplacement, vous devez effectuer l’étape 8 pour modifier l’ordre des rôles dans le nœud rôles.  
  
3.  Dans le volet droit de l’Éditeur du Registre, double-cliquez sur **DelayTimeout**.  
  
4.  Dans le **modifier la valeur DWORD** boîte de dialogue le **données de la valeur** , tapez la durée du délai d’expiration au format hexadécimal.  
  
    > [!NOTE]
    >  La valeur par défaut pour le **FRR DelayTimeout** propriété est de 600 secondes (258 hexadécimal).  
  
5.  Cliquez sur **OK**.