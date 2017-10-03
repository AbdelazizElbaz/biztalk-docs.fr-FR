---
title: "Définition de la taille de pool de threads de terminaison | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e170e76-5151-4306-9473-5b68e815219a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54afa88b51876d0ee56f548f263be1b00c37967a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-the-epm-threadpool-size"></a>Définition de la taille de la réserve de threads du Gestionnaire des points de terminaison
Cette rubrique explique comment définir la taille de la réserve de threads pour le Gestionnaire des points de terminaison.  
  
 Sur le **avancé** onglet dans le **propriétés de l’hôte** boîte de dialogue, il existe une propriété appelée **nombre maximal de moteur de messagerie threads par UC**. Pour obtenir des instructions sur l’accès à cette boîte de dialogue, consultez [la création d’un nouvel hôte](../core/how-to-create-a-new-host.md). Utilisez cette propriété pour contrôler la taille de la réserve de threads de processus que le moteur de messagerie utilise pour traiter les messages. La valeur par défaut de cette propriété est 20, ce qui signifie que le moteur de messagerie n'utilisera pas plus de 20 threads par UC sur le serveur.  
  
 Étant donné que les lots de messages sont traités par chaque thread dans le pool, ajuster la valeur de **nombre maximal de moteur de messagerie threads par UC** peut affecter les performances en modifiant la dynamique d’utilisation des ressources sur le serveur. Pour plus d’informations sur le fonctionne du pool de threads, consultez [à l’aide du moteur de messagerie BizTalk](../core/using-the-biztalk-messaging-engine.md).  
  
 Les tests ont montré que dans les cas où l’UC ou SQL Server est surchargé, la diminution de la valeur de **nombre maximal de moteur de messagerie threads par UC** peut entraîner une nette amélioration du débit. Par exemple, dans les cas où le serveur de base de données MessageBox montre une utilisation de l'UC supérieure à 90 % ou lorsque les temps d'attente de verrouillage SQL dépassent 500 à 1000 millisecondes, la réduction du nombre de threads dans la réserve a pour effet de diminuer le nombre total de connexions vers le serveur SQL Server, ce qui se traduit par un traitement plus efficace des messages. Dans certains cas, abaisser la taille maximale de la réserve de threads jusqu'à une valeur de 2 peut se traduire par une amélioration notable du débit.  
  
## <a name="recommendation"></a>Recommandation  
 Lors de l’optimisation d’une installation de BizTalk Server, il est recommandé de fine régler la valeur définie pour **nombre maximal de moteur de messagerie threads par UC**.  Si vous essayez de réduire l'utilisation du serveur de base de données MessageBox, envisagez de réduire la valeur de cette propriété.  
  
 Lorsque BizTalk server ou le serveur de base de données MessageBox n’est pas fortement utilisé, et appliquer une charge supplémentaire n’entraîne pas augmenter le débit, essayez d’augmenter la valeur de **nombre maximal de moteur de messagerie threads par UC** Pour tirer parti des ressources sous-utilisées.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer un nouvel hôte](../core/how-to-create-a-new-host.md)   
 [À l’aide du moteur de messagerie BizTalk](../core/using-the-biztalk-messaging-engine.md)