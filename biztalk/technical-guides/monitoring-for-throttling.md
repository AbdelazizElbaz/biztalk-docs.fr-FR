---
title: Analyse de limitation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d1d4c72-6942-4572-b27f-c58d37c94062
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d60b9f3deb77df927eb055b4504b809b421ae663
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-for-throttling"></a>Analyse de limitation
Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration surveille les compteurs de performance qui indiquent l’état de limitation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Certains facteurs clés à comprendre à propos de limitation sont répertoriées ci-dessous.  
  
-   La limitation basée sur le taux est par hôte et est basée sur le taux de messages entrants et messages sortants.  
  
-   Pour la limitation de remise (**MsgBox -> Orchestration ou le Port d’envoi**), Taux entrant est la vitesse à laquelle les messages sont reçus à partir de la boîte de message. Taux de sortie est la vitesse à laquelle les messages sont remis via les cartes.  
  
-   Pour la limitation de la publication (**des adaptateurs de réception** ou **Orchestrations -> MsgBox),** Taux entrant est la vitesse à laquelle les messages sont reçus des cartes et taux de sortie est le taux de messages branché MsgBox.  
  
-   Aucun mécanisme de limitation n’existe entre les hôtes autres que nombre total de messages dans la base de données.  
  
 Pour plus d’informations, reportez-vous à la rubrique [comment BizTalk Server implémente la limitation des hôtes](http://go.microsoft.com/fwlink/?LinkID=155286) (http://go.microsoft.com/fwlink/?LinkID=155286) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comprend une fonction d'auto-limitation qui permet d'éviter une surcharge du serveur en fonction de divers paramètres. Une surcharge temporaire qui entraîne un ralentissement n'a pas de signification particulière du point de vue du fonctionnement. Un ralentissement persistant, en revanche, n'a pas lieu d'être dans un environnement stable et peut révéler la présence de problèmes sous-jacents au niveau de l'infrastructure. Le Pack d’administration fournit une analyse proactive de ces conditions de limitation persistantes avec les règles de seuil de performances.  
  
 Suivi de l’utilisation et de performances quatre règles d’étendue des périodes de ralentissement dû à quatre différentes conditions, comme indiqué dans le tableau suivant.  
  
|Condition|Règle|  
|---------------|----------|  
|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]mémoire de processus de service|Avertissement : Les Throttled de BizTalk sur la mémoire de processus élevée pendant longtemps|  
|Nombre de messages en cours de traitement|Avertissement : BizTalk Throttled sur haute Inprocess Message Count pendant longtemps|  
|Nombre de threads dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processus|Avertissement : Les Throttled de BizTalk sur le nombre de threads élevé pendant longtemps|  
|Taille de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les files d’attente de base de données|Avertissement : Les Throttled de BizTalk sur la taille de base de données importante pendant longtemps|  
  
 Ces règles de seuil utilisent des fournisseurs de données basées sur les compteurs de performance d’indicateur état de limitation. Pour plus d’informations sur ces compteurs de performance, reportez-vous à la section [les compteurs de Performance](http://go.microsoft.com/fwlink/?LinkId=157269) (http://go.microsoft.com/fwlink/?LinkId=157269) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
 Ces règles sont configurées pour déclencher une alerte si la moyenne pour un certain nombre d’échantillons dépasse un seuil donné (valeur par défaut est 30). Par exemple, « Avertissement : Throttled BizTalk sur la taille de base de données importante pendant une période significative » est une règle d’analyse de l’état de limitation de tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processus sur un ordinateur donné. Cette règle utilise un fournisseur de données basé sur la limitation état indicateur performances compteur « BizTalk : Agent-High de base de données taille. » Si la valeur de ce compteur est 1, le traitement associé connaît un ralentissement, avec pour cause une base de données trop volumineuse.  
  
 La règle précédente est configurée pour calculer une moyenne sur 30 échantillons et déclenche une alerte si la moyenne des échantillons est supérieure à 0,6. Étant donné que chaque échantillon est prélevé à un intervalle d’une minute, cela implique que sur les 30 dernières minutes, au moins un ou plusieurs processus BizTalk Server sur cet ordinateur ont ralenti en raison de la taille de la base de données élevé, 60 pour cent du temps.  
  
 Cette heuristique peut ne pas convenir à votre propre scénario d'application. En fonction du comportement historique dans votre environnement comme décrit auparavant, vous devez configurer ces règles avec les valeurs correctes par soit :  
  
-   Ajuster les exemples.  
  
-   Ajustement de la valeur de seuil.  
  
-   Si nécessaire, modifier l’intervalle d’échantillonnage pour le fournisseur.