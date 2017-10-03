---
title: "Adaptateur de réception des interfaces pour une prise en charge de traitement par lots | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5289e8b8-4447-4196-9f7c-5e60c6598d8d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27b51a67f63f3088ce64c9db35c368289ce156d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-transactional-batch-supported-receive-adapter"></a>Interfaces pour un adaptateur de réception transactionnel pris en charge par lot
Un adaptateur de réception crée et contrôle les transactions lorsque l'envoi transactionnel des messages est requis.  
  
 Réception transactionnel adaptateur crée et passe un pointeur à une transaction Microsoft Distributed Transaction Coordinator (MSDTC) le **fait** méthode de la **IBTTransportBatch** interface. Ce faisant, toutes les opérations de traitement par lot sont réalisées dans l'étendue de cet objet transaction spécifique. Lorsque l'envoi du lot est terminé, la méthode de rappel de l'adaptateur valide ou annule la transaction. L'action ensuite réalisée dépend de l'état renvoyé par le proxy de transport, et éventuellement d'autres travaux associés à la transaction réalisés par l'adaptateur et non visibles pour le proxy de transport. L'adaptateur détermine si la transaction est un échec ou un succès. L’adaptateur renvoie le résultat de la transaction (commit ou rollback) pour le proxy de transport à l’aide de la **DTCCommitConfirm** méthode de la**IBTDTCCommitConfirm** interface. Il transmet la valeur `true` en cas de succès de la transaction ou la valeur `false` en cas d'échec.  
  
 L'illustration suivante indique les interactions d'objets impliquées dans la création d'un adaptateur de réception transactionnel pris en charge par lot.  
  
 ![](../core/media/ebiz-sdk-devadapter2.gif "ebiz_sdk_devadapter2")  
Workflow d'un adaptateur de réception envoyant un lot de messages à l'aide de transactions DTC  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’adaptateur](../core/adapter-variables.md)   
 [Développement d’un adaptateur de réception](../core/developing-a-receive-adapter.md)   
 [Instanciation et initialisation un adaptateur de réception](../core/instantiating-and-initializing-a-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour In-Process](../core/interfaces-for-an-in-process-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour un hôte isolé](../core/interfaces-for-an-isolated-receive-adapter.md)   
 [Interfaces pour un lot pris en charge par l’adaptateur de réception](../core/interfaces-for-a-batch-supported-receive-adapter.md)   
 [Adaptateur de réception des interfaces pour une demande-réponse synchrone](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)