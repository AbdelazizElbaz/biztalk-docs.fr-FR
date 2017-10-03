---
title: "Analyse les définitions de l’état | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa2c8247-5e25-4624-9f0d-c7fe621ffba2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97007535e67a4c3540278cee7ff82fec18d492c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="state-monitoring-definitions"></a>Définitions de l’analyse d’état
Analyse de l’état aident à répondre à la question si un ordinateur contrôlé fonctionne correctement à un moment donné à partir de la perspective d’une application particulière. System Center Operations Manager (SCOM) met à jour l’état des différentes entités gérées présentées à l’utilisateur et affiche l’état en tant que partie de l’état d’affichage d’analyse.  
  
 Pour comprendre la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] état d’affichage d’analyse, vous devez comprendre les concepts d’analyse de l’état SCOM. La terminologie répertoriée ci-dessous est utilisée pour décrire les composants clés de la surveillance de l'état :  
  
-   **Rôle** -un rôle qui effectue un serveur dans un environnement, tel que déterminé par la découverte de service. Par exemple, le rôle d’exécution BizTalk encapsule les artefacts de runtime et les instances dans BizTalk Server.  
  
-   **Composant** -un rôle secondaire qui est utilisé dans le cadre de l’évolution de l’intégrité pour mesurer l’intégrité globale du rôle de serveur. Par exemple, le composant d’alerte BAM est utilisé pour générer des alertes pour indiquer l’état de santé.  
  
-   **Instance** -un ordinateur donné peut héberger une ou plusieurs instances du rôle de serveur.  
  
 En bref, voici les principes essentiels de l’analyse de l’état SCOM :  
  
-   Contrôle d’intégrité d’un groupe d’ordinateurs est dérivé de l’intégrité des ordinateurs qui sont contenus dans le groupe d’ordinateurs.  
  
-   L’état de l’ordinateur indique si les applications (désignées comme rôles de serveur) en cours d’exécution sur l’ordinateur sont sains, et l’état d’intégrité est dérivé de l’intégrité des applications hébergées.  
  
-   Au niveau de l'application (rôle de serveur), l'état du rôle de serveur correspond à l'état général de toutes les instances d'application de ce rôle de serveur. Par exemple, l’intégrité d’un ou plusieurs des artefacts tels que des orchestrations, reçoit des emplacements, reçoit les ports et ainsi de suite affecte l’état et l’intégrité globale d’une application BizTalk.  
  
-   Au niveau instance application (instance de rôle de serveur), l’intégrité de l’instance d’application est dérivée de l’intégrité des différentes zones de l’instance d’application (connue en tant que composants).  
  
-   Alertes SCOM sont associés à l’intégrité d’un composant. État d’un composant est défini sur rouge, jaune ou vert lorsque des alertes sont déclenchées pour indiquer l’état global.  
  
-   Le fonctionnement d'un composant contribue au fonctionnement du rôle de serveur.  
  
 Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
-   Chaque serveur BizTalk Server est considéré comme une instance de rôle BizTalk Server.  
  
-   Le rôle BizTalk Server dans un ordinateur est donc calculé comme le résultat de tous les événements/activités de l'ensemble des processus BizTalk Server de cet ordinateur.  
  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration fournit une analyse de l’état des artefacts BizTalk Server qui inclut  
  
-   Artefacts tels que les orchestrations de l’application. Composants de messagerie telles que ports de réception, emplacements de réception et ports d’envoi.  
  
-   Artefacts de déploiement tels que les serveurs, instances de l’hôte, l’authentification unique et ainsi de suite.  
  
 Le tableau suivant répertorie les trois États qui expriment de l’état d’intégrité de toutes les plates-formes et applications niveau artefacts de BizTalk Server. Cela fournit à l’opérateur SCOM une vue d’ensemble d’un déploiement de plusieurs serveurs afin de vous concentrer sur les problèmes importants rapidement.  
  
|Artefacts|Vert|Jaune|Rouge|  
|---------------|-----------|------------|---------|  
|Artefacts de niveau application|Sont en cours d’exécution.|Inférieur à 70 % des instances sont défectueux.|Plus de 70 % des instances sont défaillantes ou ont engendré des erreurs critiques.|  
|Artefacts de niveau de déploiement|Sont en cours d’exécution.|Non applicable|Ne sont pas en cours d’exécution ou est arrêté.|