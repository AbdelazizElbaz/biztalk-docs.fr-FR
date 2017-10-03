---
title: "FRR des Ports d’envoi des Messages aux gestionnaires personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, send ports
- custom handlers
- FRR, custom handlers
- send ports, FRR
- send ports, custom handlers
ms.assetid: 486d7410-fde1-4a9b-a9c2-64c1ed85ebc0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6babc312ddad7d77a96e29bc9e59ec9298aa6ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-send-ports-for-messages-to-the-custom-handlers"></a>FRR des Ports d’envoi des Messages aux gestionnaires personnalisés
Pour activer des gestionnaires personnalisés pour FRR, vous devez créer une série de ports d’envoi FRR, chacun d’eux qui achemine une copie d’un message d’origine d’un certain type aux gestionnaires personnalisés. Ces ports d’envoi doivent doivent les composants suivants :  
  
-   L’assembleur SWIFT dans la phase d’assemblage  
  
-   Le composant de pipeline SWIFTSendFrrComponent dans la phase de codage  
  
 Pour tous les messages à l’exception des messages SWIFT FIN catégorie 0 à 9 qui ne sont pas envoyés avec succès, le port d’envoi doit avoir les filtres suivants :  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SendingServiceType == [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService  
  
-   BIZTALK SERVER. La valeur requise pour chaque type de message de l’opération. Les valeurs possibles pour le BTS. Propriété de l’opération, consultez le tableau dans [créer les Ports d’envoi FRR à envoyer aux gestionnaires personnalisé](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).  
  
 Pour les messages de la catégorie de 0 à 9 SWIFT FIN qui ne sont pas envoyés avec succès, le port d’envoi doit avoir les filtres suivants :  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SendingServiceTyp ==[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrFailed == true  
  
-   BIZTALK SERVER. Opération ==[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendMTMsg  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason défini sur la valeur requise pour chaque type de message. Les valeurs possibles pour le BTS. Propriété de l’opération, consultez le tableau dans [créer les Ports d’envoi FRR à envoyer aux gestionnaires personnalisé](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).