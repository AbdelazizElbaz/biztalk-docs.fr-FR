---
title: Gestion des niveaux de service | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: add50343-5470-4db3-a029-c827523e2f2c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86b7ba1672660af2a68a5d193729a0a9009173d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="service-level-management"></a>Gestion du niveau de service
Le Gestionnaire de niveau de Service SMS AmberPoint offre une visibilité en performances spécifiques et des problèmes de disponibilité dans les systèmes de niveau entreprise SOA. Il instrumente et effectue le suivi des métriques pour chaque Microsoft BizTalk Server l’emplacement de réception et le port d’envoi. Cela fournit l’indication d’intégrité et l’état en temps réel, en plus de la caractérisation des performances en cours de ces composants. La figure 1 illustre l’affichage des métriques associés à un emplacement de réception.  
  
 ![Emplacement de réception AmberPoint](../esb-toolkit/media/ch9-amberpointreceivelocation.gif "Ch9-AmberPointReceiveLocation")  
  
 **Figure 1**  
  
 **Les métriques associées à un emplacement de réception**  
  
 Analytique d’exécution AmberPoint permettre aux utilisateurs de définir des seuils et envoyer des alertes lorsqu’un système dépasse un seuil d’événements critiques, y compris les événements d’avertissements de conformité, les événements de violations de conformité et un retour suivant à la conformité. La figure 2 illustre l’affichage où les utilisateurs configurer des contrats de niveau de service et afficher les alertes générées pour ce contrat de niveau de service.  
  
 ![SLA AmberPoint](../esb-toolkit/media/ch9-amberpointsla.gif "Ch9-AmberPointSLA")  
  
 **Figure 2**  
  
 **Les écrans pour configurer un contrat de niveau de service et afficher des alertes**  
  
 Vous pouvez établir des objectifs de performances dans le niveau de Service Manager. Le logiciel puis effectue le suivi des messages individuels, des messages à partir d’un utilisateur spécifique ou des messages à partir de groupes d’utilisateurs, pour mesurer les performances par rapport à ces cibles.  
  
 Vous pouvez également configurer des stratégies de journalisation qui commandent aux AmberPoint SMS pour collecter et examiner le contexte du message et les données transitant par BizTalk Server, comme indiqué dans la Figure 3 dynamiquement. Vous pouvez ensuite utiliser ces journaux pour la résolution des problèmes « à la volée », pour une analyse des problèmes technique et d’archivage pour se conformer à des réglementations spécifiques.  
  
 ![Messages du Service BizTalk](../esb-toolkit/media/ch9-biztalkservicemessages.jpg "Ch9-BizTalkServiceMessages")  
  
 **Figure 3**  
  
 **Le fichier journal pour les messages du service BizTalk Server**