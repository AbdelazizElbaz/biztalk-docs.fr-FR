---
title: La gestion des artefacts | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], artifacts
- managing [artifacts]
- artifacts, managing
- managing [artifacts], about managing artificats
ms.assetid: aa7c5e60-7c16-4bcf-b913-b1bdfc5c7543
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ccca48682f009a24f538015b055c45dd79a9587
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-artifacts"></a>Gestion des artefacts
Cette section explique comment gérer les artefacts, notamment comment les ajouter à une application BizTalk et les en supprimer, et comment configurer leurs propriétés.  
  
 Les artefacts sont les éléments contenus dans une application BizTalk nécessaires à son exécution. Pour des informations générales sur l’utilisation des artefacts dans une application BizTalk, consultez [qu’est une Application BizTalk ?](../core/what-is-a-biztalk-application.md) Pour plus d’informations générales sur les artefacts, consultez [Architecture d’exécution](../core/runtime-architecture.md). Pour plus d’informations sur la gestion des artefacts lorsque vous créez et modifiez une application BizTalk, consultez [création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md).  

## <a name="tracking-artifacts"></a>Artefacts de suivi
Une grande partie de la gestion des artefacts que vous créez est suivi. La console Administration de BizTalk Server permet de configurer diverses options de suivi pour les orchestrations, ports d'envoi, ports de réception et pipelines. Vous pouvez modifier ces options à tout moment, sans interrompre le processus d'entreprise.

Les paramètres de configuration du suivi permettent de suivre les types de données suivants :

- les données d'événements entrants et/ou sortants, par exemple, l'ID d'un message, les heures de début et de fin d'un artefact ;

- les propriétés de messages entrants et/ou sortants, par exemple, les propriétés générales et promues de chaque message traité par l'artefact ;

- les corps et parties de messages entrants et/ou sortants, par exemple, le corps et les parties de chaque message traité par l'artefact ;

- Orchestrations : données d'exécution des formes d'orchestration.

[Affichage du Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md) fournit des informations de bonne. 


> [!TIP]
> Si vous définissez des options de suivi sur un pipeline, les options de suivi sont définies globalement pour tous les ports qui utilisant le pipeline. Par conséquent beaucoup plus de données en cours de suivi que vous éventuellement l’intention d’et pouvez avoir un impact sur les performances du système. Pendant le développement, cela peut être normal. Dans les scénarios de production, nous vous recommandons d’activer les options de suivi sur les ports d’envoi et de ports, au lieu des pipelines de réception.
  
## <a name="in-this-section"></a>Contenu de cette section  
  
-   [La gestion des Orchestrations](../core/managing-orchestrations.md)  
  
-   [Gestion des liens de rôle](../core/managing-role-links.md)  
  
-   [La gestion des Ports d’envoi et groupes de ports d’envoi](../core/managing-send-ports-and-send-port-groups.md)  
  
-   [La gestion des Ports de réception](../core/managing-receive-ports.md)  
  
-   [La gestion des emplacements de réception](../core/managing-receive-locations.md)  
  
-   [Gestion des stratégies](../core/managing-policies.md)  
  
-   [Gestion des schémas](../core/managing-schemas.md)  
  
-   [La gestion des mappages](../core/managing-maps.md)  
  
-   [Gestion des Pipelines](../core/managing-pipelines.md)  
  
-   [La gestion des ressources](../core/managing-resources.md)