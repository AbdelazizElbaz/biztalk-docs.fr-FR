---
title: Instrumentation de meilleures pratiques pour les Solutions de haute Performance BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd16ea1e-055a-429b-912f-bff2b91f0fdb
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ef6f243f894071aebb0089f063ed0242ee09d9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instrumentation-best-practices-for-high-performance-biztalk-solutions"></a>Instrumentation de meilleures pratiques pour les Solutions BizTalk de hautes performances
Pour télécharger une copie de ce document, accédez à [http://go.microsoft.com/fwlink/?LinkId=205874](http://go.microsoft.com/fwlink/?LinkId=205874).  
  
 **Date de publication :** novembre 2010  
  
 **Auteur :** Valery Mizonov, Microsoft Corporation  
  
 **Révisé par :**  
  
-   Mark Simms, Microsoft Corporation  
  
-   Jayanthi Sampathkumar, Microsoft Corporation  
  
-   Krish Srinivasan, Microsoft Corporation  
  
 **S’applique à :** Microsoft BizTalk Server  
  
 **Résumé :** les méthodes traditionnelles d’instrumentation de solutions BizTalk pas peuvent toujours être le plus efficace à partir d’un point de vue des performances. L’instrumentation couramment utilisée et les composants de suivi en exploitant les API de débogage Win32 peuvent introduire un goulot d’étranglement potentiel et sont désormais chargés des dégradations de performances dans les applications multithread BizTalk en cours d’exécution sous une charge importante.  
  
 À partir de l’autre côté, instrumentation de code source fournit un niveau élevé de visibilité sur le comportement des applications et permet de réduire les efforts de dépannage générales. Par conséquent, une approche totalement nouvelle à l’instrumentation des solutions de haute performance BizTalk est devenue une importance cruciale activer la collecte des informations de diagnostic complet et détaillées de manière non intrusive avec pratiquement aucune surcharge et aucun impact sur les performances de l’application.  
  
 Le [équipe de consultants de client de Windows Server AppFabric](http://blogs.msdn.com/appfabriccat) chez Microsoft visant à fournir à la Communauté validés meilleures pratiques pour aider les développeurs BizTalk à enrichir leurs solutions et l’instrumentation de hautes performances en interne, adoptée par de nombreux produits Microsoft. Ces meilleures pratiques apparaissent sous la forme d’une structure réutilisable qui BizTalk les développeurs peuvent facilement incorporer et adopter dans leurs propres implémentations.  
  
 Vous pouvez télécharger une copie complète de [Instrumentation meilleures pratiques pour les Solutions de haute Performance BizTalk](http://go.microsoft.com/fwlink/?LinkId=205874) (http://go.microsoft.com/fwlink/?LinkId=205874) sur du Microsoft Download Center.