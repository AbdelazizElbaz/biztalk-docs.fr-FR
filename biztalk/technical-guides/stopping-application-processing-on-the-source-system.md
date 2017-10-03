---
title: "L’arrêt d’Application de traitement sur le système Source | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cde5fc62-4bc2-4ef0-81bc-c7d39ff36cb6
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70fe980e3f29e2bd4cf13aa2b74a1923126fcec2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="stopping-application-processing-on-the-source-system"></a>L’arrêt d’Application de traitement sur le système Source
Traitement de l’application doit être arrêté lorsque la source de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime serveurs sont toujours en mesure de participer au traitement de document à l’aide de serveurs de base de données existants. Dans ce scénario, le traitement d’activité doit être arrêté afin qu’une opération de restauration de cohérence peut être effectuée.  
  
 Pour arrêter le traitement de l’application sur le système source, assurez-vous qu’aucune connexion n’est ouverte entre la production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs d’exécution et la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les ordinateurs qui hébergent le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Procédez comme suit pour arrêter le traitement de l’application sur la production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs d’exécution :  
  
1.  Désactiver tous les emplacements de réception sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs dans le groupe BizTalk. Prenez note de tous les recevoir des emplacements qui sont désactivées afin que ces emplacements de réception peuvent être réactivés ultérieurement. Cela arrêtera [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de traiter les messages entrants.  
  
2.  Arrêtez toutes les instances d’hôte de l’exécution sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs du groupe. Cela est possible à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Prenez note de toutes les instances d’hôte qui ont été arrêtés afin que ces instances d’hôte peuvent être redémarrées ultérieurement.  
  
3.  Arrêtez tous les [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] travaux de l’Agent liés aux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les ordinateurs qui hébergent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
  
4.  Si BAM est en cours d’utilisation, désactivez tous les packages BAM cube mise à jour et les données maintenance SSIS. Cela est possible à l’aide de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio.  
  
5.  Arrêt des Services d’analyse sur le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les ordinateurs qui hébergent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Cela est possible en arrêtant toutes les instances de MSSQLServerOLAPService sur le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateurs sur lesquels Analysis Services est installé.  
  
6.  Arrêter tous les autres [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services dans Gestionnaire des Services qui peuvent s’exécuter sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs dans le groupe, par exemple, l’entreprise unique Service d’authentification et le Service de mise à jour du moteur de règle. Prenez note des services qui sont arrêtés de façon à pouvoir être redémarrés plus tard.  
  
7.  Fermez toutes les applications qui se connectent à la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les ordinateurs qui hébergent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Cela inclut des instances de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, [!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)], et n’importe quel autre installé des applications BizTalk.  
  
8.  Vérifiez qu’il n’existe aucune activité de base de données générée par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Utilisez [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio pour voir quels processus sont connectés à la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les ordinateurs qui hébergent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Cela est possible en développant **gestion** en double-cliquant sur **moniteur d’activité** dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio. Puis sélectionnez **informations sur le processus**. Vous pouvez également utiliser les procédures stockées système **sp_who** ou **sp_who2** pour identifier toutes les connexions ouvertes à la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les ordinateurs qui hébergent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. S’il existe des processus connectés, les localiser et les terminer normalement ; ou en dernier recours, sur chaque processus dans le **informations sur le processus** volet [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio et cliquez sur **tuer un processus** pour mettre fin à la connexion.  
  
9. Traitement de la base de données supplémentaires pouvant survenir dans les bases de données application. Si ces bases de données seront restaurées, assurez-vous que tout le traitement s’est arrêté.  
  
## <a name="see-also"></a>Voir aussi  
 [Restauration du groupe BizTalk](../technical-guides/restoring-the-biztalk-group.md)