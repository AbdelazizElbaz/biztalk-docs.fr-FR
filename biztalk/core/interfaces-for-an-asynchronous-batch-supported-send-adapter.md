---
title: "Adaptateur d’envoi de lot est pris en charge des interfaces pour asynchrone | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d38b8b87-508a-499b-86b2-846938050b44
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4af0a5c116c19c4cb1fa728cc016144594f42f13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-an-asynchronous-batch-supported-send-adapter"></a>Interfaces pour un adaptateur d'envoi asynchrone pris en charge par lot
Les adaptateurs qui reconnaissent les lots peuvent envoyer des messages de manière synchrone ou asynchrone, ainsi qu'effectuer des opérations de traitement des envois. Pour pouvoir envoyer des lots de messages, un adaptateur d'envoi doit implémenter les interfaces suivantes :  
  
-   **IBTTransport**  
  
-   **IBaseComponent**  
  
-   **IBTTransportControl**  
  
-   **IPersistPropertyBag**  
  
-   **IBTBatchTransmitter**  
  
-   **IBTTransmitterBatch**  
  
 Dans le cas de l'envoi asynchrone de lot, le moteur de messagerie reçoit un lot de la part de l'adaptateur et ajoute les messages à transmettre à ce lot. Les messages sont envoyés uniquement lorsque le moteur de messagerie appelle la **fait** méthode sur le lot. L'adaptateur retourne `False` pour chaque message transmis de manière asynchrone. L'adaptateur reçoit ensuite un lot de la part du proxy de l'adaptateur et supprime les messages déjà transmis.  
  
 Le schéma ci-dessous indique les interactions d'objets impliquées dans la création d'un adaptateur d'envoi asynchrone prenant en charge les lots.  
  
 ![](../core/media/ebiz-sdk-devadapter7.gif "ebiz_sdk_devadapter7")  
Workflow pour l'envoi d'un message de manière asynchrone  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’adaptateur](../core/adapter-variables.md)   
 [Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md)   
 [Instanciation et initialisation d’un adaptateur d’envoi](../core/instantiating-and-initializing-a-send-adapter.md)   
 [Interfaces pour un envoi synchrone adaptateur](../core/interfaces-for-a-synchronous-send-adapter.md)   
 [Interfaces pour un envoi asynchrone adaptateur](../core/interfaces-for-an-asynchronous-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi synchrone de lot est pris en charge](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi de lot est pris en charge asynchrone transactionnelle](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)   
 [Adaptateur d’envoi des interfaces pour une type sollicitation-réponse](../core/interfaces-for-a-solicit-response-send-adapter.md)