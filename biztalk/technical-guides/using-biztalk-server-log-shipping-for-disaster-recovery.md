---
title: "À l’aide des journaux de BizTalk Server pour la récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d65015c-de53-4590-b644-5c2f66f763db
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16f2cf9e1d8b717ff42536ef9c0dba79132b9663
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-biztalk-server-log-shipping-for-disaster-recovery"></a>À l’aide des journaux de BizTalk Server pour la récupération d’urgence
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]implémente des fonctionnalités en attente via l’utilisation de base de données de base de données des journaux. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]envoi de journaux automatise la sauvegarde et la restauration de base de données et les fichiers journaux, ce qui permet un serveur de secours reprendre le traitement de la base de données dans le cas où la défaillance du serveur de base de données de production.  
  
## <a name="how-log-shipping-works"></a>La copie des journaux fonctionne  
 Le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des travaux de l’Agent utilisés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l’envoi de journaux synchroniser les données entre le serveur source utilisé en production et le serveur de destination utilisé comme un serveur de secours toutes les 15 minutes par défaut (chaque fois que le travail de sauvegarde de BizTalk Server s’exécute).  
  
## <a name="using-log-shipping-for-disaster-recovery"></a>À l’aide des journaux de transaction pour la récupération d’urgence  
 Procédez comme suit lors de l’utilisation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des journaux de récupération d’urgence :  
  
-   Suivez les étapes décrites dans la rubrique [Checklist : Increasing Availability with la récupération d’urgence](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md) pour augmenter la disponibilité d’une production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement à l’aide de la récupération d’urgence.  
  
-   Vérifiez que les serveurs de récupération d’urgence ont la capacité de gérer la charge de production.  
  
     Assurez-vous que les serveurs de secours ont identiques ou similaires ressources disponibles (processeur, mémoire/disque) en tant que les serveurs de production.  
  
-   Assurez-vous que les spécificités de votre routine de récupération d’urgence sont bien documentées.  
  
     Documentez chaque étape de votre préparation de récupération d’urgence et de l’implémentation en détail. Reprise après sinistre rarement avertissements lorsqu’il est pratique on suppose que les parties responsables de l’implémentation de la procédure de récupération d’urgence démarrent leur premier jour de travail et s’effectuer cette action pour la première fois.  
  
-   Dans le cadre de régulière test, essai de basculement pour le site de récupération d’urgence, en particulier en tant que nouvelle BizTalk applications sont placées en production.  
  
     Effectuer un basculement de test en tant qu’une partie de test et la maintenance pour vous assurer qu’il peut être effectuée sans heurts régulière.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’urgence](../technical-guides/disaster-recovery.md)