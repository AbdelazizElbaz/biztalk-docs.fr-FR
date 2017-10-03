---
title: Orchestrations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations
- correlations, orchestrations
- orchestrations, correlations
- orchestrations, deploying
- deploying, orchestrations
- orchestrations, about orchestrations
ms.assetid: fb01f78a-b805-46be-a7d9-2b7597daab96
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73fb7a4af3a8ef7da8e9da97047006470eb8cc18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestrations"></a>Orchestrations
*Orchestrations* sont des processus d’entreprise exécutables qui peuvent s’abonner à (réception) et publier des messages (envoyer) via la base de données MessageBox. Les orchestrations peuvent en outre construire de nouveaux messages. Les messages sont reçus à l’aide de l’abonnement et l’infrastructure de routage de [cycle de vie d’un Message](../core/lifecycle-of-a-message.md). Lorsque des abonnements sont définis pour les orchestrations, une nouvelle instance est activée et le message est remis, ou, dans le cas d'abonnements d'instance, l'instance est réalimentée si nécessaire et le message est ensuite remis. Lorsque des messages sont envoyés à partir d'une orchestration, ils sont publiés dans la base de données MessageBox de la même manière que lorsqu'un message arrive sur un emplacement de réception, les propriétés appropriées sont insérées dans la base de données pour être utilisées dans le routage.  
  
 Les messages construits dans une orchestration doivent être placés dans la base de données MessageBox et être référencés par l'instance de l'orchestration. N'ayant pas encore été envoyés, ils ne doivent toutefois pas être publiés. Le sous-service XLANG/s appelle l'API de l'agent des messages pour insérer directement les messages. Cela permet au moteur d'orchestration d'insérer le corps du message dans la base MessageBox et de l'associer directement à l'instance d'orchestration en cours d'exécution. La persistance du message construit dans la base de données MessageBox est réalisée avec des points de persistance dans l'orchestration qui constituent une optimisation supplémentaire des opérations de base de données.  
  
 Dans les orchestrations, le concept de liaison semble donner un aperçu différent de la publication et de l'abonnement. Les ports d'orchestration sont des ports logiques qui décrivent une interaction. Vous devez lier ces ports logiques à un port physique pour que les messages soient remis, mais ce processus de liaison revient en fait à configurer des abonnements pour le routage des messages.  
  
 Il existe quatre options de base pour lier ces ports :  
  
