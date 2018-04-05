---
title: Taille d’enregistrement dans les bases de données de suivi | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: be7a891b-2674-49a3-a8e0-6aa11a918bf2
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1f4d09d1af92ce4777f5036885d81ea7bf3e648
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="record-size-in-tracking-databases"></a>Taille d'enregistrement dans les bases de données de suivis
Pour vous aider à planifier la configuration matérielle requise pour BizTalk, le tableau suivant indique la taille d'enregistrement prévue pour différents enregistrements d'événement dans la base de données des suivis.  
  
|Type d’action|Taille|Remarques|  
|-----------------|----------|-----------|  
|Déploiement d'un service|1864 + taille des informations symboliques|Les informations symboliques dépendent de la taille de l'orchestration. Par exemple, une orchestration qui reçoit un message et renvoie un message contenant 2 formes nécessite environ 4 000 octets.|  
|Instance de service ayant démarré et abouti|Normalement, 252 octets.<br /><br /> 735 octets dans les cas extrêmes.||  
|Instance de service ayant démarré et échoué ou rencontré une erreur|Normalement, 252 octets + informations sur l'erreur.<br /><br /> 735 octets + les informations sur l'erreur dans les cas extrêmes.|Les informations sur l'erreur sont les données texte renvoyées par un composant BizTalk ou utilisateur. Elles peuvent nécessiter de 100 octets à 2 Ko.|  
|Début/fin d'une forme dans une orchestration|120 octets chacun.||  
|Événements d'entrée/sortie de message|162 octets au minimum.<br /><br /> Premier affichage du message : 202 octets + propriétés du message (si un suivi est effectué).<br /><br /> 2 930 octets dans les cas extrêmes.|Si aucun suivi des propriétés des messages n'est effectué, vous pouvez compter sur une taille moyenne de 128 octets.|  
|Taille des propriétés des messages|40 à 288 octets si DTA reconnaît les propriétés de suivi.<br /><br /> Ajoutez jusqu'à 268 octets s'il s'agit du suivi initial d'une propriété.||  
  
## <a name="see-also"></a>Voir aussi  
 [Quel est le suivi des messages ?](../core/what-is-message-tracking.md)   
 [Gestion et l’Architecture de suivi](../core/management-and-tracking-architecture.md)