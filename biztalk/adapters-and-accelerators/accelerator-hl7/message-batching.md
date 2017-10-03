---
title: Le traitement par lot des messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching
- batching, about batching
- messages, batching
- batching, messages
ms.assetid: d852cf00-3882-4f0f-a4c3-2a39483710ee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 849f14113d5a5e4776c303ef7a5ea4e1e50a552b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-batching"></a>Le traitement par lots du message
La nécessité de messages par lot peuvent encourager les normes des protocoles, les problèmes de planification ou les limitations de taille de message. Un lot de contrôle d’intégrité au niveau sept (HL7) se compose de messages délimités par un en-tête de lot HL7 et le code de fin du lot. Séparateurs de message séparer les messages individuels dans le lot.  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] message prend en charge les trois suivantes des scénarios de traitement par lot :  
  
-   **Par lot entrant fragmenté**. Dans ce scénario, BTAHL7 reçoit un lot de messages HL7, puis achemine les messages individuels dans le système de destination.  
  
-   **Traitement par lots dans / hors du lot**. Dans ce scénario, BTAHL7 reçoit un lot de messages HL7, vérifie les messages individuels dans le lot et achemine ensuite le lot de messages pour le système de destination.  
  
-   **Créer le lot ou le traitement par lot sortant**. Dans ce scénario, BTAHL7 reçoit des messages individuels et les lots avant de les router vers le système de destination.  
  
    > [!NOTE]
    >  BTAHL7 n’active pas le traitement par lots du message pour le traitement par lot sortant par défaut. Vous devez utiliser l’Explorateur BizTalk pour tout d’abord inscrire l’orchestration de traitement par lots de BTAHL7 et puis démarrer l’orchestration de traitement par lots. Pour plus d’informations sur l’activation du message de traitement par lot, consultez [configuration de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Par lot entrant fragmenté](../../adapters-and-accelerators/accelerator-hl7/fragmented-inbound-batch.md)  
  
-   [Configurer le traitement par lot](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)  
  
-   [Planification de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/scheduling-batching.md)  
  
-   [Configuration des accusés de réception de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/configuring-batching-acknowledgments.md)