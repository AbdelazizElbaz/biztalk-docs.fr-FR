---
title: "Présentation de la Solution de gestion des processus métier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solutions, resources
- process management solutions, applications
- process management solution tutorial, background information
- process management solutions, about process management solutions
- applications, process management solutions
ms.assetid: fa6ad8d2-08d7-4770-9394-835f99bfd146
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9759f6521297377b204f0695a511de40d22a830d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understanding-the-business-process-management-solution"></a>Présentation de la solution de gestion des processus d'entreprise
La solution décrite dans cette section présente une manière d'implémenter une application de gestion des processus d'entreprise. Dans un gestionnaire de processus d'entreprise idéal, les parties de la solution représentant le processus d'entreprise (les règles d'entreprise communiquant avec des systèmes principaux spécifiques, envoyant des messages de réponse) sont séparées de l'infrastructure prenant en charge le processus.  
  
 Dans cette solution, un système de commande de service de câble pour Southridge Video, le processus d'entreprise est divisé en étapes. Un gestionnaire de commandes, qui ignore les règles d'entreprise et les systèmes principaux, dirige l'opération des étapes. Le gestionnaire de commandes reçoit des commandes d'un courtier de commandes qui peut diriger les commandes vers plusieurs gestionnaires de commandes différents.  
  
 La solution utilise pleinement les fonctions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et montre notamment l'utilisation de messages internes à l'application pour la coordination des parties de l'application.  
  
## <a name="reader-guidance"></a>Conseils à destination du lecteur  
 Ce document suppose que vous connaissez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Il suppose également que vous comprenez les concepts de base sur l’intégration d’applications d’entreprise et les services Web.  
  
 En outre, pour lire et suivre la documentation du développeur, vous devez être familiarisé avec la création d’applications à l’aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et effectuer les tâches suivantes : création de projets, références et le débogage et test BizTalk solutions.  
  
## <a name="ordering-cable-service-from-southridge-video"></a>Commande de service de câble de Southridge Video  
 La solution de gestion des processus d'entreprise implémente un système de commande de service de câble pour Southridge Video. Les clients appellent un centre où un agent du service clientèle prend la commande et l'entre dans le système de commande. Le diagramme suivant illustre le flux général d'une commande dans le système :  
  
 ![Flux de travail des solutions métier processus gestion](../core/media/business-process-manager-solution-work-flow.gif "Business_Process_Manager_Solution_Work_Flow")  
  
 Les commandes sont transmises au courtier de commandes, qui envoie la commande au gestionnaire de commandes. Le gestionnaire de commandes exécute les étapes de traitement dans l'ordre correct pour traiter la commande. Notez que certains types d'erreurs passent à un centre d'opérations pour correction et nouvel envoi et que la solution enregistre l'historique de chaque commande dans une table SQL Server.  
  
 Le diagramme suivant illustre les grandes lignes des étapes de traitement d'une commande.  
  
 ![La séquence de la Solution de gestion du processus métier](../core/media/business-process-manager-solution-sequence.gif "Business_Process_Manager_Solution_Sequence")  
  
 Notez qu'une commande peut être mise à jour et annulée.  
  
## <a name="business-requirements"></a>Impératifs de l'entreprise  
 La solution de gestion des processus d'entreprise est un exemple de système de commande pour Southridge Video, un fournisseur de service de câble. Elle illustre une manière d'implémenter le modèle de gestionnaire de processus dans Microsoft BizTalk Server. La solution utilise une orchestration pour gérer le flux des commandes via deux orchestrations satellites qui implémentent le processus d'entreprise. Cette structure provient des impératifs de l'entreprise de la solution qui incluent les éléments suivants :  
  
-   Contrôler les versions du processus d'entreprise  
  
-   Traiter les commandes à long terme  
  
-   Modifier ou annuler des commandes qui sont toujours en cours de traitement (compléter les commandes en vol)  
  
-   Éviter les commandes interrompues  
  
-   Suivre les commandes tout au long du processus  
  
-   Traiter des commandes par lot  
  
-   Accepter les commandes des centres de données à distance  
  
-   Permettre à différents groupes de gérer des parties du traitement de commande  
  
-   Faire évoluer l'application en ajoutant des groupes BizTalk  
  
-   Exposer, par l'accès à distance, le gestionnaire de commandes en tant que serveur d'applications  
  
 Les besoins de l’entreprise de Southridge vidéo produisent une structure en trois parties : un courtier de commandes, un gestionnaire de processus et l’activité traiter lui-même. Southridge Video a deux groupes informatiques distincts impliqués dans l'application. Un groupe de messagerie maintient l'infrastructure de messagerie d'entreprise et fournit les composants pour connecter les applications à cette infrastructure. Un autre groupe écrit et maintient les applications pour des processus d'entreprise spécifiques. Par conséquent, le courtier de commandes est séparé du gestionnaire de processus de commande et des étapes du processus afin qu'il puisse être maintenu par un groupe distinct. Comme il s'agit d'un composant séparé, le courtier de commandes peut également être étendu pour négocier les commandes destinées à plusieurs gestionnaires de processus. Un gestionnaire de processus peut être ajouté pour prendre en charge un nouveau secteur, tel qu'un service VIP.  
  
 Les commandes Southridge Video sont longs processus en cours d’exécution : une commande de câble peut prendre n’importe où à partir d’une minute et une année. Comme une instance d'une orchestration BizTalk doit être exécutée jusqu'à la fin, une instance d'orchestration peut avoir une durée de vie allant jusqu'à un an.  
  
 Southridge Video a besoin d'une architecture pour les processus à long terme qui permet la modification des composants d'application lors du traitement de commande. Par conséquent, Southridge divise le traitement de commande en plusieurs étapes afin qu'une commande puisse être effectuée à l'aide des composants de processus les plus récents. Pour plus d’informations sur la façon de déterminer les limites d’étape dans un processus d’entreprise, consultez [certains principes de conception dans la Solution de gestion des processus métier](../core/some-design-principles-in-the-business-process-management-solution.md).  
  
 Le long temps de traitement d'une commande détermine, en partie, le besoin de modifier les commandes en vol. La modification des commandes est l'une des raisons pour lesquelles la solution inclut un système extensif d'interruptions. Ce système d'interruptions simplifie la modification de commandes ou leur annulation avant qu'elles ne soient terminées. La solution utilise des messages .NET pour communiquer entre les parties fonctionnelles de la solution pour gérer les interruptions.  
  
 Le système ayant plusieurs dépendances externes, certaines opérations peuvent être tentées de nouveau après échec. Par exemple, si un système principal est indisponible et qu'une demande expire, la solution attend un intervalle approprié et retente la demande. Étant donné que les connexions aux systèmes externes sont effectuées via un code personnalisé, cette partie de la solution exploite pleinement la réflexion .NET pour permettre aux méthodes d'objet de faire l'objet d'une nouvelle tentative.  
  
 Comme l'entreprise réelle sur laquelle elle est basée, la solution suppose que des problèmes liés au traitement de commande peuvent être gérés par des membres du groupe d'opérations. De même, certains types d'erreurs liées aux commandes sont mentionnés à un agent du service clientèle qui peut annuler ou corriger et renvoyer la commande.  
  
## <a name="business-process-management-solution-resources"></a>Ressources de la solution de gestion des processus d'entreprise  
 Lisez les documents suivants pour plus d'informations sur la solution de gestion des processus d'entreprise.  
  
### <a name="business-process-management-solution-resources"></a>Ressources de la solution de gestion des processus d'entreprise  
  
-   [Développement d’une Solution de gestion des processus métiers](../core/developing-a-business-process-management-solution.md)  
  
     Les développeurs et les architectes de logiciel peuvent utiliser ce guide pour documenter tous les problèmes de conception de code, de modèles, d'architecture et de performances requis pour créer et exécuter l'application de gestion des processus d'entreprise.  
  
-   [Déploiement de la Solution gestion des processus d’entreprise](../core/deploying-the-business-process-management-solution.md)  
  
     L'informaticien ayant une compréhension générale de BizTalk Server peut utiliser ce guide pour créer et exécuter l'application de gestion des processus d'entreprise. Le guide suppose d'avoir une idée générale du fonctionnement de l'application dans un environnement distribué.  
  
## <a name="see-also"></a>Voir aussi  
 [Solution de gestion des processus métiers](../core/business-process-management-solution.md)