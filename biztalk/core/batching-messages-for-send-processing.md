---
title: "Traitement par lot des Messages pour le traitement d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d9115ec-13bc-41a8-8928-57b168c95af4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e87600bec54679688fae5084af3b4a1bde9ca807
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batching-messages-for-send-processing"></a>Traitement par lot des messages pour le traitement d'envoi
## <a name="send-adapter-batch-management"></a>Gestion par lots de l'adaptateur d'envoi  
 Lorsque vous utilisez des transactions côté envoi, la même transaction, créée par BizTalk Server et utilisée pour l'envoi vers le système cible, est utilisée pour la suppression du message correspondant une fois qu'il a été envoyé avec succès. En cas d'échec, la transaction peut être interrompue, auquel cas la suppression est annulée et les données demeurent dans BizTalk Server et non dans le système cible. Ceci évite la duplication des messages. Les transactions ne sont prises en charge que pour les adaptateurs d'envoi asynchrones. Vous ne devez pas utiliser de transactions pour les adaptateurs d'envoi synchrones.  
  
 Mais l'adaptateur ne doit pas simplement mettre fin à la transaction; il doit également gérer correctement l'état des messages qui lui ont été donnés. Plus précisément, l’adaptateur doit appeler les méthodes **renvoyer**, **MoveToNextTransport**, et **MoveToSuspendQ** manière appropriée selon le nombre de tentatives et si un transport secondaire n’est disponible.  
  
 Il est important de placer la **supprimer** et **SubmitResponse** opérations ensemble dans un lot qui utilise la même transaction. En cas d'échec, le système met fin à la transaction (afin de garantir que les données ne sont envoyées qu'une seule fois à un système externe). Mais vous souhaitez soumettre à nouveau ou appeler **MoveToNextTransport** pour renvoyer les message à BizTalk Server. Pour ce faire, utilisez un lot normal (non transactionnel) distinct pour ces types d'opérations.  
  
 La figure suivante illustre l'utilisation de lots distincts pour les messages de réponse.  
  
 ![À l’aide d’un lot distinct pour les messages de réponse](../core/media/eawp-seperatebatch.gif "EAWP_SeperateBatch")  
  
## <a name="sorting-the-send-side-transactional-batches-by-endpoint"></a>Tri des lots de transactions côté envoi par point de terminaison  
 Les lots de messages envoyés par BizTalk Server à l'adaptateur peuvent s'étendre sur plusieurs ports d'envoi (ou points de terminaison). Étant donné que l’adaptateur souhaite généralement avoir une transaction à un seul point de terminaison, l’adaptateur doit trier les messages basés sur le port d’envoi (**SPName** ou **OutboundTransportLocation**). En procédant ainsi, il peut créer une transaction qui ne concerne qu'un seul port d'envoi.  
  
 Par exemple, lorsqu'un adaptateur d'envoi FTP reçoit un lot de messages de BizTalk Server, il obtient un lot mixte de messages destinés à tous les ports d'envoi FTP actuellement actifs. Ceci est dû au fait que l'API est basée sur un singleton, ce qui signifie qu'un seul adaptateur FTP est chargé et non un par port d'envoi.  
  
 L'adaptateur doit d'abord trier le lot de messages qui lui a été fourni par BizTalk Server en lots séparés, un par point de terminaison. Ensuite, il peut traiter tour à tour chaque point de terminaison et générer probablement des lots de suppression pour chaque point de terminaison. Les classes réutilisables génériques de BaseAdapter dans l'exemple de code SDK fonctionnent de la même manière.  
  
## <a name="sorting-for-dynamic-send"></a>Tri pour l'envoi dynamique  
 Une orchestration BizTalk Server peut envoyer un message à un port qui n'a pas été configuré, à condition de fournir suffisamment d'informations de configuration dans l'en-tête du message et dans l'URL proprement dite. BizTalk Server doit reconnaître le protocole de l'URL.  
  
 Lors du tri des messages, pensez à établir ce qui définit un point de terminaison. Ceci est particulièrement vrai dans le cas d'un envoi dynamique. Si seule l'URI définit le point de terminaison, les choses sont simples. Toutefois, dans une session FTP, les informations de connexion de l'utilisateur peuvent être utilisées par le serveur FTP pour définir le point de terminaison véritable. Dans ce cas, si l'adaptateur se connecte sous un nom de compte différent, il est possible qu'il soit connecté à un répertoire différent.  
  
 Dans certains cas, le point de terminaison véritable n’est pas connu jusqu'à ce que vous avez exécuté la commande Enterprise Single Sign-On (SSO) **ValidateAndRedeemTicket**.  
  
 Dans le cas de MQSeries, il est possible de configurer l'utilisation ou non de transactions. En fonction de l'architecture et de l'utilisation d'un objet COM+ distant, il est préférable de considérer un point de terminaison transactionnel comme distinct d'un point de terminaison non transactionnel.  
  
 Pour résumer, le tri des messages en lots pour des points de terminaison uniques est parfois une tâche non triviale, qui peut faire intervenir des étapes supplémentaires comme la prise en compte des valeurs de contexte ou même le résultat d'un appel au service d'authentification unique de l'entreprise.  
  
## <a name="sorting-for-static-send"></a>Tri pour l'envoi statique  
 Si le point de terminaison est configuré de manière statique, il existe un GUID unique pour le contexte du message appelé ID de port statique (SPID). Cette valeur peut être utilisée pour le tri du point de terminaison. Vous pouvez utiliser le code suivant pour la récupérer.  
  
```  
string spid = (string)message.Context.Read("SPID", "http://schemas.microsoft.com/BizTalk/2003/system-properties");  
```  
  
 Ceci est pratique si on prend en compte les problèmes introduits par la structure de configuration basée sur la définition de schéma XML (XSD). Avec cette structure, une propriété peut faire partie de la clé du point de terminaison enfouie dans XML, dans une propriété de contexte unique. Si vous disposez d'un SPID sur le contexte, vous pouvez l'utiliser pour le tri du lot. Sinon, vous procédez à un envoi dynamique et vous devez construire une clé alternative qui vous permettra de trier le lot.  
  
 L'illustration suivante montre le tri des messages par point de terminaison.  
  
 ![Tri des messages par point de terminaison](../core/media/eawp-sortbatch.gif "EAWP_SortBatch")  
  
 Rappelez-vous que le nombre de tentatives pour un message n'est pas conscient de la réussite ou de l'échec du lot. Côté envoi, un lot de messages peut échouer car quelques messages du lot ont échoué. L'adaptateur doit effectuer une détermination pour chaque message qu'il reçoit. Dans un scénario de lot en échec, vous pouvez supposer que tous les messages ont été soumis à nouveau. Toutefois, si tous les messages d'un lot en échec sont soumis à nouveau, le nombre de tentatives (qui est géré par le moteur BizTalk Server) est incrémenté à tort pour les messages réussis par ce qu'ils se trouvaient dans le même lot que les messages en échec. Dans cette situation, un adaptateur peut reformer le lot sortant et représenter les messages réussis sur le système externe.