---
title: "Interfaces pour un adaptateur d’envoi de lot est pris en charge asynchrone transactionnelle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b2dbdf-e6ba-4b58-a0a5-fc78feaf5c35
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 948000883c092c8e247b1d4f41fb2bc7e2280e40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter"></a>Interfaces pour un adaptateur d'envoi asynchrone transactionnel pris en charge par lot
Un adaptateur d'envoi peut créer et contrôler des transactions lorsque la transmission transactionnelle des messages est requise. Pour prendre en charge l'envoi transactionnel, l'adaptateur doit implémenter les interfaces suivantes :  
  
-   **IBTTransport**  
  
-   **IBaseComponent**  
  
-   **IBTTransportControl**  
  
-   **IPersistPropertyBag**  
  
-   **IBTBatchTransmitter**  
  
-   **IBTTransmitterBatch**  
  
-   **IBTBatchCallBack**  
  
 Un adaptateur crée une transaction MSDTC et retourne un pointeur vers cet objet dans l’appel à la **BeginBatch** méthode de la **IBTTransmitterBatch** interface. Le moteur de messagerie appelle cette méthode pour obtenir un lot grâce auquel il envoie les messages sortants vers l'adaptateur d'envoi. Lorsque l’adaptateur termine l’opération d’envoi et valide ou annule une transaction, il notifie le moteur de messagerie du résultat de la transaction à l’aide de la **DTCCommitConfirm** méthode de la **IBTDTCCommitConfirm**  interface.  
  
 L'illustration suivante indique l'interaction entre le proxy de transport et l'adaptateur d'envoi lors d'une opération d'envoi transactionnel.  
  
 ![](../core/media/ebiz-sdk-devadapter8.gif "ebiz_sdk_devadapter8")  
Workflow pour l'envoi d'un message transactionnel de manière asynchrone  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’adaptateur](../core/adapter-variables.md)   
 [Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md)   
 [Instanciation et initialisation d’un adaptateur d’envoi](../core/instantiating-and-initializing-a-send-adapter.md)   
 [Interfaces pour un envoi synchrone adaptateur](../core/interfaces-for-a-synchronous-send-adapter.md)   
 [Interfaces pour un envoi asynchrone adaptateur](../core/interfaces-for-an-asynchronous-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi synchrone de lot est pris en charge](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi asynchrone de lot est pris en charge](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md)   
 [Adaptateur d’envoi des interfaces pour une type sollicitation-réponse](../core/interfaces-for-a-solicit-response-send-adapter.md)