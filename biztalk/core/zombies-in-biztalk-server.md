---
title: Zombies dans BizTalk Server | Documents Microsoft
description: Causes courantes des messages zombies dans BizTalk Server
ms.custom: 
ms.date: 03/23/2016
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c684891-e984-442f-b5fd-de5f7cf32b44
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9764522d2ff5265b6f28f2f125cb33b2982a7605
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="zombies-in-biztalk-server"></a>Zombies dans BizTalk Server

## <a name="what-is-a-zombie"></a>Qu'est-ce qu'un zombie ?  
  
-   Un message zombie est un message qui a été acheminé vers une orchestration en cours d'exécution depuis la MessageBox et qui se trouve "en vol" au moment où l'orchestration prend fin. Un message "en vol" est un message qui a été acheminé vers une instance de service et qui se trouve donc dans une file d'attente de la MessageBox dédiée à cette instance de service. Puisque le message ne peut plus être utilisée par l'instance d'orchestration d'abonnement, il est suspendu et reçoit la valeur Instance de service/État "Suspendu (ne peut être repris)".  
  
-   Une instance de service zombie est une instance d'orchestration qui a pris fin pendant qu'un message en cours d'acheminement vers l'instance d'orchestration à partir la MessageBox se trouvait encore "en vol". Puisque l'instance d'orchestration est terminée, elle ne peut plus utiliser les messages "en vol" ; elle est donc suspendue et reçoit la valeur Instance de service/État "Suspendu (ne peut être repris)".  
  
## <a name="typical-causes"></a>Causes courantes
Les occurrences de zombies appartiennent en général à l'une des catégories suivantes :  
  
1.  **Messages de contrôle d’arrêt** – le moteur d’orchestration permet l’utilisation des messages de contrôle pour annuler tout le travail en cours d’exécution dans une instance d’orchestration spécifique. Puisque le message de contrôle stoppe immédiatement l'orchestration en cours d'exécution, les instances zombies ne sont impossibles. Plusieurs conceptions relatives au Human Workflow, entre autres, ont tendance à utiliser ce mécanisme.  
  
2.  **Réceptions en écoute parallèle** : dans ce scénario de l’instance de service attend 1 sur n messages et lorsqu’il reçoit certains messages il effectue certaines tâches et se termine. Si des messages sont reçus sur une branche parallèle au moment où l'instance de service prend fin, des zombies sont créés.  
  
3.  **Convois séquentiels avec points de terminaison non déterministes** – dans ce scénario, une planification d’orchestration principale est conçue pour gérer tous les messages d’un certain type afin de satisfaire à un type d’exigence de conception de système. Ces exigences de conception incluent la livraison chronologique des messages, les distributeurs de ressources et le traitement par lot. Pour ce scénario, il est question de définir une boucle while d'écoute, avec une branche de la forme Réception et l'autre de la forme Attente, suivies d'une certaine construction contenant des variables gouvernant l'arrêt de la boucle while. Il n'est pas question de déterminisme car un message peut être livré même si l'attente est déclenchée. Les points de terminaison non déterministes de ce type ont tendance à générer des zombies.  
  
 Lorsqu’une instance de service zombie est suspendue, le message d’erreur suivant est généré :  
  
`0xC0C01B4C The instance completed without consuming all of its messages. The instance and its unconsumed messages have been suspended.`  
  
 Vous pouvez utiliser la [BizTalk Terminator](https://www.microsoft.com/download/details.aspx?id=2846) pour supprimer les zombies.  
  
## <a name="see-also"></a>Voir aussi  
 **Suppression d’Instances de Service suspendues**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]