---
title: "Mise en attente de l’orchestration et la réactivation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57d7c0bf-a707-4ebd-afab-e75dd80c3c34
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7cee568cda6c869ede94e28bce441462c0c7cdc
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="orchestration-dehydration-and-rehydration"></a>Mise en attente et réactivation des orchestrations
Lorsque plusieurs processus d'entreprise à long terme sont exécutés en même temps, la mémoire et les performances constituent des problèmes potentiels. Le moteur d'orchestration résout ces problèmes en « mettant en attente » et en « réalimentant » les instances d'orchestration.  
  
 La mise en attente est le processus qui consiste à sérialiser l'état d'une orchestration dans une base de données SQL Server. La réactivation est le processus inverse : la désérialisation du dernier état d’exécution d’une orchestration à partir de la base de données. La mise en attente est utilisée pour réduire au maximum l'utilisation de ressources système en réduisant le nombre d'orchestrations qui doivent être instanciées simultanément.  
  
## <a name="dehydration"></a>Mise en attente  
 Le moteur d'orchestration est susceptible de déterminer qu'une instance d'orchestration est inactive depuis relativement longtemps. Il calcule des seuils pour déterminer le temps pendant lequel il devra attendre que diverses actions aient lieu. Si ces seuils sont dépassés, il mettra en attente l'instance. Cela peut se produire dans les circonstances suivantes :  
  
-   Quand l'orchestration attend de recevoir un message et que l'attente est plus longue qu'un seuil déterminé par le moteur.  
  
-   Lorsque l’orchestration « écoute » pour un message, comme lorsque vous utilisez un **écouter** forme et qu’aucune branche est déclenchée avant un seuil déterminé par le moteur. La seule exception est lorsque le **écouter** forme contient une activation de réception.  
  
-   Quand, dans l'orchestration, un délai est plus long qu'un seuil déterminé par le moteur.  
  
 Le moteur met l'instance en attente en enregistrant l'état et libère la mémoire requise par l'instance. En mettant les instances d’orchestration dormantes, le moteur rend possible pour un grand nombre de processus d’entreprise longue à s’exécuter simultanément sur le même ordinateur.  
  
 Douze propriétés sont disponibles pour configurer le fonctionnement de la mise en attente dans BizTalk Server. Les rubriques de cette section fournissent une description de ces propriétés et de leur valeur par défaut, et présentent la manière dont les différentes valeurs affectent le comportement de la mise en attente.  
  
## <a name="rehydration"></a>Réactivation  
 Le moteur d'orchestration peut être amené à réalimenter une instance d'orchestration suite à la réception d'un message ou à l'expiration d'un délai spécifié dans une forme Attente. Il charge l’instance d’orchestration enregistrée dans la mémoire, restaure son état et il s’exécute à partir du point où elle s’est arrêté. Pour plus d’informations sur l’utilisation des formes dans les orchestrations, consultez [formes d’Orchestration](../core/orchestration-shapes.md).  
  
 Il est possible de configurer une orchestration pour qu'elle s'exécute sur plusieurs serveurs. Après sa mise en attente, une instance d'orchestration peut être réalimentée sur n'importe lequel de ces serveurs. Si un serveur tombe en panne, le moteur continue d’exécuter l’orchestration sur un autre serveur, à partir de son état précédent. Cette fonctionnalité permet également au moteur d'implémenter l'équilibrage des charges sur les serveurs.  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Propriétés par défaut de mise en attente](../core/dehydration-default-properties.md)  
  
-   [Mode de mise en attente de calcul](../core/how-to-calculate-dehydration.md)  
  
-   [Exemple de calcul de mise en attente](../core/sample-dehydration-calculation.md)  
  
-   [Compteurs de performances de la mise en attente des orchestrations](../core/orchestration-dehydration-performance-counters.md)  
  
-   [Fichier BTSNTSvc.exe.config](../core/btsntsvc-exe-config-file.md)  
  
-   [Autres activités susceptibles d’affecter le comportement de mise en attente](../core/other-activities-that-can-affect-dehydration-behavior.md)