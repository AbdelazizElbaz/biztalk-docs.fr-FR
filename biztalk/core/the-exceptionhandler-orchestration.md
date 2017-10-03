---
title: Cette Orchestration | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, systems
- errors, applications
- applications, errors
- orchestrations, errors [process management solutions]
- process management solution tutorial, errors
ms.assetid: ac154e76-9dfe-433a-948b-e098df705fe5
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1b79a1c6d9e6fada206ba0298913fe8f369783c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-exceptionhandler-orchestration"></a>Orchestration ExceptionHandler
La solution de gestion des processus d'entreprise utilise deux types d'exceptions : les exceptions de système et les exceptions d'application. Les exceptions de système incluent des erreurs de ressource, telles qu'un échec de connexion réseau. Il se peut qu'un tel problème puisse se résoudre de lui-même après un intervalle afin que la solution tente à nouveau toutes les opérations qui produisent des exceptions de système. Les exceptions d'application sont produites par des problèmes moins susceptibles de se résoudre d'eux-mêmes, tels que des erreurs logiques ou une certaine forme d'incohérence. La solution utilise le **ExceptionHandlerOrch** orchestration pour traiter les erreurs système et application.  
  
 Étapes de traitement des commandes (**CableOrder1**, **CableOrder2**) et leurs orchestrations satellites (**activer**, **analyser**,  **Annuler**, **modification**, **Complete**, **Validate**) utilisent tous **ExceptionHandlerOrch**.  
  
> [!NOTE]
>  Vous pouvez souhaiter lire cette section avec les **ExceptionHandlerOrch** orchestration ouverte dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## <a name="application-errors"></a>Erreurs d'application  
 Le Gestionnaire d’exceptions connecte d’abord l’erreur en appelant le **PostError** méthode de la **ErrorHandler** de l’objet dans le **utilitaires** assembly. Le gestionnaire d'exceptions vérifie ensuite si l'erreur était une erreur système ou d'application. La capture d'écran suivante montre la branche d'orchestration qui traite les exceptions d'application :  
  
 ![Branche d’application de l’orchestration Exceptionhandler](../core/media/applicationerrorbranchofexceptionhandler.gif "ApplicationErrorBranchofExceptionHandler")  
  
 Pour une erreur d’application, l’orchestration construit une chaîne décrivant l’erreur et appelle le **ErrorHandlerOrch** orchestration. Cette orchestration envoie l'erreur aux opérations où un opérateur décide de réparer l'erreur ou de terminer l'opération. Si l'opérateur répare l'erreur, le message réparé revient de l'orchestration ErrorHandlerOrch et l'opération est tentée à nouveau. Le Gestionnaire d’exceptions pour cela, en appelant le **Invoke** méthode de la **Recaller** de l’objet dans le **utilitaires** assembly. Le **Recaller** objet utilise la réflexion pour appeler le code qui a provoqué l’erreur.  
  
 Si l’appel à **Invoke** réussit, la fermeture de gestionnaire de l’exception. Sinon, il exécute une boucle et tente de l’appel à **Invoke** à nouveau. Pour plus d’informations sur la **Recaller** d’objets, consultez [l’objet Recaller](../core/the-recaller-object.md).  
  
## <a name="system-errors"></a>Erreurs système  
 Le diagramme suivant illustre la branche d’erreur de système de la **ExceptionHandler** orchestration :  
  
 ![Erreur du système de l’Orchestration ExceptionHandler](../core/media/systemerrorbranchofexceptionhandler.gif "SystemErrorBranchofExceptionHandler")  
  
 Une erreur système, le Gestionnaire d’exceptions appelle d’abord la **CheckInterrupt** orchestration, puis attend une minute. Cette attente permet aux erreurs temporaires, à court terme, telles que des problèmes de connexion réseau, de se résoudre avant une nouvelle tentative. Lors d'appels distants, le risque d'un problème réseau existe toujours.  
  
> [!NOTE]
>  Dans une conception pouvant être interrompue, en règle générale, vous voulez vérifier l'existence d'une interruption pendant ou immédiatement après une période d'attente afin de voir si une interruption a eu lieu.  
  
 Après le délai d’attente, le Gestionnaire utilise la **Invoke** méthode de la **Recaller** objet pour exécuter le code d’origine. Si l'appel aboutit, le gestionnaire se ferme. Dans le cas contraire, le gestionnaire essaie à deux nouvelles reprises d'exécuter le code d'origine. Si les trois tentatives échouent, le gestionnaire construit une chaîne d’erreur et appelle le **ErrorHandlerOrch** orchestration.  
  
 Si le traitement d'une exception de système provoque une exception, le bloc d'exception l'intercepte :  
  
 ![Gestionnaire d’exceptions pour la branche d’erreurs système](../core/media/exceptionhandlerofsystemerrorbranch.gif "ExceptionHandlerofSystemErrorBranch")  
  
 Le gestionnaire d'exceptions teste le type d'exception et décrémente le compte de tentatives s'il s'agit d'une exception de système ou définit un indicateur pour spécifier une exception d'application.  
  
## <a name="the-errorhandlerorch-orchestration"></a>Orchestration ErrorHandlerOrch  
 Le diagramme suivant illustre la première partie de la **ErrorHandlerOrch** orchestration :  
  
 ![Orchestration de gestionnaire d’erreurs, première partie](../core/media/errorhandlerfirstpart.gif "ErrorHandlerFirstPart")  
  
 Le **ErrorHandlerOrch** orchestration premiers tests les **IsBadOrder** paramètre pour voir si l’erreur est une commande incorrecte (**IsBadOrder** a la valeur true) ou une autre erreur. Si l'erreur est une commande incorrecte, elle attribue la destination du message à partir de l'adresse de l'expéditeur de la commande d'origine et renvoie le message au système de service client. Si l'erreur n'est pas une commande incorrecte, l'orchestration crée un message d'erreur de commande et l'envoie au système d'opérations.  
  
 Après chaque erreur, l'orchestration écoute un message de réponse ou un message d'interruption :  
  
 ![ErrorHandler, deuxième partie](../core/media/errorhandlersecondpart.gif "ErrorHandlerSecondPart")  
  
 Si l'orchestration reçoit une réponse, elle la renvoie à l'appelant. Si l’orchestration reçoit un message d’interruption, il transmet le message à un port d’interruption et lève une personnalisée **InterruptException**.  
  
 Pour plus d’informations sur la façon dont la solution utilise et gère les interruptions, consultez [d’interruption de la gestion dans la Solution de gestion des processus métier](../core/interrupt-handling-in-the-business-process-management-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions dans la Solution gestion des processus d’entreprise](../core/exception-handling-in-the-business-process-management-solution.md)   
 [Exceptions personnalisées](../core/custom-exceptions.md)   
 [Gestion des interruptions dans la Solution gestion des processus d’entreprise](../core/interrupt-handling-in-the-business-process-management-solution.md)   
 [Objet Recaller](../core/the-recaller-object.md)