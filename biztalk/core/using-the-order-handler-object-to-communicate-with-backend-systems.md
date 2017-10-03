---
title: "À l’aide de l’objet de gestionnaire de commande pour communiquer avec les systèmes back-end | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IOrderHandler interface
- process management solution tutorial, IOrderHandler interface
ms.assetid: b9fe4120-bf2a-4d15-a34b-6b98f026b984
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d7621c4e5737def0e9fc0682de709ae57f98790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-order-handler-object-to-communicate-with-backend-systems"></a>À l’aide de l’objet de gestionnaire de commande pour communiquer avec les systèmes principaux
La solution de gestion des processus d'entreprise peut communiquer de diverses manières avec le système de commande principal hérité, c'est-à-dire le système d'approvisionnement en câble qui reçoit les commandes finales. Afin de communiquer avec ce système d'approvisionnement, la solution tire parti des installations d'accès à distance .NET incluses dans Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)].  
  
 La solution fait appel à une technique courante qui consiste à utiliser une interface pour définir l'objet d'accès au système principal. En plaçant l'interface dans un assembly séparé, l'assembly client peut accéder à l'objet distant sans nécessairement devoir disposer d'un accès à l'assembly compilé.  
  
 Le **IOrderHandler** interface définit les méthodes pour communiquer avec le système de commande principal. Elle inclut des méthodes pour analyser, activer, annuler et terminer les commandes. Elle fournit également une méthode permettant d'identifier le type de service ; cette méthode est requise lors de l'annulation d'une commande.  
  
 Le **CableOrder1**, **CableOrder2**, et les orchestrations satellites utilisent le **OrderHandlerWrapper** objet qui implémente **IOrderHandler**. Le **OrderHandlerWrapper** objet, appelle à son tour, une instance distante d’un **OrderHandler** objet fourni par le **CableProvisioningSystemServer** exécutable. L'utilisation de l'objet de wrapper répond aux besoins de l'entreprise en matière d'utilisation de l'accès à distance .NET pour communiquer avec le système de commande principal tout en exploitant les fonctionnalités de nouvelles tentatives des composants de gestion des exceptions.  
  
 Étant donné qu’un doit être capable de sérialiser tous les objets référencés dans une orchestration, le **OrderHandlerWrapper** peuvent également être sérialisées. À l’aide de la **OrderHandlerWrapper** isole le code de sérialisation à partir d’orchestrations.  
  
 Si vous examinez le code, vous allez se qui le **OrderHandlerWrapper** objet implémente de manière explicite la **ISerializable** interface. L'objet doit gérer sa propre sérialisation, car il utilise un constructeur personnalisé.  
  
 La communication avec le système principal via l'accès à distance .NET est une méthode plus efficace que celle utilisant la messagerie. D'un autre côté, les orchestrations sont plus étroitement liées au système principal qu'elles ne le seraient avec une solution de messagerie pure. L'utilisation de l'accès à distance .NET empêche également la solution de tirer parti des fonctionnalités de BizTalk Server intégrées qui permettent d'effectuer de nouvelles tentatives de requêtes.  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [Logique du Gestionnaire de processus](../core/process-manager-logic.md)