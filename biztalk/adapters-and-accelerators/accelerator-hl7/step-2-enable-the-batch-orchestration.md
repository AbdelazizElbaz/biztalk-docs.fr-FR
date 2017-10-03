---
title: "Étape 2 : Activer l’Orchestration de traitement par lots | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4badf807-f461-4d0a-a3b6-9f671e580d91
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f8b18e41aacf61ac4e55e1c8047e9685179656a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-enable-the-batch-orchestration"></a>Étape 2 : Activer l’Orchestration de traitement par lots
L’orchestration de traitement par lots contrôle le traitement par lots de créer. Conserve les références pour tous les messages à inclure dans le lot, contrôle de la transaction par lot sortant, génère le message du lot, achemine le lot sortant et traite les lots d’accusé de réception entrant. Vous devez inscrire l’orchestration de traitement par lots pour le traitement par lots de créer fonctionner.  
  
### <a name="to-enable-the-batch-orchestration"></a>Pour activer l’orchestration de traitement par lots  
  
1.  Dans la Console Administration de BizTalk, cliquez sur **Orchestrations**, avec le bouton droit **BatchOrchestration.Orchestration_1**, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue Propriétés d’Orchestration dans l’arborescence de la console, cliquez sur **liaisons**.  
  
3.  Dans le **liaisons** volet, pour **hôte**, sélectionnez **BizTalkServerApplication**. Cliquez sur **OK**.  
  
4.  Dans la Console Administration de BizTalk, cliquez sur **BatchOrchestration.Orchestration_1**, puis cliquez sur **Enlist**.  
  
 Passez à [étape 3 : créer et configurer un tiers de Destination](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-configure-a-destination-party.md).