---
title: "Interface utilisateur du débogueur orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.hat.orchdebugger
helpviewer_keywords:
- Orchestration Debugger, debug mode
- Orchestration Debugger, Interactive mode
ms.assetid: ca18f1e2-63b7-4177-82ba-4accc3369a2a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4663a642ffc960d969c994b5471d866a80fde828
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-debugger-user-interface"></a>Interface utilisateur du débogueur de l'orchestration
En mode interactif (débogage), la vue débogueur Orchestration contient trois zones : volet, volet événements suivis et le volet Orchestration de Service. En bas de la vue, figurent également la liste des variables et les propriétés des variables.  
  
> [!NOTE]
>  Le débogueur d’Orchestration ne peut pas afficher l’état réel du service, sauf s’il apparaît dans **point d’arrêt** mode et que vous l’ayez joint à l’instance.  
  
## <a name="service-pane-in-orchestration-debugger"></a>Volet Service du débogueur de l'orchestration  
 Le volet supérieur de la fenêtre du débogueur de l'orchestration comporte les informations suivantes :  
  
|Balise|Détail|  
|---------|------------|  
|Nom|Indique la vue active (Débogueur orchestration) et vous permet d'accéder à la vue Flux message.|  
|Détails de l'instance|Indique le nom du service et le GUID qui identifie de manière unique l'instance d'orchestration active.|  
|Modes|Mode de débogage (recommencer/activé), état de l'orchestration (Démarré, Suspendu, Réussi, etc.), mode Joint (Oui ou Non) et Mode du point d'arrêt (Sur la classe ou Sur l'instance).|  
|Options du service|Liste déroulante d'actions que vous pouvez effectuer en fonction de l'état du débogueur et de l'instance.|  
  
 Sous ces informations, le débogueur de l'orchestration présente deux volets, Événements suivis à gauche et Orchestration à droite.  
  
## <a name="tracked-events-pane-in-orchestration-debugger"></a>Volet Événements suivis du débogueur de l'orchestration  
 Le volet Événements suivis répertorie les états des actions exécutées dans l'orchestration et indique, par exemple, si une action a démarré ou est terminée. Lorsque vous sélectionnez une ligne de ce volet, la forme correspondante dans le volet Orchestration s'affiche en surbrillance, en vert quand la forme démarre et en bleu quand elle se termine.  
  
 Le volet Événements suivis contient les colonnes suivantes :  
  
|Option|Action|  
|------------|------------|  
|État de l'action (colonne de gauche)|État de l'action choisie. Une flèche indique que l'action a démarré et une forme de fin indique qu'elle est terminée.|  
|Nom de l'action|Nom désignant l'action dans l'orchestration.|  
|Type d’action|Type de forme représentant l'action. Une flèche indique que l’action a démarré et une forme de fin indique qu’elle soit terminée.|  
|Time|Heure à laquelle l'action a été exécutée.|  
|Date|Date à laquelle l'action a été exécutée.|  
  
## <a name="orchestration-pane-in-orchestration-debugger"></a>Volet Orchestration du débogueur de l'orchestration  
 Dans la page Hub du groupe, le volet Orchestration de la fenêtre du résultat de suivi des événements de messages et d'instances de suivi correspond à la zone dans laquelle l'instance d'orchestration affiche toutes ses formes. Le tableau suivant répertorie les actions du menu Contexte pour le volet Orchestration.  
  
|Option|Action|  
|------------|------------|  
|Définir le point d'arrêt sur la classe|Cliquez sur une forme pour la **définir un point d’arrêt sur la classe** option. Un point rouge apparaît sur la forme, indiquant que le point d'arrêt a été défini.|  
|Définir le point d'arrêt sur l'instance|Cliquez sur une forme pour la **définir un point d’arrêt sur l’Instance** option. Un point rouge apparaît sur la forme, indiquant que le point d'arrêt a été défini.|  
|Supprimer le point d'arrêt de la classe|Cliquez sur une forme pour la **supprimer un point d’arrêt** option. Le point rouge disparaît de la forme, indiquant que le point d'arrêt a été supprimé.|  
|Supprimer le point d'arrêt sur l'instance|Cliquez sur une forme pour la **définir un point d’arrêt sur l’Instance** option. Le point rouge disparaît de la forme, indiquant que le point d'arrêt a été supprimé.|  
  
### <a name="variable-list-and-variable-properties-panes"></a>Volets Liste des variables et Propriétés de la variable  
 Ces volets apparaissent uniquement pour le débogage interactif lorsqu’il est attaché à l’exécution d’Orchestration à l’aide du **attacher** option de service. Ils sont situés en bas de l'écran.  
  
 Le volet Liste des variables présente le nom, la valeur et le type de la variable. L'entrée Valeur indique s'il s'agit ou non d'une variable Null et, si elle n'est pas Null, quel type d'objet elle contient. Le type est le **assembly.EspaceNoms.nom** de l’objet.  
  
 Le volet Propriétés de la variable comporte différentes propriétés qui varient selon le type de l'objet. Par exemple, lorsqu'il s'agit d'un port, cette zone indique l'adresse, le nom, l'étendue, le type et la valeur du port. Lorsqu'il s'agit de messages, le raccourci est affiché ; chacune des parties d'un message comporte un nom, une taille, des propriétés, un type et une valeur. Les regroupements, tels que le contexte et les propriétés, apparaissent dans une fenêtre contextuelle. Un affichage partiel de la valeur apparaît sous forme d'info-bulle.  
  
 L'utilisateur avance dans la planification de point d'arrêt en point d'arrêt et examine l'état des variables.  
  
 Le tableau ci-dessous présente les actions du menu Contexte sur la liste des variables.  
  
|Option|Action|  
|------------|------------|  
|Enregistrer le message|Cliquez sur un Message qui n’est pas null dans le volet de la liste de variables pour le **enregistrer le Message** option. Un message apparaît, vous invitant à sélectionner le répertoire dans lequel enregistrer le message.|  
  
### <a name="service-options-drop-down-list"></a>Liste déroulante Options du service  
 La liste Options du service répertorie les actions valides, selon l'état de l'instance et du débogueur. Le tableau ci-dessous présente les différentes actions disponibles dans cette liste.  
  
|Option|Action|  
|------------|------------|  
|Continuer les services|Continue une instance de l'orchestration qui s'est arrêtée à un point d'arrêt si vous avez joint le service.|  
|Reprendre en mode de débogage|Reprend une instance de l'orchestration suspendue en mode de débogage. Cette action vous permet de passer au mode interactif, de joindre l'instance et de la déboguer de façon interactive.<br /><br /> Cette option est disponible à partir des vues Opérations et du débogueur de l'orchestration. Elle s'applique uniquement aux orchestrations.|  
|Terminer le service|Termine une instance de l'orchestration.|  
|Attacher|Joint le service à l'instance de l'orchestration et récupère l'état actuel et les variables.|  
|Supprimer tous les points d'arrêt de la classe|Supprime tous les points d'arrêt de la classe d'orchestration. Option disponible uniquement si le service n'est pas joint.|  
|Supprimer les points d’arrêt|Supprime tous les points d'arrêt de l'instance de l'orchestration. Option disponible uniquement si le service est joint.|  
|Enregistrer tous les messages|Enregistre tous les messages associés à l'instance de l'orchestration, à condition que vous ayez sélectionné le suivi de tous les messages entrants/sortants.|  
|Afficher action au point d'arrêt|Met en surbrillance (en jaune) la forme de la dernière action exécutée avant le point d'arrêt.|  
|Afficher orchestration d'appel|Renvoie la vue à l'instance de l'orchestration qui a effectué l'appel. Revient à l'orchestration parente.<br /><br /> Option disponible uniquement pour les instances d'orchestration appelées.|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Mode de création de rapports dans le débogueur de l’Orchestration](../core/reporting-mode-in-orchestration-debugger.md)  
  
-   [Mode interactif dans le débogueur de l’Orchestration](../core/interactive-mode-in-orchestration-debugger.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’une Orchestration](../core/debugging-an-orchestration.md)