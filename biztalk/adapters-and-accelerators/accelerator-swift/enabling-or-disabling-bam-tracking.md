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
# <a name="enabling-or-disabling-bam-tracking"></a>Activer ou désactiver le suivi BAM
Vous pouvez activer ou désactiver le suivi à tout moment, même si le processus de réparation de Message et nouvelle Transmission a des transactions dans le processus BAM. Toutefois, si vous désactivez le suivi BAM tandis que les transactions sont en cours, les données BAM peuvent être incomplètes pour ces transactions. Si cela se produit, la table d’historique contient toujours des données précises pour toutes les instances.  
  
 Pour plus d’informations sur l’activation ou la désactivation de suivi dans le cadre du processus de configuration d’A4SWIFT composant BAM, consultez [définition des propriétés A4SWIFT](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md).  
  
### <a name="to-enable-or-disable-bam-tracking"></a>Pour activer ou désactiver le suivi BAM  
  
1.  Dans le Client Web du profil, cliquez sur **BizTalk Accelerator pour SWIFT** dans l’arborescence de la console, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue Propriétés globales, désactiver le suivi BAM, en désactivant **activer le suivi BAM**, ou activer le suivi en la sélectionnant BAM.  
  
3.  Cliquez sur **OK**.  
  
4.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, **groupe BizTalk**, puis **paramètres de plateforme**. Cliquez sur **Instances d’hôte**.  
  
5.  Dans le volet de détails, cliquez sur l’instance d’hôte, puis cliquez sur **redémarrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des propriétés A4SWIFT](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md)