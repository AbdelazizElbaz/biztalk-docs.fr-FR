---
title: "La gestion avec l’adaptateur MSMQ de transaction | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, transaction handling
- transactions, MSMQ adapters
ms.assetid: 2e5dd0da-3852-48bf-9372-b019ecab23be
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bea79413042ec99cfd1cbc5bc6dee500aef4ac4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="transaction-handling-with-the-msmq-adapter"></a>La gestion avec l’adaptateur MSMQ de transaction
Cette section traite de la manière dont les transactions fonctionnent en réception et en envoi.  
  
> [!NOTE]
>  Pour l'adaptateur MSMQ, une transaction s'étend de la base de données MessageBox BizTalk à la file d'attente Message Queuing locale, même si vous utilisez une file d'attente distante.  
  
 Vous pouvez utiliser des transactions sur l'envoi et la réception avec l'adaptateur MSMQ. Sur les envois traités, l'adaptateur accumule les messages jusqu'à obtenir un lot complet. L'adaptateur soumet ensuite le lot au service Message Queuing local comme une transaction unique. En cas d'échec de l'opération, l'adaptateur réessaie de soumettre le lot. Si la nouvelle tentative échoue, l'adaptateur passe au transport secondaire.  
  
> [!NOTE]
>  L'adaptateur prend en charge les lectures transactionnelles des files d'attente distantes uniquement avec Message Queuing 4.0 ou une version ultérieure. Dans ce scénario BizTalk Server et le serveur Message Queuing distant doivent exécuter Message Queuing 4.0 ou version ultérieure.  
  
 Sur les réceptions traitées, l'adaptateur suspend les messages ayant échoué de façon à n'en perdre aucun. Au cours d'une réception traitée, l'adaptateur ajoute des messages à un lot jusqu'à ce que ce dernier soit complet. Il soumet ensuite le lot :  
  
-   S'il n'y a pas de problème et que le serveur reçoit les messages, l'adaptateur valide la transaction.  
  
-   En cas de problème, l'adaptateur crée un lot faisant partie de la transaction actuelle. Il déplace ensuite les messages problématiques vers ce nouveau lot. Puis, il soumet à nouveau le premier lot et envoie le nouveau lot en tant que lot de messages suspendus. L'adaptateur valide la transaction si cette nouvelle soumission ne génère pas de problème.  
  
 Si vous exécutez un gestionnaire d'envoi d'adaptateur MSMQ dans une instance de l'hôte BizTalk en cluster, vous devez mettre en cluster le service MSMQ dans le même groupe de clusters pour garantir la cohérence transactionnelle.  
  
 Si l'« accès DTC réseau » est désactivé dans l'utilitaire DCOMCNFG, une opération de réception distante transactionnelle de MSMQ échoue en générant un message d'erreur chiffré.  Pour opérer une réception distante transactionnelle avec l'adaptateur MSMQ, l'« accès DTC réseau » doit être activé. Plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=124623](http://go.microsoft.com/fwlink/?LinkId=124623).  
  
 Si vous exécutez un gestionnaire de réception d'adaptateur MSMQ dans une instance de l'hôte BizTalk en cluster, vous devez mettre en cluster le service MSMQ dans le même groupe de clusters de façon à prendre en charge les lectures traitées locales, car MSMQ ne prend pas en charge les lectures transactionnelles distantes. Pour plus d’informations sur l’exécution des gestionnaires d’adaptateur MSMQ dans une instance en cluster d’un hôte BizTalk, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution dans un cluster hôte](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie sécurisée à l’aide de l’adaptateur MSMQ](../core/reliable-messaging-with-the-msmq-adapter.md)