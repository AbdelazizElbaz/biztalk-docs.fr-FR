---
title: Interfaces pour un envoi asynchrone adaptateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a214716-8f39-400d-a111-ba1b92a284b4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db156f5a95a088ae706bb2b1c801d8dee89cdece
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-an-asynchronous-send-adapter"></a>Interfaces pour un adaptateur d'envoi asynchrone
Les adaptateurs qui envoient les messages un par un peuvent les envoyer de manière synchrone ou asynchrone. Un adaptateur envoie les messages de manière asynchrone s'il ne bloque pas le thread du proxy de transport mais qu'il utilise à la place un thread distinct pour les opérations d'envoi. Pour pouvoir envoyer les messages de manière asynchrone, l'adaptateur doit implémenter les interfaces suivantes :  
  
-   **IBTTransport**  
  
-   **IBaseComponent**  
  
-   **IBTTransportControl**  
  
-   **IPersistPropertyBag**  
  
-   **IBTTransmitter**  
  
 Les étapes suivantes décrivent la séquence d'actions effectuée par un adaptateur d'envoi afin de transmettre les messages à partir du serveur à la demande du moteur de messagerie.  
  
1.  Le moteur de messagerie utilise le proxy de transport pour transmettre un message sortant à un adaptateur d’envoi en appelant le **TransmitMessage** méthode de la **IBTTransmitter** interface.  
  
2.  L’adaptateur retourne immédiatement à partir de **TransmitMessage** après avoir stocké le message à envoyer à une file d’attente interne et retourne `False` pour **bDeleteMessage**. Ceci indique au moteur de messagerie que le message sera transmis de manière asynchrone.  
  
3.  L'adaptateur envoie le message en utilisant sa propre réserve de threads.  
  
4.  Une fois l'opération d'envoi terminée, l'adaptateur supprime le message d'origine de la base de données MessageBox. Il obtient un lot du moteur de messagerie en utilisant le **IBTTransportBatch.GetBatch** méthode de proxy de transport, puis appelle **DeleteMessage**.  
  
     Le schéma ci-dessous indique les interactions d'objets impliquées dans la création d'un adaptateur d'envoi asynchrone.  
  
     ![](../core/media/ebiz-sdk-devadapter5.gif "ebiz_sdk_devadapter5")  
Workflow pour l'envoi d'un message de manière asynchrone  
  
> [!NOTE]
>  Nous recommandons que l'adaptateur conserve le décompte du nombre de messages en cours de traitement. L’adaptateur doit bloquer la **Terminate** méthode jusqu'à ce que le nombre de messages a atteint zéro. Pour les adaptateurs d’envoi, les messages sont en cours de traitement doivent être gérées correctement. Cela signifie que tout message correctement remis de manière asynchrone doit être supprimé de la file d'attente de messages de l'application privée de l'adaptateur afin d'éviter que les messages ne soient envoyés deux fois. En général, après avoir **Terminate** est appelée par le moteur de messagerie, il n’accepte pas les demandes de publication des nouveaux messages à partir de l’adaptateur. La seule exception à cette règle concerne les messages de réponse liés aux paires sollicitation-réponse.  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’adaptateur](../core/adapter-variables.md)   
 [Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md)   
 [Instanciation et initialisation d’un adaptateur d’envoi](../core/instantiating-and-initializing-a-send-adapter.md)   
 [Interfaces pour un envoi synchrone adaptateur](../core/interfaces-for-a-synchronous-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi synchrone de lot est pris en charge](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi asynchrone de lot est pris en charge](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md)   
 [Interfaces pour un adaptateur d’envoi de lot est pris en charge asynchrone transactionnelle](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)   
 [Adaptateur d’envoi des interfaces pour une type sollicitation-réponse](../core/interfaces-for-a-solicit-response-send-adapter.md)