---
title: "Étape 8 : configurer les informations de tiers pour le système ADT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0d750c2-a3c6-4571-a4e1-0d0aaaa4d400
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42b92e3b55cd4de181103e28526abf3ecde29412
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-8a-configure-party-information-for-the-adt-system"></a>Étape 8 : configurer les informations de tiers pour le système ADT
Dans cette étape, vous configurez les informations de tiers pour le système ADT.  
  
### <a name="to-configure-the-adt-system-party-information"></a>Pour configurer les informations de tiers ADT système  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.  
  
2.  Dans la boîte de dialogue Propriétés du tiers dans le **nom** , tapez **Tutorial_ADTSystem**. (La valeur que vous tapez dans cette zone est à partir de l’instance de message HL7 d’origine, ADT^A03.txt MSH3.)  
  
3.  Dans l’arborescence de la console, cliquez sur **Ports d’envoi**.  
  
4.  Dans le volet Ports d’envoi, cliquez sur le champ vide dans le **nom** colonne, sélectionnez **Tutorial_sendAck_ADT**, puis cliquez sur **OK**.  
  
5.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator pour HL7**, puis cliquez sur  **BTAHL7 L’Explorateur de Configuration**.  
  
6.  Dans l’Explorateur de Configuration BTAHL7, sélectionnez le **accusé de réception** onglet. Pour **type d’accusé de réception**, sélectionnez **EnhancedMode**.  
  
7.  Cliquez sur **enregistrer**, puis fermez l’Explorateur de Configuration BTAHL7.  
  
 Passez à [étape 8 : configurer les informations de tiers pour le système RX](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-rx-system.md).