---
title: "Étape 4 : Configurez la partie de la Source pour le scénario de traitement par lots Créer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b06b6545-4c2e-4a56-9feb-bd3f9574d4d1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12f7ca9eebb28bb97ae925aec4fc34cefd5a2dcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-configure-the-source-party-for-the-create-batch-scenario"></a>Étape 4 : Configurez la partie de la Source pour le scénario de traitement par lots Créer
Dans cette étape, vous configurez la partie de la source pour le scénario de traitement par lots de créer. Vous également sélectionnez les accusés de réception que BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) lot, tel que défini pour ce tiers. Vous définissez la planification pour le traitement de l’accusé de réception que [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] créera le lot après le nombre de messages atteint 2.  
  
> [!NOTE]
>  Dans ce scénario, vous utilisez la même partie source que vous avez créé dans [étape 7 : créer et configurer un tiers Source](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md) de la partie 1 de ce didacticiel (la fragmentation lot scénario entrant).  
  
### <a name="to-configure-the-source-party-for-the-create-batch-scenario"></a>Pour configurer le tiers source pour le scénario de traitement par lots de créer  
  
1.  Dans l’Explorateur de Configuration de BTAHL7, sur le **Parties** dans l’arborescence de la console, cliquez sur **Tutorial_BatchSource**.  
  
2.  Cliquez sur le **accusé de réception** onglet dans le volet détails. Vérifiez que le **type d’accusé de réception** est **OriginalMode**.  
  
3.  Cliquez sur le **définition de lot** onglet. Sous **accusés de réception de Message disponibles**, cliquez sur **BTAHL7Schemas.ADT_A03_231_GLO_DEF**, cliquez sur le déplacement vers la droite (**>>**) pour ajouter ce schéma au  **Sélectionné des accusés de réception de Message**, puis cliquez sur **enregistrer**.  
  
4.  Cliquez sur le **planification par lot** onglet. Dans le **Répétez le traitement par lots après** section, sélectionnez **Messages**, puis tapez **2** dans les **Messages** boîte.  
  
5.  Cliquez sur **démarrer planification**.  
  
 Passez à [étape 5 : créer le Port d’envoi pour le lot de messages](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-send-port-for-the-message-batch.md).