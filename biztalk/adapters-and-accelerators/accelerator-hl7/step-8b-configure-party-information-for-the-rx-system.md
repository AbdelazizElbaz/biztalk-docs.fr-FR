---
title: "Étape 8 : configurer les informations de tiers pour le système RX | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0b34ec9-220d-4a6b-9712-54c8099b663b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ce204ed2e892a6206f6e2db28bbccd0201e2f0f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-8b-configure-party-information-for-the-rx-system"></a>Étape 8 : configurer les informations de tiers pour le système RX
Dans cette étape, vous configurez les informations de tiers pour le système RX.  
  
### <a name="to-configure-the-rx-system-party-information"></a>Pour configurer les informations de tiers RX système  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
2.  Dans la boîte de dialogue Propriétés du tiers dans le **nom** , tapez **Tutorial_RXSystem**.  
  
3.  Dans l’arborescence de la console, cliquez sur **Ports d’envoi**.  
  
4.  Dans le volet Ports d’envoi, cliquez sur le champ vide dans le **nom** colonne, sélectionnez **Tutorial_sendMsg_RX**, puis cliquez sur **OK**.  
  
5.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator pour HL7**, puis cliquez sur  **BTAHL7 L’Explorateur de Configuration**.  
  
6.  Dans l’Explorateur de Configuration BTAHL7, sélectionnez le **MSH carte** onglet, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**MSH3**|Type **BTAHL7** dans la zone de texte de gauche.|  
    |**MSH5**|Type **Tutorial_RXSystem** dans la zone de texte de gauche.|  
  
7.  Cliquez sur **enregistrer**, puis fermez l’Explorateur de Configuration BTAHL7.  
  
 Passez à [étape 8C : configurer les informations de tiers pour le système HI](../../adapters-and-accelerators/accelerator-hl7/step-8c-configure-party-information-for-the-hi-system.md).