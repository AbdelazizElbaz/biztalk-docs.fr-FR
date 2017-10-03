---
title: "En cours d’exécution Orchestrations3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, running
- Receive shape [Orchestration Designer], starting orchestrations
- Start Orchestration shape [Orchestration Designer], starting orchestrations
- Call Orchestration shape [Orchestration Designer], starting orchestrations
- Receive shape [Orchestration Designer], activating orchestrations
ms.assetid: 5bfe61c9-80e0-4a0a-b6b1-ab48037e665e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 550fc1e03f3583215a817028917000c9a9c3074a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-orchestrations"></a>Orchestrations en cours d’exécution
Instances d’orchestration sont conçus pour être déclenchées soit par un appel explicite à partir d’une autre orchestration, à l’aide un **appeler Orchestration** forme ou **démarrer Orchestration** forme, ou à la réception d’un message d’activation. Le schéma du message d’activation est spécifié dans le **Message** propriété. Vous devez concevoir votre orchestration en conséquence, et définissez la **activer** propriété sur un **réception** forme sur true ou assurez-vous qu’une orchestration d’appel existe et qu’il est configurée correctement pour exécuter le nouvelle orchestration.  
  
 Avant qu'une instance puisse s'exécuter, vous devez lier et déployer l'assembly BizTalk, puis inscrire et démarrer le moteur d'orchestration afin de mettre en route le traitement. Pour plus d’informations, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md) et [déploiement et la gestion des Applications BizTalk](../core/deploying-and-managing-biztalk-applications.md). Lorsqu'une orchestration est appelée à partir d'une autre orchestration, ou qu'un message est présenté au moteur qui correspond aux critères d'une réception avec activation, le moteur crée une nouvelle instance de l'orchestration et l'exécute. Le moteur peut exécuter de nombreuses instances différentes simultanément.  
  
## <a name="calling-and-starting-orchestrations"></a>Appel et démarrage d'orchestrations  
 Le **appeler Orchestration** forme et **démarrer Orchestration** forme peut être utilisée pour activer une autre orchestration. Dans les deux cas, l'appelant peut transmettre des paramètres pour échanger des informations avec l'autre orchestration. Pour plus d’informations, consultez [comment ajouter des paramètres aux Orchestrations](../core/how-to-add-parameters-to-orchestrations.md).  
  
## <a name="using-activation-receives-with-filter-expression"></a>Utilisation des réceptions avec activation avec une expression de filtre  
 Le **réception** forme peut-être également utiliser une expression de filtre pour requérir d’autres critères pour l’activation. Si le message est du type approprié et une ou plusieurs propriétés du message de répondre à tous les critères dans l’expression de filtre, le **réception** forme accepte le message et l’orchestration est activée. Une telle forme réception est appelée un *réception avec activation*.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer la forme appeler Orchestration](../core/how-to-configure-the-call-orchestration-shape.md)   
 [Comment configurer la forme Démarrer Orchestration](../core/how-to-configure-the-start-orchestration-shape.md)   
 [Comment configurer la forme réception](../core/how-to-configure-the-receive-shape.md)   
 [Création et l’exécution des Orchestrations](../core/building-and-running-orchestrations.md)