-   Spécifier maintenant (spécification des ports directement dans l'orchestration)  
  
-   Spécifier plus tard (spécification des ports au moment du déploiement)  
  
-   Utilisation d'un port d'envoi dynamique pour lequel l'adresse est définie dans le code de l'orchestration  
  
-   Création d'une liaison directe depuis l'orchestration vers la base de données MessageBox ou une autre orchestration  
  
## <a name="deploying-orchestrations"></a>Déploiement des orchestrations  
 Lorsqu'une liaison est spécifiée au moment de la conception, le port physique correspondant aux paramètres configurés dans l'orchestration est créé lors du déploiement de l'orchestration. Lorsque la liaison est configurée au moment du déploiement, tout port correspondant aux paramètres du port logique peut être lié au port de l'orchestration. Dans le cadre de la liaison dynamique, un port physique est créé de la même façon qu'avec l'option Spécifier maintenant, mais il s'agit d'un port d'envoi dynamique sans informations d'adresse configurées.  
  
 Là où la situation se complique, c'est que même si un port d'envoi d'une orchestration est lié à un port d'envoi physique, le message peut être remis à d'autres abonnés. En d'autres termes, si un autre port d'envoi possède un abonnement au message envoyé au port lié par le biais de ses filtres, le message est envoyé aux deux ports d'envoi. La liaison permet simplement de créer l'abonnement de sorte que le message envoyé depuis l'orchestration corresponde toujours aux critères du port d'envoi lié. De même, le port d’orchestration lié à un port de réception crée l’abonnement approprié en fonction de l’ID de message type et receive port. Les abonnements garantissent que les messages sortants vers et depuis l’orchestration sont bien remis aux ports liés, mais les messages toujours passent par la même publication et abonnement décrit précédemment.  
  
 L'option de liaison directe est probablement l'option de liaison la plus difficile à comprendre. La liaison directe permet à une orchestration de publier des messages dans la base de données MessageBox avec diverses propriétés de routage, de manière similaire à la publication des messages par les emplacements de réception. Dans la messagerie directe simple, le message est publié dans la base de données MessageBox avec ses propriétés promues pour être acheminé comme tout autre message publié que BizTalk Server reçoit. Cela permet à tous les abonnés de recevoir le message. Dans ce système cependant, au moins un abonné doit exister, faute de quoi, l'orchestration reçoit une erreur signalant l'échec du routage.  
  
 Une autre option de liaison directe consiste à utiliser des ports d'autocorrélation. Les ports d'autocorrélation sont des ports qui créent un jeton de corrélation unique pour l'utiliser dans la corrélation des messages avec les instances. Ce type de port est couramment utilisé pour appeler ou démarrer une orchestration transmettant un paramètre de port. Dans l'orchestration appelée, le port peut être utilisé pour envoyer un message, alors que dans l'orchestration d'appel, le même port peut servir à recevoir un message. Le port possédant un jeton de corrélation unique, le message est réacheminé vers l'orchestration d'appel. Les ports d'autocorrélation font office de canaux de communication privés entre les instances d'orchestration.  
  
 La dernière option consiste à utiliser l'orchestration d'un partenaire dans laquelle, pour l'orchestration d'appel comme pour l'orchestration appelée, le port est configuré à l'aide du même type de port partagé, et, dans la configuration du port, le même port est sélectionné. Par exemple, dans Orch1 et Orch2, Orch2.MyDirectPort est sélectionné. Ce type de liaison définit un abonnement pour l'orchestration de réception en fonction du type d'orchestration d'envoi, du nom du port et du nom de l'opération. Ce processus garantit une fois de plus que les messages seront acheminés vers la bonne instance.  
  
 Toutes les options de messagerie directe utilisent le modèle de publication et d'abonnement sous-jacent. La différence entre ces options réside dans les propriétés utilisées pour la création des abonnements et le routage, et dans les cas d'utilisation qu'elles permettent de résoudre.  
  
 L'un des problèmes courants rencontrés lors de l'utilisation de ports liés directs dans les orchestrations est qu'une orchestration peut publier un message auquel elle est également abonnée. Supposons, par exemple, qu'une orchestration est configurée pour être activée par un message PurchaseOrder. Cette orchestration utilise un port direct pour publier le message PurchaseOrder dans MessageBox. Cependant, en plus de recevoir le message comme prévu, une autre instance de l'orchestration est démarrée, car celle-ci est également abonnée aux messages PurchaseOrder. Ce type de traitement s'engage dans une boucle sans fin et un développeur peut mettre un certain temps avant de comprendre ce qui s'est passé.  
  
## <a name="correlation"></a>Correlation  
 *Corrélation* dans les orchestrations est le mécanisme de réception des messages connexes dans la même instance d’orchestration en cours d’exécution. Dans le Concepteur d'orchestration, un développeur procède de la manière suivante pour utiliser une corrélation :  
  
-   Il définit un type de corrélation qui inclut les propriétés promues utilisées pour mettre en relation des messages.  
  
-   Il définit un ensemble de corrélations constituant une instance du type de corrélation défini plus avant.  
  
-   Il spécifie si les ports d'envoi et de réception initient ou suivent un ensemble de corrélations donné.  
  
 Les abonnements d'instance entrent en jeu lorsqu'un ensemble de corrélations est initié, par exemple lorsque des abonnements sont créés pour tous les ports qui suivent cet ensemble de corrélations pour la réception des messages. Le type de corrélation définissant les propriétés utilisées pour la corrélation, le moteur d'orchestration peut les extraire du message envoyé ou reçu par l'action initiatrice. Ces valeurs sont ensuite utilisées pour définir des abonnements pour toutes les actions restantes qui suivent cet ensemble de corrélations.  
  
 Il est important que les propriétés promues des messages reçus dans BizTalk Server et destinés à être utilisés dans une corrélation soient correctement définies et promues dans le contexte de message. La plupart des propriétés sont promues lorsqu'un composant désassembleur dans un pipeline extrait les valeurs lors de la réception initiale du message. De ce fait, il n'est pas possible d'utiliser le pipeline de réception PassThrough pour recevoir des messages devant être corrélés à une instance d'orchestration en cours d'exécution. Ce problème survient lorsque vous utilisez l'adaptateur de réception SOAP pour recevoir des messages de corrélation, car le pipeline PassThrough est le pipeline de réception utilisé par défaut lorsque vous travaillez dans l'Assistant Publication de services Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Artefacts](../core/artifacts.md)   
 [Création d’Orchestrations à l’aide du Concepteur d’Orchestration](../core/creating-orchestrations-using-orchestration-designer.md)