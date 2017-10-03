---
title: "Développement d’un Service de la Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorials, developing
- service solution tutorial, background information
- service solution tutorial, developing
- developing, tutorials
- developing, service solution tutorial
ms.assetid: 7979a05c-7fd3-4476-a623-55de8abdc493
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d8e33baa51a551d0f1f851410fda696abc96983
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-service-oriented-solution"></a>Développement d’un Service de la Solution orientée services
La solution orientée services illustre un système de consultation de solde de comptes pour Woodgrove Bank. Informations relatives à un compte proviennent de trois systèmes hérités : un système SAP qui fournit la limite de crédit, un système de transactions en attente en cours d’exécution sur un macroordinateur et un système de suivi de paiement à l’aide de MQSeries. Les demandes de vérification de solde sont transmises via un service Web ou un système de réponse vocale interactif. Pour plus d’informations sur ce scénario, consultez [présentation de la Solution orientée services](../core/understanding-the-service-oriented-solution.md).  
  
 Ce guide du développeur présente une approche pour la création d'une solution d'architecture orientée services pour le scénario Woodgrove Bank. Il commence par décrire une solution correspondant aux modèles normalisés du secteur. La section « Modèles de la solution orientée services » décrit la conversion de ces modèles en artefacts appropriés d'une application BizTalk. La section suivante (Composants de la solution orientée services) synthétise les différentes composantes de l'application et leurs relations. La section « Caractéristiques de l'implémentation » aborde divers aspects (tels que l'utilisation de l'authentification unique de l'entreprise) qui impliquent des étapes spécifiques pour satisfaire les critères du scénario. La section « Contrôle de la solution orientée services à l'aide de l'analyse BAM » décrit l'utilisation de l'API BAM par la solution pour suivre l'avancement des requêtes et des résultats. Les sections « Gestion des versions de la solution orientée services » et « Évolution de la solution orientée services » proposent des méthodes d'extension ou de modification de la solution. La section « Références » répertorie les fichiers de la solution et fournit une référence pour les messages.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Modèles dans le Service de la Solution orientée services](../core/patterns-in-the-service-oriented-solution.md)  
  
-   [Solution orientée services de composants du Service](../core/components-of-the-service-oriented-solution.md)  
  
-   [Caractéristiques de l’implémentation du Service orienté solutions](../core/implementation-highlights-of-the-service-oriented-solution.md)  
  
-   [Le Service d’analyse de la Solution avec BAM orientée services](../core/monitoring-the-service-oriented-solution-with-bam.md)  
  
-   [Solution orientée services de contrôle de version du Service](../core/versioning-the-service-oriented-solution.md)  
  
-   [Le Service de mise à l’échelle de la Solution orientée services](../core/scaling-the-service-oriented-solution.md)  
  
-   [Référence de la Solution orientée services](../core/service-oriented-solution-reference.md)