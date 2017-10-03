---
title: Le moteur de messagerie BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0c8d3e6-953d-4a04-adfc-b77ef7173464
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f8e0f4fa694699e2dfbc499b6f2fd3440656935
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-biztalk-server-messaging-engine"></a>Moteur de messagerie BizTalk Server
Le moteur de messagerie [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet aux utilisateurs de créer des processus d'entreprise qui englobent plusieurs applications au moyen de deux éléments principaux :  
  
-   une méthode pour spécifier et implémenter la logique directrice de ce processus d'entreprise ;  
  
-   un dispositif de communication entre les applications qu'utilise ce processus d'entreprise.  
  
 La figure ci-dessous illustre les principaux composants du moteur qui répondent à ces deux attentes.  
  
 ![](../core/media/understandingbts-04-engine4.gif "UnderstandingBTS_04_Engine4")  
  
 Comme le montre le diagramme, un message est reçu via un **l’adaptateur de réception**. Différents adaptateurs offrent différents mécanismes de communication ; un message peut donc être acquis en accédant à un service Web, en lisant un fichier ou par d'autres moyens. Le message est ensuite traité via un **pipeline de réception**. Celui-ci peut contenir divers composants effectuant des actions telles que la conversion d'un message au format natif en un document XML, la validation de la signature numérique d'un message, etc. Le message est alors envoyé dans une base de données appelée la **MessageBox**, qui est implémentée à l’aide de Microsoft SQL Server.  
  
 La logique qui gère un processus d’entreprise est implémentée en tant qu’un ou plusieurs **orchestrations**, dont chacun se compose de code exécutable. Ces orchestrations ne sont toutefois pas créées en écrivant du code dans un langage comme C#. Un analyste d'entreprise ou (très certainement) un développeur utilise ensuite un outil approprié pour classer de manière graphique un groupe de formes défini permettant d'exprimer des conditions, des boucles et d'autres comportements. Orchestrations peuvent éventuellement utiliser le **moteur de règles métier**, qui fournit un simple et facilement modifiable pour exprimer des ensembles de règles dans un processus d’entreprise complexes.  
  
 Chaque orchestration crée **abonnements** pour indiquer les types de messages qu’il souhaite recevoir. Lorsqu'un message répondant aux critères arrive dans MessageBox, il est affiché dans l'orchestration cible, qui effectue l'action qui lui est dictée par le processus d'entreprise. Dans la plupart des cas, le résultat de ce processus consiste en la création d'un autre message généré par l'orchestration et enregistré dans MessageBox. Ce message, à son tour, est traité par un **pipeline d’envoi**, qui peut le convertir à partir du format XML interne utilisé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] au format requis par sa destination, ajouter une signature numérique et bien plus encore. Le message est ensuite envoyé à l’aide un **l’adaptateur d’envoi**, qui utilise un mécanisme approprié pour communiquer avec l’application pour laquelle ce message est destiné.  
  
 Complète **solution** reposant sur la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] moteur peut contenir plusieurs parties (parfois appelée artefacts) : orchestrations, des pipelines, des schémas de message et bien plus encore. Ces parties, ou artefacts, peuvent être manipulées comme une unité unique, appelée un **application BizTalk**. Une application BizTalk regroupe au sein d'une seule unité logique toutes les parties requises d'une solution. Elle constitue ainsi l'abstraction fondamentale pour les opérations de gestion et de déploiement.  
  
 Le moteur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] donne l'opportunité à différents types de personnes d'exécuter différentes actions. A **analyste d’entreprise**, par exemple, vous pouvez définir les règles et les comportements qui constituent un processus d’entreprise. Elle détermine également le flux de celui-ci, c'est-à-dire qu'elle définit les informations à envoyer à chaque application, ainsi que la manière dont un document commercial est mappé sur un autre. Une fois que l’analyste d’entreprise a défini le processus, un **développeur** peut créer une application BizTalk qui l’implémente. Ses attributions consistent à définir les schémas XML des documents commerciaux à utiliser, à spécifier le mappage détaillé entre eux et à créer les orchestrations requises pour implémenter le processus. Un **administrateur** joue également un rôle important en configurant les communications entre les parties, le déploiement de l’application BizTalk de façon évolutive et effectuer d’autres tâches. Les trois rôles (analyste d'entreprise, développeur et administrateur) sont nécessaires à la création et à la gestion des solutions [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Connexion de systèmes](../core/connecting-systems.md)  
  
-   [Définition des processus d’entreprise](../core/defining-business-processes.md)  
  
-   [Gestion et surveillance](../core/management-and-monitoring.md)  
  
-   [Enterprise Single Sign-On](../core/enterprise-single-sign-on-sso.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de BizTalk Server](../core/biztalk-server-architecture.md)   
 [Architecture d’exécution](../core/runtime-architecture.md)