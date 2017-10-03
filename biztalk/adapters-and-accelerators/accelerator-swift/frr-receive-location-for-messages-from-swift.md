---
title: "FRR emplacement de réception pour les Messages à partir de SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, receive locations
- receive locations, FRR
ms.assetid: d15989de-56f9-4d62-8394-f4fd6e971495
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d609cfc8c5177581f32ee0957a6a7ae7c1fe9a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-receive-location-for-messages-from-swift"></a>FRR emplacement de réception pour les Messages à partir de SWIFT
Pour activer le rapprochement de réponse FIN (FRR), vous devez configurer un FRR composant de pipeline pour recevoir un message de SAA et la préparer pour le traitement par [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. Le pipeline de réception contient les composants suivants :  
  
-   Le désassembleur SWIFT dans la phase de désassemblage  
  
-   Le composant de pipeline décodeur de FRR SWIFT à l’étape de décodeur  
  
-   Le composant de pipeline Résolution de l’ensemblecorrélations FRR SWIFT dans la phase de résolution de tiers  
  
 Lorsque [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] reçoit une panoramique/NAN, SWIFT FRR décodeur lit la propriété de contexte MQ commentaires pour déterminer si la réponse est un panoramique ou une valeur NAN. Il définit le transport indépendant [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRTransportLevelAck booléen valeurs True pour un panoramique ou la valeur false pour une valeur NAN.  
  
 Le composant de pipeline Résolution de l’ensemblecorrélations SWIFT FRR remplace la propriété du message de réponse FRRCorrelationToken, qui utilise de l’orchestration FRR, avec la valeur dans la MQMD. Propriété de CorrelId.