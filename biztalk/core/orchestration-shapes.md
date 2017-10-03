---
title: "Formes d’orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Delay shape [Orchestration Designer]
- Loop shape [Orchestration Designer]
- Throw Exception shape [Orchestration Designer]
- Expression shape [Orchestration Designer]
- Decide shape [Orchestration Designer]
- Receive shape [Orchestration Designer]
- Compensate shape [Orchestration Designer]
- orchestrations, shapes
- Suspend shape [Orchestration Designer]
- Send shape [Orchestration Designer]
- Group shape [Orchestration Designer]
- Listen shape [Orchestration Designer]
- shapes, about shapes
- Construct Message shape [Orchestration Designer]
- Parallel Actions shape [Orchestration Designer]
- Call Rules shape [Orchestration Designer]
- Start Orchestration shape [Orchestration Designer]
- Transform shape [Orchestration Designer]
- Message Assignment shape [Orchestration Designer]
- Role Link shape [Orchestration Designer]
- Call Orchestration shape [Orchestration Designer]
- Port shape [Orchestration Designer]
- shapes
- Scope shape [Orchestration Designer]
- Terminate shape [Orchestration Designer]
- Orchestration Designer, shapes
- Insufficient Configuration Smart Tag [Orchestration Designer]
ms.assetid: a1d03baa-a267-499d-94fc-700b3e959458
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 181656208b757c595feb9d19ee786fe91f1b78f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-shapes"></a>Formes d'orchestration
Le Concepteur d'orchestration est un outil visuel permettant de créer des orchestrations Il fournit plusieurs formes que vous pouvez placer sur la surface de conception en tant que représentations visuelles d'actions sous-jacentes, et qui vous permettent de concevoir et d'implémenter efficacement une orchestration.  
  
 **Action de Configuration insuffisante**  
  
 ![](../core/media/ebiz-orch-insufficconfig.gif "ebiz_orch_insufficconfig")  
  
> [!NOTE]
>  L’action relative à une configuration insuffisante s’affiche dans le Concepteur d’orchestration lorsque celui-ci détecte que la forme associée n’est pas complètement configurée. Si une forme dans une orchestration n'est pas complètement configurée, l'orchestration associée ne se compilera pas.  
  
 Le tableau suivant répertorie les formes disponibles et propose une brève description de la fonction de chacune d'elles.  
  
|Graphique à base de formes|Nom de la forme|Fonction|  
|-----------|----------------|-------------|  
|![](../core/media/ebiz-orch-callorchestrat.gif "ebiz_orch_callorchestrat")|**Appeler Orchestration**|Permet à l'orchestration d'en appeler une autre de façon synchronisée.|  
|![](../core/media/ebiz-orch-call-rules.gif "ebiz_orch_call_rules")|**Appeler règles**|Permet de configurer une stratégie de règles d'entreprise à exécuter dans l'orchestration.|  
|![](../core/media/ebiz-orch-compensate.gif "ebiz_orch_compensate")|**Compenser**|Permet d'appeler un code pour annuler ou compenser les opérations déjà effectuées par l'orchestration en cas d'erreur.|  
|![](../core/media/ebiz-orch-constructmsg.gif "ebiz_orch_constructmsg")|**Forme construire un Message**|Permet de construire un message.|  
|![](../core/media/ebiz-orch-decide.gif "ebiz_orch_decide")|**Décider**|Permet d'exécuter la branche sous certaines conditions dans l'orchestration.|  
|![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")|**Délai**|Permet de créer des délais d'attente dans l'orchestration en fonction d'un intervalle.|  
|![](../core/media/ebiz-orch-assign.gif "ebiz_orch_assign")|**Expression**|Permet d'affecter des valeurs aux variables ou d'exécuter des appels .NET.|  
|![](../core/media/ebiz-orch-group.gif "ebiz_orch_group")|**Grouper**|Vous permet de regrouper des opérations dans une seule unité réductible et développable pour des raisons de commodité visuelle.|  
|![](../core/media/ebiz-orch-listen.gif "ebiz_orch_listen")|**Écouter**|Permet à l'orchestration d'exécuter la branche sous certaines conditions selon les messages reçus ou l'expiration du délai.|  
|![](../core/media/ebiz-orch-loop.gif "ebiz_orch_loop")|**Boucle**|Permet à l'orchestration de boucler jusqu'à ce que la condition soit remplie.|  
|![](../core/media/ebiz-orch-assign.gif "ebiz_orch_assign")|**Assignation du message**|Permet d'attribuer des valeurs de message.|  
|![](../core/media/ebiz-orch-paralactions.gif "ebiz_orch_paralactions")|**Actions parallèles**|Permet à l'orchestration d'exécuter plusieurs opérations indépendamment les unes des autres.|  
|![](../core/media/ebiz-orch-port.gif "ebiz_orch_port")|**Port**|Définit le moment et le mode de transmission des messages.|  
|![](../core/media/ebiz-orch-receive.gif "ebiz_orch_receive")|**Réception**|Permet de recevoir un message dans l'orchestration.|  
|![](../core/media/ebiz-orch-rolelink.gif "ebiz_orch_rolelink")|**Lien de rôle**|Permet de créer un ensemble de ports communiquant avec le même partenaire logique, éventuellement via des transports ou points de terminaison différents.|  
|![](../core/media/ebiz-orch-scope.gif "ebiz_orch_scope")|**Portée**|Fournit un cadre pour la gestion des transactions et des exceptions.|  
|![](../core/media/ebiz-orch-send.gif "ebiz_orch_send")|**Envoyer**|Permet d'envoyer un message à partir de l'orchestration.|  
|![](../core/media/ebiz-orch-strtorchestrat.gif "ebiz_orch_strtorchestrat")|**Démarrer Orchestration**|Permet l’orchestration à appeler une autre orchestration de manière asynchrone.|  
|![](../core/media/ebiz-orch-suspend.gif "ebiz_orch_suspend")|**Suspendre**|Suspend l'opération de l'orchestration afin de permettre une intervention en cas d'erreur.|  
|![](../core/media/ebiz-orch-terminate.gif "ebiz_orch_terminate")|**Arrêter**|Permet de mettre fin immédiatement à l'opération de l'orchestration en cas d'erreur.|  
|![](../core/media/ebiz-orch-throwexcept.gif "ebiz_orch_throwexcept")|**Lever Exception**|Permet de lever une exception de façon explicite en cas d'erreur.|  
|![](../core/media/ebiz-orch-transform.gif "ebiz_orch_transform")|**Transformation**|Vous permet de mapper les champs des messages existants dans les nouveaux messages.|