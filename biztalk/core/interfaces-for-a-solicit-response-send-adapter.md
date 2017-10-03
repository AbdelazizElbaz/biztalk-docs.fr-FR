---
title: "Adaptateur d’envoi des interfaces pour une type sollicitation-réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c54650e8-dbfb-4c66-843b-0b82c8183dd4
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb8ce9b625bfea144f9a4a615a604efdbe2a3cb1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-solicit-response-send-adapter"></a>Interfaces pour un adaptateur d'envoi de sollicitation-réponse
Les adaptateurs d'envoi utilisent le même mécanisme de lot que les adaptateurs de réception pour envoyer les messages de réponse au serveur.  
  
> [!NOTE]
>  Il est recommandé qu'un adaptateur de sollicitation-réponse traite les messages de manière asynchrone. S'il traite les messages de manière synchrone, ces derniers risquent d'être dupliqués.  
  
 Les adaptateurs d'envoi doivent implémenter les interfaces suivantes pour fonctionner en mode de sollicitation-réponse :  
  
-   **IBTTransport**  
  
-   **IBaseComponent**  
  
-   **IBTTransportControl**  
  
-   **IPersistPropertyBag**  
  
-   **IBTTransmitter**  
  
-   **IBTTransmitterBatch** et **IBTBatchTransmitter** (si le traitement par lot d’envoi est requis)  
  
-   **IBTBatchCallBack**  
  
 Les étapes de l'interaction des objets sont les suivantes :  
  
1.  Une fois que l'adaptateur a envoyé un message de sollicitation, il reçoit en retour un message de réponse du serveur de destination. Il obtient alors un lot du proxy de transport.  
  
2.  L’adaptateur ajoute le message de réponse au lot en appelant **IBTTransportProxy::SubmitResponseMessage**.  
  
3.  L’adaptateur envoie le lot en appelant **IBTTransportProxy::Done** en passant un pointeur vers son **IBTBatchComplete** interface pour le rappel du moteur de messagerie.  
  
4.  Le moteur de messagerie appelle l’adaptateur **IBTBatchCallBack::BatchComplete** méthode de rappel à l’aide du proxy de transport informer du résultat de l’opération d’envoi.  
  
 Le schéma ci-dessous indique les interactions d'objets impliquées dans la création d'un adaptateur d'envoi de sollicitation-réponse.  
  
 ![](../core/media/ebiz-sdk-devadapter13.gif "ebiz_sdk_devadapter13")  
Diagramme d'interaction d'un adaptateur d'envoi de sollicitation-réponse  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’adaptateur](../core/adapter-variables.md)   
 [Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md)   
 [Instanciation et initialisation d’un adaptateur d’envoi](../core/instantiating-and-initializing-a-send-adapter.md)   
 [Interfaces pour un envoi synchrone adaptateur](../core/interfaces-for-a-synchronous-send-adapter.md)   
 [Interfaces pour un envoi asynchrone adaptateur](../core/interfaces-for-an-asynchronous-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi synchrone de lot est pris en charge](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi asynchrone de lot est pris en charge](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi de lot est pris en charge asynchrone transactionnelle](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)