---
title: "Leçon 2 : Confirmer le déploiement à l’aide de l’outil de Composer de règle métier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, verifying
- verifying, business rules
- verifying, Business Rule Composer tool
- business rules, Business Rule Composer tool
- Business Rule Composer tool
ms.assetid: 337dc469-cf9e-406b-90ae-0f580b17d7c9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3115dc425fedca9019f0e5e5171f7234e6fbdbb2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool"></a>Leçon 2 : Confirmer le déploiement à l’aide de l’outil de Composer de règle métier
Dans cette leçon, vous confirmez que l’outil Éditeur des règles d’entreprise créé vos vocabulaires et déployé vos stratégies. Un vocabulaire est une collection d’éléments de vocabulaire que vous utilisez dans la composition de règle. une stratégie est une collection avec versions de règles d'entreprise.  
  
### <a name="to-confirm-the-deployment-using-the-business-rule-composer-tool"></a>Pour confirmer le déploiement à l’aide de l’outil Éditeur des règles d’entreprise  
  
1.  Démarrer **Éditeur des règles d’entreprise** dans BizTalk Server.  
  
2.  Dans la boîte de dialogue Ouvrir le magasin de règles, cliquez sur **OK**.  
  
3.  Dans le volet Explorateur de faits de l’outil Éditeur des règles d’entreprise, vérifiez que les vocabulaires que vous souhaitez que s’affichent dans l’Explorateur de faits, comme indiqué dans l’illustration suivante.  
  
     ![](../../adapters-and-accelerators/accelerator-swift/media/tut2-scrn2.gif "Tut2_scrn2")  
  
4.  Dans l’Explorateur de stratégies, vérifiez que l’outil Éditeur des règles d’entreprise déployé les stratégies suivantes :  
  
     MT103_Master_Policy  
  
     MT103_Validation_Policy  
  
     SWIFT_NetworkRule149_Policy  
  
     SWIFT_NetworkRule150_Policy  
  
     SWIFT_NetworkRule151_Policy  
  
     SWIFT_NetworkRule175_Policy  
  
     SWIFT_NetworkRule2_Policy  
  
     SWIFT_NetworkRule201_Policy  
  
     SWIFT_NetworkRule202_Policy  
  
     SWIFT_NetworkRule203_Policy  
  
     SWIFT_NetworkRule204_Policy  
  
     SWIFT_NetworkRule205_Policy  
  
     SWIFT_NetworkRule206_Policy  
  
     SWIFT_NetworkRule207_Policy  
  
     SWIFT_NetworkRule209_Policy  
  
     SWIFT_NetworkRule210_Policy  
  
     SWIFT_NetworkRule212_Policy  
  
     SWIFT_NetworkRule213_Policy  
  
     SWIFT_NetworkRule215_Policy  
  
     SWIFT_NetworkRule216_Policy  
  
     SWIFT_NetworkRule217_Policy  
  
     SWIFT_NetworkRule218_Policy  
  
     SWIFT_NetworkRule244_Policy  
  
     SWIFT_NetworkRule245_Policy  
  
     SWIFT_NetworkRule81_Policy  
  
     SWIFT_PartyIdentifier_Policy  
  
     SWIFT_Reference_Policy  
  
### <a name="to-view-a-policy"></a>Pour afficher une stratégie  
  
1.  Dans le volet Explorateur de stratégies de l’éditeur des règles d’entreprise, vérifiez que le **SWIFT_NetworkRule149_Policy** est développé, puis cliquez sur le **Version 1.0 – Deployed** nœud.  
  
2.  Double-cliquez sur le **Validate_MT103** nœud pour l’ouvrir.  
  
     La stratégie s’ouvre dans le volet de l’éditeur sur le côté droit de l’écran.  
  
 Passez à [Module 7 : test d’une Instance de fichier plat valide](../../adapters-and-accelerators/accelerator-swift/module-7-testing-a-valid-flat-file-instance.md).