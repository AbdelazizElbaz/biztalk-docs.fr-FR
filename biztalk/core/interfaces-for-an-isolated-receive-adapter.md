---
title: "Interfaces pour un hôte isolé adaptateur de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c6b195e-76bf-4c3e-a324-5513bc24fed1
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7848e5c808ad2e7517d0e850e449f8a8575ec5da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-an-isolated-receive-adapter"></a>Interfaces pour adaptateur de réception isolé
Les adaptateurs de réception isolés sont hébergés dans un processus autre que le processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour interagir avec le moteur de messagerie, un adaptateur de réception isolé s'inscrit lui-même au démarrage, de sorte à être configuré et contrôlé par le moteur. L’adaptateur crée le proxy de transport, recherche l’interface **IBTTransportProxy**et les appels **IBTTransportProxy.RegisterIsolatedReceiver** pour inscrire son  **IBTTransportConfig** interface de rappel avec le moteur de messagerie. Cet appel synchrone a lieu avant que l'adaptateur n'envoie son premier message à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cela permet au moteur de messagerie d'effectuer un rappel dans l'adaptateur et d'indiquer les points de terminaison actifs devant être écoutés pour les messages entrants. Les adaptateurs isolés doivent implémenter les interfaces suivantes :  
  
-   **IBTTransport**  
  
-   **IBTTransportConfig**  
  
-   **IBaseComponent**  
  
-   **IPersistPropertyBag**  
  
 L'inscription de l'adaptateur implique que l'adaptateur envoie un emplacement de réception configuré et activé. Le processus hôte de l'adaptateur doit être membre du groupe Utilisateurs d'hôtes BizTalk isolés. En outre, l'adaptateur est interrogé afin de vérifier qu'il dispose de l'ID de classe approprié et qu'il s'exécute sur l'ordinateur qui a été configuré pour cette instance d'hôte.  
  
 Une fois que l’adaptateur est inscrit auprès du proxy de transport, le moteur de messagerie transmet les informations de configuration et les autres emplacements à l’adaptateur de réception en appelant le **charge** méthode de la  **IPersistPropertyBag** interface et **AddReceiveEndpoint** méthode de la **IBTTransportConfig** respectivement l’interface.  
  
 Lors de la réception isolé adaptateur termine le traitement des messages et va être arrêté, il doit appeler la **TerminateIsolatedReceiver** méthode de la **IBTTransportProxy** interface.  
  
 L'illustration suivante montre les interactions d'objets impliquées dans la création d'un adaptateur de réception isolé.  
  
 ![](../core/media/ebiz-sdk-devadapter9.gif "ebiz_sdk_devadapter9")  
Workflow d'initialisation d'un adaptateur de réception isolé  
  
> [!NOTE]
>  Il est préférable que l'adaptateur effectue un suivi des requêtes en cours d'exécution vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L’adaptateur doit bloquer la **Terminate** méthode jusqu'à ce que le nombre de tâches a atteint zéro. Au niveau de la réception, cela inclut les demandes en suspens qui n'ont pas été publiées dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Notez que les messages de réponse ne sont généralement pas remises à un adaptateur de réception après **Terminate** est appelée. En règle générale, une fois l’adaptateur appelle la **Terminate** méthode, le moteur de messagerie n’accepte pas les demandes de publication des nouveaux messages, à l’exception des messages de réponse des paires sollicitation-réponse.  
  
> [!NOTE]
>  Un processus peut héberger plusieurs instances d'adaptateurs isolés, mais un seul processus peut héberger un adaptateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’adaptateur](../core/adapter-variables.md)   
 [Développement d’un adaptateur de réception](../core/developing-a-receive-adapter.md)   
 [Instanciation et initialisation un adaptateur de réception](../core/instantiating-and-initializing-a-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour In-Process](../core/interfaces-for-an-in-process-receive-adapter.md)   
 [Interfaces pour un lot pris en charge par l’adaptateur de réception](../core/interfaces-for-a-batch-supported-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour un transactionnel pris en charge par lot](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour une demande-réponse synchrone](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)