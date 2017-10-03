---
title: "Adaptateur d’envoi de lot est pris en charge des interfaces pour synchrone | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b191c41-ca4f-4d2b-bd15-a93ad87a743d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ab61fd6624468e0464cfe0c648fcc868bd20005
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-synchronous-batch-supported-send-adapter"></a>Interfaces pour un adaptateur d'envoi synchrone pris en charge par lot
Les adaptateurs qui reconnaissent les lots peuvent envoyer des messages de manière synchrone ou asynchrone et effectuer des opérations de traitement des envois. Pour pouvoir envoyer des lots de messages, un adaptateur d'envoi doit implémenter les interfaces suivantes :  
  
-   **IBTTransport**  
  
-   **IBaseComponent**  
  
-   **IBTTransportControl**  
  
-   **IPersistPropertyBag**  
  
-   **IBTBatchTransmitter**  
  
-   **IBTTransmitterBatch**  
  
 Dans le cas de l'envoi synchrone de lot, le moteur de messagerie reçoit un lot de la part de l'adaptateur et ajoute les messages à transmettre à ce lot. Le moteur de messagerie ajoute chaque message au lot et envoie les messages uniquement lorsqu’il appelle le **fait** méthode sur le lot. L’adaptateur retourne `True` pour **bDeleteMessage** pour chaque message transmis de manière synchrone. L’adaptateur doit enregistrer les données du message, par opposition à un pointeur de message, dans son **TransmitMessage** mise en œuvre. Cela est dû au fait que le pointeur du message n'est plus valide une fois la valeur `True` retournée et ne doit pas être réutilisé ni mis en cache pour une utilisation ultérieure.  
  
 Le schéma ci-dessous indique les interactions d'objets impliquées dans la création d'un adaptateur d'envoi synchrone prenant en charge les lots.  
  
 ![](../core/media/ebiz-sdk-devadapter6.gif "ebiz_sdk_devadapter6")  
Workflow pour l'envoi d'un message de manière synchrone  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’adaptateur](../core/adapter-variables.md)   
 [Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md)   
 [Instanciation et initialisation d’un adaptateur d’envoi](../core/instantiating-and-initializing-a-send-adapter.md)   
 [Interfaces pour un envoi synchrone adaptateur](../core/interfaces-for-a-synchronous-send-adapter.md)   
 [Interfaces pour un envoi asynchrone adaptateur](../core/interfaces-for-an-asynchronous-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi asynchrone de lot est pris en charge](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi de lot est pris en charge asynchrone transactionnelle](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)   
 [Adaptateur d’envoi des interfaces pour une type sollicitation-réponse](../core/interfaces-for-a-solicit-response-send-adapter.md)