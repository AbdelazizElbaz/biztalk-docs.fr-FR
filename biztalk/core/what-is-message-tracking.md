---
title: "Qu'est-ce que le suivi des messages ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HAT, metadata
- HAT, messages
- messages, tracking
- data, HAT
- metadata, tracking
- tracking, metadata
- HAT, data security
- tracking, messages
- configuring [HAT tracking], messages
- data, security
ms.assetid: 51cec59d-b411-4d8f-b771-7b2cf0f38945
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c898c2a30d883da4507957c62a0acb75e56a71b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-message-tracking"></a>Qu'est-ce que le suivi des messages ?
Un message est une instance électronique de données, échangée, par exemple, entre deux processus d'entreprise ou applications en cours d'exécution. Une instance de message est constituée d'un corps de message, de propriétés de message et de métadonnées.  
  
 Vous pouvez utiliser la console Administration de BizTalk Server pour activer le suivi des propriétés de message et des corps de message. Vous pouvez y consulter le corps de message suivi, notamment des informations sur le schéma, le nom fort et toutes les propriétés promues du message généré.  
  
## <a name="message-body"></a>Corps du message  
 Le suivi des corps de message permet de conserver une trace des messages envoyés et reçus. Pour enregistrer des messages une fois le traitement des instances de service terminé, vous devez activer le suivi du corps des messages. Après avoir activé les options de suivi, vous devez parfois attendre plusieurs minutes avant de pouvoir afficher les messages.  
  
> [!IMPORTANT]
>  Le service SQL Server Agent doit être en cours d'exécution sur toutes les bases de données MessageBox. Le TrackedMessages_Copy_\<Nommessagebox > au travail, les corps de message disponibles pour le suivi des requêtes et WMI. Pour une copie efficace des corps de message, ils restent dans la base de données MessageBox et sont régulièrement copiés à la base de données des suivis BizTalk (BizTalkDTADb) par le TrackedMessages_Copy_\<Nommessagebox > tâche. Pour que le processus d'archivage et de purge s'effectue correctement, le service SQL Server Agent doit également être en cours d'exécution.  
  
 Vous pouvez utiliser les messages suivis pour fournir une confirmation de réception, activer le dépannage et autoriser l'exploration des données des transactions historiques. Vous pouvez effectuer le suivi des corps de message au niveau des entrées et des sorties des ports, des pipelines et des orchestrations. Vous pouvez récupérer ces messages à l'aide de la console Administration de BizTalk Server, du modèle OM (Operations object model) (recommandé) ou des API (interfaces de programmation d'application) WMI (Windows Management Instrumentation).  
  
 BizTalk Server n'effectue pas le suivi des messages qui ne franchissent pas correctement l'un des points de suivi. Dans certains cas, par exemple, lorsqu'un message est interrompu parce qu'il n'est pas valide ou si aucun hôte n'attend le message, il peut être placé dans la file d'attente des messages interrompus sans suivi. Si vous arrêtez le message, il n'y aura aucun enregistrement de celui-ci.  
  
> [!IMPORTANT]
>  Le suivi des corps de message ne peut pas remplacer l'audit et ne prend pas en charge la non-répudiation.  
  
## <a name="message-properties"></a>Propriétés du message  
 Les propriétés de message incluent les propriétés promues, les informations de routage et les données relatives aux partenaires commerciaux. Le suivi des propriétés des messages vous permet de localiser un message particulier parmi les milliers de messages suivis, en fournissant un enregistrement des propriétés promues pour chaque message de la liste des résultats. Vous pouvez suivre un sous-ensemble du message lui-même, à l'aide de l'une de ces propriétés.  
  
 Pour suivre les propriétés de contexte, vous devez définir un schéma de propriété pour l'espace de noms utilisé dans le contexte pour stocker les propriétés. À partir de cette vue, vous pouvez sélectionner les propriétés de contexte que vous souhaitez suivre. BizTalk Server opère de la même manière que lorsqu'il s'agit de propriétés de message promues.  
  
> [!NOTE]
>  Vérifiez que vous donnez des noms différents aux propriétés dans le schéma. Un message d'erreur apparaît si vous créez des doublons.  
  
 Par exemple, vous pouvez utiliser l'Éditeur de schéma pour promouvoir le champ du numéro de commande depuis un schéma de bon de commande. Ensuite, dans la vue Rechercher un message, vous pouvez rechercher les instances de message contenant une valeur pour le champ suivi, telle que Numéro de commande = 16995.  
  
 Le suivi des propriétés de message génère bien moins de traitement que le suivi des corps de message car il n'intervient que sur les champs sélectionnés. Après avoir défini les options de suivi des propriétés de message, vous devrez patienter quelques minutes avant de pouvoir consulter les propriétés.  
  
## <a name="metadata"></a>Métadonnées  
 Métadonnées, telles que l'identificateur d'instance de message, l'orchestration ou le pipeline consignant le message, le point auquel l'orchestration ou le pipeline consigne le message et d'autres détails de suivi pertinents. Pour qu'un message de la base de données MessageBox puisse être acheminé vers un processus d'entreprise, il doit contenir des propriétés de contexte, telles que le type et l'origine du message. Ces propriétés deviennent des métadonnées. Le suivi des messages et des instances de service utilise les critères d'abonnement pour exécuter une requête sur ces métadonnées.  
  
 Via la console Administration de BizTalk Server, vous pouvez promouvoir des propriétés de contexte en sélectionnant un schéma système. Les schémas système se trouvent dans le nœud Applications\BizTalk.System\Schemas. BizTalk Server effectue le suivi de ces propriétés de contexte de manière globale, c'est-à-dire que tous les messages contenant une propriété de contexte sont suivis. Par conséquent, la taille de la base de données des suivis BizTalk peut augmenter considérablement.  
  
## <a name="sensitive-data"></a>Données sensibles  
 Vous pouvez sécuriser les données ci-dessous de sorte qu'elles n'apparaissent pas dans la fenêtre des propriétés de schéma correspondante et qu'ainsi, elles ne puissent pas faire l'objet d'un suivi.  
  
-   Appliquer le **isSensitive** attribut à des propriétés sensibles dans un schéma de propriété, il n’est plus visible dans la propriété de Message de suivi des sélections de configuration.  
  
-   Tous les transports prêts à l'emploi contiennent des mots de passe considérés comme données sensibles. Par conséquent, les transports ne peuvent pas être suivis.  
  
-   En outre, les données sensibles ne figurent plus dans la base de données de gestion. Par conséquent, si vous définissez des options de suivi directement dans la base de données, ces données ne feront pas l'objet d'un suivi.  
  
-   Si vous suivez un corps de message en cours de transmission vers l'extérieur, le suivi des messages supprime toutes les propriétés de transport du raccourci du corps de message suivi. Par conséquent, outre la suppression des propriétés du transport sortant, figurant dans le raccourci du corps de message suivi, le suivi des messages supprime également les propriétés des transports entrants.  
  
    > [!IMPORTANT]
    >  Une propriété promue peut contenir des données sensibles. Si les requêtes de suivi de la page Hub du groupe effectuent le suivi d'une propriété incluant des données sensibles, les utilisateurs autorisés à exécuter des requêtes de suivi peuvent consulter ces données.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration du suivi à l’aide de la Console Administration de BizTalk Server](http://msdn.microsoft.com/en-us/49b7f9d3-60b5-41bd-ba8b-029253926bef)