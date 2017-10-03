---
title: "FRR Port d’envoi de Messages SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, send ports
- send ports, FRR
ms.assetid: 905c69a3-dff3-4a60-803d-dd617ffb6896
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a442b45f57009b839b4e184ef9662b253ba32b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-send-port-for-messages-to-swift"></a>FRR Port d’envoi de Messages SWIFT
Pour activer le rapprochement de réponse FIN (FRR), vous devez configurer un port d’envoi FRR qui envoie un message à SAA via l’adaptateur BizTalk pour MQSeries. Cette itinéraires de port d’envoi un message via un FRR personnalisé envoyer composant de pipeline que vous devez créer avec les composants suivants :  
  
-   L’assembleur SWIFT dans la phase d’assemblage  
  
-   Le composant de pipeline SWIFTAsmFrrMQSeriesHelper dans la phase de codage  
  
 Le composant de pipeline SWIFTAsmFrrMQSeriesHelper définit la propriété MQMD_MsgID du message sortant à la valeur de la propriété FRRCorrelationToken. Aussi, il assigne et promeut d’autres propriétés de contexte requis commençant par « MQ » avec les valeurs définies au moment du design du pipeline. Le pipeline d’envoi inclut chaque propriété définie pour MQSeries comme une propriété configurable. Chaque valeur par défaut est « Non utilisé ».  
  
 Le port d’envoi traite les messages qui ont [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed == False et [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND == True. Le mécanisme de transport est de l’adaptateur BizTalk pour MQSeries. Pour plus d’informations sur les propriétés de transport, telles que la taille de la fragmentation, consultez la documentation de MQSeries.