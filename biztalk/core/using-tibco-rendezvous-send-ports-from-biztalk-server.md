---
title: À l’aide de Ports d’envoi TIBCO Rendezvous à partir de BizTalk Server | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 34e3edf7-cfc5-4c89-8069-63e8784bc9f9
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 950c4c367fe053195ba14029405f5015381fc6be
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="using-tibco-rendezvous-send-ports"></a>À l’aide de Ports d’envoi TIBCO Rendezvous
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

## <a name="using-biztalk-to-send-messages"></a>À l’aide de BizTalk pour envoyer des Messages
L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous utilise l'API asynchrone (Transport.Send). Vous pouvez spécifier le type de message envoyé par l'adaptateur à l'aide d'une propriété de contexte de message :  
  
-   **Structuré**: l’adaptateur génère un message structuré TIBRVMSG_MSG, basé sur les données XML reçues de BizTalk Server. (*)  
  
 Si BizTalk Server envoie un message avec des champs dont le nom comporte plus de 127 caractères, l'adaptateur BizTalk pour TIBCO Rendezvous tronque les noms en fonction de la taille de nom de champ maximale pour TIBCO Rendezvous (127).  
  
 Si une propriété `reply subject name` est fournie, elle est utilisée pour définir l'objet de réponse sur le message TIBCO Rendezvous. Il est supposé qu'un port de réception est défini pour écouter la réponse et la transmettre à BizTalk Server, ou qu'un autre programme TIBCO Rendezvous traite la réponse.  
  
 Le triplet (service, démon, réseau) constitue la configuration de transport. Une configuration de transport vide (par défaut) entraîne l'envoi d'un message via l'objet de transport par défaut.  
  
 Si la page de code n'est pas spécifiée, l'adaptateur utilise le codage UTF-8 (page de code 65001). Les messages certifiés ne sont pas pris en charge du côté transmetteur.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de Ports d’envoi](../core/creating-send-ports2.md)   
 [Création de gestionnaires d’envoi TIBCO Rendezvous](../core/creating-tibco-rendezvous-send-handlers.md)