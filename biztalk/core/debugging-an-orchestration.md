---
title: "Débogage d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging, Orchestration Debugger
- debugging, orchestrations
- Orchestration Debugger, about Orchestration Debugger
- Orchestrations Debugger
- orchestrations, debugging
- debugging, HAT
- HAT, debugging
ms.assetid: aae99cfd-d3dd-41c8-ae7a-b2733352cd69
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c231513ad75520fcadd88e5dd7d88104ddeeced5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="debugging-an-orchestration"></a>Débogage d'une orchestration
Le débogueur de l'orchestration permet de suivre l'activité d'une seule instance de l'orchestration pour chaque forme. Il présente un rendu de l'orchestration créée dans le Concepteur d'orchestration.  
  
 Vous accédez au débogueur orchestration dans la page Présentation du groupe de la console Administration de BizTalk Server.  Pour ce faire, utilisez la sortie d'une requête de suivi au travers d'un menu contextuel accessible en cliquant avec le bouton droit sur une instance de message ou de service associée à un type d'orchestration. Une fois dans cette page, vous avez la possibilité de basculer entre l'affichage Flux message et le débogueur orchestration.  
  
 Le débogueur de l'orchestration permet d'effectuer les opérations suivantes :  
  
-   afficher un rendu de l'orchestration dans lequel vous pouvez revoir chaque étape du traitement de cette orchestration ;  
  
-   définir des points d'arrêt avant n'importe quelle forme de l'orchestration et continuer l'exécution ;  
  
-   consulter des données de message et des variables spécifiques ;  
  
-   activer automatiquement toutes les options de suivi pour une instance d'orchestration particulière quand cette dernière est ouverte dans le débogueur de l'orchestration ;  
  
-   continuer, reprendre en mode de débogage et terminer une instance d'orchestration particulière.  
  
    > [!NOTE]
    >  Quand vous annulez le déploiement d'un assembly, la base de données conserve les options de suivi et les informations sur les points d'arrêt pour cet assembly. Si, par la suite, vous déployez le même assembly, ces options de suivi et ces informations de points d'arrêt sont restaurées.  
  
 Les deux modes disponibles lors de l'utilisation du débogueur de l'orchestration sont les suivants :  
  
-   [Mode de création de rapports dans le débogueur de l’Orchestration](../core/reporting-mode-in-orchestration-debugger.md)  
  
-   [Mode interactif dans le débogueur de l’Orchestration](../core/interactive-mode-in-orchestration-debugger.md)  
  
 Les fonctionnalités varient selon l'état du service. Vous pouvez effectuer un débogage interactif en appelant une instance de service dont l'état est Point d'arrêt, à partir de n'importe quelle vue. Pour plus d’informations sur le débogage d’une orchestration, consultez [comment appeler le débogueur d’Orchestration et les vues de flux de Message](../core/how-to-invoke-the-orchestration-debugger-and-the-message-flow-views.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Interface utilisateur du débogueur d’orchestration](../core/orchestration-debugger-user-interface.md)  
  
-   [Considérations sur l’utilisation du débogueur de l’Orchestration](../core/considerations-when-using-orchestration-debugger.md)  
  
-   [Utilisation de la vue débogueur Orchestration](../core/working-with-the-orchestration-debugger-view.md)