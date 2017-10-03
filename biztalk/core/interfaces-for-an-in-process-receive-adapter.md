---
title: "Adaptateur de réception des interfaces pour In-Process | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ed668d9-7512-4026-a8f3-df05aeed4df6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7135471700cf640f61b56506ad159b5c47c7d877
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-an-in-process-receive-adapter"></a>Interfaces d'un adaptateur de réception In-process
Le moteur de messagerie instancie et configure les adaptateurs In-process, en transmettant le proxy de transport afin de permettre à l'adaptateur d'accéder à sa fonctionnalité. Pour permettre la configuration et la liaison vers le proxy de transport, les adaptateurs doivent implémenter les interfaces de configuration suivantes :  
  
-   **IBTTransport**  
  
-   **IBTTransportControl**  
  
-   **IBTTransportConfig**  
  
-   **IBaseComponent**  
  
 Si vous le souhaitez si l’adaptateur souhaite recevoir des informations de gestionnaire lors de l’initialisation qu’il doit implémenter **IPersistPropertyBag**.  
  
 Le moteur de messagerie crée une instance d'un adaptateur, l'initialise et définit la configuration des emplacements de réception. Le moteur de messagerie transmet un sac de propriétés à une carte le **AddReceiveEndpoint** appel de méthode. Ce jeu de propriétés contient la configuration de l'emplacement et du gestionnaire de réception. La configuration est stockée dans la base de données sous la forme d'un jeu de propriétés XML. Le moteur de messagerie lit les données XML et à partir de ces données, réalimente un jeu de propriétés. Après l'ajout d'au moins un point de terminaison (emplacement de réception), l'adaptateur peut commencer à envoyer des messages.  
  
> [!NOTE]
>  Adaptateurs ne doivent pas empêcher le moteur de messagerie appelle comme **IBTTransportControl.Initialize**, **IPersistPropertyBag.Load**, et **IBTTransportConfig.AddReceiveEndpoint**. Traitement excessif dans ces appels affectera le temps de démarrage du service.  
  
 L'illustration suivante montre les interactions d'objets impliquées dans la création d'un adaptateur de réception in-process.  
  
 ![](../core/media/ebiz-sdk-devadapter11.gif "ebiz_sdk_devadapter11")  
Workflow d'un adaptateur de réception In-process  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’adaptateur](../core/adapter-variables.md)   
 [Développement d’un adaptateur de réception](../core/developing-a-receive-adapter.md)   
 [Instanciation et initialisation un adaptateur de réception](../core/instantiating-and-initializing-a-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour un hôte isolé](../core/interfaces-for-an-isolated-receive-adapter.md)   
 [Interfaces pour un lot pris en charge par l’adaptateur de réception](../core/interfaces-for-a-batch-supported-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour un transactionnel pris en charge par lot](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour une demande-réponse synchrone](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)