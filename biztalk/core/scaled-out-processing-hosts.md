---
title: "Montée en charge des hôtes de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- high availability
- hosts, processing
- hosts, high availability
- scaling, hosts
- hosts, planning
- hosts, scaling
- clustering
ms.assetid: c72ce8fc-7593-4700-8398-23d1a20515c3
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01ee36777a5c64713fd31e86fe6ef2a1886b3348
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-out-processing-hosts"></a>Mise à l'échelle des hôtes de traitement
Un hôte de traitement mis à l'échelle permet d'améliorer les performances et fournit une disponibilité élevée en isolant la fonctionnalité d'orchestration sur deux ordinateurs hôtes distincts (ou plus). Ce principe d'isolation permet d'ajouter plusieurs ordinateurs dans un hôte de traitement afin d'obtenir une redondance. Dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un hôte de traitement exécute une ou plusieurs instances d'hôtes capables de coordonner les différents processus d'entreprise et crée une instance d'objets de programmation pour les orchestrations.  
  
 Le schéma suivant montre un déploiement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui offre une disponibilité élevée à l'hôte de traitement en mettant à sa disposition deux ordinateurs pour exécuter ses instances. Remarquez que les hôtes de réception et d'envoi représentés ici ne sont pas des hôtes hautement disponibles.  
  
 ![Monté en charge de l’hôte de traitement](../core/media/tdi-ha-scaleprocess.gif "TDI_HA_ScaleProcess")  
  
 Dans cette configuration, la charge de travail représentée par le traitement des orchestrations est répartie entre deux ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comportant des instances de l'hôte de traitement et s'exécutant indépendamment l'un de l'autre. Si l'un des ordinateurs rencontre des problèmes ou s'arrête, le serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise automatiquement l'instance de l'hôte présente sur l'autre ordinateur afin de traiter les orchestrations restantes.  
  
## <a name="maintaining-orchestration-state"></a>Gestion de l'état de l'orchestration  
 Le serveur BizTalk Server gère l'état de l'orchestration de manière centralisée dans Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et non localement sur chaque ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En conservant l'état de l'orchestration dans la base de données MessageBox, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contourne le problème que représente le fait de ne s'appuyer que sur une seule instance de l'hôte de traitement pour l'orchestration. En outre, il est alors possible à n'importe quelle instance de l'hôte de traitement de traiter l'orchestration. Si une erreur se produit alors que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est en cours de traitement d'une orchestration, une autre instance du même hôte de traitement peut terminer le processus d'orchestration à partir du dernier état conservé.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de la haute disponibilité pour des hôtes BizTalk](../core/providing-high-availability-for-biztalk-hosts.md)