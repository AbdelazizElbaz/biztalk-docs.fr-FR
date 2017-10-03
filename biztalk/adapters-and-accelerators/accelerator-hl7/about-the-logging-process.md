---
title: "Sur le processus d’enregistrement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logging, about logging
- auditing, about auditing
- logging
- auditing
ms.assetid: 859ee1f5-aae4-4a47-ab39-8d2b4168a429
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07dba617358d6ad451c53eeb75dbe5d1986f9066
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-the-logging-process"></a>Sur le processus d’enregistrement
Étant donné que vos applications gèrent critiques, données sensibles et monétaires heure, l’audit devient un élément essentiel de l’application. Pour activer la gestion de niveau entreprise et la disponibilité, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] s’appuie sur l’exécution partagée suivante et les composants d’administration :  
  
-   **Journalisation**: pour collecter et acheminer tous les événements du journal d’une manière managée pour une base de données désigné  
  
-   **Surveillance des événements et le débogage de Service**: pour configurer le comportement de journalisation et pour examiner et gérer les informations collectées pour les administrateurs système et autres professionnels de l’informatique  
  
 Fonctionnalités d’audit avec le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)], vous pouvez optimiser l’efficacité opérationnelle, de sécurité et de performances pour assurer la conformité aux réglementations de HL7.  
  
## <a name="types-of-data"></a>Types de données  
 Cette rubrique décrit les différents types de données de journalisation utilisées par la fonctionnalité de journalisation et où ces données sont stockées :  
  
-   Données de configuration : enregistrement de données de configuration sont stockée dans la base de données de Configuration (également appelée la base de données BizTalk Management) et inclut des informations et audit des données d’audit de SQL ([!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)] Observateur d’événements, la base de données centralisée WMI) emplacement.  
  
-   Données d’archivage : table du journal des événements dans le journal SQL stocke les données de « Enregistrement ».  
  
## <a name="how-logging-works"></a>Fonctionne de la journalisation  
 Cette rubrique décrit les trois types d’événements se connecte le logiciel, ainsi que les trois emplacements où vous pouvez stocker les données enregistrées.  
  
|Composant|Fonction|  
|---------------|-------------|  
|Éditeur de configuration|Pour spécifier l’emplacement où enregistrer les données du journal. BTAHL7 prend en charge la journalisation dans n’importe quelle combinaison des éléments suivants : journalisation de l’Observateur d’événements, WMI et SQL Server.|  
|Événement Broker|Pour recevoir le journal des événements déclenchés par d’autres composants et ouvrir une session en fonction des données de configuration de journalisation.|  
|API de journalisation|Journalisation de l’interface appelée par tous les assemblys de BTAHL7.|  
  
### <a name="types-of-logging"></a>Types de journalisation  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]enregistre les trois types d’erreurs :  
  
-   Événements d’information, d’un service démarré ou arrêté ou d’un événement a échoué.  
  
-   Événements d’avertissement tels que des erreurs non critiques et avertissements dans [!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)] des journaux des événements. Par exemple, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] suspend un message, car la validation des données a échoué.  
  
-   Événements d’erreur pour les défaillances critiques dans un composant. Par exemple, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] suspend un message en raison d’échecs de l’analyseur.  
  
 Le système peut se connecter [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] des événements dans des emplacements configurables suivants :  
  
-   [!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)]Observateur d’événements  
  
-   Événements WMI  
  
-   Base de données centralisée (base de données de journalisation SQL)  
  
 Un broker d’événements reçoit tous les [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] journalisation des événements et, selon les informations de configuration, les envoie à l’emplacement approprié.  
  
### <a name="overview-of-features"></a>Vue d’ensemble des fonctionnalités  
 Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] fournit des fonctionnalités de journalisation :  
  
-   Un procédé unifié de la journalisation de tous les messages d’erreur  
  
-   Un référentiel centralisé pour stocker tous les détails de l’événement  
  
-   Un modèle objet cohérent pour les messages de journalisation à circuler vers les applications métier-discrètes  
  
-   Une combinaison de journalisation et de traçage à mettre en corrélation les administrateurs de système d’aide a enregistré des erreurs avec des documents  
  
## <a name="event-log-data"></a>Données de journal des événements  
 Cette rubrique décrit le format et le contenu des données du journal des événements.  
  
 Le tableau suivant présente les données enregistrées par défaut pour les partenaires.  
  
|data| Description|  
|----------|-----------------|  
|Transactionsrestauration|Enregistrement des données|  
|Numéro_catégorie|Numéro de catégorie|  
|EntryType|Type de l'événement|  
|ID d’événement|ID d'événement|  
|MachineName|Nom d'ordinateur|  
|Message|Détails du message|  
|Source|Création, mise à jour, lors de la lecture, suppression, le déploiement ou l’archivage des données|  
|TimeGenerated|Réussite ou l’échec|  
|UserName|Nom d'utilisateur|  
|MsgGuid|GUID du message|  
|SvcGuid|GUID du service|  
|Opération|Détail de l’opération|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de la journalisation](../../adapters-and-accelerators/accelerator-hl7/configuring-logging.md)