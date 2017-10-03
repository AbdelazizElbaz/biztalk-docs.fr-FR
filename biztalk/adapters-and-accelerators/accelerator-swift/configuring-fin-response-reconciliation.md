---
title: "Configuration de rapprochement de réponse FIN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, configuring
- configuring, FIN Response Reconciliation
ms.assetid: dc934530-76ff-4cdb-b182-46f9ea0343b7
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 384a2ea27e3d208864c8b16ec52562e6e1cfa28e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fin-response-reconciliation"></a>Configuration de rapprochement de réponse FIN
Vous devez effectuer les étapes dans les sections suivantes pour configurer le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fonctionnalité rapprochement de réponse de FIN (FRR), comme indiqué dans l’illustration suivante.  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-frr-configuration.jpg "A4SWIFT_FRR_Configuration")  
  
 Dans l’Assistant Installation d’A4SWIFT, vous pouvez choisir d’installer Message Repair et New Submission et FRR, ou Message Repair et New Submission sans FRR ou FRR sans Message Repair et New Submission. Par conséquent, les instructions de cette section ne supposent pas que vous installez et configurez Message Repair et New Submission. Ils, toutefois, supposez que vous avez effectué les étapes décrites dans le [configuration de l’exécution de A4SWIFT](../../adapters-and-accelerators/accelerator-swift/configuring-the-a4swift-runtime.md).  
  
 Contenu de cette section :  
  
-   [Liaison et démarrage de l’Orchestration FRR](../../adapters-and-accelerators/accelerator-swift/binding-and-starting-the-frr-orchestration.md)  
  
-   [Création de la FRR le Pipeline de réception](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-receive-pipeline.md)  
  
-   [Création de la FRR emplacement de réception pour la réception de l’Application Back-End](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-receive-location-for-receiving-from-the-back-end-application.md)  
  
-   [Création de la FRR emplacement de réception pour recevoir des SWIFT](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-receive-location-for-receiving-from-swift.md)  
  
-   [Créer le Pipeline d’envoi FRR](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-pipeline.md)  
  
-   [Création du Port d’envoi FRR pour l’envoi à SWIFT](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-port-for-sending-to-swift.md)  
  
-   [Création de Ports d’envoi pour envoyer aux gestionnaires personnalisés FRR](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)