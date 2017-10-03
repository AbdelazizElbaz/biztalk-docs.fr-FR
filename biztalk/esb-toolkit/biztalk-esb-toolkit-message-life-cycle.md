---
title: BizTalk ESB Toolkit Cycle de vie | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c72fdbda-b9ef-431a-8322-56dba98e9eab
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cb15a4c87a497a5595327b65019ca95b3201664
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-esb-toolkit-message-life-cycle"></a>BizTalk ESB Toolkit Cycle de vie
Voici le cycle de vie d’un message qui provient d’un système externe et parcourt l’ESB d’atteindre sa destination finale :  
  
1.  Une rampe d’entrée reçoit le message. Selon le tiers émetteur ou le client, le message peut ou ne peut pas contenir un itinéraire qui définit les instructions de traitement du message.  
  
2.  Composants de pipeline ESB copient la feuille de route (s’il est présent dans l’en-tête SOAP) dans le contexte du message en tant que propriétés promues. Si le message est reçu sans un itinéraire, un composant de pipeline spécifique peut être configuré pour sélectionner l’itinéraire approprié à partir d’une base de données, selon le contenu du message ou le contexte, puis copiez la feuille de route dans le contexte du message. Pendant la durée de la durée de vie du message, l’itinéraire est conservée dans le contexte du message.  
  
3.  Dans le pipeline, l’itinéraire est évaluée et basée sur message des services d’itinéraire peuvent traiter le message. Ces services d’itinéraire peuvent transformer le message ou configurer des points de terminaison de routage.  
  
4.  Le message est publié dans la base de données de la boîte de Message de Microsoft BizTalk Server.  
  
5.  BizTalk Server évalue les propriétés promues du message et les files d’attente du message pour un ou plusieurs abonnés.  
  
6.  Les abonnés traitent le message à l’aide des mécanismes standards de BizTalk Server. Un abonné peut être une des opérations suivantes :  
  
    -   Port de réception une orchestration BizTalk Server avec un filtre configuré sur une liaison directe  
  
    -   Un serveur BizTalk dynamique port d’envoi, qui est également appelé une ESB rampe. La feuille de route détermine la façon dont le port est configuré pour continuer le traitement du message.  
  
 Comme alternative à un message arrive via un itinéraire rampe d’entrée, les orchestrations BizTalk Server peuvent également publier des messages dans la boîte de Message pour le traitement d’ESB :  
  
1.  Un message est créé dans une orchestration BizTalk Server.  
  
2.  Contexte du message est remplie avec la feuille de route ESB.  
  
3.  Le message est publié via un port de liaison directe à la base de données de la boîte de Message.