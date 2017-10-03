---
title: "Propriétés de la messagerie fiable avec l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, properties
- queues, MSMQ adapters
- MSMQ adapters, dead letters
- queues, failures [MSMQ adapters]
- MSMQ adapters, impersonation
- MSMQ adapters, remote queues
- queues
- reliability, MSMQ adapters
- impersonation, MSMQ adapters
- MSMQ adapters, queue failures
- clustering, MSMQ adapters
- queues, remote
- MSMQ adapters, reliability
- MSMQ adapters, clustering
ms.assetid: 34bfe028-b2aa-4816-a437-3679d19dffb2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49aebf12c86ae72d5dcb224d078c62afefcb8f46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="properties-for-reliable-messaging-with-the-msmq-adapter"></a>Propriétés de la messagerie fiable avec l’adaptateur MSMQ
La fiabilité de l'envoi et de la réception de messages via l'adaptateur MSMQ peut être améliorée selon la manière dont vous configurez ce dernier. Cette rubrique traite de l'utilisation de plusieurs propriétés de configuration pour garantir la fiabilité de la messagerie.  
  
## <a name="running-msmq-adapter-handlers-within-a-clustered-biztalk-host"></a>Exécution des gestionnaires d'adaptateur MSMQ au sein d'un hôte BizTalk en cluster  
 Une approche de haute disponibilité consiste à exécuter simultanément des gestionnaires de l'adaptateur dans plusieurs instances de l'hôte et sur plusieurs serveurs BizTalk. Toutefois, il n'est pas recommandé d'employer cette méthode avec les gestionnaires de l'adaptateur MSMQ, car MSMQ ne prend pas en charge les opérations de lectures traitées distantes et car le gestionnaire d'envoi MSMQ conserve une dépendance vis à vis de l'instance du service MSMQ exécutée localement. Pour obtenir des gestionnaires d'envoi et de réception MSMQ haute disponibilité, il est recommandé d'exécuter les gestionnaires de l'adaptateur MSMQ dans une instance d'hôte BizTalk mise en cluster. Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  
  
## <a name="queue-failure-and-the-dead-letter-queue"></a>Échec de la file d'attente et file d'attente de messages non distribués  
 Après l'envoi d'un message, aucune erreur n'est générée pour indiquer aux messages suivants que la file d'attente de réception est désactivée ou a été supprimée. Une telle situation peut entraîner la perte de messages.  
  
 Définition de la **file d’attente de lettres mortes utilisation** propriété configuration **True** vous empêche de perdre des messages. Lorsque la propriété a la valeur `True`, les messages que la file d'attente ne reçoit pas sont placés dans la file d'attente des messages non distribués.  
  
## <a name="impersonation-and-remote-queues"></a>Emprunt d'identité et files d'attente distantes  
 Vous devez également définir le **file d’attente de lettres mortes utiliser** propriété configuration **True** lorsque vous utilisez des files d’attente distantes. Si l'adaptateur pour MSMQ emprunte l'identité d'un utilisateur sans disposer de l'autorisation pour utiliser la file d'attente, le message risque d'être perdu.  
  
 Lorsque la propriété est **True** et l’utilisateur représenté ne dispose pas d’autorisation d’utiliser la file d’attente distante, il est placé dans la file d’attente de lettres mortes sur l’ordinateur local ou distant. Dans le cas d'un envoi transactionnel, le message est placé dans la file d'attente des messages non distribués de l'ordinateur local. Dans le cas d'un envoi non transactionnel, il est placé dans celle de l'ordinateur distant.  
  
## <a name="recoverable-and-use-journal-queue-properties"></a>Propriétés Récupérable et Utiliser file d'attente journal  
 Les deux le **récupérable** et **file d’attente du Journal utilisation** propriétés enregistrent des copies des messages envoyés. Pour plus d’informations sur ces propriétés, consultez [comment configurer un emplacement de réception MSMQ](../core/how-to-configure-an-msmq-receive-location.md) et [comment configurer un Port d’envoi MSMQ](../core/how-to-configure-an-msmq-send-port.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie fiable avec l’adaptateur MSMQ](../core/reliable-messaging-with-the-msmq-adapter.md)   
 [Considérations pour l’exécution des gestionnaires d’adaptateur au sein d’un hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)