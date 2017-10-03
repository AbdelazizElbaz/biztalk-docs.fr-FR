---
title: "Conversion des modèles de la Solution de gestion des processus métier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- artifacts, patterns
- patterns [process management solutions], orchestration boundaries
- patterns [process management solutions], translating patterns to artifacts
- orchestrations, patterns
- orchestrations, boundaries
ms.assetid: 69f37732-f235-4bbb-bc85-31b4971c95ce
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23603e66e80461baecea88648100442eb9da0166
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="translating-the-patterns-of-the-business-process-management-solution"></a>Conversion des modèles de la Solution gestion des processus d’entreprise
Cette section décrit les modalités de conversion du diagramme modèle en artefacts BizTalk Server par la solution.  
  
 ![Modèles de Solution gestion des processus métier](../core/media/bts-cp-business-process-management-patterns.gif "bts_cp_Business_Process_Management_Patterns")  
  
## <a name="connections"></a>Connexions  
 Les connexions représentent les chemins d'accès des messages entre les composants de la solution. Il est plus simple de commencer par l'interface du service. BizTalk Server simplifie la présentation d'une orchestration en tant que service Web. Pour plus d’informations sur l’exposition des orchestrations en tant que services web, consultez [comment le mappage des Orchestrations aux Services Web](../core/how-to-map-orchestrations-to-web-services.md).  
  
 D'autres connexions existent entre le service et la section de prétraitement, entre la section de prétraitement et le gestionnaire de processus, et entre le gestionnaire de processus et les étapes du traitement. Des connexions existent également entre les étapes et les systèmes principaux, ainsi qu'entre le prétraitement, la base de données de l'historique et le système de service.  
  
> [!NOTE]
>  Les convertisseurs correspondent aux mappages BizTalk. Les cartes sont, à son tour, parties de pipelines ou **transformer** formes d’orchestration.  
  
 Le choix du type de la connexion (synchrone ou asynchrone) au gestionnaire de processus demande de la réflexion. Contrairement à une vérification de solvabilité, l'exécution d'une commande dans le cadre d'un processus (par exemple, commande de service de câble) prend généralement du temps. La logique de gestion du processus est plus complexe si la connexion au gestionnaire de processus est asynchrone et nécessite une corrélation. En effet, cette solution utilise une connexion asynchrone au gestionnaire de processus en publiant des messages dans la base de données MessageBox.  
  
 Les connexions entre le gestionnaire de processus et les étapes représentent un compromis similaire entre la préservation des ressources de serveur et la simplification de la logique. Le délai de traitement des étapes est plus court que celui du gestionnaire de processus. Chaque étape doit être terminée avant que le traitement ne passe à l'étape suivante. Cependant, comme les étapes peuvent être modifiées, le gestionnaire de processus ne peut pas être étroitement couplé avec elles. Dans l'application, la connexion peut être décrite comme un modèle de publication/abonnement limité. Le gestionnaire de processus envoie des messages aux étapes via un port dédié unique. De leur côté, les étapes filtrent les messages pour récupérer ceux qui leur sont destinés.  
  
## <a name="determining-orchestration-boundaries"></a>Identification des limites de l'orchestration  
 Le modèle se situe en trois zones principales : prétraitement des messages, la gestion des processus d’entreprise et le processus d’entreprise lui-même. Le prétraitement gère la connexion à un service Web, convertit les messages en messages pour la réponse, notifie le système de service, crée des entrées dans la base de données de l'historique et transmet les messages au gestionnaire de processus. Dans l'application, le prétraitement est géré par une seule orchestration. Une autre orchestration gère le processus d'entreprise. Le processus d'entreprise géré est divisé en étapes appropriées. Chaque étape correspond à une orchestration pour permettre l'insertion d'ajouts et de suppressions représentant les modifications du processus de commande. Pour plus d’informations sur la conception des étapes de traitement de commande, consultez « Division des processus d’entreprise » dans [certains principes de conception dans la Solution de gestion des processus métier](../core/some-design-principles-in-the-business-process-management-solution.md).  
  
## <a name="translating-the-components-into-orchestrations"></a>Conversion des composants en orchestrations  
 La première orchestration **OrderBroker**, convertit le diagramme de façon simple et directe. L'orchestration assure le mappage des formes utilisées pour créer les messages de notification et le message de commande pour le gestionnaire de processus. Pour obtenir une liste complète des formes d’orchestration, consultez [formes d’Orchestration](../core/orchestration-shapes.md).  
  
 La logique du gestionnaire de processus et de ses assemblys est relativement complexe. Pour plus d’informations sur la logique de l’orchestration du Gestionnaire de processus, **OrderManager**, consultez [logique du Gestionnaire de processus](../core/process-manager-logic.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles dans la Solution gestion des processus d’entreprise](../core/patterns-in-the-business-process-management-solution.md)   
 [Conception de modèles : la Solution gestion des processus d’entreprise](../core/designing-with-patterns-the-business-process-management-solution.md)   
 [Catalogue de modèles pour la Solution gestion des processus d’entreprise](../core/pattern-catalog-for-the-business-process-management-solution.md)