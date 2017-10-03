---
title: "FAQ sur les adaptateurs WCF : Gestion des erreurs WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdbd1ea6-4898-415c-ac5e-f804565759a8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efbac0b7aaffd6121cba406031a8330cfd5bbf2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-adapter-faq-wcf-error-handling"></a>FAQ sur les adaptateurs WCF : Gestion des erreurs WCF
## <a name="how-do-the-wcf-adapters-handle-errors-and-soap-faults-during-message-processing"></a>Gestion des erreurs SOAP par les adaptateurs WCF lors du traitement des messages  
 Pour un emplacement de réception, vous pouvez configurer une des deux options de gestion des erreurs sous le **gestion des erreurs** section sur le **Messages** onglet dans le **propriétés du Transport** boîte de dialogue zone.  
  
 Si le **suspendre le message de demande en cas d’échec** option est sélectionnée, le message de demande entrant sera suspendu doit renfermer une erreur de traitement dans le pipeline de réception ou d’un échec dans le routage du message. L'expéditeur du message peut ainsi réussir sa transmission vers BizTalk Server et recevoir un message d'accusé de réception. BizTalk Server suspend le message et enregistre l'intégralité de l'erreur pour le message ayant échoué. Cependant, dans ce cas, il ne renvoie pas l'exception du message à l'expéditeur. Ceci s'applique uniquement aux ports unidirectionnels. Un accusé de réception est envoyé si l'option est sélectionnée, et un accusé de réception négatif est envoyé si elle ne l'est pas. Pour les ports bidirectionnels, en cas d'échec du traitement, BizTalk reçoit un accusé de réception négatif.  
  
 Toutefois, si le client a besoin d’accéder à l’exception d’échec, activez la **incluent les détails de l’exception dans les erreurs** option. Lorsque cette option est sélectionnée, une erreur SOAP est renvoyée à l'appelant en cas d'erreur de traitement. Cela équivaut à spécifier le comportement de serviceDebug avec « IncludeExceptionDetailsInFaults » sur True dans le **comportement** onglet des adaptateurs WCF-Custom ou WCF-CustomIsolated. L'exception détaillée est alors envoyée au client. Cette option est plus sûre et pratique à utiliser lors du développement d'une application que lors de sa production, car il est probable que les messages d'erreurs internes ne soient pas envoyés aux appelants du service.  
  
 Pour le port d’envoi bidirectionnel, vous pouvez choisir de transférer les messages d’erreur SOAP à l’appelant d’origine sur une type sollicitation-réponse port d’envoi en sélectionnant **répercuter le message d’erreur**. Si cette option est désactivée, BizTalk Server génère un accusé de réception négatif, puis suspend le message. Si cette option est activée, BizTalk Server traite le message en tant que message de réponse WCF valide provenant du service externe, et le message de réponse n'est pas suspendu mais répercuté.  
  
## <a name="how-do-the-wcf-adapters-handle-message-transmission-timing-issues"></a>Gestion par les adaptateurs WCF des problèmes relatifs aux délais de transmission de message  
 Vous pouvez contrôler les problèmes de synchronisation pour les adaptateurs WCF à l’aide de la **liaison** onglet dans le **propriétés du Transport** boîte de dialogue. Ces paramètres sont **ouvrir**, **envoyer**, et **délai**. (Il existe également un délai d'attente de réception que vous pouvez définir à l'aide des adaptateurs personnalisés.) Ces paramètres correspondent respectivement à la durée d'une opération d'ouverture, d'envoi (de réception) et de fermeture de canal. Par défaut, ces paramètres sont définis sur une valeur comprise entre 1 minute (valeur minimale) et 23h59 (valeur maximale).