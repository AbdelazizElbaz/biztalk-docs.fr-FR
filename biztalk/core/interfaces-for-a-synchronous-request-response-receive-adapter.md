---
title: "Interfaces pour une demande-réponse synchrone adaptateur de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0c60832-52b5-4d2c-81ec-94c46c375b15
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9abd84bab5da623c2dff61c6e07a5898110588af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-synchronous-request-response-receive-adapter"></a>Interfaces pour adaptateur de réception synchrone de type requête-réponse
Tous les adaptateurs de réception doivent implémenter les interfaces suivantes pour fonctionner en mode de requête-réponse :  
  
-   **IBTTransport**  
  
-   **IBTTransportControl** (adaptateurs normaux uniquement)  
  
-   **IBTTransportConfig**  
  
-   **IBaseComponent**  
  
-   **IPersistPropertyBag**  
  
-   **IBTBatchCallBack**  
  
-   **IBTTransmitter**  
  
 Les adaptateurs de réception qui prennent en charge les protocoles de requête-réponse (l'adaptateur de réception HTTP par exemple) effectuent les opérations suivantes lorsqu'ils envoient des messages de requête :  
  
1.  L'adaptateur de réception reçoit les messages de requête entrants. Il obtient un lot du proxy de transport en appelant le **GetBatch** méthode de la **IBTTransportProxy** interface. Dans cet appel, l’adaptateur transmet un pointeur de rappel à son implémentation de la **IBTBatchCallBack.BatchComplete** (méthode).  
  
2.  L’adaptateur ajoute les messages de demande dans le lot en appelant le **SubmitRequestMessage** méthode de la **IBTTransportBatch** interface, une fois pour chaque message de demande.  
  
3.  Lorsque tous les messages ont été ajoutés, l’adaptateur appelle la **fait**méthode de la **IBTTransportBatch** interface, qui envoie le lot au moteur de messagerie via le proxy de transport.  
  
4.  Une fois que le lot a été traité, le moteur de messagerie appelle l’adaptateur **IBTBatchCallBack.BatchComplete** méthode de rappel via le proxy de transport. L'état de l'envoi est transmis à l'adaptateur sous forme de tableau de valeurs HRESULT correspondant à chaque message du lot. Si le lot échoue, que ce soit dans le pipeline ou dans l'orchestration, le message d'erreur SOAP est retourné à l'adaptateur en réponse.  
  
5.  Les messages de requête entrants sont susceptibles d'avoir des abonnés à l'orchestration. Une fois que l’orchestration terminée et le message de demande a été traité, le moteur de messagerie envoie le message de réponse via le proxy de transport à l’adaptateur en appelant l’adaptateur **TransmitMessage** à partir de la (méthode) **IBTTransmitter** interface.  
  
6.  L'adaptateur envoie un message de réponse et supprime le message d'origine de la base de données MessageBox.  
  
 Le schéma ci-dessous indique les interactions d'objets impliquées dans la création d'un adaptateur de réception synchrone de type requête-réponse.  
  
 ![](../core/media/ebiz-sdk-devadapter3.gif "ebiz_sdk_devadapter3")  
Workflow d'un adaptateur de réception envoyant un message synchrone  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’adaptateur](../core/adapter-variables.md)   
 [Développement d’un adaptateur de réception](../core/developing-a-receive-adapter.md)   
 [Instanciation et initialisation un adaptateur de réception](../core/instantiating-and-initializing-a-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour In-Process](../core/interfaces-for-an-in-process-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour un hôte isolé](../core/interfaces-for-an-isolated-receive-adapter.md)   
 [Interfaces pour un lot pris en charge par l’adaptateur de réception](../core/interfaces-for-a-batch-supported-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour un transactionnel pris en charge par lot](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md)