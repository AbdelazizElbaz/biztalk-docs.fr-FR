---
title: Analyse des Applications | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4be98ba2-6acd-4dee-b6ea-db71bbd368f0
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67c937ae0edb1698991ad111622a582ebfc64d76
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="monitoring-applications"></a>Analyse des Applications
Configuration de Microsoft System Center Operations Manager pour surveiller BizTalk applications généralement peuvent être réparties dans un processus en quatre étapes progressif comme suit :  
  
1.  **Modifier les règles existantes et/ou les règles de copie pour un pack d’administration personnalisé pour analyser une application BizTalk personnalisée**  
  
     Vous devrez copier beaucoup de ces règles plusieurs fois. C’est le cas si vous surveillez un nombre de partages de fichiers, par exemple. Dans ce scénario, vous voulez copier la règle de base une fois pour chaque partage de fichiers avec l’adresse du partage de fichier ajouté dans le champ de description sur le **critères** onglet de la règle. En ajoutant l’adresse, Operations Manager génère une alerte pour chaque partage de fichiers individuels. Lorsque vous copiez une règle existante, vérifiez que vous sélectionnez **activer** règle-désactiver les remplacements pour cette règle ou vous recevrez des alertes en double.  
  
     Un autre élément que vous devez ajouter à chaque règle que vous créez est la base de connaissances sur le **Base de connaissances** onglet de la propriété de règle. Ces données sont attachées à la notification est déclenchée lorsque Operations Manager envoie une alerte. La puissance de cette fonctionnalité devient évident lorsque vous incluez des étapes qui peuvent aider à résoudre l’erreur.  
  
2.  **Créer des actions pour chaque règle définie**  
  
     Création ou copie d’une règle est réellement la première étape dans le processus. L’étape suivante consiste à effectuer une opération basée sur cette règle. S’il existe aucune action ne basé sur une règle puis pas très important que l’événement a été déjà analysée. L’action effectuée plus fréquemment consiste à avertir un opérateur ou l’administrateur une erreur s’est produite. Operations Manager fournit également un nombre d’autres actions peut être utilisé lorsqu’un événement est déclenché. Ces actions incluent :  
  
    -   À partir d’un script  
  
    -   Envoi d’une interruption SNMP Simple Network Management Protocol () (dans SNMP, les agents analysent l’activité dans les différents appareils sur le réseau et d’un rapport à la console réseau)  
  
    -   Envoi d’une notification à un groupe de Notification  
  
    -   L’exécution d’un fichier de commandes  
  
    -   Mise à jour d’une variable d’état  
  
    -   Transfert d’un fichier  
  
    -   Appel d’une méthode sur un assembly de code managé  
  
3.  **Créer un processus itératif pour automatiser les tâches manuelles**  
  
     L’étape suivante est un processus itératif et dépasse le mécanisme d’alerte de base. Avec Operations Manager est en mesure d’appeler le script et le code .NET, le processus d’automatisation des tâches manuelles basés sur les événements déclenchés est une fonctionnalité de l’enregistrement puissante et le temps. Un exemple est d’exécuter un script pour démarrer automatiquement un port, si un message d’événement désactivé / arrêté est connecté. Ce processus est itératif, car de nombreux processus peuvent être automatisées.  
  
4.  **Utilisez les règles de seuil pour automatiser des tâches manuelles**  
  
     L’étape suivante de traitement consiste à déplacer au-delà de la génération d’alertes réactive et d’utiliser des règles de seuil. Le Pack d’administration de BizTalk Server ne contient pas toutes les règles de seuil par défaut. Il s’agit, car ces règles sont généralement spécifiques à l’application personnalisée et sont différents pour chaque application. Un seuil représente une règle d’entreprise concernant l’application personnalisée et fournit un moyen proactive de surveillance d’un système. Vous pouvez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournis avec l’outil performances analyse des journaux (PAL) pour définir des règles de modèles de seuil.  
  
     Un exemple d’une règle de seuil de ce type consiste à mesurer les lorsque les processeurs sur un serveur exécuté constamment supérieure à 75 % pour une période spécifique. Cela peut indiquer que vous devez faire évoluer le système. Encore un autre exemple est lorsque vous créez une règle de seuil qui analyse un ensemble unique de compteurs. Cette règle peut ensuite appeler le code pour initialiser les instances d’hôte BizTalk sur un serveur de sauvegarde précédemment configuré pendant les périodes de forte demande.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de BizTalk Server avec System Center Operations Manager 2007](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)