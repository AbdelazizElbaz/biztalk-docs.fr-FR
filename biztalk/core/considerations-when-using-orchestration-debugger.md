---
title: "Considérations sur l’utilisation du débogueur d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Orchestration Debugger, modified orchestrations
- Orchestration Debugger, planning
- atomic scopes
- planning, Orchestration Debugger
- Orchestration Debugger, atomic scopes
- Orchestration Debugger, simple types
- orchestrations, modifying
ms.assetid: 55bfef48-08bd-48bb-abd5-7264e683da46
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2815da55bc74d822cb5fe2540347855db75b3a8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-using-orchestration-debugger"></a>Informations sur l'utilisation du débogueur de l'orchestration
Les informations suivantes sont à prendre en compte lors de l'utilisation du débogueur de l'orchestration.  
  
## <a name="tracking-atomic-scopes"></a>Suivi des étendues atomiques  
 Une orchestration peut contenir des étendues atomiques permettant d'inclure des appels dans le moteur des règles. Si vous joignez une instance dans le débogueur de l'orchestration, toute étendue atomique dans l'instance de l'orchestration provoquera l'apparition d'emplacements vides dans la liste des événements suivis. Ceci se produit pour deux raisons :  
  
-   Les événements pour les formes à l'intérieur des transactions atomiques ne sont pas conservées tant que l'étendue n'est pas validée.  
  
-   Le débogueur recharge des événements à la fin de la liste, de sorte que tous les emplacements vides le restent pendant la session active.   
  
 Pour éliminer les emplacements vides, actualisez la vue.  
  
> [!NOTE]
>  Vous ne pouvez pas définir un point d'arrêt sur des formes à l'intérieur d'une étendue atomique.  
  
## <a name="setting-breakpoints-in-the-exception-handler-scope"></a>Définition de points d'arrêt dans l'étendue du gestionnaire d'exception  
 Si le point d'arrêt est défini au niveau du gestionnaire catch d'exception, les types d'exceptions doivent être marqués comme étant sérialisables, faute de quoi le débogueur d'orchestrations ne s'arrêtera pas aux points d'arrêt définis. Cela est dû au fait que le débogueur d'orchestrations effectue une persistance au niveau du point d'arrêt. Par conséquent, lorsque l'état de l'instance d'orchestration comporte un objet non sérialisable, une exception de persistance est générée, et, dans le cas présent, une exception DebugBreakPointFailedException est également envoyée.  
  
## <a name="tracking-a-modified-orchestration"></a>Suivi d'une orchestration modifiée  
 Si vous suivez une orchestration modifiée sans changer le numéro de version, vous devez redémarrer toutes les instances hôtes auxquelles l'orchestration est inscrite. Cette opération garantit que toute modification de forme dans la nouvelle version déployée s'affiche correctement pendant votre utilisation du débogueur de l'orchestration.  
  
## <a name="tracking-simple-types"></a>Suivi des types simples  
 Le débogueur de l'orchestration ne prend en charge que les types simples. Par exemple, si vous effectuez le suivi d'un message multipartie contenant un objet .NET, vous pouvez afficher les propriétés de toutes les parties du message, à l'exception des propriétés de l'objet .NET.  
  
 Lorsqu'une orchestration apparaît avec l'état Point d'arrêt et que le débogueur de l'orchestration démarre, vous pouvez exécuter les actions suivantes :  
  
-   Utilisez le **attacher** option de service.  
  
-   vérifier les étapes déjà achevées ;  
  
-   afficher l'état des variables et des messages ;  
  
-   définir des points d'arrêt supplémentaires ;  
  
-   Sélectionnez le **continuer les services** option.  
  
-   répéter une étape autant de fois que nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Mode interactif dans le débogueur de l’Orchestration](../core/interactive-mode-in-orchestration-debugger.md)   
 [Débogage d’une Orchestration](../core/debugging-an-orchestration.md)