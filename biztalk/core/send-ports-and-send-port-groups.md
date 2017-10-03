---
title: "Ports d’envoi et groupes de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, states
- send port groups
- send port groups, states
- send ports, about send ports
- send ports
- send port groups, about send port groups
- states, send ports
ms.assetid: 274bdd27-9098-46a2-8762-8b57bbfc95b8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e57e56d05cf3b1a98bba83d0df92d52f09c6eda5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="send-ports-and-send-port-groups"></a>Ports d'envoi et groupes de ports d'envoi
A *port d’envoi* est l’emplacement dans lequel Microsoft BizTalk Server envoie des messages ou à partir de laquelle BizTalk Server reçoit des messages. Le port d'envoi apporte à BizTalk Server la technologie dont il a besoin pour mettre en œuvre l'action de communication. Le nom du port identifie l'emplacement de façon unique.  
  
 Chaque fois qu'un message est envoyé à un port d'envoi, une nouvelle instance d'un service de port d'envoi est créée. Il s'agit d'une instance de service, également appelée instance de port d'envoi.  
  
> [!NOTE]
>  Il ne peut y avoir qu'une instance d'un port d'envoi de livraison chronologique.  
  
 A *groupe de ports d’envoi* est une collection nommée de ports d’envoi que BizTalk Server peut utiliser pour envoyer le même message à plusieurs destinations dans une configuration.  
  
 BizTalk Server peut acheminer directement des messages des emplacements de réception vers un port d'envoi ou vers un groupe de ports d'envoi. BizTalk Server envoie les messages acheminés vers un groupe de ports d'envoi à tous les ports d'envoi de ce groupe.  
  
 Les ports d'envoi qui sont membres d'un groupe de ports d'envoi traitent les messages de deux manières :  
  
-   En tant que membre d'un groupe de ports d'envoi  
  
-   Comme si BizTalk Server avait acheminé les messages directement au port d'envoi  
  
## <a name="send-port-and-send-port-group-states"></a>Ports d'envoi et états du groupe de ports d'envoi  
 La Console Administration de BizTalk affiche des ports d’envoi et groupes de ports d’envoi dans un des états suivants :  
  
-   **Lié**. à l'aide de la console Administration de BizTalk Server, un administrateur lie le port d'envoi ou le groupe de ports d'envoi à une orchestration. Avant que BizTalk Server achemine des messages vers ce port ou ce groupe, un administrateur doit inscrire et démarrer le port d'envoi ou le groupe de ports d'envoi lié.  
  
-   **Démarré**. l'abonnement au port d'envoi ou au groupe de ports d'envoi existe et est actif. Lorsque le port d'envoi ou le groupe de ports d'envoi sont dans l'état Démarré, BizTalk Server remet des messages à ce port ou à ce groupe pour qu'il les traite. Avant de démarrer un port d'envoi ou un groupe de ports d'envoi, un administrateur doit utiliser la console Administration de BizTalk pour inscrire ce port ou ce groupe de ports lié.  
  
-   **Arrêté**. le port d'envoi ou le groupe de ports d'envoi n'est pas exécuté. Si vous l'avez démarré, puis arrêté, le traitement se poursuit dans la file d'attente de travail. BizTalk Server envoie tous les nouveaux messages acheminés vers un port ou un groupe de ports d'envoi à la file d'attente des messages interrompus de l'hôte, sur lequel le gestionnaire d'envoi est exécuté.  
  
 Le tableau suivant répertorie les actions disponibles dans chaque état et le résultat obtenu à chaque fois.  
  
||Lié|Arrêté|Démarré|  
|------|-----------|-------------|-------------|  
|**Inscrire**|Arrêté|Non disponible|Non disponible|  
|**Démarrer**|Démarré|Démarré|Non disponible|  
|**Arrêter**|Non disponible|Non disponible|Arrêté|  
|**Annuler l’inscription**|Non disponible|Lié|Lié|  
  
 L'état combiné d'un port d'envoi et le groupe de ports d'envoi auquel il appartient déterminent si ce port ou ce groupe traite ou non un message.  
  
 Le tableau suivant décrit les combinaisons d'états possibles pour les ports d'envoi et les groupes de ports d'envoi.  
  
|Message envoyé|État de groupe de ports d'envoi|État du port d'envoi|Résultat|  
|------------------|------------------------------|------------------------|-------------|  
|Directement au port d'envoi|Tout état|Démarré|Message traité|  
|Directement au port d'envoi|Tout état|Arrêté|Message suspendu|  
|Au port d'envoi via un groupe de ports d'envoi|Démarré|Démarré|Message traité|  
|Au port d'envoi via un groupe de ports d'envoi|Tout état|Arrêté|Message suspendu|  
|Au port d'envoi via un groupe de ports d'envoi|Arrêté|Tout état|Message suspendu|  
  
## <a name="see-also"></a>Voir aussi  
 [Artefacts](../core/artifacts.md)