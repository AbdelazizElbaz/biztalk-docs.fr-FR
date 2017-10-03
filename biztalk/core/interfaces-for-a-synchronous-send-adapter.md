---
title: Interfaces pour un envoi synchrone adaptateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e1b397a-3a35-4447-8522-d8a5f39a42d7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1012b52bf5c6ab564cc219926b97445e43f60dd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-synchronous-send-adapter"></a>Interfaces pour un adaptateur d'envoi synchrone
Un adaptateur envoie les messages de manière synchrone lorsqu'il bloque le thread appelant du moteur de messagerie tout en effectuant son opération d'envoi. Pour pouvoir envoyer les messages de manière synchrone, l'adaptateur doit implémenter les interfaces suivantes :  
  
-   **IBTTransport**  
  
-   **IBaseComponent**  
  
-   **IBTTransportControl**  
  
-   **IPersistPropertyBag**  
  
-   **IBTTransmitter**  
  
 Dans un envoi synchrone, l’adaptateur envoie le message tout en bloquant **TransmitMessage**, et après le retour de la transmission réussie`True.`  
  
 Le schéma ci-dessous indique les interactions d'objets impliquées dans la création d'un adaptateur d'envoi synchrone.  
  
 ![](../core/media/ebiz-sdk-devadapter4.gif "ebiz_sdk_devadapter4")  
Flux de travail pour envoyer un message de façon synchrone  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’adaptateur](../core/adapter-variables.md)   
 [Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md)   
 [Instanciation et initialisation d’un adaptateur d’envoi](../core/instantiating-and-initializing-a-send-adapter.md)   
 [Interfaces pour un envoi asynchrone adaptateur](../core/interfaces-for-an-asynchronous-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi synchrone de lot est pris en charge](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi asynchrone de lot est pris en charge](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi de lot est pris en charge asynchrone transactionnelle](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)   
 [Adaptateur d’envoi des interfaces pour une type sollicitation-réponse](../core/interfaces-for-a-solicit-response-send-adapter.md)