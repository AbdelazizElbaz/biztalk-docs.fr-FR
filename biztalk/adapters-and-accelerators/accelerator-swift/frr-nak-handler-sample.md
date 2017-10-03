---
title: Exemple de gestionnaire FRR NAK | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, NAKs
- examples, FRR
- NAKs
- acknowledgements
- FRR, examples
- examples, FRR NAK handler
ms.assetid: be992507-ba8c-461f-a563-f1d7b2ab221d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a3881b8bcf4b62af7653ef6214b4fccdf8402d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-nak-handler-sample"></a>Exemple de gestionnaire FRR NAK
L’exemple de gestionnaire de NAK FRR montre comment créer un gestionnaire personnalisé pour traiter les messages rapprochement de réponse de FIN (FRR) a mis en corrélation avec les réponses SWIFT. Ce gestionnaire personnalisé traite les messages qui FRR a mis en corrélation avec un message MTS21_FIN_ACKNAK-accusé de réception négatif, ce qui indique que SWIFT n’a pas été reçu le message d’A4SWIFT. Le gestionnaire personnalisé ajoute un objet d’erreur pour le message, en rendant un message en deux parties, un message et promeut les propriétés qui provoquent l’orchestration de réparation de message récupérer le message. Par conséquent, un réparateur peut résoudre le message et le renvoyer à l’accès de Alliance SWIFT (SAA).  
  
 **Exemples de composants**  
  
 L’exemple de gestionnaire de NAK FRR inclut les composants suivants :  
  
-   **RepairSWIFTRejectedMessage.odx.** Cette orchestration est le gestionnaire personnalisé qui traite un message SWIFT n'a pas reçu, routage à l’orchestration de réparation de message pour un réparateur peut corriger et renvoyer le message.  
  
-   **RepairSWIFTRejectedMessage.btproj.** Ce projet comprend RepairSWIFTRejectedMessage.odx et les références requises pour le projet pour générer et déployer.  
  
-   **RepairSWIFTRejectedMessage.sln.** Cette solution inclut le projet RepairSWIFTRejectedMessage.btproj.  
  
 Contenu de cette section :  
  
-   [Implémentation de l’exemple de gestionnaire FRR NAK](../../adapters-and-accelerators/accelerator-swift/implementing-the-frr-nak-handler-sample.md)  
  
-   [Fonctionne de l’exemple de gestionnaire FRR NAK](../../adapters-and-accelerators/accelerator-swift/how-the-frr-nak-handler-sample-works.md)  
  
