---
title: "FAQ sur les adaptateurs WCF : Architecture de Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bad0063-ccff-41f4-b4e0-a02b49403c2d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b73b70474fd30e3a571f59558d6dc439cb981f64
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-adapter-faq-service-architecture"></a>Forum aux questions sur les adaptateurs WCF : Architecture du Service
## <a name="what-is-the-difference-between-a-wcf-custom-behavior-and-a-biztalk-pipeline-component"></a>Quelle est la différence entre un comportement personnalisé WCF et un composant de pipeline BizTalk ?  
 À première vue, un comportement personnalisé WCF est relativement semblable à un pipeline BizTalk classique. Tous deux sont basés sur le concept d'interception d'un message qui vise à interrompre le flux du message vers sa destination, exécuter des traitements personnalisés sur le message et transmettre celui-ci à sa destination. L'interception peut intervenir avant (si elle est liée à un emplacement de réception) ou après (si elle est liée à un port d'envoi) le traitement d'un message par BizTalk Server. Les modalités de l'interception en relation avec ces deux méthodes diffèrent non seulement en termes d'implémentation, mais également au niveau du point d'interception. Voici quelques différences :  
  
-   Les pipelines peuvent être utilisés par une orchestration. Les comportements WCF peuvent seulement être appelés par un adaptateur WCF depuis BizTalk Server.  
  
-   Les pipelines constituent une technologie plus ancienne, spécifique à BizTalk Server. Les comportements WCF peuvent être utilisés par BizTalk Server, mais également dans d'autres scénarios WCF purs.  
  
-   Pipelines dynamique au sein de l’ensemble de canalisation, telles que le décodage, validation, etc.. Les comportements WCF peuvent être branchés sur le flux de messages dans l’un de ses points d’entrée quatre l’interception (décrits brièvement).  
  
-   Les pipelines s'apparentent à un moteur d'exécution en termes de fonctionnalités. Il en va de même pour les comportements WCF, à la différence que ces derniers peuvent également appliquer des contraintes relationnelles ou de données sur la base des valeurs définies dans la configuration via la console Administration de BizTalk Server.  
  
-   Les pipelines peuvent agir sur un message BizTalk tandis que les comportements WCF agissent sur un message WCF. En d'autres termes, le pipeline peut effectuer diverses tâches telles que promouvoir une propriété de contexte BizTalk, tandis qu'un comportement WCF peut accéder à la propriété d'un message WCF.  
  
-   Il n'existe pas de modèle de messages à parties multiples dans WCF ou dans les adaptateurs WCF. Toutefois, comme un composant de pipeline peut manipuler le message BizTalk, il peut traiter un message à parties multiples le cas échéant.  
  
## <a name="for-the-receive-locations-or-send-ports-using-the-wcf-basichttp-and-wcf-wshttp-adapters-what-type-of-encoding-should-i-select"></a>Quel type de codage dois-je sélectionner pour les emplacements de réception et ports d'envoi qui utilisent les adaptateurs WCF-BasicHttp et WCF-WSHttp ?  
 Ces adaptateurs utilisent le codage de texte et de message HTTP. Le codage de message spécifie l'encodeur SOAP utilisé pour le message : MTOM (Message Transmission Organization Mechanism) ou Texte. Si l'option Texte est sélectionnée, le codage de texte doit être sélectionné. Les valeurs possibles sont unicodeFFF (Big Endian), utf-16 (codage 16 bits) et utf-8 (codage 8 bits).  
  
 MTOM est le mécanisme de transfert le plus efficace pour les données binaires. Il requiert toutefois que le service puisse traiter les données MTOM, de sorte que cette option est moins portable que l'option Texte brut. Dans le cadre du transfert standard de données non binaires, MTOM peut être moins efficace que l'option Texte. Cette dernière est universellement acceptée et offre une interopérabilité multiplateforme accrue. Elle constitue toutefois le choix le moins efficace si les données transmises contiennent des éléments non textuels. Il s'agit d'un aspect important lors du choix des liens de codage dans le cadre de l'utilisation des contrats de service WCF. La connaissance des données que les opérations WCF transfèrent et traitent affecte le choix du codage de message.