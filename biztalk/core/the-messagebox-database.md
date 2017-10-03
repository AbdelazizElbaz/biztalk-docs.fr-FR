---
title: "La base de données MessageBox | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, MessageBox database
- messages, suspended messages
- MessageBox database, messages
- MessageBox database, about MessageBox database
- MessageBox database, suspended messages
- suspended messages
- MessageBox database
- suspended messages, MessageBox database
ms.assetid: f89eb02c-1b83-4127-8a91-e78fb4a1f96e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edf1fb3a89d6e08f6a0183a3242c53c4be890e60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-messagebox-database"></a>La base de données MessageBox
Le cœur du moteur de publication/d'abonnement de Microsoft BizTalk Server est la base de données MessageBox. MessageBox est constitué de deux composants : un ou plusieurs bases de données Microsoft SQL Server et l’Agent de messagerie. La base de données SQL Server assure le stockage permanent de nombreuses choses comme les messages, les parties et propriétés des messages, les abonnements, l'état des orchestrations, les données de suivi, les files d'attente hôte pour le routage, etc. Le groupe BizTalk Server peut posséder une ou plusieurs bases de données MessageBox dans lesquelles il publie des messages et à partir desquelles les abonnés extraient ces messages.  
  
 La base de données fournit une partie de la logique liée au routage des messages et aux réponses aux abonnements. L'agent des messages est toutefois le composant qui encapsule et résume le composant de base de données. Il s'agit de l'interface utilisée par BizTalk Server pour interagir avec le MessageBox. L'agent des messages est un composant COM (Component Object Model) qui fournit des interfaces pour la publication des messages, l'inscription aux messages, la récupération des messages, etc. Cette interface est le seul mécanisme utilisé par les autres composants BizTalk Server, comme l'infrastructure d'adaptateurs et les orchestrations, pour interagir avec le MessageBox.  
  
## <a name="the-messagebox-and-the-message"></a>MessageBox et message  
 Un abonnement à la base de données MessageBox est un ensemble d'informations établies et d'informations de service. Les informations établies (ou de prédicat) correspondent aux critères qu'un message doit remplir. Les informations de service indiquent ce qu'il faut faire du message qui répond aux critères. Toutes ces informations sont stockées dans un ensemble de tables qui appellent le moteur de messagerie et d'orchestration.  
  
 Lorsque BizTalk Server reçoit un message, il le traite dans un pipeline, puis le place dans la base de données MessageBox. Le message entrant comporte un contexte. Le contexte du message est un ensemble de propriétés associées au message. Il existe trois types de propriétés de contexte de message :  
  
-   Propriétés écrites simples  
  
-   Propriétés promues  
  
-   Propriétés de prédicat  
  
 Les propriétés promues et de prédicat indiquent le processus d'entreprise qui s'abonne à ce message, et si ce processus dispose des autorisations nécessaires pour recevoir ce message.  
  
 Si un processus d'entreprise s'abonne au message, la base de données MessageBox envoie ce message au processus. Lorsque le processus d'entreprise reçoit le message, il le traite sur une instance de l'hôte disponible. Une fois le message traité, si le processus d'entreprise s'abonne à un pipeline ou un port d'envoi, il envoie un message de retour à la base de données MessageBox.  
  
 Pour chaque hôte BizTalk, la base de données MessageBox associée comprend une file de travail et une file d'attente des messages interrompus. En outre, chaque base de données MessageBox contient un ensemble de tables pour les états statiques, dynamiques et d'instance. Pour plus d’informations sur les hôtes BizTalk, consultez [entités](../core/entities.md).  
  
> [!IMPORTANT]
>  Si un hôte n'est plus disponible, par exemple lorsque la base de données MessageBox qui reçoit des messages de cet hôte devient indisponible, aucune autre base de données MessageBox n'est plus disponible.  
  
 Vous créez la première base de données MessageBox lorsque vous exécutez l'Assistant Configuration. La base de données MessageBox configurée devient la base de données principale MessageBox. Cette base de données évalue et achemine les abonnements vers toutes les autres bases de données MessageBox dans l'environnement BizTalk Server. Pour plus d’informations sur l’amélioration des performances pour la base de données principale, consultez [la gestion des bases de données MessageBox](../core/managing-messagebox-databases.md).  
  
> [!IMPORTANT]
>  Vous devez utiliser la mise en cluster de SQL Server pour assurer une protection par basculement pour les bases de données MessageBox.  
  
## <a name="suspended-messages-in-the-messagebox-database"></a>Messages suspendus dans la base de données MessageBox  
 BizTalk Server stocke les messages associés aux pipelines suspendus dans la base de données MessageBox. En cas de problème dans le pipeline, BizTalk Server suspend l'instance d'un message. Il existe deux types d'instances de service suspendues :  
  
-   les instances suspendues que vous pouvez reprendre ;  
  
-   les instances suspendues que vous ne pouvez pas reprendre. Il s'agit par exemple d'une instance endommagée.  
  
 Selon la cause de la suspension, vous pouvez reprendre les services suspendus par BizTalk Server. Il en est ainsi par exemple si une orchestration atteint une forme Interrompre ou si un transport n'a pas réussi à livrer un message. BizTalk Server ne supprime pas automatiquement de la base de données MessageBox les instances suspendues impossibles à reprendre. Vous pouvez choisir d'enregistrer une instance de service sur disque avant de la supprimer de la file d'attente des messages interrompus.  
  
 Pour plus d’informations sur la sauvegarde des bases de données MessageBox, consultez [sauvegarde et restauration de bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Le moteur de messagerie](../core/the-messaging-engine.md)