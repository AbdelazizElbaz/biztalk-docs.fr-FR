---
title: "À l’aide de Ports d’envoi TIBCO Rendezvous à partir de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, handling
- message handling
- BizTalk Server, using send ports from
- send ports, using from BizTalk Server
- messages, generating
ms.assetid: 34e3edf7-cfc5-4c89-8069-63e8784bc9f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04e11657e8e15ac0739124178e85f0c7c5c0a70e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-tibco-rendezvous-send-ports-from-biztalk-server"></a>Utilisation des ports d'envoi TIBCO Rendezvous à partir de BizTalk Server
Un port de transmission peut envoyer tout type de message. Lorsque BizTalk Server envoie un message via l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous, l'adaptateur génère le message d'après les valeurs des propriétés de contexte du message ou sur la base des valeurs par défaut, puis il l'envoie vers l'objet spécifié.  
  
> [!NOTE]
>  Selon la documentation de TIBCO Rendezvous, les caractères génériques ne sont pas pris en charge dans les noms d'objets de transmission.  
  
## <a name="message-handling"></a>Gestion des messages  
 L'adaptateur conserve un état et traite les messages BizTalk Server entrants en conséquence.  
  
-   Lorsqu'un message ne peut pas être envoyé à cause d'une défaillance au niveau du transport, BizTalk Server reçoit comme consigne de retenter son envoi ultérieurement.  
  
-   Lorsqu'un message ne peut pas être envoyé car l'adaptateur est toujours en cours d'initialisation, le message BizTalk Server est mis en file d'attente. Si l'initialisation échoue, BizTalk Server reçoit comme consigne de retenter son envoi ultérieurement.  
  
## <a name="message-generation"></a>Création de messages  
 Grâce à l'adaptateur de transmission, l'adaptateur BizTalk pour TIBCO Rendezvous ignore l'espace de noms cible du message et l'élément racine. Lors de l'envoi de messages par l'adaptateur, ce dernier envoie la charge en l'état. Lors de la création d'un message structuré TIBCO Rendezvous par l'adaptateur, le nom de l'élément racine est ignoré (un message n'a pas de nom). Dans chaque situation, l'adaptateur fait appel à une propriété de contexte pour rechercher l'objet à utiliser lors de la publication du message.  
  
 Pour plus d’informations, consultez [propriétés de contexte du Message BizTalk Server (gestionnaires d’envoi)](../core/biztalk-server-message-context-properties-send-handlers.md) et [mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création de Ports d’envoi](../core/creating-send-ports2.md)   
 [Création gestionnaires d’envoi TIBCO Rendezvous](../core/creating-tibco-rendezvous-send-handlers.md)