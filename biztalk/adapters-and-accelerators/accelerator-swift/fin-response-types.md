---
title: "Types de réponse FIN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, response types
- deploying, schemas
- FIN Response Reconciliation, message types
- FRR, deploying schemas
- schemas, deploying
- FIN Response Reconciliation, response types
- messages, message types
- response types [FIN Response Reconciliation]
ms.assetid: a6ef2f20-08ab-40d3-a0a5-cc4048ce0987
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54c890a5e0f51207cce1897b10095a87ae438793
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fin-response-types"></a>Types de réponse FIN
Rapprochement de réponse FIN (FRR) rapproche les réponses à un message de FIN de SWIFT catégorie 0 à 9. En réponse à un de ces messages FIN, l’application de la FIN de SWIFT toujours envoie au moins et éventuellement plusieurs, accusé de réception (ACK) ou (NAK) de l’accusé de réception négatif. Le tableau suivant présente les types des messages sortants et entrants (réponse) les messages traités par FRR.  
  
|Sortant /<br /><br /> en entrée|type de message|État du message|  
|----------------------------|------------------|--------------------|  
|Sortant|Tous les types de messages SWIFT FIN catégorie 0 à 9|Néant|  
|Trafic entrant|MQ Series panoramique/NAN (au niveau du transport MQSeries l’accusé de réception/NON-RÉCEPTION)|Accusé de réception de transport MQSeries|  
||MT010 (avertissement de non-remise)|SWIFT envoyé avec succès la version d’origine du message au partenaire, mais n’est pas informé que le partenaire a reçu le message. Si [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] reçoit plusieurs messages d’avertissement de Non remise (NDW), il effectue une itération et attend que le prochain message attendu.|  
||MT011 (accusé de réception)|SWIFT envoyé avec succès la version d’origine du message au partenaire et a reçu une indication que le partenaire a reçu le message.|  
||MT012 (Notification de l’expéditeur)|SWIFT a reçu le message d’origine à partir de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].|  
||MT015 (DNK ou NAK retardé)|SWIFT n'a pas envoyé le message d’origine au partenaire.|  
||MT019 (abandon de Notification)|Interruption de la transmission de message à SWIFT.|  
||MTS21_FIN_ACKNAK (accusé de réception ou un accusé de réception négatif d’un message FIN envoyé par un LT (accusé de réception/NON-RÉCEPTION))|SWIFT avec ou sans succès a reçu le message de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. Ce message décrit ces deux cas. S’il s’agit d’un accusé de réception ou un NAK est déterminée par la valeur dans le champ 451 du message (« 0 » pour l’accusé de réception) et « 1 » pour NAK. Il s’agit de la première réponse remise à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].|  
  
## <a name="deployment-of-schemas-for-frr"></a>Déploiement de schémas pour FRR  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]le programme d’installation déploie des schémas dans FrrSchemas.dll pour tous les messages au niveau du système (comme indiqué dans le tableau ci-dessus). L’orchestration FRR requiert ces schémas à déployer. Étant donné que [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] le programme d’installation déploie ces schémas dans FrrSchemas.dll, vous n’avez pas à et ne devez pas déployer ces schémas dans un autre projet. Ceci génère une erreur.  
  
 FRRSchemas.dll inclut les schémas suivants :  
  
-   TransportAck  
  
-   MT010  
  
-   MT011  
  
-   MT012  
  
-   MT015  
  
-   MT019  
  
-   MTS21_FIN_ACKNAK