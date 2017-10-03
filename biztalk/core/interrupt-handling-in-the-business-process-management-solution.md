---
title: "Gestion des interruptions dans la Solution gestion des processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing, pausing
- process management solution tutorial, pausing processing
ms.assetid: 23ce7617-f705-4b7d-8447-221dec9fb196
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78b98eae8ee9cbb43354c1cfc48710c70969a929
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interrupt-handling-in-the-business-process-management-solution"></a>Gestion des interruptions dans la Solution gestion des processus d’entreprise
Cette section décrit le mécanisme de gestion de l'interruption utilisé dans la solution de gestion des processus d'entreprise. Ce mécanisme permet d'arrêter le traitement des commandes lorsque l'une d'elles est mise à jour ou annulée.  
  
## <a name="interrupt-handling"></a>Gestion de l'interruption  
 Les orchestrations qui implémentent les étapes de traitement appellent l’orchestration **CheckInterrupt**, qui teste une demande d’interruption à partir d’une autre partie du processus. Le **CheckInterrupt** orchestration se compose d’un **écouter** forme. Une branche de la **écouter** forme recherche un message avec le même ID de corrélation que la commande actuelle. S’il existe un tel message, le **CheckInterrupt** orchestration envoie un message d’accusé de réception et exécute un **lever** forme. Étant donné que les branches dans un **écouter** forme sont exécutées de gauche à droite, le délai d’attente s’affiche dans la branche de droite. Notez que le délai est de zéro (0).  
  
 La combinaison de la **écouter** forme, une branche de réception et une branche délai permet à l’orchestration de rechercher des messages. Si elle trouve un message d'interruption, la branche de gauche est exécutée. Si l'orchestration ne trouve rien, la branche de droite est exécutée et est renvoyée à l'orchestration d'appel. Un message d'interruption peut être envoyé à tout moment. Étant donné que la **CheckInterrupt** orchestration est exécutée seulement occasionnellement, il peut y avoir un message d’interruption en attente.  
  
 Le **OrderManager** définit les interruptions en appelant le **Interrupter** orchestration. Le **Interrupter** orchestration envoie un message d’interruption pour le **InterruptPort** et attend une réponse. L’orchestration utilise la **délai d’attente** propriété de la forme **étendue** forme pour redémarrer la boucle si une réponse n’est reçue. Elle continue d'envoyer un message d'interruption tant que la forme Étendue expire sans recevoir de réponse. Un délai d'expiration indique que la demande correspond à un abonnement, mais que la réponse n'a pas eu le temps d'être envoyée. La boucle prend fin s’il existe une réponse, ou s’il n’existe aucun abonnement à la **InterruptPort**.  
  
 Le modèle demande-réponse-fin le **OrderManager** utilise avec les étapes du processus est un élément essentiel de la gestion de l’interruption. Étant donné que la **OrderManager** attend une réponse, un accusé de réception : à partir de la scène, il sait que l’étape de démarrage de l’exécution avant de continuer. Ceci garantit qu'une étape ne peut pas recevoir d'interruption avant d'avoir démarré. Cela permet également la **OrderManager** savoir s’il n’existe aucun abonnement à une interruption, l’étape est terminée.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement dans la Solution gestion des processus d’entreprise](../core/processing-in-the-business-process-management-solution.md)   
 [Logique du Gestionnaire de processus](../core/process-manager-logic.md)   
 [L’Orchestration ExceptionHandler](../core/the-exceptionhandler-orchestration.md)