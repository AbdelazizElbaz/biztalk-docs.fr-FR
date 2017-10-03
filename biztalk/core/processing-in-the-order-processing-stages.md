---
title: "Dans les étapes de traitement de commande de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 698005da-1ba8-4972-83db-f5ae45fd6a83
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a8eae6b814af36d0ea07065726ca66518984703
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-in-the-order-processing-stages"></a>Traitement dans les étapes de traitement de la commande
La solution de gestion des processus d’entreprise comporte deux étapes le **CableOrder1** et **CableOrder2** orchestrations, qui effectuent des actions de traitement des commandes. Pour plus d’informations sur la façon dont le processus de commande a été divisé en étapes, consultez [nombre d’étapes de traitement](../core/number-of-processing-stages.md).  
  
 Les deux étapes de traitement démarrent lorsqu’ils reçoivent un message de commande et répondent avec un message d’état pour le **OrderManager** orchestration une fois qu’ils ont démarré. De même, les deux renvoient un message à la **OrderManager** pour indiquer si l’étape s’est terminée ou arrêtée avec une erreur. Pour plus d’informations sur la connexion entre le **OrderManager** d’orchestration et les étapes de traitement, consultez [Inverse liaison directe de partenaires](../core/inverse-direct-partner-binding.md).  
  
 Les deux étapes de traitement utilisent autocorrélation, les ports dynamiques pour envoyer des informations pour le **OrderManger**. Grâce aux ports dynamiques, les orchestrations copient l'adresse de port du message envoyé au port d'envoi.  
  
 Tous les messages de commande les étapes de traitement de réception sont les messages d’ordre canonique normalisé créés dans le **OrderBroker**.  
  
> [!NOTE]
>  En raison de la longueur de la **CableOrder1** et **CableOrder2** orchestrations, vous voudrez lire cette section avec les orchestrations ouvertes dans Microsoft Visual Studio.  
  
## <a name="the-cableorder1-orchestration"></a>Orchestration CableOrder1  
 Le **CableOrder1** orchestration démarre lorsqu’il reçoit un message de commande. Elle copie l'adresse de réponse du message vers le port d'exécution de l'étape. Ensuite, il génère un message d’accusé de réception et l’envoie en réponse à la **BeginStagePort** de port et enregistre les informations de routage dans une variable locale.  
  
 L'orchestration obtient les informations de configuration de l'authentification unique. Pour plus d’informations sur la façon dont la solution utilise l’authentification unique, consultez [à l’aide de l’authentification unique efficacement dans la Solution de gestion des processus métier](../core/using-sso-efficiently-in-the-business-process-management-solution.md).  
  
 L’orchestration crée une instance de la **OrderHandler** de l’objet pour communiquer avec les processus principaux, vérifie la validité du message, analyse le message, détermine le type de service et l’action à effectuer. Selon l’action à entreprendre, il appelle l’une des orchestrations d’action de commande **activer**, **modification**, ou **Annuler** et transmet le **OrderHandler** objet à l’orchestration.  
  
 Le **CableOrder1** orchestration puis consigne une interruption éventuelle, envoie un message pour le groupe d’installations et les attentes à écouter. Si elle reçoit une réponse du groupe d'installations, elle poursuit le traitement. Sinon, en cas d'interruption, elle génère une exception d'interruption.  
  
 L’orchestration se termine par la construction d’un message de fin et en l’envoyant via la **StageCompletion** port.  
  
## <a name="the-cableorder2-orchestration"></a>Orchestration CableOrder2  
 L’orchestration CableOrder2 effectue les mêmes étapes de démarrage que l’orchestration CableOrder1 pour les informations de routage, informations de configuration de l’authentification unique et la création d’une instance de la **OrderHandler** objet.  
  
 L’orchestration puis vérifient une interruption éventuelle et transmet le **OrderHandler** objet dans un appel à la **Complete** orchestration. Ensuite, l’orchestration crée un message d’état de commande met à jour l’historique des commandes et envoie un message de saisie semi-automatique via la **StageCompletion** port.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de version de la Solution gestion des processus d’entreprise](../core/versioning-the-business-process-management-solution.md)   
 [Traitement dans la Solution gestion des processus d’entreprise](../core/processing-in-the-business-process-management-solution.md)